---
title: DatabaseID 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fd628eb44324dd76c9def9c0dff8668e0aa0fa07
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575774"
---
# <a name="databaseid-element-xmla"></a>DatabaseID 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  オブジェクト参照を含む親要素内で、データベースを識別します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <DatabaseID>...</DatabaseID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)、[Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|1-1 : 必須要素で、1 回だけ出現します|  
|他のすべて|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、[ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)、[Source](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)、[Target](../../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
