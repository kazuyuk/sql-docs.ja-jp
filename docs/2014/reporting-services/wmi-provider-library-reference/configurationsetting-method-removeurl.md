---
title: RemoveURL メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 464a37912e7751b4fa33b5a134b29e456a6ae573
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37258288"
---
# <a name="removeurl-method-wmi-msreportserverconfigurationsetting"></a>RemoveURL メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー用に予約されている URL を削除します。 削除の対象となる URL が複数ある場合は、この API を 1 つずつ呼び出して URL を削除する必要があります。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *アプリケーション*  
 予約を削除する対象のアプリケーションの名前。  
  
 *URLString*  
 予約する URL。  
  
 *lcid*  
 返されるエラー メッセージに使用するロケール。  
  
 *Error*  
 [out] 発生したエラーの説明。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>コメント  
 *UrlString* には、仮想ディレクトリの名前が含まれていません。その目的では、[SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) メソッドが提供されます。  
  
 呼び出しの前に、 [ReserveURL](configurationsetting-method-reserveurl.md)メソッド用の VirtualDirectory 構成プロパティの値を指定する必要があります、*アプリケーション*パラメーター。 [SetVirtualDirectory Method (WMI MSReportServer_ConfigurationSetting)](configurationsetting-method-setvirtualdirectory.md) メソッドを利用し、VirtualDirectory プロパティを設定します。  
  
 SSL 証明書が [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で準備されていて、他の URL でその証明書を使用する必要がない場合、その SSL 証明書は削除されます。  
  
 このメソッドにより、すべての非構成アプリケーション ドメインで強制力の高いリサイクル処理が実行され、その処理中にそれらのドメインは停止します。アプリケーション ドメインは、この処理の完了後に再起動します。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
