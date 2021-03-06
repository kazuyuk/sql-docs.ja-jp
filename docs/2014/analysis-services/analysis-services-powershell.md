---
title: Analysis Services PowerShell |Microsoft Docs
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7fe6625cf512586c5f5e42bb4d5d4f601db41a70
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265688"
---
# <a name="analysis-services-powershell"></a>Analysis Services PowerShell
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] 移動、管理、および Analysis Services オブジェクトをクエリする Windows PowerShell を使用できるように、Analysis Services PowerShell (SQLAS) プロバイダーとコマンドレットが含まれています。  
  
 Analysis Services PowerShell は、次の要素で構成されています。  
  
-   分析管理オブジェクト (AMO) 階層の移動に使用する `SQLAS` プロバイダー。  
  
-   MDX スクリプト、DMX スクリプト、または XMLA スクリプトの実行に使用する `Invoke-ASCmd` コマンドレット。  
  
-   処理、ロール管理、パーティション管理、バックアップと復元などの日常的な操作に使用するタスク固有のコマンドレット。  
  
## <a name="in-this-article"></a>この記事では、次の項目が扱われます。  
 [前提条件](#bkmk_prereq)  
  
 [Analysis Services のサポートされているバージョンとモード](#bkmk_vers)  
  
 [認証要件とセキュリティに関する考慮事項](#bkmk_auth)  
  
 [Analysis Services PowerShell タスク](#bkmk_tasks)  

構文と例については、次を参照してください。 [Analysis Services PowerShell Reference](/sql/analysis-services/powershell/analysis-services-powershell-reference)します。

##  <a name="bkmk_prereq"></a> 前提条件  
 Windows PowerShell 2.0 がインストールされている必要があります。 新しいバージョンの Windows オペレーティング システムでは、既定でインストールされます。 詳細については、次を参照してください[Windows PowerShell 2.0 のインストール。](https://msdn.microsoft.com/library/ff637750.aspx)

<!-- ff637750.aspx above is linked to by:  (http://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 SQL Server PowerShell (SQLPS) モジュールとクライアント ライブラリを含んだ SQL Server 機能をインストールする必要があります。 その最も簡単な方法は、SQL Server Management Studio をインストールすることです。SQL Server Management Studio をインストールすると、PowerShell の機能とクライアント ライブラリも自動的にインストールされます。 SQL Server PowerShell (SQLPS) モジュールには、Analysis Services オブジェクト階層の移動に使用する SQLASCmdlets モジュールと SQLAS プロバイダーなど、すべての SQL Server 機能用の PowerShell プロバイダーとコマンドレットが含まれています。  
  
 インポートする必要があります、 **SQLPS**モジュールを使用する前に、`SQLAS`プロバイダーおよびコマンドレット。 SQLAS プロバイダーの拡張機能は、`SQLServer`プロバイダー。 SQLPS モジュールをインポートするには、いくつかの方法があります。 詳細については、「 [SQLPS モジュールのインポート](../../2014/database-engine/import-the-sqlps-module.md)」を参照してください。  
  
 Analysis Services インスタンスにリモート アクセスするには、リモート管理とファイル共有を有効にしておく必要があります。 詳細については、次を参照してください。[リモート管理を有効にする](#bkmk_remote)このトピックの「します。  
  
##  <a name="bkmk_vers"></a> サポートされている Analysis Services のバージョンとモード  
 現在、Analysis Services PowerShell は、Windows Server 2008 R2、Windows Server 2008 SP1、または Windows 7 で動作する [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services のすべてのエディションでサポートされています。  
  
 次の表に、さまざまなコンテキストで利用可能な Analysis Services PowerShell の機能を示します。  
  
|コンテキスト|PowerShell の利用可能な機能|  
|-------------|-------------------------------------|  
|多次元のインスタンスとデータベース|ローカルおよびリモート管理でサポートされます。<br /><br /> Merge-partition にはローカル接続が必要です。|  
|表形式のインスタンスとデータベース|ローカルおよびリモート管理でサポートされます。<br /><br /> 詳細については、、2011 年 8 月のブログを参照してください。[表形式モデルを使用して PowerShell の管理](http://go.microsoft.com/fwlink/?linkID=227685)します。|  
|PowerPivot for SharePoint のインスタンスとデータベース|制限付きでサポートされます。 HTTP 接続と SQLAS プロバイダーを使用して、インスタンスとデータベースの情報を表示できます。<br /><br /> ただし、コマンドレットの使用はサポートされていません。 インメモリ PowerPivot データベースのバックアップと復元に Analysis Services PowerShell は使用しないでください。また、ロールの追加や削除、データの処理、任意の XMLA スクリプトの実行にも使用しないでください。<br /><br /> PowerPivot for SharePoint には、構成のために個別に提供される組み込みの PowerShell サポートがあります。 詳細については、次を参照してください。 [PowerPivot for SharePoint 用 PowerShell リファレンス](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)します。|  
|ローカル キューブへのネイティブ接続<br /><br /> "Data Source=c:\backup\test.cub"|サポートされていません。|  
|SharePoint 内の BI セマンティック モデル (.bism) 接続ファイルへの HTTP 接続<br /><br /> "データ ソース =http://server/shared_docs/name.bism"|サポートされていません。|  
|PowerPivot データベースへの埋め込み接続<br /><br /> "Data Source=$Embedded$"|サポートされていません。|  
|Analysis Services ストアド プロシージャ内のローカル サーバーのコンテキスト<br /><br /> "Data Source=*"|サポートされていません。|  
  
##  <a name="bkmk_auth"></a> 認証要件とセキュリティに関する考慮事項  
 Analysis Services に接続する際は、Windows のユーザー ID を使用して接続を確立する必要があります。 大半の接続は Windows 統合セキュリティを使用して確立されます。この場合、サーバーの動作するセキュリティ コンテキストは、現在のユーザーの ID によって設定されます。 ただし、Analysis Services への HTTP アクセスを構成すると、その他の認証方法も利用できるようになります。 このセクションでは、使用できる認証オプションが、接続の種類に応じてどのように変わるかについて説明します。  
  
 Analysis Services への接続は、大きくネイティブ接続と HTTP 接続とに分けられます。 ネイティブ接続は、クライアント アプリケーションからサーバーへの直接接続です。 PowerShell セッションでは、PowerShell クライアントが OLE DB Provider for Analysis Services を使用して直接 Analysis Services インスタンスに接続します。 ネイティブ接続は常に Windows 統合セキュリティを使用して行われます。この場合、Analysis Services PowerShell は、現在のユーザーとして実行されます。 Analysis Services では、権限借用はサポートされません。 特定のユーザーとして操作を実行するには、そのユーザーとして PowerShell セッションを開始する必要があります。  
  
 HTTP 接続は IIS を通じて間接的に確立されるため、他の認証オプション (基本認証など) を使用して、Analysis Services インスタンスに接続することができます。 IIS では権限借用がサポートされます。IIS で使用する資格情報を接続文字列に追加し、接続の確立時にその接続文字列を指定することで、権限を借用することができます。 資格情報は、–Credential パラメーターを使用して指定できます。  
  
 **使用して PowerShell では、– Credential パラメーター**  
  
 –Credential パラメーターは、ユーザー名とパスワードを指定する PSCredential オブジェクトを受け取ります。 Analysis Services PowerShell では、(既存の接続のコンテキスト内で動作するコマンドレットではなく) Analysis Services への接続要求を行うコマンドレットで –Credential パラメーターを利用できます。 接続要求を行うコマンドレットとしては、Invoke-ASCmd、Backup-ASDatabase、Restore-ASDatabase などが挙げられます。 これらのコマンドレットに関しては、次の条件が満たされている場合、–Credential パラメーターを使用できます。  
  
1.  サーバーが HTTP アクセス用に構成されている (つまり、Analysis Services に接続する際は、IIS が接続を処理し、ユーザー名とパスワードを読み取り、対応するユーザー ID の権限を借用する)。 詳細については、「[インターネット インフォメーション サービス &#40;IIS&#41; 8.0 上の Analysis Services への HTTP アクセスの構成](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)」を参照してください。  
  
2.  Analysis Services の HTTP アクセス用に作成された IIS 仮想ディレクトリが、基本認証を使用するように構成されている。  
  
3.  資格情報オブジェクトによって指定されたユーザー名とパスワードが、Windows ユーザー ID へと解決される。 Analysis Services は、この ID を現在のユーザーとして使用します。 Windows ユーザーでない場合、または要求された操作を実行するための十分な権限がそのユーザーにない場合、要求は失敗します。  
  
 資格情報オブジェクトを作成するには、Get-Credential コマンドレットを使用して、対象のオペレーターの資格情報を収集します。 この資格情報オブジェクトを Analysis Services への接続コマンドに使用できます。 次の例は、1 つの方法を示しています。 この例の接続の対象は、HTTP アクセス用に構成されたローカル インスタンスです。  
  
```  
PS SQLSERVER:\SQLAS\HTTP_DS> $cred = Get-credential adventureworks\dbadmin  
PS SQLSERVER:\SQLAS\HTTP_DS> Invoke-ASCmd –Inputfile:”c:\discoverconnections.xmla” –Credential:$cred  
```  
  
 基本認証を使用する際は、暗号化された接続を介してユーザー名とパスワードが送信されるように、必ず HTTPS と SSL を使用してください。 詳細については、次を参照してください。 [IIS 7.0 で Secure Sockets Layer の構成](http://go.microsoft.com/fwlink/?linkID=184299)と[基本認証を構成する (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=230776)します。  
  
 PowerShell で指定した資格情報、クエリ、およびコマンドは、そのままトランスポート層に渡されることに注意してください。 機密性の高いコンテンツがスクリプトに含まれていると、悪質なインジェクション攻撃のリスクが増大します。  
  
 **Microsoft.Secure.String オブジェクトとしてパスワードを提供します。**  
  
 バックアップや復元など、一部の操作については、コマンドにパスワードを指定した場合にアクティブ化される暗号化オプションがサポートされます。 パスワードを指定すると、バックアップ ファイルを暗号化 (または暗号化を解除) するように、Analysis Services 伝えられます。 このパスワードは、Analysis Services において、セキュリティで保護された文字列オブジェクトとしてインスタンス化されます。 次の例では、オペレーターから実行時にパスワードを収集します。  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd = read-host -AsSecureString -Prompt "Password"  
Password: ****  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd -is [System.IDisposable]   
True  
```  
  
 これで、password パラメーターに $pwd 変数を渡すことによって、暗号化されたデータベース ファイルをバックアップまたは復元することができます。 他のコマンドレットも含む完全な例を表示するを参照してください。 [Backup-asdatabase コマンドレット](/sql/analysis-services/powershell/backup-asdatabase-cmdlet)と[Restore-asdatabase コマンドレット](/sql/analysis-services/powershell/restore-asdatabase-cmdlet)します。
  
 最後に、パスワードと変数の両方をセッションから削除します。  
  
```  
PS SQLSERVER:\SQLAS\Localhost\default> $pwd.Dispose()  
PS SQLSERVER:\SQLAS\Localhost\default> Remove-Variable -Name pwd  
```  
  
##  <a name="bkmk_tasks"></a> Analysis Services PowerShell タスク  
 Analysis Services PowerShell は、Windows PowerShell 管理シェルまたは Windows コマンド プロンプトから実行できます。 Analysis Services PowerShell を [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] から実行することはできません。  
  
 ここでは、Analysis Services PowerShell を使用する一般的なタスクについて説明します。  
  
-   [読み込み、分析サービスのプロバイダーおよびコマンドレット](#bkmk_load)  
  
-   [リモート管理を有効にします。](#bkmk_remote)  
  
-   [接続する Analysis Services オブジェクト](#bkmk_connect)  
  
-   [サービスを管理します。](#bkmk_admin)  
  
-   [Analysis Services PowerShell のヘルプを表示します。](#bkmk_help)  
  
###  <a name="bkmk_load"></a> 読み込み、分析サービスのプロバイダーおよびコマンドレット  
 Analysis Services プロバイダーは、SQLPS モジュールをインポートすると利用可能になる SQL Server ルート プロバイダーの拡張機能です。 Analysis Services コマンドレットも同時に読み込まれます。プロバイダーなしでコマンドレットを使用する場合は、コマンドレットを別に読み込むこともできます。  
  
-   Import-module コマンドレットを実行して、Analysis Services PowerShell のすべての機能を含む SQLPS を読み込みます。 モジュールをインポートできない場合は、モジュールを読み込む目的で、一時的に実行ポリシーを無制限に変更することができます。 詳細については、「 [SQLPS モジュールのインポート](../../2014/database-engine/import-the-sqlps-module.md)」を参照してください。  
  
    ```  
    Import-module “sqlps”  
    ```  
  
     または、`import-module “sqlps” –disablenamechecking` を使用して、承認されていない動詞の名前についての警告を抑制します。  
  
-   Analysis Services プロバイダーも Invoke-ASCmd コマンドレットも読み込まずに、タスク固有の Analysis Services コマンドレットのみを読み込むには、独立した操作として SQLASCmdlets モジュールを読み込みます。  
  
    ```  
    Import-module “sqlascmdlets”  
    ```  
  
###  <a name="bkmk_remote"></a> リモート管理を有効にします。  
 リモートの Analysis Services インスタンスと共に Analysis Services PowerShell を使用するには、まずリモート管理とファイル共有を有効にする必要があります。 次のエラーは、ファイアウォールの構成に問題があることを示しています。"RPC サーバーを利用できません  (HRESULT からの例外: 0x800706BA)"。  
  
1.  ローカル コンピューターとリモート コンピューターの両方で、クライアント ツールとサーバー ツールが [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] のバージョンであることを確認します。  
  
2.  Analysis Services インスタンスをホストしているリモート サーバーで、Windows ファイアウォールの TCP ポート 2383 を開きます。 Analysis Services を名前付きインスタンスとしてインストールした場合やカスタム ポートを使用している場合は、ポート番号は異なります。 詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」をご参照ください。  
  
3.  リモート サーバーで、リモート プロシージャ コール (RPC) サービス、TCP/IP NetBIOS Helper サービス、WMI (Windows Management Instrumentation) サービス、Windows リモート管理 (WS-Management) サービスが開始されていることを確認します。  
  
4.  リモート サーバーで、グループ ポリシー オブジェクト エディター スナップイン (gpedit.msc) を起動します。  
  
5.  [コンピューターの構成]、[管理用テンプレート]、[ネットワーク]、[ネットワーク接続]、[Windows ファイアウォール]、[ドメイン プロファイル] の順に開きます。  
  
6.  ダブルクリック**Windows ファイアウォール: 着信リモート管理例外を許可する**を選択します**有効**、順にクリックします**OK**。  
  
7.  ダブルクリック**Windows ファイアウォール: 着信ファイルとプリンター共有の例外を許可する**を選択します**有効**、順にクリックします**OK**します。  
  
8.  クライアント ツールのあるローカル コンピューター上の実際のサーバー名に置き換えて、リモート管理を確認する次のコマンドレットを使用して、*リモート サーバー名*プレース ホルダーです。 Analysis Services が既定のインスタンスとしてインストールされている場合は、インスタンス名は省略します。 このコマンドが機能するためには、事前に SQLPS モジュールをインポートしておく必要があります。  
  
    ```  
    PS SQLSERVER:\> cd sqlas  
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 場合によっては、追加的な構成が必要になることもあります。 たとえば、リモート サーバーに対して別のコンピューターからコマンドを実行するには、リモート サーバーで次のコマンドを実行する必要があります。  
  
```  
Enable-psremoting  
```  
  
  
###  <a name="bkmk_connect"></a> 接続する Analysis Services オブジェクト  
 Analysis Services PowerShell プロバイダーは、Analysis Services オブジェクト階層の移動をサポートし、コマンド実行のコンテキストを設定します。 プロバイダーは、SQLPS モジュールを通じて利用できる SQLSERVER ルート プロバイダーの拡張機能です。 SQLPS モジュールを読み込むと、パスを移動できます。  
  
 ローカルまたはリモートのインスタンスに接続できますが、一部のコマンドレットはローカル インスタンス (マージ パーティション) のみで動作します。 ネイティブ接続、または HTTP アクセス用に構成した Analysis Services サーバーの HTTP 接続を使用できます。 次の図は、ネイティブ接続と HTTP 接続のナビゲーション パスを示しています。 次の図は、ネイティブ接続と HTTP 接続のナビゲーション パスを示しています。  
  
 **Analysis Services へのネイティブ接続**  
  
 ![Analysis Services への接続をネイティブ](media/ssas-powershell-nativeconnection.gif "Analysis Services へのネイティブ接続")  
  
 次の例は、ネイティブ接続を使用してオブジェクト階層を移動する方法を示しています。 プロバイダーから `dir` を実行して、インスタンスの情報を表示できます。 `cd` を使用して、そのインスタンスのオブジェクトを表示できます。  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 アセンブリ、データベース、ロール、トレースの各コレクションを確認する必要があります。 `cd` と `dir` を引き続き使用して、各コレクションの内容を表示できます。  
  
 **Analysis Services への HTTP 接続**  
  
 ![Analysis Services への HTTP 接続](media/ssas-powershell-httpconnection.gif "Analysis Services への HTTP 接続")  
  
 HTTP 接続はこのトピックの手順を使用して HTTP アクセス用にサーバーを構成した場合に便利です[インターネット インフォメーション サービスでの Analysis Services への HTTP アクセスの構成&#40;IIS&#41; 8.0。](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
 サーバーの URL と仮定するとhttp://localhost/olap/msmdpump.dll接続は、次のようになります。  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName “http://localhost/olap/msmdpump.dll”  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 アセンブリ、データベース、ロール、トレースの各コレクションを確認する必要があります。 これらのコレクションの内容を表示できない場合は、OLAP 仮想ディレクトリの認証設定を確認します。 匿名アクセスが無効になっていることを確認します。 Windows 認証を使用する場合は、Windows ユーザー アカウントが Analysis Services インスタンスに対する管理権限を持っていることを確認します。  
  
###  <a name="bkmk_admin"></a> サービスを管理します。  
 サービスが実行されていることを確認します。 Analysis Services (MSSQLServerOLAPService) とデータベース エンジンを含む、SQL Server サービスの状態、名前、表示名が返されます。  
  
```  
Get-service mssql*  
```  
  
 プロセス ID、ハンドル数、メモリ使用量を含むプロセスのプロパティが返されます。  
  
```  
Get-process msmdsrv  
```  
  
 管理者シェルから次のコマンドレットを実行すると、サービスを再起動します。  
  
```  
Restart-service mssqlserverolapservice  
```  
  
###  <a name="bkmk_help"></a> Analysis Services PowerShell のヘルプを表示します。  
 次のコマンドレットを使用して、コマンドレットの機能を確認したり、サービス、プロセス、およびオブジェクトの詳細情報を表示できます。  
  
1.  `Get-help` は、Analysis Services コマンドレットの組み込みのヘルプ (例を含む) を返します。  
  
    ```  
    Get-help invoke-ascmd -examples  
    ```  
  
2.  `Get-command` は、11 個の Analysis Services PowerShell コマンドレットの一覧を返します。  
  
    ```  
    get-command –module SQLASCmdlets  
    ```  
  
3.  `Get-member` は、サービスまたはプロセスのプロパティやメソッドを返します。  
  
    ```  
    Get-service mssqlserverolapservice | get-member –type Property  
    ```  
  
    ```  
    Get-service mssqlserverolapservice | get-member –type Method  
    ```  
  
    ```  
    Get-process msmdsrv | get-member –type Property  
    ```  
  
4.  `Get-member` には、サーバー インスタンスを指定する SQLAS プロバイダーを使用してオブジェクトのプロパティやメソッド (サーバー オブジェクトの AMO メソッドなど) を返すという使用方法もあります。  
  
    ```  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | get-member –type Method  
    ```  
  
5.  `Get-PSdrive` は、現在インストールされているプロバイダーの一覧を返します。 SQLPS モジュールをインポートしてあると、`SQLServer` プロバイダーが一覧に表示されます (SQLAS は SQLServer プロバイダーの一部であり、個別に一覧には表示されません)。  
  
    ```  
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a>参照  
 [SQL Server PowerShell をインストールします。](../database-engine/install-windows/install-sql-server-powershell.md)   
 [表形式のモデルを使用して PowerShell (ブログ) を管理します。](http://go.microsoft.com/fwlink/?linkID=227685)   
 [インターネット インフォメーション サービスでの Analysis Services への HTTP アクセスの構成&#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
