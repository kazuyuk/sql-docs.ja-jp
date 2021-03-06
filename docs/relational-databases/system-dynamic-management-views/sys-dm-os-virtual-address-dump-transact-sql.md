---
title: sys.dm_os_virtual_address_dump (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_virtual_address_dump
- sys.dm_os_virtual_address_dump_TSQL
- sys.dm_os_virtual_address_dump
- dm_os_virtual_address_dump_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_virtual_address_dump dynamic management view
ms.assetid: 7b24ea55-3873-42fd-a86c-441c92eb6175
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 49513c26f240cf9b46e201f29481a84890576064
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562116"
---
# <a name="sysdmosvirtualaddressdump-transact-sql"></a>sys.dm_os_virtual_address_dump (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  呼び出しプロセスの仮想アドレス空間におけるページ範囲の情報を返します。  
  
> [!NOTE]  
>  この情報がによって返されることも、 **VirtualQuery** Windows API。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_virtual_address_dump**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**region_base_address**|**varbinary(8)**|ページ領域の基本アドレスへのポインター。 NULL 値は許可されません。|  
|**region_allocation_base_address**|**varbinary(8)**|VirtualAlloc Windows API 関数により割り当てられるページ範囲の基本アドレスへのポインター。 BaseAddress メンバーによりポイントされるページは、この割り当て範囲内に含まれます。 NULL 値は許可されません。|  
|**region_allocation_protection**|**varbinary(8)**|領域が最初に割り当てられたときの保護属性。 値は次のいずれかになります。<br /><br /> -   PAGE_READONLY<br />-   PAGE_READWRITE<br />-です。<br />-PAGE_WRITECOPY<br />-   PAGE_EXECUTE<br />-   PAGE_EXECUTE_READ<br />-   PAGE_EXECUTE_READWRITE<br />-   PAGE_EXECUTE_WRITECOPY<br />-PAGE_GUARD<br />-PAGE_NOCACHE<br /><br /> NULL 値は許可されません。|  
|**region_size_in_bytes**|**bigint**|領域サイズ (バイト単位)。すべてのページが同じ属性となる基本アドレスから始まります。 NULL 値は許可されません。|  
|**region_state**|**varbinary(8)**|領域の現在の状態。 これは、次のいずれかです。<br /><br /> -   MEM_COMMIT<br />-   MEM_RESERVE<br />-   MEM_FREE<br /><br /> NULL 値は許可されません。|  
|**region_current_protection**|**varbinary(8)**|保護属性。 値は次のいずれかになります。<br /><br /> -   PAGE_READONLY<br />-   PAGE_READWRITE<br />-です。<br />-PAGE_WRITECOPY<br />-   PAGE_EXECUTE<br />-   PAGE_EXECUTE_READ<br />-   PAGE_EXECUTE_READWRITE<br />-   PAGE_EXECUTE_WRITECOPY<br />-PAGE_GUARD<br />-PAGE_NOCACHE<br /><br /> NULL 値は許可されません。|  
|**region_type**|**varbinary(8)**|領域内のページの種類。 値は、次のいずれかです。<br /><br /> -   MEM_PRIVATE<br />-MEM_MAPPED<br />-   MEM_IMAGE<br /><br /> NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


