---
title: srv_sendmsg (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_sendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 31c558a3deb0080c11b8ba4f055f7341fd1a4443
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32937347"
---
# <a name="srvsendmsg-extended-stored-procedure-api"></a>srv_sendmsg (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 クライアントにメッセージを送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、言語要求を受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *msgtype*  
 サーバーから送信されるメッセージの種類が情報メッセージかエラー メッセージかによって、SRV_MSG_INFO または SRV_MSG_ERROR を指定します。  
  
 *msgnum*  
 4 バイトのメッセージ番号です。  
  
 *class*  
 エラーの重大度を指定します。 重大度が 10 以下の場合は、情報メッセージと見なされます。  
  
 *state*  
 現在のメッセージのエラー状態番号を指定します。 エラー状態番号により、エラーの内容に関する情報を得ることができます。 有効な状態番号の範囲は 0 ～ 255 です。  
  
 *rpcname*  
 現時点では、サポートされません。  
  
 *rpcnamelen*  
 現時点では、サポートされません。  
  
 *linenum*  
 メッセージが該当する言語コマンド バッチ内の行番号です。 行番号は 1 から始まります。 メッセージに *linenum* が不要である場合は、0 に設定します。  
  
 *message*  
 クライアントに送信される文字列を指すポインターです。  
  
 *msglen*  
 *message* の長さをバイト数で指定します。 *message* が NULL 終端である場合は、*msglen* を SRV_NULLTERM に設定します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL を返します。  
  
## <a name="remarks"></a>Remarks  
 この関数は、エラー メッセージまたは情報メッセージをクライアントに送信する場合に使用します。 メッセージが送信されるたびに呼び出されます。  
  
 メッセージは、**srv_sendrow** によるすべての行 (あれば) の送信前後に任意の順序で **srv_sendmsg** を使用してクライアントに送信できます。 すべてのメッセージ (あれば) は **srv_senddone** で完了状態が送信される前にクライアントに送信しておく必要があります。  
  
 Unicode でメッセージを送信するには、**srv_sendmsg** ではなく **srv_wsendmsg** を使用してください。  
  
 詳しくは、「[Unicode データおよびサーバー コード ページ](../../relational-databases/extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)」をご覧ください。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
