---
title: 明示的階層を作成する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d75b956b6d9be23bd17e3df705724d3876d583
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219492"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>明示的階層を作成する (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で任意のレベルでメンバーが存在できる不規則階層が必要な場合、明示的階層を作成します。 明示的階層には、1 つのエンティティのメンバーが含まれています。  
  
 明示的階層を作成したら、 **[エクスプローラー]** 機能領域で明示的階層にメンバーを追加できます。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[システム管理]** 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](administrators-master-data-services.md)」を参照してください。  
  
-   エンティティは、明示的階層およびコレクションに対して有効化されている必要があります。 詳細については、次を参照してください。[明示的階層およびコレクションに対してエンティティを有効にする&#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)します。  
  
### <a name="to-create-an-explicit-hierarchy"></a>明示的階層を作成するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。  
  
2.  **[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。  
  
3.  **[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  明示的階層を作成するエンティティの行を選択します。  
  
5.  **[選択したエンティティの編集]** をクリックします。  
  
6.  **エンティティの編集**] ページの [、**明示的階層**ウィンドウで、をクリックして**明示的階層の追加**します。  
  
7.  **明示的階層の追加**ページで、**明示的階層名**ボックスに、階層の名前を入力します。  
  
8.  必要に応じて、 **[必須階層]** チェック ボックスをオフにして、任意の階層として明示的階層を作成します。 階層の種類の詳細については、「[明示的階層 (マスター データ サービス)](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)」を参照してください。  
  
9. クリックして**階層の保存**します。  
  
10. **エンティティの編集**] ページで [**エンティティの保存**します。  
  
## <a name="next-steps"></a>次の手順  
  
-   [統合メンバーを作成&#40;マスター データ サービス&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [階層内のメンバーを移動&#40;マスター データ サービス&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [明示的階層&#40;マスター データ サービス&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [明示的なキャップを持つ派生階層 &#40;マスター データ サービス&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [明示的階層名を変更する&#40;マスター データ サービス&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
