---
title: クロス検証レポートのメジャー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7d45c1ff8501dff8c74de22a16ac47b69c5375a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304644"
---
# <a name="measures-in-the-cross-validation-report"></a>相互検証レポートのメジャー
  相互検証では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はマイニング構造のデータを複数のセクションにパーティション分割し、構造および関連マイニング モデルのテストを反復的に実行します。 この分析に基づき、構造および各モデルの標準の精度のメジャーを出力します。  
  
 レポートでは、データ内のフォールドの数や各フォールド内のデータの量に関するいくつかの基本情報に加えて、データの分布を示す一連の一般的な基準が表示されます。 それぞれのセクションに対する一般的な基準を比較することで、構造またはモデルの信頼性を評価できます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、マイニング モデルの一連の詳細メジャーも表示されます。 これらのメジャーは、分析するモデルの種類や、不連続であるか連続であるかなど属性の型によって異なります。  
  
 ここでは、 **[相互検証]** レポートに含まれるメジャーおよびその意味の一覧を示します。 各メジャーの計算方法の詳細については、「 [クロス検証の式](cross-validation-formulas.md)」を参照してください。  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>相互検証レポートのメジャーの一覧  
 次の表は、相互検証レポートに表示されるメジャーの一覧を示します。 メジャーは、表の左の列に表示されている *テストの種類*でグループ化されています。 右の列には、レポートに表示されるメジャーの名前、および意味に関する簡単な説明を示します。  
  
|テストの種類|基準と説明|  
|---------------|-------------------------------|  
|クラスター|クラスター モデルに適用されるメジャー:<br /><br /> **尤度をケース**: このメジャーが通常がある可能性の度合いを示します、ケースが特定のクラスターに所属します。 <br />                      相互検証の場合、スコアが集計された後、ケースの数で割られます。スコアは、ケースの平均確率となります。|  
|分類|分類モデルに適用されるメジャー:<br /><br /> **真陽性**/<br />                      **負の値を true**/ **誤**/ **誤**: 行または値が予測された状態が対象の状態と一致するパーティションの数と予測確率は、指定されたしきい値を超えています。 対象の属性の不足値がある場合は除外すると、すべての値の数を意味追加されない場合が|  
||**合格/不合格**: が予測された状態が対象の状態と一致し、予測の確率値が 0 より大きい、行またはパーティション内の値の数します。|  
|Likelihood|Likelihood メジャーは、複数の種類のモデルに適用されます。<br /><br /> **リフト**: 実際の予測確率対テスト_ケースの周辺確率の比です。 対象の属性の不足値があるケースは除外されます。 通常、モデルが使用されるときに対象の結果の確率がどれだけ向上するかを示します。<br /><br /> **Root Mean Square Error**: すべてのパーティション ケースの平均誤差の平方根が対象の属性の不足値がある行の除外、パーティション内のケースの数で割った値します。 RMSE は、予測モデルの一般的な推定機能です。 スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。<br /><br /> **ログ スコア**: 各ケースの実際の確率の対数合計し、対象の属性の不足値がある行の除外、入力データセット内の行の数で割った値します。 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近い数値ほど、良いスコアになります。 生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。|  
|Estimation|連続する数値属性を予測する推定モデルのみに適用されるメジャー:<br /><br /> **Root Mean Square Error**: 予測値が実際の値と比較した場合の平均誤差。 RMSE は、予測モデルの一般的な推定機能です。 スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。<br /><br /> **平均絶対誤差**: 誤差の絶対合計の平均として計算されます、実際の値は予測値と比較した場合の平均誤差。 平均絶対誤差は、予測全体が実際の値にどの程度近いかを判断するときに便利です。 小さいスコアは、予測が正確だったことを意味します。<br /><br /> **ログ スコア**: 各ケースの実際の確率の対数合計し、対象の属性の不足値がある行の除外、入力データセット内の行の数で割った値します。 確率は小数で表されるので、ログ スコアは常に負の数値になります。 0 に近い数値ほど、良いスコアになります。 生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。|  
|集計|集計メジャーは、各パーティションの結果における分散を示す値を指定します。<br /><br /> **意味**: パーティションの平均が特定のメジャーの値します。<br /><br /> **標準偏差**:、モデル内のすべてのパーティションを対象の特定のメジャーの平均から偏差の平均です。 相互検証の場合、このスコアの値が高いことは、フォールドの間の変動が大きいことを意味します。|  
  
## <a name="see-also"></a>参照  
 [テストと検証&#40;データ マイニング&#41;](testing-and-validation-data-mining.md)  
  
  
