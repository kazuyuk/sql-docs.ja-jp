---
title: IpAddresses プロパティ (ServerNetworkProtocol クラス) |Microsoft Docs
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
- IpAddresses Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
caps.latest.revision: 31
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 20979e9647d2d80f7498a5ec517d7403cd0ccf83
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150623"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>IpAddresses プロパティ (ServerNetworkProtocol クラス)
  サーバー ネットワーク プロトコルに関連付けられた IP アドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.IpAddresses [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスによって使用されるネットワーク プロトコルを表す `ServerNetworkProtocol` オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 配列の[ServerNetworkProtocolIPAdress クラス](../servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md)サーバー ネットワーク プロトコルによってサポートされる IP アドレスを表すオブジェクト。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
