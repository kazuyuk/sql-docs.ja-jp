---
title: 'タスク 7: DQS クレンジング変換をデータ フローを追加する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3104a1fc5d3c1e4cb81ba9b74f6d3eb33798dc61
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196584"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a>タスク 7: DQS クレンジング変換をデータ フローに追加する
  ここでは、DQS クレンジング変換をデータ フローに追加して、入力済みの仕入先データを DQS を使用してクレンジングします。 参照してください **[DQS クレンジング変換](http://msdn.microsoft.com/library/ee677619.aspx)** 変換の詳細についてはします。  
  
1.  右クリックして**DQS クレンジング**で、**データ フロー**タブをクリックし、をクリックして**の名前を変更**します。 型**Cleanse Supplier Data**、キーを押します**ENTER**します。  
  
2.  選択**Read Supplier Data from Excel ファイル**; 青色コネクタをドラッグして**Cleanse Supplier Data**します。 これでコンポーネントが接続されました。  
  
     ![Read Supplier Data-> Cleanse Supplier Data](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Read Supplier Data-> 仕入先データのクレンジング")  
  
3.  ダブルクリック**仕入先データ クレンジング**します。  
  
4.  **DQS クレンジング変換エディター**、 をクリックして**新規**横に、**データ品質接続マネージャーの一覧から**します。  
  
5.  **DQS クレンジング接続マネージャー**ダイアログ ボックスに「 **(local)** または**期間**(.)、ローカル サーバーに接続します。 このレッスンは、ローカル サーバーに DQS がインストールされていることを前提としています。  
  
6.  クリックして**接続のテスト**DQS サーバーへの接続をテストします。  
  
7.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
8.  選択**Suppliers**の**データ品質ナレッジ ベース**します。  
  
     ![DQS クレンジング変換エディター - 仕入先 KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS クレンジング変換エディター - 仕入先 KB")  
  
9. 切り替えて、**マッピング**上部にあるタブ。  
  
10. **使用できる入力列**、 **Supplier Name**、 **ContactEmailAddress**、 **Address Line**、 **市区町村**、**状態**、**国**、および**郵便番号/zip Code**チェック ボックスをオンします。  
  
     ![DQS クレンジング変換エディター - マッピング](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS クレンジング変換エディター - マッピング")  
  
11. 下のペインで、これらの列をマップでのドロップダウン リストを使用して、**ドメイン**列。  
  
    |[列]|[ドメイン]|  
    |------------|------------|  
    |Supplier Name|Supplier Name|  
    |ContactEmailAddress|Contact Email|  
    |Address Line|Address Line|  
    |City|City|  
    |状態|状態|  
    |Country|Country|  
    |Zip Code|Zip|  
  
12. クリックして**OK**を閉じる、 **DQS クレンジング変換エディター**  ダイアログ ボックス。  
  
## <a name="next-step"></a>次の手順  
 [タスク 8: 条件分割変換を追加してクレンジング出力を分割する](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
