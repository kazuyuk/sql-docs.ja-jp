---
title: WillConnect イベント (ADO) |Microsoft ドキュメント
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
- WillConnect
- Connection::WillConnect
helpviewer_keywords:
- WillConnect event [ADO]
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a2ddca516e9c5141e0e874074660579e8144ba7
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282871"
---
# <a name="willconnect-event-ado"></a>WillConnect イベント (ADO)
**WillConnect**の接続を開始する前に、イベントが呼び出されます。  
  
 **適用対象:** [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
WillConnect ConnectionString, UserID, Password, Options, adStatus, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 A**文字列**保留中の接続の接続情報を格納します。  
  
 *UserID*  
 A**文字列**保留中の接続のユーザー名を格納しています。  
  
 *Password*  
 A**文字列**保留中の接続のパスワードを格納しています。  
  
 *[オプション]*  
 A**長い**プロバイダーを評価する方法を示す値、 *ConnectionString*です。 唯一のオプションは**adAsyncOpen**です。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 このイベントが呼び出されると、このパラメーターに設定されている**adStatusOK**既定です。 設定されている**adStatusCantDeny**イベントが保留中の操作の取り消しを要求できない場合。  
  
 このイベントが返される前に、このパラメーターを設定**adStatusUnwantedEvent**を後続の通知を防ぐためにします。 このパラメーターに設定**adStatusCancel**この通知の取り消しの原因となった接続操作を要求します。  
  
 *pConnection*  
 [接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトに対してこのイベント通知が適用されます。 パラメーターへの変更、**接続**によって、 **WillConnect**イベント ハンドラーは効果がなく、**接続**です。  
  
## <a name="remarks"></a>コメント  
 ときに**WillConnect**が呼び出されたが、 *ConnectionString*、 *UserID*、*パスワード*、および*オプション*パラメーターは、操作 (保留中の接続)、このイベントの原因し、イベントを返します。 前に変更することができますをによって確立された値に設定されます。 **WillConnect**保留中の接続をキャンセルする要求を返す可能性があります。  
  
 このイベントが取り消されると、 **ConnectComplete**呼び出しに使用されるその*adStatus*パラメーターに設定**adStatusErrorsOccurred**です。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
