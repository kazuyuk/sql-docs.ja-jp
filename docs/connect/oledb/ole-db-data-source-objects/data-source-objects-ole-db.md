---
title: データ ソース オブジェクト (OLE DB) |Microsoft Docs
description: データ ソース オブジェクト (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-source-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], data source objects
- OLE DB Driver for SQL Server, data source objects
- MSOLEDBSQL, data source objects
- OLE DB Driver for SQL Server, data source objects
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- CLSID
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 58007040bc4f96749172644b229dba4769929d66
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106078"
---
# <a name="data-source-objects-ole-db"></a>データ ソース オブジェクト (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] などのデータ ストアへのリンクを確立するために使用する OLE DB インターフェイスのセットのことをデータ ソースと呼びます。 OLE DB Driver for SQL Server コンシューマーの最初のタスクは、プロバイダーのデータ ソース オブジェクトのインスタンスを作成します。  
  
 すべての OLE DB プロバイダーは、そのプロバイダー自体のクラス ID (CLSID) を宣言します。 OLE DB Driver for SQL Server の CLSID は、C/C++ GUID CLSID_MSOLEDBSQL (MSOLEDBSQL_CLSID が正しいを解決するシンボルを参照する msoledbsql.h ファイルに progid)。 コンシューマーは、CLSID を指定して OLE **CoCreateInstance** 関数を使用し、データ ソース オブジェクトのインスタンスを作成します。  
  
 OLE DB Driver for SQL Server は、インプロセス サーバーです。 実行可能なコンテキストを示すために、CLSCTX_INPROC_SERVER マクロを使用して、OLE DB Driver for SQL Server のオブジェクトのインスタンスを作成します。  
  
 OLE DB Driver for SQL Server のデータ ソース オブジェクトでは、OLE DB 初期化インターフェイスが公開されます。コンシューマーは、このインターフェイスを使用して、既存の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに接続できます。  
  
 SQL Server の OLE DB ドライバーを通じて行うすべての接続では、これらのオプションが自動的に設定します。  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 次の例では、クラス ID マクロを使用して、OLE DB Driver for SQL Server のデータ ソース オブジェクトを作成し、そのデータ ソース オブジェクトの **IDBInitialize** インターフェイスを取得します。  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 OLE DB Driver for SQL Server のデータ ソース オブジェクトのインスタンスが正常に作成された場合、データ ソースを初期化し、セッションを作成することで、コンシューマー アプリケーションを続行できます。 OLE DB セッションは、データへのアクセスや操作を可能にするインターフェイスを提供します。  
  
 OLE DB Driver for SQL Server は、データ ソースを正常に初期化する作業の一環として、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の指定されたインスタンスへの最初の接続を行います。 いずれかのデータ ソース初期化インターフェイスで参照が保持されている間、または **IDBInitialize::Uninitialize** メソッドが呼び出されるまで、その最初の接続が維持されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースのプロパティ &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [データ ソース情報のプロパティ](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [初期化プロパティと承認プロパティ](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [セッション](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [セッションのプロパティ - OLE DB Driver for SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [保存されるデータ ソース オブジェクト](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
