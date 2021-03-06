---
title: '手順 2: Foreach ループ コンテナーの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52aa26064a9a0e80af03649d89140a71a78f41d7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312002"
---
# <a name="step-2-adding-and-configuring-the-foreach-loop-container"></a>手順 2: Foreach ループ コンテナーの追加と構成
  この実習では、フラット ファイルのフォルダー全体にループ機能を付加し、レッスン 1 で使用したデータ フロー変換と同じ変換を各フラット ファイルに適用します。 そのためには、Foreach ループ コンテナーを制御フローに追加して、構成します。  
  
 Foreach ループ コンテナーを追加したら、フォルダー内の各フラット ファイルに接続できるようにする必要があります。 フォルダー内のファイルはすべて同じ形式なので、Foreach ループ コンテナーは、どのファイルに接続する場合でも同じフラット ファイル接続マネージャーを使用できます。 このループ コンテナーが使用するフラット ファイル接続マネージャーは、レッスン 1 で作成したフラット ファイル接続マネージャーと同じものです。  
  
 レッスン 1 で作成したフラット ファイル接続マネージャーは、現在、1 つのフラット ファイルにのみ接続しています。 フォルダーの各フラット ファイルに 1 つずつ接続するには、Foreach ループ コンテナーとフラット ファイル接続マネージャーをそれぞれ次のように構成します。  
  
-   **ForEach ループ コンテナー:** このコンテナーの列挙値をユーザー定義のパッケージ変数にマップします。 ForEach ループ コンテナーは、このユーザー定義の変数を使用して、フラット ファイル接続マネージャーの `ConnectionString` プロパティを動的に変更しながら、フォルダー内の各フラット ファイルへ順番に接続します。  
  
-   **フラット ファイル接続マネージャー:** は、ユーザー定義変数を使用して、接続マネージャーの設定によって、レッスン 1 で作成された接続マネージャーを変更`ConnectionString`プロパティ。  
  
 この実習の手順では、ForEach ループ コンテナーを作成し、ユーザー定義パッケージ変数を使用するように変更する方法、およびデータ フロー タスクをこのループに追加する方法を説明します。 次の実習では、ユーザー定義変数を使用するようにフラット ファイル接続マネージャーを変更します。  
  
 上記のように変更した後でこのパッケージを実行すると、Foreach ループ コンテナーによって、Sample Data フォルダー内のすべてのファイルが反復的に処理されます。 条件と一致するファイルが検出されるたびに、ユーザー定義の変数にそのファイルの名前が取り込まれ、Sample Currency Data フラット ファイル接続マネージャーの `ConnectionString` プロパティにマップされます。さらに、そのファイルに対してデータ フローが実行されます。 つまり、Foreach ループの反復処理が実行されるたびに、データ フロー タスクではそれぞれ異なるフラット ファイルが使用されることになります。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では制御フローとデータ フローが分離されているので、制御フローにループを追加した場合でも、データ フローを修正する必要はありません。 したがって、レッスン 1 で作成したデータ フローは変更する必要がありません。  
  
### <a name="to-add-a-foreach-loop-container"></a>ForEach ループ コンテナーを追加するには  
  
1.  **SQL Server Data Tools**で **[制御フロー]** タブをクリックします。  
  
2.  **SSIS ツールボックス**で **[コンテナー]** を展開し、 **[ForEach ループ コンテナー]** を **[制御フロー]** タブのデザイン画面にドラッグします。  
  
3.  新しく追加した **[ForEach ループ コンテナー]** を右クリックし、 **[編集]** をクリックします。  
  
4.  **Foreach ループ エディター**  ダイアログ ボックスの 、**全般** ページの**名前**、入力`Foreach File in Folder`します。 **[OK]** をクリックします。  
  
5.  Foreach ループ コンテナーを右クリックし、をクリックして**プロパティ**、[プロパティ] ウィンドウであることを確認し、`LocaleID`プロパティに設定されて**英語 (米国)** します。  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a>ForEach ループ コンテナーの列挙子を構成するには  
  
1.  [Foreach File in Folder] をダブルクリックして、 **[Foreach ループ エディター]** をもう一度開きます。  
  
2.  **[コレクション]** をクリックします。  
  
3.  **[コレクション]** ページで、 **[Foreach File 列挙子]** を選択します。  
  
4.  **[列挙子の構成]** で、 **[参照]** をクリックします。  
  
5.  **[フォルダーの参照]** ダイアログ ボックスで、Currency_*.txt ファイルが保存されている、コンピューター上のフォルダーに移動します。  
  
     このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。 サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。  
  
    1.  「 [Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  **[ダウンロード]** タブをクリックします。  
  
    3.  ハイパーリンクをクリックして"http://msftisprodsamples.codeplex.com/downloads/get/578097"SQL2012 します。Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルです。  
  
6.  **[ファイル]** ボックスに「**Currency_\*.txt**」と入力します。  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a>ユーザー定義の変数に列挙子をマップするには  
  
1.  **[変数のマッピング]** をクリックします。  
  
2.  **[変数のマッピング]** ページで、**[変数]** 列の空いているセルをクリックし、**\<新しい変数…>** をクリックします。  
  
3.  **変数の追加** ダイアログ ボックスの**名前**、型`varFileName`します。  
  
    > [!IMPORTANT]  
    >  変数名では大文字と小文字が区別されます。  
  
4.  **[OK]** をクリックします。  
  
5.  再び **[OK]** をクリックし、 **[Foreach ループ エディター]** ダイアログ ボックスを閉じます。  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a>データ フロー タスクをループに追加するには  
  
-   ドラッグ、 **Extract Sample Currency Data**データ フロー タスクの名前を変更した Foreach ループ コンテナーを`Foreach File in Folder`します。  
  
## <a name="next-lesson-task"></a>次のレッスンの作業  
 [手順 3: フラット ファイル接続マネージャーの変更](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a>参照  
 [Foreach ループ コンテナーを構成します。](control-flow/foreach-loop-container.md)   
 [パッケージで変数を使用する](use-variables-in-packages.md)  
  
  
