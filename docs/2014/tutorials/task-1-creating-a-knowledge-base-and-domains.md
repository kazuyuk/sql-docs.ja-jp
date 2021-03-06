---
title: 'タスク 1: ナレッジ ベースとドメインを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9114289ed2a4e09a5f7b59ed016c553c1d225dfc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226582"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a>タスク 1: ナレッジ ベースとドメインを作成する
  は、このタスクを作成、 **Suppliers**ナレッジ ベースを重複を削除するデータのクレンジングおよびデータの照合に使用されるドメインを作成するとします。  
  
1.  起動**Data Quality Client**します。 クリックして**開始**、 をポイント**すべてのプログラム**、 をクリックして**Microsoft SQL Server 2012**、 をクリックして**Data Quality Services**順にクリックします**Data Quality Client**します。  
  
2.  **サーバーへの接続** ダイアログ ボックスで、データベース サーバー インスタンスを DQS がインストールされているし、クリックを選択**Connect**します。  
  
     ![サーバー ダイアログ ボックスへの接続](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "サーバー ダイアログ ボックスへの接続")  
  
3.  Data Quality Client のホーム ページの**ナレッジ ベース管理**ウィンドウで、をクリックして**新しいナレッジ ベース**します。  
  
     ![ナレッジ ベースの管理 - 新しい KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "ナレッジ ベースの管理 - 新しい KB")  
  
4.  入力**Suppliers**の**名前**ナレッジ ベースの。  
  
     ![新しいナレッジ ベース - ドメイン管理](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "新しいナレッジ ベースのドメインの管理")  
  
5.  確認します**からナレッジ ベースを作成する**にフィールドが設定されている**None**作成しているため、 **Suppliers**ナレッジ ベースを最初から。  
  
6.  確認します**ドメイン管理**が選択されている、**アクティビティ** をクリック**次**します。 ドメイン管理アクティビティを使用すると、ナレッジ ベース内のドメインを作成および管理できます。  
  
7.  **ドメイン管理**ウィンドウで、をクリックして**ドメインを作成する**ドメインを作成するツール バー ボタン。  
  
     ![ツール バー ボタンのドメインを作成する](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "ドメイン ツール バー ボタンの作成")  
  
8.  **ドメインの作成**ダイアログ ボックスに「 **Supplier ID**の、**ドメイン名** をクリック**OK**します。  
  
     ![ドメイン ダイアログ ボックスを作成する](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "ドメイン ダイアログ ボックスの作成")  
  
9. 前の手順を繰り返して、すべて既定の設定になっている次のドメインを作成します。 このチュートリアルを簡潔にするに設定する、**データ型**としてすべてのドメインの**文字列**します。 他に使用できるデータ型には、Integer、Decimal、および Date があります。 ときに、**先頭の値を使用して**オプションが選択されている (既定値)、すべてのシノニムは出力に、シノニムのグループの先頭の値に置き換えられます。 設定**文字列を正規化**オプション (既定)、ドメインの値で特殊文字を削除します。 **形式の出力先**オプションを使用して、ドメイン内のデータ値が出力時に適用される書式設定を選択できます。 選択**スペル チェックを有効にする**ドメインを設定するときに、すべての文字列値に対してスペル チェックを実行するには、(既定)。 **言語**の言語バージョンを指定する設定、**スペル チェック**を適用します。 選択**構文エラーのアルゴリズムを無効にする**に構文エラーの文字列値をチェックせずにドメインを設定します。 参照してください[ドメインを作成する](http://msdn.microsoft.com/library/hh510401.aspx)詳細については、MSDN ライブラリのトピックです。  
  
    -   Supplier Name  
  
    -   Contact Email  
  
    -   Address Line  
  
    -   City  
  
    -   状態  
  
    -   Country  
  
    -   Zip  
  
## <a name="next-step"></a>次の手順  
 [タスク 2: ドメイン値を手動で追加する](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
