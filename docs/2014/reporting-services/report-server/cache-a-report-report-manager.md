---
title: レポートのキャッシュ (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5b33fba7407dad306db7bed7b78d3a6d078c1c62
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301722"
---
# <a name="cache-a-report-report-manager"></a>レポートのキャッシュ (レポート マネージャー)
  パフォーマンスを向上させる方法の 1 つに、レポートのキャッシュ プロパティを構成するという方法があります。 レポートをキャッシュに格納した場合、表示されたレポートのコピーが短時間、保存されます。 レポートを要求した 1 人目のユーザーは、すべての処理が完了しないとレポートを閲覧できませんが、 それ以降、同じレポートを要求したユーザーは、キャッシュの保持時間内であれば、処理が既に完了しているため、すぐにレポートを閲覧できます。  
  
 キャッシュできるレポートの種類には制限があります。 たとえば、レポート出力がユーザー ID によって異なる場合や、レポートを要求したユーザーのセキュリティ トークンを使ってデータが取得される場合、レポートをキャッシュすることはできません。 詳細については、「 [レポートのキャッシュ (SSRS)](caching-reports-ssrs.md)でキャッシュを事前に読み込む唯一の方法でした。  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>キャッシュされたレポートの有効期限をスケジュールするには  
  
1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 キャッシュ プロパティを設定するレポートに移動し、アイテムの上にマウス ポインターを移動して、下矢印をクリックします。  
  
3.  ドロップダウン メニューの **[管理]** をクリックします。  
  
4.  左フレームの **[処理オプション]** をクリックします。  
  
5.  このページで、 **[常に最新データを使用して、このレポートを実行する]** を選択します。  
  
6.  次の 2 つのキャッシュ オプションのいずれかを選択し、以下のように有効期限を構成します。  
  
    -   キャッシュされたコピーが、特定の期間が過ぎた後で有効期限が切れるように構成するには、**レポートの一時コピーをキャッシュします。レポートのコピーの有効期限は数分後に切れます** をクリックします。 レポートの有効期限を分単位で入力します。  
  
    -   キャッシュされたコピーが、スケジュールに基づいて有効期限が切れるように構成するには、**[レポートの一時コピーをキャッシュします。次のスケジュールでレポートのコピーの有効期限は切れます。]** をクリックします。 **[構成]** をクリックするか、レポートの有効期限を制御する共有スケジュールを選択します。  
  
7.  **[適用]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート処理プロパティを設定します。](set-report-processing-properties.md)   
 [レポートのキャッシュ&#40;SSRS&#41;](caching-reports-ssrs.md)  
  
  
