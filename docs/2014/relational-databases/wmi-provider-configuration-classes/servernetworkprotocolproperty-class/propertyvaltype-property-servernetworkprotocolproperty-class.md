---
title: PropertyValType プロパティ (ServerNetworkProtocolProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 52331d787707fbd4882055023ba289a60b2dc250
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201122"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>PropertyValType プロパティ (ServerNetworkProtocolProperty クラス)
  参照されたプロパティに格納される値のデータ型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [ServerNetworkProtocolProperty クラス](servernetworkprotocolproperty-class.md)オブジェクトのインスタンス上のネットワーク プロトコルの属性を表す[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 プロパティ値のデータ型を指定する `uint32` 値。 文字列型の値の場合は 0、数値型の値の場合は 1 を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
