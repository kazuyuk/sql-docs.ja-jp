---
title: IncrementalProcessingNotification データ型 (ASSL) |Microsoft Docs
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
- IncrementalProcessingNotification Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotification data type
ms.assetid: 66e27f92-65c1-4a34-b9c2-bfbb5aeb7d7c
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 38ca951d727e32f576e4dc65bc005a5b423e90c0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231812"
---
# <a name="incrementalprocessingnotification-data-type-assl"></a>IncrementalProcessingNotification データ型 (ASSL)
  情報を表す派生データ型を定義、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリの要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<IncrementalProcessingNotification>  
   <!-- The following elements extend QueryNotification -->  
   <TableID>...</TableID>  
   <ProcessingQuery>...</ProcessingQuery>  
</IncrementalProcessingNotification>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[QueryNotification](../objects/querynotification-element-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ProcessingQuery](../properties/query-element-assl.md)、 [TableID](../properties/id-element-assl.md)|  
|派生要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingQueryBinding データ型&#40;ASSL&#41;](binding-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
