---
title: 基本的なテーブル レポートの作成 (SSRS チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
caps.latest.revision: 61
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: a5c3560a7aafd3fcf53f9b10d606e1f999bbf063
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196812"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>基本的なテーブル レポートの作成 (SSRS チュートリアル)
  このチュートリアルはに基づいて基本的なテーブル レポートを作成するために設計されています、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベースのレポート デザイナーを使用します。 レポートの作成には、レポート ビルダーまたはレポート ウィザードを使用することもできます。 ここでは、レポート プロジェクトの作成、接続情報の設定、クエリの定義、表のデータ領域、グループ フィールド、および合計フィールドの追加、レポートのプレビュー表示を行います。  
  
> [!NOTE]  
>  このチュートリアルを完了するには、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] をネイティブ モードで実行する必要があります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を SharePoint 統合モードで実行していると、レポート サーバーの URL を使用するステップを実行できません。 詳細については[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]モードを参照してください[Reporting Services レポート サーバー](reporting-services-report-server.md)します。  
  
## <a name="requirements"></a>要件  
 このチュートリアルを使用するには、システムに以下のコンポーネントがインストールされている必要があります。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] データベース エンジン  
  
-   [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース。  詳細については、次を参照してください。 [Adventure Works for SQL Server 2012 (SQL Server 2012 用 Adventure Works)](http://go.microsoft.com/fwlink/?LinkId=245471) (http://go.microsoft.com/fwlink/?LinkId=245471).します。 サポートの詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]サンプル データベースとサンプル コードの[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]を参照してください[Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391) CodePlex Web サイト。  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 データを取得する読み取り専用権限も必要、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベース。  
  
## <a name="tasks"></a>処理手順  
 [レッスン 1: レポート サーバー プロジェクトを作成する&#40;Reporting Services&#41;](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [レッスン 2: 接続情報を指定する&#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [レッスン 3: テーブル レポートのデータセットを定義する&#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [レッスン 4: レポートにテーブルを追加する&#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [レッスン 5: レポートの書式設定&#40;Reporting Services&#41;](lesson-5-formatting-a-report-reporting-services.md)  
  
 [レッスン 6: グループと合計の追加&#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  追加することをお勧めのチュートリアルを確認する際に**次**と**前**ドキュメント ビューアーのツールバーにボタン。 詳細については、以下を参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services チュートリアル &#40;SSRS&#41;](reporting-services-tutorials-ssrs.md)  
  
  
