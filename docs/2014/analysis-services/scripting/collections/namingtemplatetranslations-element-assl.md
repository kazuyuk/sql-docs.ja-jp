---
title: NamingTemplateTranslations 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- NamingTemplateTranslations Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2965971734625c4d0c553f652160e1044eb48546
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204402"
---
# <a name="namingtemplatetranslations-element-assl"></a>NamingTemplateTranslations 要素 (ASSL)
  ローカライズされた変換のコレクションを提供します、 [NamingTemplate](../properties/namingtemplate-element-assl.md)要素は親の[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[属性](../objects/attribute-element-assl.md)型の[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|子要素|[NamingTemplateTranslation](../objects/translation-element-assl.md)型の[翻訳](translations-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 値、`NamingTemplateTranslation`要素の親属性によってのみ使用されます (つまり、他の値、[使用状況](../properties/usage-element-dimensionattribute-assl.md)要素の親の`DimensionAttribute`に設定されている*親*)。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionAttribute>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
