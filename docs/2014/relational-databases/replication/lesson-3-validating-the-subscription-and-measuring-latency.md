---
title: 'レッスン 3 : サブスクリプションの検証と待機時間の計測 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: beb76874d66e6808b2ec0e31bbdf22624d73edab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284918"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>レッスン 3 : サブスクリプションの検証と待機時間の計測
  このレッスンでは、トレーサー トークンを使用して、変更がサブスクライバーにレプリケートされているかどうかを検証し、待機時間を計測します。待機時間とは、パブリッシャーで加えられた変更がサブスクライバーに反映されるまでの所用時間です。 このレッスンを始める前に、前のレッスンの [「レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成」](lesson-2-creating-a-subscription-to-the-transactional-publication.md)を完了している必要があります。  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>トレーサー トークンを挿入してトークンの情報を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、 **[レプリケーション モニターの起動]** をクリックします。  
  
     レプリケーション モニターが起動します。  
  
2.  左ペインでパブリッシャー グループを展開し、パブリッシャー インスタンスを展開して、 **[AdvWorksProductTrans]** パブリケーションをクリックします。  
  
3.  **[トレーサー トークン]** タブをクリックします。  
  
4.  **[トレーサーの挿入]** をクリックします。  
  
5.  **[パブリッシャーからディストリビューターまで]** 列、 **[ディストリビューターからサブスクライバーまで]** 列、および **[合計待機時間]** 列で、トレーサー トークンの経過時間を表示します。 **[保留中]** と表示された場合は、トークンが特定のポイントに到達していないことを示します。  
  
## <a name="next-steps"></a>次の手順  
 このレッスンでは、トレーサー トークンを使用して、データの変更がパブリッシャーからスクライバへレプリケートされているかどうかを検証しました。 パブリッシャー側の **Product** テーブルに対してデータの挿入、更新、または削除を行い、レプリケーション後、サブスクライバー側の **Product** テーブルをクエリすることもできます。  
  
 チュートリアル「常時接続サーバー間でのデータのレプリケーション」はこれで完了です。 マージ レプリケーションを使用する類似のチュートリアルについては、 [「チュートリアル: モバイル クライアントとの間のデータのレプリケーション」](tutorial-replicating-data-with-mobile-clients.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [トランザクション レプリケーションの待機時間の計測および接続の検証](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
