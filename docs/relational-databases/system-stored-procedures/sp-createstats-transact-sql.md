---
title: sp_createstats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_createstats_TSQL
- sp_createstats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_createstats
ms.assetid: 8204f6f2-5704-40a7-8d51-43fc832eeb54
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 75e05e36dfea3a36fa01d08ca79b22c3abb7e2c4
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555162"
---
# <a name="spcreatestats-transact-sql"></a>sp_createstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  呼び出し、 [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)単一列統計を統計オブジェクトの最初の列にはない列を作成するステートメント。 統計を 1 列ずつ作成すると、ヒストグラムの数が増えて、カーディナリティの推定、クエリ プラン、およびクエリのパフォーマンスが向上します。 統計オブジェクトの最初の列にはヒストグラムがありますが、その他の列にはありません。  
  
 sp_createstats は、クエリの実行時間が重要であるためにクエリ オプティマイザーによって 1 列ずつの統計が生成されるのを待てないアプリケーション (ベンチマークなど) で使用できます。 ほとんどの場合、その必要はありません。 sp_createstats を使用するにはクエリ オプティマイザーでは、クエリを向上させるために必要に応じて単一列統計が生成されるプランの場合に、 **AUTO_CREATE_STATISTICS**オプションがオンにします。  
  
 統計の詳細については、「[統計](../../relational-databases/statistics/statistics.md)」を参照してください。 単一列の統計情報の生成の詳細については、次を参照してください。、 **AUTO_CREATE_STATISTICS**オプション[ALTER DATABASE SET Options &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_createstats   
    [   [ @indexonly =   ] { 'indexonly'   | 'NO' } ]   
    [ , [ @fullscan =    ] { 'fullscan'    | 'NO' } ]   
    [ , [ @norecompute = ] { 'norecompute' | 'NO' } ]  
    [ , [ @incremental = ] { 'incremental' | 'NO' } ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@indexonly=** ] **'indexonly'**  
 既存のインデックスに含まれている、インデックス定義の最初の列にはなっていない列についてのみ、統計を作成します。 **indexonly**は**char (9)** します。 既定値は NO です。  
  
 [  **@fullscan=** ] **'fullscan'**  
 使用して、 [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)ステートメントを**FULLSCAN**オプション。 **fullscan**は**char (9)** します。  既定値は NO です。  
  
 [  **@norecompute=** ] **'norecompute'**  
 使用して、 [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)ステートメントを**NORECOMPUTE**オプション。 **norecompute**は**char (12)** します。  既定値は NO です。  
  
 [  **@incremental=** ] **'増分'**  
 使用して、 [CREATE STATISTICS](../../t-sql/statements/create-statistics-transact-sql.md)ステートメントを**INCREMENTAL = ON**オプション。 **増分**は**char (12)** します。  既定値は NO です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 新しい統計オブジェクトの名前は、その統計オブジェクトが作成された列の名前と同じです。  
  
## <a name="remarks"></a>コメント  
 sp_createstats が作成または、既存の統計オブジェクトの最初の列である列の統計を更新していません。 これには、インデックス、AUTO_CREATE_STATISTICS オプションを生成された単一列統計の列、および CREATE STATISTICS ステートメントを使用して作成された統計の最初の列に対して作成された統計の最初の列が含まれます。 その列が別の有効なインデックスで使用する場合を除き、sp_createstats は無効化されたインデックスの最初の列に統計を作成できません。 sp_createstats では、無効になっているクラスター化インデックスを持つテーブルの統計は作成されません。  
  
 テーブルに列セットが含まれている場合、sp_createstats ではスパース列に対する統計は作成されません。 列セットとスパース列の詳細については、次を参照してください。[列セットの使用](../../relational-databases/tables/use-column-sets.md)と[スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-single-column-statistics-on-all-eligible-columns"></a>A. 条件を満たすすべての列の統計を 1 列ずつ作成する  
 次の例では、現在のデータベースで、条件を満たすすべての列の統計を 1 列ずつ作成します。  
  
```  
EXEC sp_createstats;  
GO  
```  
  
### <a name="b-create-single-column-statistics-on-all-eligible-index-columns"></a>B. 条件を満たすすべてのインデックス列の統計を 1 列ずつ作成する  
 次の例では、既にインデックスに含まれていてインデックスの最初の列にはなっていない、条件を満たすすべての列の統計を 1 列ずつ作成します。  
  
```  
EXEC sp_createstats 'indexonly';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [統計](../../relational-databases/statistics/statistics.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
