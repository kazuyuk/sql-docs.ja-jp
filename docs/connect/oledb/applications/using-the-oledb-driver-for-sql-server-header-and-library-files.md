---
title: SQL Server ヘッダーとライブラリ ファイルでの OLE DB ドライバーの使用 | Microsoft Docs
description: SQL Server ヘッダーとライブラリ ファイルでの OLE DB ドライバーの使用
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 847d25310542a6eb10f929a04ee4e5e066bbb38e
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108704"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>SQL Server ヘッダーとライブラリ ファイルでの OLE DB ドライバーの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server ヘッダーとライブラリ ファイルは、インストール プロセス中に、OLE DB Driver for SQL Server SDK のオプションが選択されているときにインストールされます。 アプリケーションを開発するときは、開発に必要なすべてのファイルを開発環境にコピーしてインストールすることが重要です。 インストールして、SQL Server の OLE DB Driver の再配布の詳細については、次を参照してください。[をインストールする OLE DB Driver for SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)します。  
  
 SQL Server ヘッダーとライブラリ ファイルの OLE DB Driver は、次の場所にインストールされます。  
  
 *%PROGRAM FILES %* \Microsoft の SQL Server\Client SDK\OLEDB\181\SDK  
  
 SQL Server データ アクセス機能のカスタム アプリケーションに OLE DB ドライバーを追加する、OLE DB Driver for SQL Server ヘッダー ファイル (msoledbsql.h) を使用できます。 OLE DB Driver for SQL Server ヘッダー ファイルには、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入された新しい機能を使用するために必要なすべての定義、属性、プロパティ、およびインターフェイスが含まれています。  
  
 だけでなく、OLE DB Driver for SQL Server のヘッダー ファイル、またファイルがある msoledbsql.lib ライブラリ エクスポート ライブラリであるため[OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)機能します。  
  
 OLE DB Driver for SQL Server ヘッダー ファイルは、MDAC (Microsoft Data Access Components) と共に使用する sqloledb.h ヘッダー ファイルに対して下位互換性がありますが、SQLOLEDB (MDAC 付属の OLE DB provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) の CLSID や (OLE DB Driver for SQL Server でサポートされない) XML 機能のシンボルは含まれていません。    
  
 OLE DB Driver for SQL Server を使用して、OLE DB アプリケーションのみ、msoledbsql.h を参照する必要があります。 1 つのアプリケーションで MDAC (SQLOLEDB) と OLE DB Driver for SQL Server の両方を使用する場合、sqloledb.h と msoledbsql.h の両方を参照できますが、sqloledb.h を先に参照する必要があります。  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>SQL Server のヘッダー ファイルの OLE DB ドライバーを使用します。  
 OLE DB Driver for SQL Server のヘッダー ファイルを使用することを使用する必要があります、**含める**C/C++ プログラミング コード内のステートメント。 次のセクションでは、この OLE DB アプリケーションを実行する方法について説明します。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server ヘッダーとライブラリ ファイルは、Visual Studio C 2012 を使用してコンパイルされた以降にのみできます。  
  
### <a name="ole-db"></a>OLE DB (OLE DB)  
 OLE DB ドライバーを使用して、プログラミング コードの次の行を使用して、OLE DB アプリケーションで SQL Server のヘッダー ファイル。  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  アプリケーションがある場合、**を含める**sqloledb.h、ステートメント、**含める**msoledbsql.h のステートメントをその後に記述する必要があります。  
  
 SQL Server の OLE DB ドライバーを通じてデータ ソースへの接続を作成するときに、プロバイダー名文字列として"MSOLEDBSQL"を使用します。  

  
## <a name="component-names-and-properties-by-version"></a>各バージョンのコンポーネント名とプロパティ  

|プロパティ|OLE DB Driver for SQL Server|MDAC|  
|--------|----------------------------|----|   
|OLE DB PROGID|MSOLEDBSQL|SQLOLEDB|  
|OLE DB ヘッダー ファイル名|msoledbsql.h|Sqloledb.h|  
|OLE DB プロバイダー DLL|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>静的リンクと BCP 関数  
 BCP 関数を使用するアプリケーションでは、アプリケーションのコンパイルに使用されたヘッダー ファイルおよびライブラリに付属するのと同じバージョンのドライバーを接続文字列で指定することが重要です。  
  
 詳細については、実行を参照してください。[一括コピー操作を実行する](../../oledb/features/performing-bulk-copy-operations.md)します。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server を使用したアプリケーションの構築](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
