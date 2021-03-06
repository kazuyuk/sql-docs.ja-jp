---
title: プログラムによるパスワードの変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], password expiration
- SQL Server Native Client ODBC driver, passwords
- SQL Server Native Client OLE DB provider, passwords
- passwords [SQL Server], expiration
- SQLNCLI, password expiration
- expiration [SQL Server Native Client]
- passwords [SQL Server], modifying
- expired passwords [SQL Server Native Client]
- SQL Server Native Client, password expiration
- modifying passwords
ms.assetid: 624ad949-5fed-4ce5-b319-878549f9487b
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a89101132ebbad9edfcf8bd2c6190e8f86caf32
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408451"
---
# <a name="changing-passwords-programmatically"></a>プログラムによるパスワードの変更
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のリリースでは、ユーザーのパスワードの有効期限が切れたとき、そのパスワードをリセットできるのは管理者だけでした。 以降で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]プログラムで両方のパスワードの有効期限の処理 Native Client では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC ドライバー、およびを変更して、**SQL Server ログイン** ダイアログ ボックス。  
  
> [!NOTE]  
>  可能であれば、実行時にユーザーの資格情報を入力し、それらの資格情報を永続的な形式で保存しないように求めるメッセージが表示されます。 自分の資格情報を保持する必要がある場合、それらを暗号化する必要がありますを使用して、 [Win32 crypto API](http://go.microsoft.com/fwlink/?LinkId=64532)します。 パスワードの使用に関する詳細については、次を参照してください。[強力なパスワード](../../security/strong-passwords.md)します。  
  
## <a name="sql-server-login-error-codes"></a>SQL Server ログイン エラー コード  
 認証の問題により接続できない場合、アプリケーションでは次のいずれかの SQL Server エラー コードを使用して、診断と復旧に役立てることができます。  
  
|SQL Server エラー コード|エラー メッセージ|  
|---------------------------|-------------------|  
|15113|ユーザー '%.*ls' はログインできませんでした。理由: パスワードの検証に失敗しました。 アカウントはロックアウトされています。|  
|18463|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 この時点ではパスワードを使用できません。|  
|18464|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 このパスワードは短すぎるので、Windows ポリシーの要件を満たしません。|  
|18465|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 パスワードは長すぎるために、ポリシーの要件を満たしていません。|  
|18466|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 このパスワードはあまり複雑ではないので、Windows のポリシー要件を満たしません。|  
|18467|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 パスワードがパスワード フィルター DLL の要件を満たしていません。|  
|18468|ユーザー '%.*ls' はログインできませんでした。 理由: パスワードを変更できませんでした。 パスワードの検証で予期しないエラーが発生しました。|  
|18487|ユーザー '%.*ls' はログインできませんでした。 理由: このアカウントのパスワードの有効期限が切れています。|  
|18488|ユーザー '%.*ls' はログインできませんでした。 理由: このアカウントのパスワードを変更する必要があります。|  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがユーザー インターフェイスのパスワードの有効期限をサポートしていると、プログラムを使用します。  
  
### <a name="ole-db-user-interface-password-expiration"></a>OLE DB ユーザー インターフェイスによるパスワード期限切れの処理  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、パスワードの期限切れに加えられた変更をサポートしている、 **SQL Server ログイン** ダイアログ ボックス。 DBPROP_INIT_PROMPT の値を DBPROMPT_NOPROMPT に設定すると、パスワードの有効期限が切れている場合に、最初の接続試行が失敗します。  
  
 DBPROP_INIT_PROMPT は、その他の値に設定されているが表示されます、 **SQL Server ログイン**ダイアログ ボックスで、パスワードが期限切れかどうかに関係なく、します。 ユーザーがクリックしてできる、**オプション**ボタンをクリックし、確認**パスワードの変更**パスワードを変更します。  
  
 ユーザーが [ok] をクリックし、パスワードの有効期限が切れている場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]と使用して新しいパスワードの確認入力を求めるメッセージが、 **SQL Server のパスワードの変更**ダイアログ。  
  
#### <a name="ole-db-prompt-behavior-and-locked-accounts"></a>OLE DB プロンプトの動作とロックされたアカウント  
 アカウントがロックされていることにより、接続に失敗することがあります。 この場合、表示された後、 **SQL Server ログイン**ダイアログ ボックスで、サーバーのエラー メッセージは、ユーザーに表示され、接続試行が中止されます。 次の表示のことがあります、 **SQL Server のパスワードの変更**ダイアログの場合は、ユーザーが、古いパスワードの無効な値を入力します。 この場合も同じエラー メッセージが表示され、接続試行が中止されます。  
  
#### <a name="ole-db-connection-pooling-password-expiration-and-locked-accounts"></a>OLE DB 接続プーリング、パスワードの期限切れ、およびロックされたアカウント  
 接続プール内で接続がアクティブな状態になっている間に、アカウントがロックされたり、そのアカウントのパスワードの有効期限が切れたりすることがあります。 サーバーでは、期限切れのパスワードとロックされたアカウントを 2 回チェックします。 最初のチェックは、初回接続時に行われます。 2 回目のチェックは、接続のリセット時、接続がプールから取り除かれるときに行われます。  
  
 リセットの試行が失敗すると、その接続はプールから削除され、エラーが返されます。  
  
### <a name="ole-db-programmatic-password-expiration"></a>OLE DB プログラムによるパスワード期限切れの処理  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBPROPSET_SQLSERVERDBINIT プロパティ セットに追加された SSPROP_AUTH_OLD_PASSWORD (型 VT_BSTR) プロパティの追加によってパスワードの有効期限をサポートしています。  
  
 既存の "Password" プロパティは DBPROP_AUTH_PASSWORD を参照し、新しいパスワードを保存する場合に使用されます。  
  
> [!NOTE]  
>  接続文字列の "Old Password" プロパティは SSPROP_AUTH_OLD_PASSWORD に設定され、現在の (または期限切れの) パスワードが設定されます。このパスワードをプロバイダー文字列のプロパティ経由で使用することはできません。  
  
 プロバイダーでは、このプロパティの値が保存されません。 このプロパティを設定すると新しい接続が行われるので、プロバイダーでは最初の接続に接続プールが使用されません。 パスワード変更が正常に行われた場合でも、現在の接続にはまだ古いパスワードが含まれているので再利用できません。古いパスワードとは、変更後に無効になるパスワードのことです。 また、ログインに成功すると、このプロパティはクリアされます。 クリア後に古いパスワードを取得しようとすると、VT_EMPTY が返されます。  
  
> [!NOTE]  
>  SSPROP_AUTH_OLD_PASSWORD は、パスワードの有効期限が切れたときにしか使用されないので、保存しないでください。  
  
 "Old Password" プロパティが設定されると、プロバイダーでは、パスワードの変更が試行されていることが想定されます。ただし、Windows 認証も指定されている場合は除きます。この場合は、常に Windows 認証が優先されるためです。  
  
 かどうか、古いパスワードが必須または省略可能として指定それぞれされ DBPROPSTATUS_ の状態の値に応じて、DB_E_ERRORSOCCURRED または DB_S_ERRORSOCCURRED のいずれかでの結果を古いパスワードを指定するか Windows 認証を使用する場合返される CONFLICTINGBADVALUE *dwStatus*します。 これが検出されたときに**idbinitialize::initialize**が呼び出されます。  
  
 パスワード変更の試行が予期せず失敗すると、サーバーからエラー コード 18468 が返されます。 接続試行からは標準の OLE DB エラーが返されます。  
  
 DBPROPSET_SQLSERVERDBINIT プロパティ セットの詳細については、次を参照してください。[初期化プロパティと承認プロパティ](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)します。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがユーザー インターフェイスのパスワードの有効期限をサポートしていると、プログラムを使用します。  
  
### <a name="odbc-user-interface-password-expiration"></a>ODBC ユーザー インターフェイスによるパスワード期限切れの処理  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、パスワードの期限切れに加えられた変更をサポートしている、 **SQL Server ログイン** ダイアログ ボックス。  
  
 場合[SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)と呼びますの値と**DriverCompletion**パスワードの有効期限が切れている場合に SQL_DRIVER_NOPROMPT、最初の接続が失敗に設定されます。 SQLSTATE 値 28000 とネイティブ エラー コード値 18487 が後続の呼び出しによって返される**SQLError**または**SQLGetDiagRec**します。  
  
 場合**DriverCompletion**ユーザーに表示されるその他の任意の値に設定されて、 **SQL Server ログイン**ダイアログ ボックスで、パスワードが期限切れかどうかに関係なく、します。 ユーザーがクリックしてできる、**オプション**ボタンをクリックし、確認**パスワードの変更**パスワードを変更します。  
  
 ユーザーが [ok] をクリックし、パスワードの有効期限が切れている場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]と使用して新しいパスワードの確認入力を画面の指示、 **SQL Server のパスワードの変更**ダイアログ。  
  
#### <a name="odbc-prompt-behavior-and-locked-accounts"></a>ODBC プロンプトの動作とロックされたアカウント  
 アカウントがロックされていることにより、接続に失敗することがあります。 この場合、表示された後、 **SQL Server ログイン**ダイアログ ボックスで、サーバーのエラー メッセージは、ユーザーに表示され、接続試行が中止されます。 次の表示のことがあります、 **SQL Server のパスワードの変更**ダイアログの場合は、ユーザーが、古いパスワードの無効な値を入力します。 この場合も同じエラー メッセージが表示され、接続試行が中止されます。  
  
#### <a name="odbc-connection-pooling-password-expiry-and-locked-accounts"></a>ODBC 接続プーリング、パスワードの期限切れ、およびロックされたアカウント  
 接続プール内で接続がアクティブな状態になっている間に、アカウントがロックされたり、そのアカウントのパスワードの有効期限が切れたりすることがあります。 サーバーでは、期限切れのパスワードとロックされたアカウントを 2 回チェックします。 最初のチェックは、初回接続時に行われます。 2 回目のチェックは、接続のリセット時、接続がプールから取り除かれるときに行われます。  
  
 リセットの試行が失敗すると、その接続はプールから削除され、エラーが返されます。  
  
### <a name="odbc-programmatic-password-expiration"></a>ODBC プログラムによるパスワードの有効期限  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのサポートを使用して、サーバーに接続する前に設定されている SQL_COPT_SS_OLDPWD 属性の追加によってパスワードの有効期限、 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)関数。  
  
 接続ハンドルの SQL_COPT_SS_OLDPWD 属性は、期限切れのパスワードを表します。 接続文字列の属性は接続プーリングに影響を与えることになるので、この属性に関する接続文字列属性はありません。 ログインに成功すると、この属性はクリアされます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、この機能の 4 つのケースで SQL_ERROR を返します。 パスワードの有効期限、パスワード ポリシーの競合、アカウントのロックアウトと Windows 認証を使用しているときに古いパスワードのプロパティを設定するとします。 ドライバーでは、適切なエラー メッセージをユーザーに返すときに[SQLGetDiagField](../../native-client-odbc-api/sqlgetdiagfield.md)が呼び出されます。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
