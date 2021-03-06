---
title: SQLXML 4.0 のガイドラインと制限 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 73475361af623ecb2f4f3e832329675e415d57e4
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39548293"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a>SQLXML 4.0 のガイドラインと制限
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  SQLXML 4.0 を使用する場合は次の点に注意してください。  
  
-   クエリ結果として返される XML は、XML を生成したマッピング スキーマに対して検証されません。  
  
-   SQLXML 4.0 には、バージョン固有ではない PROGID とバージョン固有の PROGID が含まれています。 すべての実稼働アプリケーションでは、バージョン固有の PROGID を使用することをお勧めします。 SQLXML 4.0 には旧バージョンとの互換性は完全ではないため、これは特に重要です。 バージョン固有の PROGID を使用すると、新しいリリースをインストールして動作に問題が起こった場合にプログラムを保護できます。 リリースが変わるたび、バグ修正や設計変更などさまざまな理由によって、プログラムの動作は変更される可能性があります。 バージョン固有の PROGID を使用すると、新しいリリースをインストールして予期しないエラーが発生した場合にプログラムを保護できます。 バージョン固有の PROGID を使用すれば、新しいバージョンのリリースをインストールしても、アプリケーションは問題なく正常に動作します。 それまで使っていたバージョン固有の PROGID を変更し、新しいリリースで最新のものを使用する場合は、実稼働する前にアプリケーションをテストする必要があります。 たとえば、バージョン固有の PROGID を使用するアプリケーションでは、特定の状況下でエラーが発生する可能性があります。  
  
     つまり、SQLXML 4.0 とバージョン固有の PROGID を使用するアプリケーションを実行している状態で、他のソフトウェア プログラムをインストールすると、 このプログラムによって以前のバージョンの SQLXML がインストールされる可能性があり、 この場合、アプリケーションのバージョン固有の PROGID では以前のバージョンの SQLXML が参照されるため、アプリケーションで使用する SQLXML 機能が含まれていないと、エラーが発生します。  
  
-   SQLXML の機能のプロバイダーを設定するはありません、SQLXMLOLEDB プロバイダーを使用して、SQLOLEDB を使用する代わりに、何らかの理由で場合、 **SQLXML Version**プロパティを"SQLXML.4.0"。  
  
  
