---
title: Password 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f82fbcfecff5e6d216c3758ce442d82591a24d78
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050423"
---
# <a name="password-element-xmla"></a>Password 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  親によって使用されるパスワードを決定します。[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)または[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)コマンドでは、暗号化またはバックアップ ファイルを復号化します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[バックアップ](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)、[復元](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 **バックアップ**コマンドの場合、**パスワード**バックアップ ファイルが暗号化されていない、要素が含まれていないか、空の文字列が含まれています。  
  
 **復元**コマンドの場合、**パスワード**要素が含まれていないまたはエラーが発生した暗号化されたバックアップ ファイルを復元しようとしています。 空の文字列が含まれています。  
  
 場合**場所**いずれかで要素が含まれて、**バックアップ**または**復元**コマンドを同じ**パスワード**要素は、バックアップの使用およびリモート バックアップ ファイルです。 リモート バックアップ ファイルの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
## <a name="see-also"></a>参照
 [Location 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
