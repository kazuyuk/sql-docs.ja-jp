---
title: ビットごとの演算子 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: d6bf579a902d058a79ac3b7777e44692ea88cd04
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458956"
---
# <a name="bitwise-operators-transact-sql"></a>ビットごとの演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ビットごとの演算子は、整数型に分類されるデータ型を持つ 2 つの式に対してビット操作を実行します。  
  ビットごとの演算子は 2 つの整数値をバイナリ ビットに変換し、各ビットに対して AND、OR、または NOT 演算を実行して結果を生成します。 次にその結果を整数に変換します。  
  
  たとえば、整数 170 はバイナリの 1010 1010 に変換されます。
整数 75 はバイナリの 0100 1011 に変換されます。

|演算子 (operator)|ビットごとの数値演算|
|---- |---- |
|[AND] <br> 任意の位置にあるビットが両方とも 1 の場合、結果は 1 になります。 |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 0000 1010 =  10 |
|スイッチまたは <br> 任意の位置にあるいずれかのビットが 1 の場合、結果は 1 になります。 |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 1110 1011 = 235|
|[NOT]  <br> すべてのビット位置にあるビット値を反転させます。 |1010 1010 = 170 <br>----------------- <br>  0101 0101 =   85 |
  
次のトピックを参照してください。   
* [& &#40;ビット演算 AND&#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [&= &#40;ビットごとの AND 代入&#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124; &#40;ビットごとの OR&#41;](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124;= &#40;ビットごとの OR 代入&#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ &#40;ビットごとの排他的 OR&#41;](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^= &#40;ビットごとの排他的 OR 代入&#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ &#40;ビット演算子 NOT&#41;](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 ビットごとの演算子のオペランドは、整数または **image** 型を除くバイナリ文字列型に分類されるデータ型です。ただし、両方のオペランドがバイナリ文字列型に分類されるデータ型であってはなりません。 次の表は、サポートされているオペランドのデータ型を示します。  
  
|左オペランド|右オペランド|  
|------------------|-------------------|  
|[[バイナリ]](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**、**smallint**、または **tinyint**|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|**int**、**smallint**、**tinyint**、または **bit**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**、**smallint**、**tinyint**、**binary**、または **varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**、**smallint**、**tinyint**、**binary**、または **varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**、**smallint**、**tinyint**、**binary**、または **varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**、**smallint**、または **tinyint**|  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [複合演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
