---
title: ODBCCONF です。EXE |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f7a6e48f6a7a17c8ea3decd79d765fb176080e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914307"
---
# <a name="odbcconfexe"></a>ODBCCONF です。EXE
ODBCCONF.exe は、ODBC ドライバーとデータ ソース名を構成できるようにするコマンド ライン ツールです。  
  
> [!NOTE]  
>  ODBCCONF.exe は、Windows Data Access Components の将来のバージョンで削除されます。 この機能を使用しないし、現在この機能を使用しているアプリケーションの変更を計画します。 PowerShell コマンドを使用すると、ドライバーとデータ ソースを管理します。 これらの PowerShell コマンドの詳細については、次を参照してください。 [Windows Data Access Components コマンドレット](https://technet.microsoft.com/library/hh771019.aspx)です。  
  
## <a name="syntax"></a>構文  
  
```  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>引数  
 *スイッチ*  
 0 個以上のスイッチ オプションです。 使用可能なスイッチの一覧で、このトピックの後半の「解説」を参照してください。  
  
 *action*  
 1 つのアクションを実行します。 使用可能なオプションの一覧では、「解説」セクションを参照してください。  
  
## <a name="remarks"></a>解説  
 次のスイッチを使用できます。  
  
|スイッチ|Description|  
|------------|-----------------|  
|/A {*アクション*}|アクションを指定します。<br /><br /> /A は 1 つのアクションが指定した場合のみ省略できます。|  
|/?|ODBCCONF の使用状況を表示します。EXE です。|  
|/C|処理するには、アクションが失敗したかどうかは続行されます。|  
|/E|処理が完了したら、/F で指定された応答ファイルを消去します。|  
|/F|など、応答ファイルを使用して`odbcconf /F my.rsp`です。<br /><br /> my.rsp は、次のようになります。 `REGSVR c:\my.dll`<br /><br /> /A は、応答ファイルでは使用されません。|  
|/H|使用法 (ヘルプ) を表示します。 このスイッチは、同じ/ください。|  
|/L [*モード*]*ファイル名*|3 つのモードのいずれかのファイルにプログラムの出力を送信します。 標準 (n)、詳細な (v)、およびデバッグ (d)。 モードのレコード odbcconf.exe によって読み込まれる Dll をデバッグします。<br /><br /> /L、モードなしを指定する場合、ログ ファイルは空になります。<br /><br /> たとえば、 **/Lv log.txt**です。|  
|/R|アクションは、再起動後に実行されます。|  
|/S|サイレント モード。 エラー メッセージは表示されません。|  
  
 次の操作を使用できます。  
  
|操作|Description|  
|------------|-----------------|  
|CONFIGDRIVER *driver_name * * ドライバー固有の構成パラメーター*|適切なドライバーのセットアップ DLL と呼び出しを読み込み、 **ConfigDriver**関数。<br /><br /> 等価の[SQLConfigDriver 関数](../odbc/reference/syntax/sqlconfigdriver-function.md)です。<br /><br /> 以下に例を示します。<br /><br /> /A {CONFIGDRIVER「ドライバ名」"CPTimeout = 60"}<br /><br /> /A {CONFIGDRIVER「ドライバ名」"DriverODBCVer 03.80 を ="}|  
|CONFIGDSN *driver_name* DSN =*名前* &#124; *属性*|追加またはシステム データ ソースを変更します。<br /><br /> 等価の[SQLConfigDataSource 関数](../odbc/reference/syntax/sqlconfigdatasource-function.md)です。<br /><br /> 以下に例を示します。<br /><br /> /A {CONFIGDSN"SQL Server""DSN の名前を =&#124;サーバー = srv"}|  
|CONFIGSYSDSN *driver_name* DSN =*名前* &#124; *属性*|追加またはシステム データ ソースを変更します。<br /><br /> 等価の[SQLConfigDataSource 関数](../odbc/reference/syntax/sqlconfigdatasource-function.md)です。<br /><br /> 以下に例を示します。<br /><br /> /A {CONFIGSYSDSN"SQL Server""DSN の名前を =&#124;サーバー = srv"}|  
|INSTALLDRIVER|等価[SQLInstallDriverEx 関数](../odbc/reference/syntax/sqlinstalldriverex-function.md)です。<br /><br /> INSTALLDRIVER に渡されるキーワードと値のペアの構文については、次を参照してください。[ドライバー仕様サブキー](../odbc/reference/install/driver-specification-subkeys.md)です。<br /><br /> 以下に例を示します。<br /><br /> /A {INSTALLDRIVER"は、ドライバー &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; FileUsage 0 を = &#124; SQLLevel = 1"}|  
|INSTALLTRANSLATOR*変換プログラムの構成 * * ドライバーのパス*|変換プログラムに関する情報を追加、**見つかりました。INI\ODBC トランスレーター**レジストリ キー。<br /><br /> 等価[SQLInstallTranslatorEx 関数](../odbc/reference/syntax/sqlinstalltranslatorex-function.md)です。<br /><br /> INSTALLDRIVER に渡されるキーワードと値のペアの構文については、次を参照してください。[トランスレーター仕様サブキー](../odbc/reference/install/translator-specification-subkeys.md)です。<br /><br /> 以下に例を示します。<br /><br /> /A {INSTALLTRANSLATOR"My トランスレーター &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll"}|  
|REGSVR *dll*|DLL を登録します。<br /><br /> Regsvr32.exe に相当します。<br /><br /> 以下に例を示します。<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|ときに HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC です。INI\ODBC ファイル DSN\DefaultDSNDir が存在しない、SETFILEDSNDIR アクションはそれが作成され、\ODBC\Data ソースが付いた HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir で値を割り当てます。<br /><br /> HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC 値です。INI\ODBC ファイル DSN\DefaultDSNDir では、ファイル ベースのデータ ソースを作成するときに、ODBC データ ソース アドミニストレーターによってを使用する既定の場所を指定します。<br /><br /> 以下に例を示します。<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>参照  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
