---
title: AffectEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 797ee0a58457848b3dec133c695d1d36dc579bbe
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275701"
---
# <a name="affectenum"></a>AffectEnum
操作によって、対象となるレコードを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|ない場合は、[フィルター](../../../ado/reference/ado-api/filter-property.md)に適用される、 **Recordset**、すべてのレコードに影響します。<br /><br /> 場合、**フィルター**文字列基準にプロパティが設定されている (など"作成者 ="smith から"")、操作が現在のチャプターに表示されるレコードに影響し、します。<br /><br /> 場合、**フィルター**プロパティのメンバーに設定されて、 [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)またはブックマークから、操作の配列はのすべての行に影響を与える、 **Recordset**です。 **注:****adAffectAll** Visual Basic オブジェクト ブラウザーで非表示になります。|  
|**呼び出します**|4|すべての兄弟に関する章のすべてのレコードに影響を与える、 **Recordset**、いずれかを使用して非表示を含め**フィルター**現在適用されています。|  
|**adAffectCurrent**|1|現在のレコードのみに影響します。|  
|**adAffectGroup**|2|現在の適合するレコードのみに影響を与える[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティの設定。 設定する必要があります、**フィルター**プロパティを**FilterGroupEnum**値または配列の**ブックマーク**このオプションを使用します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[CancelBatch メソッド (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Resync メソッド](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)|
