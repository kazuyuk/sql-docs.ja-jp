---
title: シーケンス クラスター モデル (中級者向けデータ マイニング チュートリアル) で予測の作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 006418a07f393fd50334a2ea9c122cdd92353cda
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198302"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>シーケンス クラスター モデルでの予測の作成 (中級者向けデータ マイニング チュートリアル)
  予測クエリ ビルダーを使用して予測クエリを作成するには、シーケンス クラスター モデルの改善をビューアーで順を理解したら、**マイニング モデル予測**データ マイニング デザイナーのタブ。 予測を作成するには、まずシーケンス クラスター モデルを選択し、次に入力データを選択します。 入力については、外部データ ソースを使用するか、単一クエリを作成してダイアログ ボックスで値を指定することができます。  
  
 このレッスンでは、予測クエリ ビルダーの使用方法について理解していることを前提に、シーケンス クラスター モデルに固有のクエリの作成方法について説明します。 予測クエリ ビルダーを使用する方法については、次を参照してください[データ マイニング クエリ インターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)かの基本的なデータ マイニングのチュートリアルでは、セクション[を作成する予測&#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).  
  
## <a name="creating-predictions-on-the-regional-model"></a>地域モデルでの予測の作成  
 このシナリオでは、まずいくつかの単一予測クエリを作成し、予測が地域ごとにどのように異なるかについて確認します。  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>シーケンス クラスター モデルに対する単一クエリを作成するには  
  
1.  をクリックして、**マイニング モデル予測**データ マイニング デザイナーのタブ。  
  
2.  **マイニング モデルの**列メニューで、**単一クエリ**します。  
  
     **マイニング モデルの**ウィンドウと**単一クエリ入力**ウィンドウが表示されます。  
  
3.  **マイニング モデルの**ウィンドウで、をクリックして**モデルの選択**します。 (既にシーケンス クラスター モデルが選択されている場合は、この手順を省略します)。  
  
     **マイニング モデルの選択** ダイアログ ボックスが表示されます。  
  
4.  マイニング構造を表すノードを展開**Sequence Clustering with Region**、モデルを選択および**Sequence Clustering with Region**します。 **[OK]** をクリックします。 ここでは、入力ペインは無視します。入力は予測関数の設定後に指定します。  
  
5.  グリッドで空のセルをクリックします。**ソース**選択**予測関数。** 下のセルで**フィールド**、 **PredictSequence**します。  
  
    > [!NOTE]  
    >  使用することも、 **Predict**関数。 バージョンを選択することを確認するには、する場合は、 **Predict**関数の引数としてテーブル列を取得する.  
  
6.  **マイニング モデルの**ウィンドウで、入れ子になったテーブルを選択します。 `v Assoc Seq Line Items`、には、グリッドにドラッグすると、**条件と引数**のボックス、 **PredictSequence**関数。  
  
     ドラッグ アンド ドロップのテーブルおよび列名を使用すると、構文エラーのない複雑なステートメントを作成できます。 ただし、現在の他のオプションの引数を含むセルの内容を置き換えます、 **PredictSequence**関数。 その他の引数を表示するには、関数の 2 番目のインスタンスを参照用として一時的にグリッドに追加します。  
  
7.  をクリックして、**結果**予測クエリ ビルダーの上隅でボタンをクリックします。  
  
 期待どおりの結果には、という見出しの 1 つの列が含まれている**式**します。 **式**次のように列に 3 つの列を含む入れ子になったテーブルが含まれています。  
  
|$SEQUENCE|Line Number|[モデル]|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 この結果からわかることは何でしょうか。 入力を指定していないことに注意してください。 予測はケースの母集団全体に対して作成され、Analysis Services からは最も可能性の高い全体的な予測が返されます。  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>単一予測クエリへの入力の追加  
 この時点では、まだ入力を指定していません。 次のタスクでは使用して、**単一クエリ入力**ペイン、クエリにいくつかの入力を指定します。 まず、予測されたシーケンスがすべての地域で同じかどうかを判断するために、地域シーケンス クラスター モデルへの入力として [Region] を使用します。 次に、各予測の確率を追加するようにクエリを変更し、結果をフラット化して見やすくする方法について説明します。  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>特定の顧客グループの予測を生成するには  
  
1.  をクリックして、**デザイン**クエリ作成グリッドに戻るに予測クエリ ビルダーの左上隅のボタンをクリックします。  
  
2.  **単一クエリ入力**ダイアログ ボックスで、をクリックして、**値**ボックス`Region`を選択し、**ヨーロッパ**。  
  
3.  をクリックして、**結果**ヨーロッパの顧客の予測を表示するボタンをクリックします。  
  
4.  をクリックして、**デザイン**クエリ作成グリッドに戻るに予測クエリ ビルダーの左上隅のボタンをクリックします。  
  
5.  **単一クエリ入力**ダイアログ ボックスで、をクリックして、**値**ボックス`Region`を選択し、**北米**。  
  
6.  をクリックして、**結果**北米の顧客の予測を表示するボタンをクリックします。  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>カスタム式を使用した確率の追加  
 確率は予測の属性であり、入れ子になったテーブルとして出力されるので、各予測の確率を出力するのはやや複雑です。 データ マイニング拡張機能 (DMX) に慣れている場合は、入れ子になったテーブルに対する下位選択ステートメントを追加するようにクエリを簡単に変更できます。 また、予測クエリ ビルダーでカスタム式を追加して下位選択ステートメントを作成することもできます。  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>カスタム式を使用して予測されたシーケンスの確率を出力するには  
  
1.  をクリックして、**デザイン**クエリ作成グリッドに戻るに予測クエリ ビルダーの左上隅のボタンをクリックします。  
  
2.  グリッドで、**ソース**、新しい行をクリックし、選択**カスタム式**します。  
  
3.  下のまま**フィールド**空白。  
  
4.  **エイリアス**、型`t`します。  
  
5.  **条件と引数**ボックスに、次のコード サンプルで示すように、完全な下位選択ステートメントを入力します。 必ず開始かっこと終了かっこも入力してください。  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  をクリックして、**結果**ヨーロッパの顧客の予測を表示するボタンをクリックします。  
  
 結果に、2 つの入れ子になったテーブルが含まれるようになります。一方のテーブルには予測、もう一方のテーブルには予測の確率が示されます。 クエリが機能しない場合は、クエリ デザイン ビューに切り替えて、次のようなクエリ ステートメント全体を確認できます。  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a>結果の操作  
 結果に多数の入れ子になったテーブルが含まれている場合は、結果をフラット化して見やすくすることができます。 そのためには、クエリを手動で変更し、`FLATTENED` キーワードを追加します。  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>予測クエリで入れ子になった行セットをフラット化するには  
  
1.  をクリックして、**クエリ**予測クエリ ビルダーの隅にあるボタンをクリックします。  
  
     グリッドが開いたペインに変わり、予測クエリ ビルダーで作成された DMX ステートメントを表示および変更できるようになります。  
  
2.  `SELECT` キーワードの後に、「`FLATTENED`」と入力します。  
  
     クエリの完全なテキストは、次のようになります。  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  をクリックして、**結果**予測クエリ ビルダーの上隅でボタンをクリックします。  
  
 クエリを手動で編集した後、デザイン ビューに戻ると変更は失われます。 ただし、手動で作成した DMX ステートメントをテキスト ファイルに保存してからデザイン ビューに戻ることはできます。 この場合、クエリはデザイン ビューで有効であった最後のバージョンに戻ります。  
  
## <a name="creating-predictions-on-the-related-model"></a>関連モデルでの予測の作成  
 ここまでの例では、モデルで地域間の違いが見られたかどうかを確認するために、ケース テーブル列 [地域] を単一予測クエリへの入力として使用しました。 ただし、モデルの調査後に、その違いは地域ごとに製品の提案をカスタマイズするほど顕著なものではないと判断しました。 実際に予測する必要があるのは顧客が選択するアイテムです。 したがって、次のクエリでは、地域を含まないシーケンス クラスター モデルを使用して、すべての顧客に対する提案を生成します。  
  
### <a name="using-nested-table-columns-as-input"></a>入力としての入れ子になったテーブル列の使用  
 まず、単一のアイテムを入力として受け取り、次に選択される可能性が高いアイテムを返す単一予測クエリを作成します。 このような予測を得るには、入力値として入れ子になったテーブル列を使用する必要があります。 これは、予測する属性 "モデル" が入れ子になったテーブルの一部であるためです。 Analysis Services には、**入れ子になったテーブルの入力**で予測クエリを簡単に作成するためのダイアログ ボックスでは、予測クエリ ビルダーを使用してテーブルの属性が入れ子になった。  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>入れ子になったテーブルを予測への入力として使用するには  
  
1.  をクリックして、**デザイン**クエリ作成グリッドに戻るに予測クエリ ビルダーの左上隅のボタンをクリックします。  
  
2.  **単一クエリ入力**ダイアログ ボックスで、をクリックして、**値**ボックス`Region`、このフィールドの入力をクリアする空の行を選択します。  
  
3.  **単一クエリ入力**ダイアログ ボックスで、をクリックして、**値**ボックス`vAssocSeqLineItems`、し ([...]) ボタンをクリックします。  
  
4.  **入れ子になったテーブルの入力**ダイアログ ボックスで、をクリックして**追加**します。  
  
5.  新しい行の下にあるボックスをクリックします。 `Model`、一覧から Touring Tire を選択します。 **[OK]** をクリックします。  
  
6.  をクリックして、**結果**予測を表示するボタンをクリックします。  
  
 最初のアイテムとして Touring Tire を選択したすべての顧客に、次のアイテムとして以下のものがモデルによって提案されます。 モデルの調査によって、顧客が Touring Tire 製品と Touring Tire Tube 製品を一緒に購入することが多いとわかっているので、この提案は適切です。  
  
|$SEQUENCE|Line Number|[モデル]|  
|---------------|-----------------|-----------|  
|1||Touring Tire Tube|  
|2||Sport-100|  
|3||Long-Sleeve Logo Jersey|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>入れ子になったテーブルの入力を使用する一括予測クエリの作成  
 提案に使用できる予測がモデルによって作成されることを確認したので、次は外部データ ソースにマップされる予測クエリを作成します。 そのデータ ソースは、現在の製品を表す値を提供します。 顧客 ID と製品一覧を入力として提供する予測クエリを作成することが目的であるため、ケース テーブルとして顧客テーブルを、入れ子になったテーブルとして購入記録テーブルをそれぞれ追加します。 その後、提案を作成したときと同様に予測関数を追加します。  
  
 この手順は、レッスン 3 でマーケット バスケット シナリオ用の予測を作成したときと同じ手順です。ただし、シーケンス クラスター モデルの予測では、入力として注文も必要になります。  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>入れ子になったテーブルの入力を使用する予測クエリを作成するには  
  
1.  **マイニング モデルの**ウィンドウが選択されていない場合のシーケンス クラスター モデルを選択します。  
  
2.  **入力テーブルの選択**ダイアログ ボックスで、をクリックして**ケース テーブルの**します。  
  
3.  **テーブルの選択**ダイアログ ボックスで、データ ソースの注文を選択します。 **テーブル/ビュー名**リストで vAssocSeqOrders を選択してクリックして**OK**。  
  
4.  **入力テーブルの選択**ダイアログ ボックスで、をクリックして**入れ子になったテーブルの選択**します。  
  
5.  **テーブルの選択** ダイアログ ボックスの**データ ソース**注文を選択します。 **テーブル/ビュー名**一覧で、vAssocSeqLineItems を選択してクリックして**OK**します。  
  
     Analysis Services でリレーションシップの検出が試行され、データ型が一致して列名が類似している場合は、リレーションシップが自動的に作成されます。 作成されたリレーションシップが正しくない場合は、結合線を右クリックし、選択**接続の変更**、列を編集するマッピング、または結合線を右クリックして選択**削除**にリレーションシップを完全に削除します。 この場合、テーブルがデータ ソース ビューで既に結合されているため、これらのリレーションシップはデザイン ペインに自動的に追加されます。  
  
6.  グリッドに新しい行を追加します。 **ソース**、vAssocSeqOrders を選択および**フィールド**CustomerKey を選択します。  
  
7.  グリッドに新しい行を追加します。 **ソース**を選択します**予測関数**、および**フィールド**、 **PredictSequence**。  
  
8.  VAssocSeqLineItems をドラッグ、**条件と引数**ボックス。 末尾をクリックして、**条件と引数**ボックスし、次の引数を入力:`2`します。  
  
     完全なテキスト、**条件と引数**ボックスにする必要があります。 `[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. をクリックして、**結果**各顧客の予測を表示するボタンをクリックします。  
  
 これで、シーケンス クラスター モデルのチュートリアルは完了です。  
  
## <a name="next-steps"></a>次の手順  
 すべてのセクションを完了した場合、[中級者向けデータ マイニング チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)、次の手順は、データ マイニング拡張機能 (DMX) ステートメントを使用してモデルを構築する方法を学習して予測を生成します。 詳細については、次を参照してください。[の作成とクエリを実行するデータ マイニング モデルと DMX: チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)します。  
  
 プログラミングの概念について理解している場合は、分析管理オブジェクト (AMO) を使用してデータ マイニング オブジェクトをプログラムで操作することもできます。 詳細については、「 [AMO データ マイニング クラス](../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [シーケンス クラスター モデルのクエリ例](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [シーケンス クラスター モデルのマイニング モデル コンテンツ&#40;Analysis Services - データ マイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
