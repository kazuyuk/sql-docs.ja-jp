---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a97e2afca882d168f4ca0f6143680f85ccd002ae
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781043"
---
# <a name="cryptgenrandom-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

この関数は、Crypto API (CAPI) でランダムに生成された暗号数を返します。 `CRYPT_GEN_RANDOM` は、長さが指定されたバイト数の 16 進数を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>引数  
*length*  
`CRYPT_GEN_RANDOM` で作成される数値の長さ (バイト)。 *length* 引数のデータ型は **int** であり、値の範囲は 1 から 8000 です。 `CRYPT_GEN_RANDOM` は、この範囲から外れる **int** 値に対して NULL を返します。 
  
*seed*  
ランダムなシード値として使用する省略可能な 16 進数。 *seed* の長さは、*length* 引き数の値と一致する必要があります。 *seed* 引数のデータ型は **varbinary(8000)** です。
  
## <a name="returned-types"></a>返される型  
**varbinary(8000)**
  
## <a name="permissions"></a>アクセス許可  
この関数はパブリックであり、特別なアクセス許可は必要ありません。
  
## <a name="examples"></a>使用例  
  
### <a name="a-generating-a-random-number"></a>A. 乱数を生成する  
この例では、長さ 50 バイトの乱数を生成します。
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
この例では、4 バイトのシードを使用して、長さ 4 バイトの乱数を生成します。
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>参照
[RAND (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rand-transact-sql.md)
  
  
