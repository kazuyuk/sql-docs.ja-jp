---
title: DQS の既定のナレッジ ベースの使用 | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2012
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4c1471ac1a575efc9423695385ff42ca20a7740f
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35311331"
---
# <a name="using-the-dqs-default-knowledge-base"></a>DQS の既定のナレッジ ベースの使用

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  このトピックでは、 **(DQS) にインストールされている既定のナレッジ ベース、** DQS データ [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] について説明します。 これは、次のドメインを含む、あらかじめ構築された既定のナレッジ ベースです。  
  
-   **国/地域**: 各地域の通常の長い名前 (国/地域が指定した公式名) と短縮名 (一覧やマップなどで一般に使用される名前)、2 文字の省略形、3 文字の省略形、各地域の 3 桁のコードが含まれます。  先頭の値は長い名前に設定されます。  
  
-   **国/地域 (3 文字が先頭)**: 各地域の通常の長い名前 (国/地域が指定した公式名) と短縮名 (一覧やマップなどで一般に使用される名前)、2 文字の省略形、3 文字の省略形、および 3 桁のコードが含まれます。  先頭の値は、3 文字の省略形に設定されます。  
  
-   **国/地域 (2 文字が先頭)**: 各地域の通常の長い名前 (国/地域が指定した公式名) と短縮名 (一覧やマップなどで一般に使用される名前)、2 文字の省略形、3 文字の省略形、各地域の 3 桁のコードが含まれます。  先頭の値は、2 文字の省略形に設定されます。  
  
-   **米国 - 郡**: 米国の郡の一覧が含まれています。  
  
-   **米国 - 姓**: 2000 年の国勢調査で 100 例以上登録された姓の一覧です。  
  
-   **米国 - 場所 -**: 2010 年の国勢調査から抽出された、50 州、コロンビア特別区、およびプエルトリコの地域の一覧です。  
  
-   **米国 - 州**: 米国の各州の通常の長い (公式) の名前と 2 文字の省略形が含まれます。 先頭の値は通常の州名に設定されます。  
  
-   **米国 - 州 (2 文字の省略形)**: 米国の各州の通常の長い (公式) の名前と 2 文字の省略形が含まれます。 先頭の値は、州名の 2 文字の省略形に設定されます。  
  
## <a name="using-the-default-knowledge-base"></a>既定のナレッジ ベースの使用  
 既定の DQS ナレッジ ベースである DQS データは、次の方法で使用します。  
  
-   既定のナレッジ ベースを使用してクレンジング データ品質プロジェクトを開始して実行します。先に DQS の新しいナレッジ ベースを作成する必要はありません。  
  
-   既定のナレッジ ベースで、ドメイン管理、ナレッジ検出、または照合ポリシーのアクティビティを実行します。 これを実行するには、 **Data Quality Client Home Screen** の [[ナレッジ ベースを開く]](../data-quality-services/data-quality-client-home-screen.md)をクリックし、 **[ナレッジ ベースを開く]** 画面の **[DQS Data]** ナレッジ ベースを選択して、 **[アクティビティの選択]** 領域で必要なアクティビティを選択します。 **[次へ]** をクリックします。  
  
-   既定のナレッジ ベースを使用して新しいナレッジ ベースを作成します。 既存のナレッジ ベースからナレッジ ベースを作成する方法については、「 [Create a Knowledge Base](../data-quality-services/create-a-knowledge-base.md)」を参照してください。  
  
-   「 [Integration Services の DQS クレンジング コンポーネント](http://go.microsoft.com/fwlink/?LinkId=238830) 」および「 [Excel 用マスター データ サービス アドイン](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)」で、それを使用します。  
  
## <a name="see-also"></a>参照  
 [DQS のナレッジ ベースとドメイン](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
