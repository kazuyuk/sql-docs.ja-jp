---
title: パーソナル化による OLAP の拡張 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf7785c3acd3815f78e656951e8ae3f05e125245
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280358"
---
# <a name="extending-olap-through-personalizations"></a>パーソナル化による OLAP の拡張
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] には、多次元式 (MDX) やデータ マイニング拡張機能 (DMX) 言語と組み合わせて使用できる組み込み関数が豊富に用意されています。 これらの関数は、標準的な統計計算から階層に含まれるメンバーのスキャンまで、さまざまな処理に対応できるように設計されています。 ただしと他の複雑で強力な製品はあります常にこのような製品もの機能を拡張する必要が。  
  
 そのため、Analysis Services は、標準機能だけでは満たすことのできないビジネス ニーズを補うために、サービスのインスタンスにアセンブリやパーソナル化された拡張機能を追加できるようになっています。  
  
## <a name="assemblies"></a>アセンブリ  
 アセンブリにより、MDX と DMX のビジネス機能の拡張が可能になります。 必要な機能をダイナミック リンク ライブラリ (DLL) などのライブラリとして作成し、このライブラリをアセンブリとして Analysis Services のインスタンスまたは Analysis Services データベースに追加します。 ライブラリ内のパブリック メソッドは、ユーザー定義関数として、MDX および DMX 式、プロシージャ、計算、動作、およびクライアント アプリケーションに公開されます。  
  
## <a name="personalized-extensions"></a>パーソナル化拡張機能  
 SQL Server Analysis Services のパーソナル化拡張機能は、プラグイン アーキテクチャを実装するという概念の基盤です。 Analysis Services のパーソナル化拡張機能は、既存のマネージド アセンブリ アーキテクチャに対する単純で簡潔な変更で、Analysis Services の <xref:Microsoft.AnalysisServices.AdomdServer> オブジェクト モデル、多次元式 (MDX) 構文、およびスキーマ行セット全体で公開されます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../multidimensional-model-assemblies-management.md)   
 [Analysis Services のパーソナル化拡張機能](analysis-services-personalization-extensions.md)  
  
  
