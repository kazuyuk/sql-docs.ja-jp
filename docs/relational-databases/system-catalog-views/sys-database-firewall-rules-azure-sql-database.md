---
title: sys.database_firewall_rules (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ea5b9d5cb50740e349aa6d3cf58bd20f620a8ab6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038330"
---
# <a name="sysdatabasefirewallrules-azure-sql-database"></a>sys.database_firewall_rules (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  関連付けられたデータベース レベルのファイアウォール設定に関する情報を返します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。 データベース レベルのファイアウォールの設定は、包含データベース ユーザーを使用する場合に特に役立ちます。 詳細については、「 [包含データベース ユーザー - データベースの可搬性を確保する](../../relational-databases/security/contained-database-users-making-your-database-portable.md)」を参照してください。  
  
 `sys.database_firewall_rules`ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**INTEGER**|データベース レベルのファイアウォール設定の識別子。|  
|NAME|**NVARCHAR (128)**|データベース レベルのファイアウォール設定を説明し、区別するために選択した名前。|  
|start_ip_address|**VARCHAR (50)**|データベース レベルのファイアウォール設定の範囲において最も小さい IP アドレス。 これ以上の IP アドレスは、[!INCLUDE[ssSDS](../../includes/sssds-md.md)] インスタンスへの接続を試みることができます。 最下位の IP アドレスは`0.0.0.0`します。|  
|end_ip_address|**VARCHAR (50)**|データベース レベルのファイアウォール設定の範囲において最も大きい IP アドレス。 IP アドレス以下への接続にこれを試みる、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]インスタンス。 最上位の IP アドレスは`255.255.255.255`します。<br /><br /> 注: Windows Azure の接続試行が許可されますこの両方のフィールドと**start_ip_address** equals をフィールド`0.0.0.0`します。|  
|create_date|**DATETIME**|データベース レベルのファイアウォール設定が作成された UTC 日時。|  
|modify_date|**DATETIME**|データベース レベルのファイアウォール設定が最後に変更された UTC 日時。|  
  
## <a name="remarks"></a>コメント  
 データベースのファイアウォール規則を削除する使用[sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)します。 すべてのファイアウォール規則を設定する[!INCLUDE[ssSDS](../../includes/sssds-md.md)]を参照してください[sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)します。 ファイアウォール規則を既存のデータベースに関する情報を返すクエリ[sys.database_firewall_rules (Azure SQL データベース)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 このビューで使用できる、**マスター**データベースと、各ユーザー データベース。 このビューに読み取り専用のアクセスは、データベースに接続するアクセス許可を持つすべてのユーザーに使用できます。  
  
## <a name="see-also"></a>参照  
 [sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules (Azure SQL データベース)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [データベース エンジン アクセス用の Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [FILESTREAM アクセスに対するファイアウォールを構成します。](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
