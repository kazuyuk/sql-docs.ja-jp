---
title: SPID 要素 (XMLA) |Microsoft Docs
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
- SPID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#SPID
- microsoft.xml.analysis.spid
- urn:schemas-microsoft-com:xml-analysis#SPID
helpviewer_keywords:
- SPID element
ms.assetid: c4a54dcb-a0cd-4255-9e0f-a34eb990854f
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27244dab841ac4793d66c6b177d5382ca7cdc7a7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167023"
---
# <a name="spid-element-xmla"></a>SPID 要素 (XMLA)
  親を実行するアクティブ サーバー プロセス識別子 (SPID) を識別する[キャンセル](../xml-elements-commands/cancel-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cancel>  
   ...  
   <SPID>...</SPID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Cancel](../xml-elements-commands/cancel-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `SPID` 要素は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の特定のセッションで使用されるサーバー プロセス識別子 (SPID) を表します。  
  
## <a name="see-also"></a>参照  
 [CancelAssociated 要素&#40;XMLA&#41;](cancelassociated-element-xmla.md)   
 [ConnectionID 要素&#40;XMLA&#41;](id-element-xmla.md)   
 [SessionID 要素&#40;XMLA&#41;](sessionid-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
