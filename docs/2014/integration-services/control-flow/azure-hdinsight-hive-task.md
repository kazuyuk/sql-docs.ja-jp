---
title: Azure HDInsight Hive Task| Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afphivetask.f1
- sql11.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aa9be217b9d5e50611f573a80cb6b4bb49f31fe4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37239442"
---
# <a name="azure-hdinsight-hive-task"></a>Azure HDInsight Pig Task
Azure HDInsight クラスターで Hive スクリプトを実行するには、 **Azure HDInsight Hive Task** を使用します。
     
**Azure HDInsight Hive Task**を追加するには、SSIS デザイナーにドラッグ アンド ドロップし、ダブルクリックまたは右クリックして、 **[編集]** をクリックします。 **[Azure HDInsight Hive Task エディター]** ダイアログ ボックスが表示されます。  
  
 次の一覧で、このダイアログ ボックスのフィールドについて説明します。  
  
1.  **[HDInsightConnection]** フィールドで、既存の Azure HDInsight 接続マネージャーを選択するか、スクリプトを実行するために使用される Azure HDInsight クラスターを参照する新しいものを作成します。
  
2.  **[AzureStorageConnection]** フィールドで、既存の Azure ストレージ接続マネージャーを選択するか、クラスターに関連付けられている Azure ストレージ アカウントを参照する新しいものを作成します。 これは、スクリプト実行の出力とエラー ログをダウンロードする場合にのみ必要です。
 
3.  **[BlobContainer]** フィールドでは、クラスターに関連付けられているストレージ コンテナー名を指定します。 これは、スクリプト実行の出力とエラー ログをダウンロードする場合にのみ必要です。
  
4.  **[LocalLogFolder]** フィールドでは、スクリプト実行の出力およびエラー ログのダウンロード先となるフォルダーを指定します。 これは、スクリプト実行の出力とエラー ログをダウンロードする場合にのみ必要です。   
  
5.  実行する Hive スクリプトを指定するには、次の 2 つの方法があります。
  
    1.  **インライン スクリプト**: **[スクリプトの入力]** ダイアログ ボックスに実行するスクリプトをインラインで入力して、**[Script]** フィールドを指定します。
  
    2.  **スクリプト ファイル**: Azure Blob Storage にスクリプト ファイルをアップロードして、**[BlobName]** フィールドを指定します。 BLOB が HDInsight クラスターに関連付けられている既定のストレージ アカウントまたはコンテナーにない場合は、**[ExternalStorageAccountName]** と **[ExternalBlobContainer]** フィールドを指定する必要があります。 外部 BLOB の場合は、パブリックにアクセス可能として構成されていることを確認します。  
  
     両方が指定されている場合、スクリプト ファイルが使用され、インライン スクリプトは無視されます。
