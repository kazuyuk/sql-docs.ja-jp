---
title: COUNT_BIG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COUNT_BIG_TSQL
- COUNT_BIG
dev_langs:
- TSQL
helpviewer_keywords:
- totals [SQL Server], COUNT_BIG function
- counting items in group
- groups [SQL Server], number of items in
- number of group items
- COUNT_BIG function
ms.assetid: f2e3601f-487e-4917-bb01-47b1047908cd
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: fee3353a2992e56db4383e46b7f0285c28467725
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454026"
---
# <a name="countbig--sql"></a>COUNT_BIG (-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

この関数は、グループ内で見つかった項目数を返します。 `COUNT_BIG` は [COUNT](../../t-sql/functions/count-transact-sql.md) 関数と同じように動作します。 これらの関数の違いは、戻り値のデータ型のみです。 `COUNT_BIG` は常に **bigint** データ型の値を返します。 `COUNT` は常に **int** データ型の値を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for SQL Server and Azure SQL Database  
  
COUNT_BIG ( { [ ALL | DISTINCT ] expression } | * )  
   [ OVER ( [ partition_by_clause ] [ order_by_clause ] ) ]  
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Aggregation Function Syntax  
COUNT_BIG ( { [ [ ALL | DISTINCT ] expression ] | * } )  
  
-- Analytic Function Syntax  
COUNT_BIG ( { expression | * } ) OVER ( [ <partition_by_clause> ] )  
```  
  
## <a name="arguments"></a>引数  
ALL  
すべての値にこの集計関数を適用します。 既定として ALL が使用されます。
  
DISTINCT  
`COUNT_BIG` で一意の NULL ではない値の数を返すことを指定します。
  
*式 (expression)*  
任意のデータ型の[式](../../t-sql/language-elements/expressions-transact-sql.md)。 `COUNT_BIG` は、式の集計関数またはサブクエリをサポートしていません。
  
*\**  
`COUNT_BIG` ですべての行をカウントし、返すテーブルの合計行数を決定することを指定します。 `COUNT_BIG(*)` はパラメーターを受け取らず、DISTINCT の使用をサポートしていません。 `COUNT_BIG(*)` では、この関数の定義上、特定の列についての情報は使用されないため、*expression* パラメーターは必要ありません。 `COUNT_BIG(*)` は、指定されたテーブル内の行数を返し、重複する行を保持します。 各行は 1 行としてカウントされ、 これには NULL 値を保持している行も含まれます。
  
OVER **(** [ *partition_by_clause* ] [ *order_by_clause* ] **)**  
*partition_by_clause* は、`FROM` 句で生成された結果セットをパーティションに分割します。このパーティションに `COUNT_BIG` 関数が適用されます。 指定しない場合、関数ではクエリ結果セットのすべての行を 1 つのグループとして扱います。 *order_by_clause* は、操作の論理的順序を決定します。 詳細については、[OVER 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md) に関するページを参照してください。
  
## <a name="return-types"></a>戻り値の型
**bigint**
  
## <a name="remarks"></a>Remarks  
COUNT_BIG(\*) は、グループ内の項目数を返します。 これには NULL 値と重複値も含まれます。
  
COUNT_BIG (ALL *expression*) はグループ内の各行に対して *expression* を評価し、非 NULL 値の数を返します。
  
COUNT_BIG (DISTINCT *expression*) はグループ内の各行に対して *expression* を評価し、一意の非 NULL 値の数を返します。
  
COUNT_BIG は、OVER 句や ORDER BY 句***なし***で使用される場合は決定的関数です。 OVER 句や ORDER BY 句と***共に***使用される場合は、非決定的関数です。 詳細については、「[決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。
  
## <a name="examples"></a>使用例  
例については、「[COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md)」を参照してください。
  
## <a name="see-also"></a>参照
[集計関数 (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[COUNT &#40;Transact-SQL&#41;](../../t-sql/functions/count-transact-sql.md)  
[int、bigint、smallint、および tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)  
[OVER 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
