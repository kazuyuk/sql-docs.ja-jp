---
title: sys.database_service_objectives (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2016
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- エラスティック プール
- エラスティック プールの管理
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 320d8d0dd434c4453a8004a0237bc9d2cbd9f352
ms.sourcegitcommit: 84cc5ed00833279da3adbde9cb6133a4e788ed3f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39216973"
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>sys.database_service_objectives (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Azure SQL database または Azure SQL Data Warehouse に存在する場合は、edition (サービス層)、サービスの目標 (価格レベル) およびエラスティック プールの名前を返します。 Azure SQL Database サーバーの master データベースにログオンした場合は、すべてのデータベースに関する情報を返します。 Azure SQL Data Warehouse では、には、master データベースに接続する必要があります。  
  
  
 価格については、次を参照してください。 [SQL Database のオプションとパフォーマンス: SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database/)と[SQL Data Warehouse の価格](https://azure.microsoft.com/pricing/details/sql-data-warehouse/)します。  
  
 サービスの設定を変更するを参照してください。 [ALTER DATABASE (Azure SQL データベース)](../../t-sql/statements/alter-database-azure-sql-database.md)と[ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md)します。  
  
 Sys.database_service_objectives ビューには、次の列が含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|ssNoversion|Azure SQL Database サーバーのインスタンス内で一意で、データベースの ID。 結合可能な[sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)します。|  
|のエディション|sysname|データベースまたはデータ ウェアハウス用のサービス層:**基本的な**、**標準**、 **Premium**または**Data Warehouse**します。|  
|service_objective|sysname|データベースの価格レベルです。 データベースがエラスティック プール内にある場合は、返す**ElasticPool**します。<br /><br /> **基本的な**階層を返します**基本的な**します。<br /><br /> **Standard サービス レベル内の単一データベース**次のいずれかを返します: S0、S1、S2、S3、S4、S6、S7、S9 または S12 します。<br /><br /> **Premium レベルで 1 つのデータベース**次を返します: P1、P2、P4、P6、P11 または P15 します。<br /><br /> **SQL Data Warehouse** DW10000c を通じて DW100 を返します。|  
|elastic_pool_name|sysname|名前、[エラスティック プール](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)データベースが属しています。 返します**NULL**データベースが 1 つのデータベースまたはデータ warehoue 場合。|  
  
## <a name="permissions"></a>アクセス許可  
 必要があります**dbManager** master データベースに対する権限。  データベース レベルでは、ユーザーは、作成者または所有者である必要があります。  
  
## <a name="examples"></a>使用例  
 この例は、master データベースで、またはユーザー データベースで実行できます。 クエリでは、名前、サービス、およびデータベースのパフォーマンス レベルの情報を返します。  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
