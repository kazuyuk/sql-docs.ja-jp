---
title: Optimization 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Optimization Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Optimization
- urn:schemas-microsoft-com:xml-analysis#Optimization
- microsoft.xml.analysis.optimization
helpviewer_keywords:
- Optimization element
ms.assetid: fb9ff737-59e2-4d8b-9f0e-af392eb25d08
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b20e8875f982f16a3f7ee128552c65fbbfca0f60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261308"
---
# <a name="optimization-element-xmla"></a>Optimization 要素 (XMLA)
  使用される最適化のしきい値の割合を指定します、 [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)集計をデザインするコマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DesignAggregations>  
   ...  
   <Optimization>...</Optimization>  
   ...  
</DesignAggregations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Double|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
