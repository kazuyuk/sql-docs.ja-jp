---
title: サーバー グループ内の Analysis Services インスタンスの登録 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5fd3826b-8f75-48eb-910c-bf784163e53b
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 538b54cde0de7a49ff151f2f978346a2d8767317
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208082"
---
# <a name="register-an-analysis-services-instance-in-a-server-group"></a>サーバー グループへの Analysis Services インスタンスの登録
  多数の Analysis Services サーバー インスタンスがある場合、サーバー管理をより容易にするために Management Studio 内にサーバー グループを作成できます。 サーバー グループの目的は、管理ワークスペース内の関連するサーバーのグループで近接性を提供することです。 たとえば、10 個の独立した Analysis Services インスタンスを管理する必要があるとします。 サーバー モード、連続稼動条件、または部門や地域によってそれらをグループ化することで、同じ特徴を持つインスタンスをより簡単に表示および接続することができます。 サーバーがどのように使用されるかを思い出すために役立つ情報を追加することもできます。  
  
 ![登録済みサーバー ペインは、メンバー サーバーと](../media/ssas-ssms-registerserver.gif "とメンバー サーバーの登録済みサーバー ウィンドウ")  
  
 サーバー グループは、階層構造で作成することができます。 ローカル サーバー グループはルート ノードです。 これには、ローカル コンピューターで実行される Analysis Services のインスタンスが常に含まれます。 リモート サーバーは、ローカル グループを含む任意のグループに追加できます。  
  
 サーバー グループを作成後、[登録済みサーバー] ペインを使用してメンバー サーバーを表示および接続する必要があります。 このペインでは、サーバーの種類 (データベース エンジン、Analysis Services、Reporting Services、Integration Services) によって SQL Server インスタンスをフィルターします。 作成されたサーバー グループを表示するには、サーバーの種類をクリックします。 グループ内の特定のサーバーに接続するには、グループ内のサーバーをダブルクリックします。  
  
 サーバー名など、サーバーで定義されている接続情報は、サーバー登録によって保存されます。 接続情報を変更したり、他のツールを使用してサーバーに接続するときに登録名を使用したりはできません。  
  
## <a name="create-a-server-group-and-add-registered-servers"></a>サーバー グループの作成および登録サーバーの追加  
  
1.  Management Studio で、[表示] メニューの [登録済みサーバー] をクリックし、ワークスペースで [登録済みサーバー] ペインを開きます。 既定では、ローカル サーバー グループが既に作成されています。 ローカル サーバーで実行されている Analysis Services のすべてのインスタンスが、メンバーです。  
  
2.  [ローカル サーバー グループ] を右クリックし、[新しいサーバー グループ] を選択して、グループに名前を付けます。  
  
3.  サーバー グループを右クリックし、[新規サーバーの登録] をクリックします。 サーバーが名前付きインスタンスとしてインストールされた場合は、インスタンス名を含めて、ローカルまたはリモート サーバーのネットワーク名を入力します。 必要に応じて、[登録済みサーバー] に表示される、登録済みサーバーの名前を指定できます。 この名前は、[登録済みサーバー] でのみ使用されます。 サーバーの名前変更に使用することも、接続文字列に使用することもできません。 登録済みサーバー名は、実際のサーバー名よりもわかりやすくしたり、このサーバーを他のサーバーと区別するために他の識別特性を含めたりできます。  
  
  
