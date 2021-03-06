---
title: キューブ、パーティション、およびディメンションの処理 (SSAS - 多次元) のエラーの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.cubeproperties.errorconfiguration.f1
- sql12.asvs.sqlserverstudio.dimensionproperties.errorconfiguration.f1
- sql12.asvs.sqlserverstudio.partitionproperties.errorconfiguration.f1
ms.assetid: 3f442645-790d-4dc8-b60a-709c98022aae
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3edb4e923424def48ff3cacdd9eb8967f8cb6579
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275918"
---
# <a name="error-configuration-for-cube-partition-and-dimension-processing-ssas---multidimensional"></a>キューブ、パーティション、およびディメンションに関する処理のエラー構成 (SSAS - 多次元)
  処理中にデータ整合性エラーが発生した場合、キューブ、パーティション、またはディメンション オブジェクトのエラー構成プロパティによって、サーバーの応答が決定します。 通常、キー列の重複キー、見つからないキー、および NULL 値がこのようなエラーをトリガーします。エラーの原因となるレコードはデータベースに追加されず、次の動作を指定するプロパティを設定することができます。 既定では、処理が停止します。 ただし、キューブの開発中に、不完全でもインポートされたデータのキューブの動作をテストできるように、エラーが発生した場合に処理を続行する必要がある場合もあります。  
  
 このトピックのセクションは次のとおりです。  
  
-   [実行順序](#bkmk_exec)  
  
-   [既定の動作](#bkmk_default)  
  
-   [エラー構成プロパティ](#bkmk_props)  
  
-   [エラー構成プロパティを設定する場所](#bkmk_tools)  
  
-   [見つからないキー (KeyNotFound)](#bkmk_missing)  
  
-   [ファクト テーブルの NULL 外部キー (KeyNotFound)](#bkmk_nullfact)  
  
-   [ディメンションの NULL キー](#bkmk_nulldim)  
  
-   [一貫性のないリレーションシップをもたらす重複キー (KeyDuplicate)](#bkmk_dupe)  
  
-   [エラーの上限またはエラーの上限のアクションの変更](#bkmk_limit)  
  
-   [エラー ログ パスの設定](#bkmk_log)  
  
-   [次の手順](#bkmk_next)  
  
##  <a name="bkmk_exec"></a> 実行順序  
 サーバーが常に実行`NullProcessing`ルールの前に`ErrorConfiguration`各レコードの規則。 複数のエラー レコードのキー列にゼロがある場合、NULL をゼロに変換する NULL 処理プロパティによって後で重複キー エラーが生じる可能性があるため、この点を理解することが重要です。  
  
##  <a name="bkmk_default"></a> 既定の動作  
 既定では、処理はキー列が関係する最初のエラーで停止します。 この動作は、許可されたエラーの数としてゼロを指定するエラーの上限およびそのエラーの上限に達した場合にサーバーに処理の停止を指示する処理の停止ディレクティブによって制御されます。  
  
 NULL、または値が見つからないか、重複するために、エラーをトリガーするレコードは、不明なメンバーに変換されるか、破棄されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、データ整合性制約に違反するデータはインポートされません。  
  
-   ために既定では、不明なメンバーへの変換が発生する、`ConvertToUnknown`設定`KeyErrorAction`します。 不明なメンバーに割り当てられたレコードは、処理が完了した後で調査する必要がある問題の証拠としてデータベースで検疫されます。  
  
     不明なメンバーは、クエリ ワークロードから除外されますが、一部のクライアント アプリケーションで表示される場合、`UnknownMember`に設定されている**Visible**します。  
  
     不明なメンバーに変換された NULL の数を追跡する場合、`NullKeyConvertedToUnknown` プロパティを変更して、ログまたは処理ウィンドウでエラーを報告することができます。  
  
-   破棄は、手動で設定するときに発生します。、`KeyErrorAction`プロパティを`DiscardRecord`します。  
  
 エラー構成プロパティによって、エラーが発生した場合にサーバーがどのように応答するかを決定することができます。 オプションには、処理を直ちに停止する、処理は続行するがログ記録は停止する、または処理とエラーのログ記録の両方を続行するがあります。 既定値はエラーの重大度によって異なります。  
  
 エラー数は、エラーが発生した数を記録します。 上限を設定すると、この上限に達した場合にサーバーの応答が変更されます。 既定では、サーバーは上限に達すると処理を停止します。 既定の上限は 0 で、カウントされる最初のエラーで処理が停止します。  
  
 キー フィールドでキーが見つからない、または NULL 値のような影響が大きいエラーには、すぐに対処する必要があります。 既定では、これらのエラーに従う`ReportAndContinue`サーバーの動作、場所、サーバーは、エラーをキャッチ エラーの数に追加して処理を続行 (点を除いて、エラーの上限がゼロのため、処理は直ちに停止されます)。  
  
 他のエラーは、必ずしもデータ整合性の問題を引き起こすわけではないため、生成されても既定では数えられないか、ログに記録されません (これが `IgnoreError` 設定です)。  
  
 エラー数は、NULL 処理設定の影響を受けます。 ディメンション属性の場合、NULL 処理オプションによって NULL 値が発生した場合のサーバーの応答が決定されます。 既定では、文字列型の列の NULL は空の文字列として処理されますが、数値列の NULL はゼロに変換されます。 `NullProcessing` プロパティをオーバーライドして、`KeyNotFound` エラーまたは `KeyDuplicate` エラーになる前に NULL 値を見つけるようにできます。 詳細については、「 [ディメンションの NULL キー](#bkmk_nulldim) 」を参照してください。  
  
 エラーは [処理] ダイアログ ボックスで記録されますが、保存されません。 テキスト ファイル内でエラーを収集するキー エラー ログ ファイルの名前を指定できます。  
  
##  <a name="bkmk_props"></a> エラー構成プロパティ  
 エラー構成プロパティは 9 つあります。 特定のエラーが発生した場合のサーバーの応答を決定するために 5 つのプロパティが使用されます。 他の 4 つは、許可されるエラー数、上限に達した場合の動作、ログ ファイルでエラーを収集するかどうかなど、エラー構成のワークロードに範囲が設定されます。  
  
 **特定のエラーに対するサーバーの応答**  
  
|プロパティ|既定|その他の値|  
|--------------|-------------|------------------|  
|`CalculationError`<br /><br /> エラー構成を初期化するときに発生します。|`IgnoreError` ログ記録やカウント エラーです。エラーの数が上限限り処理を続行します。|`ReportAndContinue` ログに記録して、エラーの数します。<br /><br /> `ReportAndStop` エラーを報告し、エラーの上限に関係なく、すぐに処理を停止します。|  
|`KeyNotFound`<br /><br /> ファクト テーブルの外部キーに関連ディメンション テーブルで一致する主キーがない場合に発生します (たとえば、Sales ファクト テーブルに Product ディメンション テーブルに存在しない製品 ID のレコードがあります)。 このエラーは、パーティションの処理中、またはスノーフレーク ディメンションのディメンション処理中に発生する可能性があります。|`ReportAndContinue` ログに記録して、エラーの数します。|`ReportAndStop` エラーを報告し、エラーの上限に関係なく、すぐに処理を停止します。<br /><br /> `IgnoreError` ログ記録やカウント エラーです。エラーの数が上限限り処理を続行します。 このエラーをトリガーするレコードは、既定では不明なメンバーに変換されますが、`KeyErrorAction` プロパティを変更して代わりに破棄することもできます。|  
|`KeyDuplicate`<br /><br /> 重複した属性キーがディメンションに見つかったときに発生します。 ほとんどの場合、重複した属性キーは許容されますが、このエラーは重複を通知するため、属性間の一貫性のないリレーションシップにつながる可能性があるデザインの不具合についてディメンションを確認することができます。|`IgnoreError` ログ記録やカウント エラーです。エラーの数が上限限り処理を続行します。|`ReportAndContinue` ログに記録して、エラーの数します。<br /><br /> `ReportAndStop` エラーを報告し、エラーの上限に関係なく、すぐに処理を停止します。|  
|`NullKeyNotAllowed`<br /><br /> 発生したときに`NullProcessing`  =  `Error`ディメンションの属性またはメンバーを一意に識別するために使用される属性キー列に null 値が存在する場合に設定します。|`ReportAndContinue` ログに記録して、エラーの数します。|`ReportAndStop` エラーを報告し、エラーの上限に関係なく、すぐに処理を停止します。<br /><br /> `IgnoreError` ログ記録やカウント エラーです。エラーの数が上限限り処理を続行します。 このエラーをトリガーするレコードは、既定では、不明なメンバーに変換されますが、設定することができます、`KeyErrorAction`して代わりに破棄するプロパティ。|  
|`NullKeyConvertedToUnknown`<br /><br /> NULL 値がその後、不明なメンバーに変換されたときに発生します。 設定`NullProcessing`  =  `ConvertToUnknown`ディメンションの属性は、このエラーをトリガーします。|`IgnoreError` ログ記録やカウント エラーです。エラーの数が上限限り処理を続行します。|このエラーが情報であると判断した場合は、既定値のままにします。 それ以外の場合は、`ReportAndContinue` を選択して、エラーを処理ウィンドウに報告し、エラーの上限にエラーを加算することができます。<br /><br /> `ReportAndStop` エラーを報告し、エラーの上限に関係なく、すぐに処理を停止します。|  
  
 **全般プロパティ**  
  
|**プロパティ**|**値**|  
|------------------|----------------|  
|`KeyErrorAction`|これは、サーバーによって実行されるアクションと、`KeyNotFound`エラーが発生します。 このエラーに対する有効な応答を含める`ConvertToUnknown`または`DiscardRecord`します。|  
|`KeyErrorLogFile`|サービス アカウントが読み取り/書き込み権限を持つフォルダーにある、.log ファイル拡張子を持つ必要があるユーザー定義のファイル名です。 このログ ファイルには、処理中に生成されたエラーのみが含まれます。 詳細情報が必要な場合はフライト レコーダーを使用します。|  
|`KeyErrorLimit`|処理が失敗するまでにサーバーが許可するデータ整合性エラーの最大数です。 値が 1 の場合は、数に制限がないことを示します。 既定値は 0 です。これは、最初のエラーが発生した後に処理が停止することを意味します。 整数に設定することもできます。|  
|`KeyErrorLimitAction`|これはキー エラー数が上限に達した場合にサーバーが実行するアクションです。 **[処理の停止]** を選択すると、処理は直ちに終了します。 **[ログの停止]** を選択すると、処理は続行されますが、エラーは報告またはカウントされなくなります。|  
  
##  <a name="bkmk_tools"></a> エラー構成プロパティを設定する場所  
 データベースを配置した後に [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、または [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のモデル プロジェクトで、プロパティ ページを使用します。 両方のツールで同じプロパティが見つかります。 設定することもエラー構成プロパティのエラー構成、およびサーバーの既定値を変更する、msmdrsrv.ini ファイルで`Batch`と`Process`コマンド、スクリプト操作として処理されるかどうか。  
  
 スタンドアロン操作として処理できるすべてのオブジェクトのエラー構成を設定できます。  
  
#### <a name="sql-server-management-studio"></a>[SQL Server Management Studio]  
  
1.  オブジェクト エクスプローラーで、 **[プロパティ]** 、ディメンション、キューブ、パーティションのオブジェクトの 1 つを右クリックします。  
  
2.  [プロパティ] で、 **[エラーの構成]** をクリックします。  
  
#### <a name="sql-server-data-tools"></a>SQL Server Data Tools  
  
1.  ソリューション エクスプローラーで、ディメンションまたはキューブをダブルクリックします。 `ErrorConfiguration` 下のペインでは、プロパティが表示されます。  
  
2.  また、ディメンションが 1 つのみ、ソリューション エクスプ ローラーでディメンションを右クリックし、選択`Process`を選び、**設定の変更**ディメンションの処理 ダイアログ ボックス。 エラー構成オプションが [ディメンション キーのエラー] タブに表示されます。  
  
##  <a name="bkmk_missing"></a> 見つからないキー (KeyNotFound)  
 見つからないキーの値を持つレコードは、エラーが無視される場合またはエラーの上限が無制限である場合でも、データベースに追加できません。  
  
 サーバーの生成、`KeyNotFound`でファクト レコードのテーブルに外部キーの値が含まれていますが、外部キーは関連ディメンション テーブルに対応するレコードがない場合に、パーティション処理中にエラー。 また、このエラーは、関連するディメンション テーブルまたはスノーフレーク ディメンション テーブルを処理する場合に発生し、1 つのディメンションのレコードは関連するディメンションに存在しない外部キーを指定します。  
  
 `KeyNotFound` エラーが発生すると、問題のあるレコードは不明なメンバーに割り当てられます。 この動作はによって制御されます、**キー アクション**に設定して、 `ConvertToUnknown`、詳しい調査のために割り当てられたレコードを表示できるようにします。  
  
##  <a name="bkmk_nullfact"></a> ファクト テーブルの NULL 外部キー (KeyNotFound)  
 既定では、ファクト テーブルの外部キー列の NULL 値はゼロに変換されます。 ゼロは有効な外部キー値ではないとして、`KeyNotFound` エラーはログ記録され、既定ではゼロであるエラーの上限に加算されます。  
  
 処理を続行できるように、変換してエラーを確認する前に NULL を処理します。 これを行うには、次のように設定します。`NullProcessing`に`Error`します。  
  
#### <a name="set-nullprocessing-property-on-a-measure"></a>メジャーでの NullProcessing プロパティの設定  
  
1.  SQL Server Data Tools のソリューション エクスプローラーで、キューブをダブルクリックしてキューブ デザイナーで開きます。  
  
2.  [メジャー] ペインのメジャーを右クリックし、 **[プロパティ]** をクリックします。  
  
3.  [プロパティ] を展開**ソース**を表示する`NullProcessing`プロパティ。 これは既定では、OLAP アイテム用である **[自動]** に設定され、数値データを含むフィールドの NULL をゼロに変換します。  
  
4.  値を変更`Error`null から数値 (ゼロ) 変換を回避しながら、null 値を持つレコードを除外します。 この変更では、キーの列にゼロがある複数のレコードに関連するキーの重複エラーを回避し、回避することもできます。`KeyNotFound`エラー値が 0 の外部キーに関連するディメンション テーブルに等価な主キーがないです。  
  
##  <a name="bkmk_nulldim"></a> ディメンションの NULL キー  
 Null 値がスノーフレーク ディメンションの外部キーに見つかったときの処理を続行するには、null 値を最初に処理を設定して`NullProcessing`で、`KeyColumn`のディメンションの属性。 これは、`KeyNotFound` エラーが発生する前に、レコードを破棄または変換します。  
  
 ディメンション属性の NULL の処理には、次の 2 つのオプションがあります。  
  
-   設定`NullProcessing` = `UnknownMember`に null 値を持つレコードを不明なメンバーに割り当てます。 これによって、既定では無視される、`NullKeyConvertedToUnknown` エラーが生成されます。  
  
-   設定`NullProcessing` = `Error` null 値を持つレコードを除外します。 これが生成されます、`NullKeyNotAllowed`エラーをログに記録されるとカウント、キー エラーの上限に加算します。 エラー構成プロパティを設定することができます**Null 許可されていないキー**に`IgnoreError`処理を続行できるようにします。  
  
 NULL は非キー フィールドで問題になる可能性があります。NULL がゼロまたは空として解釈されるかどうかによって MDX クエリが異なる結果を返します。 このため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には変換動作をあらかじめ定義するために使用できる NULL 処理オプションが用意されています。 参照してください[不明なメンバーと Null 処理のプロパティを定義する](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)と<xref:Microsoft.AnalysisServices.NullProcessing>詳細についてはします。  
  
#### <a name="set-nullprocessing-property-on-a-dimension-attribute"></a>ディメンション属性での NullProcessing プロパティの設定  
  
1.  SQL Server Data Tools のソリューション エクスプローラーで、ディメンションをダブルクリックしてディメンション デザイナーで開きます。  
  
2.  [属性] ペインの属性を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  [プロパティ] を展開**KeyColumns**を表示する`NullProcessing`プロパティ。 これは既定では、 **[自動]** に設定され、数値データを含むフィールドで NULL をゼロに変換します。 いずれかに値を変更`Error`または`UnknownMember`します。  
  
     この変更は、基になるをトリガーする条件を削除します。`KeyNotFound`を破棄またはエラーを確認する前に、レコードを変換しています。  
  
     エラーの構成に応じて、報告およびカウントされるエラーがこれらのアクションのいずれかによって発生する場合があります。 設定など、追加のプロパティを調整する必要があります`KeyNotFound`に`ReportAndContinue`または`KeyErrorLimit`処理をこれらのエラーが報告されて、カウント時に続行できるように、0 以外の値にします。  
  
##  <a name="bkmk_dupe"></a> 一貫性のないリレーションシップをもたらす重複キー (KeyDuplicate)  
 既定では、重複キーの存在によって処理は停止されませんが、エラーは無視され、重複するレコードはデータベースから除外されます。  
  
 この動作を変更する設定`KeyDuplicate`に`ReportAndContinue`または`ReportAndStop`エラーを報告します。 次に、このエラーを調査して、ディメンションのデザインの潜在的な不具合を確認することができます。  
  
##  <a name="bkmk_limit"></a> エラーの上限またはエラーの上限のアクションの変更  
 エラーの上限を引き上げて、処理中により多くのエラーを見逃すようにできます。 エラーの上限を引き上げるためのガイダンスはありません。適切な値は使用しているシナリオによって異なります。 エラーの上限は、として指定`KeyErrorLimit`で`ErrorConfiguration`プロパティ[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]、または**エラー数**ディメンションのプロパティのエラー構成 タブ、キューブ、メジャー グループで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。  
  
 エラーの上限に達すると、処理を停止するか、ログ記録を停止するかを指定できます。 たとえば、アクションに設定する`StopLogging`100 のエラーの上限にします。 101 番目のエラーでは、処理は続行されますが、エラーはログ記録されなくなります。 エラーの上限アクションは、として指定`KeyErrorLimitAction`で`ErrorConfiguration`プロパティ[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]、または**エラー アクションに**ディメンションのプロパティのエラー構成 タブ、キューブ、メジャー グループで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="bkmk_log"></a> エラー ログ パスの設定  
 ファイルを指定して、処理中に報告されるキー関連のエラー メッセージを保存することができます。 既定では、エラーは処理ウィンドウでの対話形式の処理中には表示され、ウィンドウまたはセッションを閉じると破棄されます。 ログには、処理ダイアログ ボックスに表示されるエラーと同一の、キーに関連するエラー情報のみが含まれます。  
  
 エラーはテキスト ファイルにログ記録され、.log ファイル拡張子が必要です。 ファイルはエラーが発生しなければ空です。 既定では、ファイルは DATA フォルダーに作成されます。 Analysis Services サービス アカウントがその場所に書き込むことができる限り、別のフォルダーを指定することができます。  
  
##  <a name="bkmk_next"></a> 次の手順  
 エラーによって処理を停止するか、または無視するかを決定します。 エラーのみが無視されることに注意してください。 エラーの原因となったレコードは無視されず、破棄されるか、不明なメンバーに変換されます。 データの整合性規則に違反するレコードは、データベースには追加されません。 既定では、最初のエラーが発生したときに処理が停止しますが、エラーの上限を引き上げることによってこれを変更できます。 キューブの開発では、処理を続行できるようにエラー構成ルールを緩和することが役立つ場合があります。これによって、確認するデータが存在するようになります。  
  
 既定の NULL 処理動作を変更するかどうかを決定します。 既定では、文字列型の列の NULL は空の値として処理されますが、数値列の NULL はゼロとして処理されます。 属性に対して NULL 処理を設定する手順については、「 [不明なメンバーと NULL 処理のプロパティの定義](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md) 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ログのプロパティ](../server-properties/log-properties.md)   
 [不明なメンバーと NULL 処理のプロパティの定義](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
  
