---
title: Reporting Services のサブスクリプションを監視する | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: subscriptions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], inactive
- subscriptions [Reporting Services], status
- monitoring [Reporting Services], subscriptions
- status information [Reporting Services]
- inactive subscriptions [Reporting Services]
ms.assetid: 054c4a87-60bf-4556-9a8c-8b2d77a534e6
caps.latest.revision: 36
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b81bf16cc4f9352da7b0a4c37cac91dd73f5eff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33035739"
---
# <a name="monitor-reporting-services-subscriptions"></a>Reporting Services のサブスクリプションを監視する
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプションの監視は、ユーザー インターフェイス、Windows PowerShell、またはログ ファイルから行うことができます。 監視のために使用できるオプションは、実行しているレポート サーバーのモードによって異なります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
 **このトピックの内容:**  
  
-   [ネイティブ モードのユーザー インターフェイス](#bkmk_native_mode)  
  
-   [SharePoint モード](#bkmk_sharepoint_mode)  
  
-   [PowerShell を使用してサブスクリプションを監視する](#bkmk_use_powershell)  
  
-   [無効なサブスクリプションの管理](#bkmk_manage_inactive)  
  
##  <a name="bkmk_native_mode"></a> ネイティブ モードのユーザー インターフェイス  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の各ユーザーは、 **[個人用サブスクリプション]** ページ、またはレポート マネージャーの **[サブスクリプション]** タブを使用して、サブスクリプションの状態を監視できます。 [サブスクリプション] ページには、サブスクリプションが最後に実行された日時およびサブスクリプションの状態を示す列があります。 サブスクリプションの処理がスケジュールされると、状態メッセージが更新されます。 トリガーが発生しない場合 (レポート実行スナップショットが更新されない、スケジュールが実行されないなどの場合)、状態メッセージは更新されません。  
  
 **[状態]** 列に表示されることのある値を、次の表に示します。  
  
|状態|Description|  
|------------|-----------------|  
|新しいサブスクリプション|初めてサブスクリプションを作成するときに表示されます。|  
|無効|サブスクリプションを処理できないときに表示されます。 詳細については、このトピックの「無効なサブスクリプションの管理」を参照してください。|  
|完了: 合計 \<*number*> 件のうち、処理済み \<*number*> 件; エラー \<*number*> 件です。|データ ドリブン サブスクリプション実行の状態を表示します。このメッセージはスケジュールおよび配信のプロセッサで作成されます。|  
|\<*number*> 処理済み|スケジュールおよび配信のプロセッサが正常に配信した通知、または配信の試行が行われなくなった通知の件数です。 データ ドリブンの配信が完了したとき、処理された通知の件数と生成された通知の合計件数が等しくなる必要があります。|  
|\<*number*> 合計|最後にサブスクリプションを配信したときに生成されたサブスクリプションの通知の合計件数です。|  
|\<*number*> エラー|スケジュールおよび配信のプロセッサが配信できなかった通知、または配信の試行が行われなくなった通知の件数です。|  
|電子メールを送信できません: サーバーに接続できなかったため、配信が失敗しました。|レポート サーバーがメール サーバーに接続されなかったことを示します。このメッセージは電子メールの配信拡張機能で作成されます。|  
|ファイル \<*filename*> が \<path> に保存されました。|ファイル共有の場所への配信が成功したことを示します。このメッセージはファイル共有の配信拡張機能で作成されます。|  
|ファイルへの書き込み時に不明のエラーが発生しました。|ファイル共有の場所への配信が失敗したことを示します。このメッセージはファイル共有の配信拡張機能で作成されます。|  
|接続先のフォルダー \<path> にアクセスしようとしたときにエラーが発生しました。 接続先のフォルダーまたはファイル共有が存在することを確認してください。|指定したフォルダーが見つからなかったことを示します。このメッセージはファイル共有の配信拡張機能で作成されます。|  
|ファイル \<filename> を \<path> に書き込めませんでした。 再試行しています。|ファイルを新しいバージョンに更新できなかったことを示します。このメッセージはファイル共有の配信拡張機能で作成されます。|  
|ファイル \<filename> に書き込めません: \<message>|ファイル共有の場所への配信が失敗したことを示します。このメッセージはファイル共有の配信拡張機能で作成されます。|  
|\<カスタム ステータス メッセージ>|配信拡張機能で提供される、配信の成功および失敗に関する状態メッセージです。 サード パーティまたはカスタムの配信拡張機能を使用している場合、追加の状態メッセージが提供される可能性があります。|  
  
 また、レポート サーバー管理者は、現在処理中の標準のサブスクリプションを監視することもできます。 データ ドリブン サブスクリプションは監視できません。 詳細については、「 [実行中の処理を管理する](../../reporting-services/subscriptions/manage-a-running-process.md)」を参照してください。  
  
 サブスクリプションを配信できない場合 (たとえば、メール サーバーが利用不可能な場合)、配信拡張機能は配信を再試行します。 構成設定では、実行する試行回数を指定します。 既定値は再試行なしです。 場合によっては、レポートがデータを使用せずに処理されることがあります (たとえば、データ ソースがオフラインになっている場合)。この場合、その結果を示すテキストが、メッセージの本文に記載されます。  
  
### <a name="native-mode-log-files"></a>ネイティブ モードのログ ファイル  
 配信中にエラーが発生すると、レポート サーバーのトレース ログにエントリが作成されます。  
  
 レポート サーバー管理者は、**reportserverservice_\*.log** ファイルを参照して、サブスクリプションの配信状態を判断できます。 電子メール配信については、特定の電子メール アカウントに対する処理および配信の記録がレポート サーバーのログ ファイルに出力されます。 ログ ファイルの既定の場所を次に示します。  
  
 `C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\LogFiles`  
  
 以下にログ ファイル名の例を示します。  
  
 `ReportServerService__05_21_2014_00_05_07.log`  
  
 サブスクリプションに関連するトレース ログ ファイルのサンプル エラー メッセージを次に示します。  
  
-   library!WindowsService_7!b60!05/20/2014-22:34:36:: i 情報: サーバー システムで指定されているとおり、EnableExecutionLogging を 'True' に初期化中です properties.emailextension!WindowsService_7!b60!05/20/2014-22:34:41:: e エラー: **メールを送信中にエラーが発生しました**。 例外: System.Net.Mail.SmtpException: SMTP サーバーにセキュリティで保護された接続が必要であるか、またはクライアントが認証されていません。 サーバーの応答内容: 5.7.1 クライアントは System.Net.Mail.MailCommand.CheckResponse(SmtpStatusCode statusCode, String response) で認証されませんでした  
  
 ログ ファイルには、レポートが開かれているかどうか、または実際に配信が成功したかどうかに関する情報は含まれません。 配信が成功するということは、スケジュールおよび配信のプロセッサでエラーが生成されず、レポート サーバーがメール サーバーに接続したことを意味します。 電子メールがユーザーのメールボックスで配信不能なメッセージ エラーとなった場合、その情報はログ ファイルに含まれません。 ログ ファイルの詳細については、「 [Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)」を参照してください。  
  
##  <a name="bkmk_sharepoint_mode"></a> SharePoint モード  
 SharePoint モードでサブスクリプションを監視する: サブスクリプションの状態は **[サブスクリプションの管理]** ページから監視できます。  
  
1.  レポートがあるドキュメント ライブラリを参照します。  
  
2.  レポートのコンテキスト メニューを開きます (**…**)。  
  
3.  展開されたメニュー オプションを選択します (**…**)。  
  
4.  **[サブスクリプションの管理]** を選択します。  
  
### <a name="sharepoint-uls-log-files"></a>SharePoint ULS ログ ファイル  
 サブスクリプション関連の情報は、SharePoint ULS ログに書き込まれます。 ULS ログの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] イベント構成の詳細については、「[SharePoint トレース ログの Reporting Services イベントをオンにする (ULS)](../../reporting-services/report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)」を参照してください。  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプションに関連した ULS ログのエントリの例を次に示します。  
  
||||||||  
|-|-|-|-|-|-|-|  
|date|[処理]|領域|カテゴリ|レベル|Correlation|メッセージ|  
|5/21/2014 14:34:06:15|アプリケーション プール： a0ba039332294f40bc4a81544afde01d|SQL Server Reporting Services (SQL Server Reporting Services)|レポート サーバー電子メール拡張機能|Unexpected|(空)|**Error sending email.** 例外: System.Net.Mail.SmtpException: メールボックスが使用できません。 サーバーの応答内容: 5.7.1 クライアントは、次の場所で、この送信者として送信する権限がありません。System.Net.Mail.DataStopCommand.CheckResponse(SmtpStatusCode statusCode, String serverResponse)、System.Net.Mail.DataStopCommand.Send(SmtpConnection conn)、System.Net.Mail.SmtpClient.Send(MailMessage message)、Microsoft.ReportingServices.EmailDeliveryProvider.EmailProvider.Deliver(Notification notification)|  
  
##  <a name="bkmk_use_powershell"></a> PowerShell を使用してサブスクリプションを監視する  
 ネイティブ モードまたは SharePoint モードのサブスクリプションの状態を確認するために使用できる PowerShell スクリプトの例は、「 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../reporting-services/subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)」を参照してください。  
  
##  <a name="bkmk_manage_inactive"></a> 無効なサブスクリプションの管理  
 サブスクリプションが無効になった場合、サブスクリプションが処理されない根本的な条件を解決して、サブスクリプションを削除または再び有効にする必要があります。 処理を妨げる条件が発生すると、サブスクリプションは無効になることがあります。 このような条件の例を次に示します。  
  
-   サブスクリプションで指定された配信拡張機能を削除またはアンインストールした。  
  
-   資格情報の設定を "保存された資格情報" から "統合" または要求された値に変更した。  
  
-   レポート定義のパラメーター名またはデータ型を変更後に、レポートを再パブリッシュした。 サブスクリプションに無効になったパラメーターが含まれている場合、サブスクリプションは非アクティブになります。  
  
-   レポートの実行モードの変更 (たとえば、要求時レポートをレポート実行スナップショットとして実行するように変更)。 詳細については、「 [レポート処理プロパティの設定](../../reporting-services/report-server/set-report-processing-properties.md)」を参照してください。  
  
 無効なサブスクリプションは、サブスクリプション自体のメッセージによって示されます。 メッセージには、その原因とサブスクリプションを再び有効にする際に実行する手順が含まれています。  
  
 処理を妨げる条件が原因でサブスクリプションが無効になる場合、サブスクリプションは、レポート サーバーがサブスクリプションを実行したときにこの事実を反映します。 サブスクリプションが毎週金曜日午前 2 時にレポートを配信するようにスケジュールされているのに、使用する配信拡張機能が月曜日の午前 9 時にアンインストールされた場合、サブスクリプションは、金曜日の午前 2 時になるまで無効な状態であることを示しません。  
  
## <a name="see-also"></a>参照  
 [ネイティブ モード レポート サーバーのサブスクリプションの作成と管理](http://msdn.microsoft.com/en-us/7f46cbdb-5102-4941-bca2-5e0ff9012c6b)   
 [サブスクリプションと配信 &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)  
  
  
