---
title: '|| (論理 OR) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f69d71354db0c658a644c0cd4068e894b3fb94fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316972"
---
# <a name="-logical-or-ssis-expression"></a>|| (論理 OR) (SSIS 式)
  論理 OR 演算を実行します。 一方または両方の条件が TRUE の場合、式は TRUE に評価されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>引数  
 *boolean_expression1, boolean_expression2*  
 TRUE、FALSE、または NULL に評価される、任意の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="remarks"></a>コメント  
 次の表は、|| 演算子の結果を示します。  
  
|結果|式|式|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>SSIS 式の例  
 この例では、 **StandardCost** 列と **ListPrice** 列を使用しています。 **StandardCost** 列の値が 300 より小さいか、または **ListPrice** 列の値が 500 より大きい場合、式は TRUE に評価されます。  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 この例では、数値リテラルの代わりに変数 **SPrice** と **LPrice** を使用しています。  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>参照  
 [&#124;&#40;ビット演算包含的 OR&#41; &#40;SSIS 式&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;ビット演算子排他的 OR&#41; &#40;SSIS 式&#41;](bitwise-exclusive-or-ssis-expression.md)   
 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)   
 [演算子&#40;SSIS 式&#41;](operators-ssis-expression.md)  
  
  
