---
title: == (等しい) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- equal operator (==)
- == (equal operator)
ms.assetid: 36fd2354-7b93-4c95-9cf3-51ee24568950
caps.latest.revision: 53
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8225225bb877682f2dc97eee2f1400740ec63b7f
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405854"
---
# <a name="-equal-ssis-expression"></a>== (等しい) (SSIS 式)
  2 つの式が等しいかどうかを判別するための比較を実行します。 式エバリュエーターは、比較の実行前にさまざまなデータ型を自動的に変換します。 詳しくは、「 [式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」をご覧ください。  
  
 ただし、一部のデータ型では、式を正常に評価する前に明示的なキャストを含む必要がある場合があります。 データ型間の有効なキャストについて詳しくは、「[Cast &#40;SSIS 式&#41;](../../integration-services/expressions/cast-ssis-expression.md)」をご覧ください。  
  
## <a name="syntax"></a>構文  
  
```  
  
expression1 == expression2  
  
```  
  
## <a name="arguments"></a>引数  
 *expression1、expression2*  
 有効な式を指定します。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="remarks"></a>Remarks  
 比較する式のいずれかが NULL の場合、比較結果は NULL になります。 両方の式が NULL の場合も、結果は NULL になります。  
  
 設定する式の *expression1* と *expression2*は、次のいずれかのルールに従う必要があります。  
  
-   **数値** *expression1* と *expression2* の両方が数値データ型である必要があります。 データ型の積集合は、式エバリュエーターが実行する暗黙的な数値変換に関する規則で指定されているように、数値データ型である必要があります。 2 つの数値データ型の積集合を NULL にすることはできません。 詳しくは、「 [式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」をご覧ください。  
  
-   **文字** *expression1* と *expression2* は、どちらも DT_STR または DT_WSTR データ型に評価される必要があります。 2 つの式が評価される文字列データ型は、異なっていてもかまいません。  
  
    > [!NOTE]  
    >  文字列の比較では、大文字と小文字、アクセント、かな、および文字幅が区別されます。  
  
-   **日付、時刻、または日付/時刻** *expression1* と *expression2* は、どちらも DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET、または DT_FILETIME のいずれかのデータ型に評価される必要があります。  
  
    > [!NOTE]  
    >  時刻データ型に評価される式と、日付データ型または日付/時刻データ型に評価される式との間の比較はサポートされていません。 システムによってエラーが生成されます。  
  
     式の比較の際は、次の変換規則が記載順に適用されます。  
  
    -   2 つの式が同じデータ型に評価される場合、そのデータ型の比較が実行されます。  
  
    -   一方の式が DT_DBTIMESTAMPOFFSET データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMPOFFSET に変換され、DT_DBTIMESTAMPOFFSET の比較が実行されます。 詳しくは、「 [式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」をご覧ください。  
  
    -   一方の式が DT_DBTIMESTAMP2 データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMP2 に変換され、DT_DBTIMESTAMP2 の比較が実行されます。  
  
    -   一方の式が DT_DBTIME2 データ型の場合、もう一方の式が暗黙的に DT_DBTIME2 に変換され、DT_DBTIME2 の比較が実行されます。  
  
    -   一方の式が DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2、DT_DBTIME2 のいずれの型でもない場合、両方の式が DT_DBTIMESTAMP データ型に変換されてから比較が実行されます。  
  
     式の比較は、次の前提に基づいて実行されます。  
  
    -   それぞれの式のデータ型に秒の小数部が含まれている場合、秒の小数部の桁数が最も少ないデータ型の残りの桁の値は 0 と見なされます。  
  
    -   それぞれの式が日付データ型であり、一方のみにタイム ゾーン オフセットがある場合、タイム ゾーン オフセットがない日付データ型は協定世界時 (UTC) と見なされます。  
  
-   **論理** *expression1* と *expression2* は、どちらもブール型に評価される必要があります。  
  
-   **GUID** *expression1* と *expression2* は、どちらも DT_GUID データ型に評価される必要があります。  
  
-   **バイナリ** *expression1* と *expression2* は、どちらも DT_BYTES データ型に評価される必要があります。  
  
-   **BLOB** *expression1* と *expression2* は、どちらも同じバイナリ ラージ オブジェクト ブロック (BLOB) データ型 (DT_TEXT、DT_NTEXT、または DT_IMAGE) に評価される必要があります。  
  
 データ型について詳しくは、「 [Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」をご覧ください。  
  
## <a name="expression-examples"></a>式の例  
 現在の日付が 2003 年 7 月 4 日の場合、この例の結果は TRUE に評価されます。 詳しくは、「[GETDATE &#40;SSIS 式&#41;](../../integration-services/expressions/getdate-ssis-expression.md)」をご覧ください。  
  
 "7/4/2003" == GETDATE()  
  
 **ListPrice** 列の値が 500 の場合、この例の結果は TRUE に評価されます。  
  
```  
ListPrice == 500  
```  
  
 この例では、変数 **LPrice**を使用しています。 **LPrice** の値が 500 の場合、この例の結果は TRUE に評価されます。 式を正しく解析するには、この変数のデータ型が数値型である必要があります。  
  
```  
@LPrice == 500  
```  
  
## <a name="see-also"></a>参照  
 [!= (等しくない) (SSIS 式)](../../integration-services/expressions/unequal-ssis-expression.md)   
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
