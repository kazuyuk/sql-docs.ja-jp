---
title: 使用法に基づく最適化ウィザードの F1 ヘルプ |Microsoft Docs
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
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8e01a630552f70586b3444394e143dc6978153d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229702"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>使用法に基づく最適化ウィザードの F1 ヘルプ
  使用法に基づく最適化ウィザードを使用するとパーティションの集計をデザインすることができ、その出力は集計のデザイン ウィザードに似ています。 ただし、使用法に基づく最適化ウィザードでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのクエリ ログに記録されているクエリの特定の使用パターンに基づいて集計をデザインします。 集計を利用するとパフォーマンスが向上しますが、これは [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] が各クエリの基となるデータ ソースからデータを取得して再計算を行うのではなく、キューブのストレージから直接、事前に計算された合計を取得するためです。  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]内から使用法に基づく最適化ウィザードを開くには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトのキューブ デザイナーを開き、 **[集計]** タブをクリックします。ツール バーの **[使用法に基づく最適化]** ボタンをクリックします。  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]内から使用法に基づく最適化ウィザードを開くには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続し、 **[キューブ]** フォルダーを開きます。 キューブを選択して **[メジャー グループ]** フォルダーを開き、変更するメジャー グループを展開します。 **[パーティション]** フォルダーを右クリックし、 **[使用法に基づく最適化]** をクリックします。  
  
 こうした集計のデザインは、集計のデザイン ウィザードを使用して行います。 このウィザードでは、次の手順に従います。  
  
-   パーティション、メジャー グループ、またはキューブのストレージとキャッシュのオプションに対して、標準またはカスタムの設定を選択します。  
  
-   パーティション、メジャー グループ、またはキューブによって参照されるオブジェクトの推定カウントまたは実際のカウントを指定します。  
  
-   集計オプションと制限を指定して、デザインされた集計によって配信されるストレージとクエリのパフォーマンスを最適化します。  
  
-   パーティション、メジャー グループ、またはキューブの保存と処理 (省略可) を行い、定義された集計を生成します。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 記憶域のサイズによって制限されることができますまたはパフォーマンスの向上の推定を集計デザインを提供するパーティションの構造の統計分析に基づいて集計をデザインする集計のデザイン ウィザードを提供します。 集計のデザイン ウィザードを使用するとパーティションの全体的なパフォーマンスを向上させることができますが、このウィザードの集計デザインはビジネス ユーザーの特定のニーズに合致したものではありません。 使用法に基づく最適化ウィザードでは、こうした特定のニーズに合致した集計デザインが可能ですが、このためには [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのクエリ ログに、こうしたクエリを構築するための十分な情報が記録されている必要があります。  
  
 通常、両方のウィザードを併用することで、配置後のパフォーマンスと長期的なパフォーマンスを向上させます。 パーティション (または、パーティションを含むキューブやメジャー グループ) を最初に配置するときに、まず集計のデザイン ウィザードを使用して全体的なパフォーマンスを向上させる必要があります。 その後、一定期間が経過してパーティションに対するビジネス ユーザーのクエリがクエリ ログに記録されたら、使用法に基づく最適化ウィザードを使用します。これにより、ビジネス ユーザーのクエリ要件に適応した、よりパフォーマンスの高い集計デザインを作成することができます。  
  
> [!NOTE]  
>  クエリ ログの構成については、「 [Analysis Services クエリ ログの構成](http://www.microsoft.com/technet/prodtechnol/sql/2005/technologies/config_ssas_querylog.mspx)」をご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [変更するパーティションを選択します&#40;使用法に基づく最適化ウィザード。&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [クエリ条件の指定&#40;使用法に基づく最適化ウィザード&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [最適化されたクエリを確認する&#40;使用法に基づく最適化ウィザード&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [集計使用法の確認&#40;Optimiation ウィザードの使用法に基づく&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [オブジェクト カウントの指定&#40;使用法に基づく最適化ウィザード&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [集計オプションの設定&#40;使用法に基づく最適化ウィザード&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [ウィザードの完了&#40;使用法に基づく最適化ウィザード&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>参照  
 [集計と集計デザイン](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [多次元モデルのキューブ](multidimensional-models/cubes-in-multidimensional-models.md)   
 [集計デザイン ウィザードの F1 ヘルプ](aggregation-design-wizard-f1-help.md)   
 [Analysis Services のウィザード&#40;多次元データ&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
