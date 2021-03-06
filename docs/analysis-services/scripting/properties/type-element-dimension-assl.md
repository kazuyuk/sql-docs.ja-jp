---
title: Type 要素 (Dimension) (ASSL) |Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3af3168c39f685702154bb7c76435bd1d241a642
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37990314"
---
# <a name="type-element-dimension-assl"></a>Type 要素 (Dimension) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  ディメンションのコンテンツに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
      ...  
   <Type>...</Type>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*正規表現*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 値によって**型**、たとえば*アカウント*、特定の動作を決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*正規表現*|ディメンションは標準ディメンションです。|  
|*[時刻]*|ディメンションは時間ディメンションです。<br /><br /> 注: この値は、ディメンションが時間ディメンションに固有の機能をサポートしていることを示します。|  
|*Geography*|ディメンションに地域属性が含まれています。|  
|*組織*|ディメンションに組織属性が含まれています。|  
|*BillOfMaterials*|ディメンションに部品表属性が含まれています。|  
|*Accounts*|ディメンションに勘定科目関連の属性が含まれています。<br /><br /> 注: この値は、ディメンションに勘定科目ディメンションに固有の機能がサポートしていることを示します。|  
|*顧客*|ディメンションに顧客関連の属性が含まれています。|  
|*製品*|ディメンションに製品関連の属性が含まれています。|  
|*シナリオ*|ディメンションにシナリオ関連の属性が含まれています。|  
|*定量的*|ディメンションに数量属性が含まれています。|  
|*Utility*|ディメンションにユーティリティ属性が含まれています。|  
|*通貨*|ディメンションに通貨属性が含まれています。|  
|*料金*|ディメンションに換算レート属性が含まれています。|  
|*Channel*|ディメンションにチャネル属性が含まれています。|  
|*プロモーション*|ディメンションにプロモーション関連の属性が含まれています。|  
  
 許容された値に対応する列挙体**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DimensionType>します。  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Dimension>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
