---
title: Integration Services サーバー上のパッケージの一覧を表示する | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f301b1e98d58d39c1d060bc3270349d0f2448cfd
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35408164"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Integration Services サーバー上のパッケージの一覧を表示する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに格納されているパッケージの一覧は、次の 2 つの方法のいずれかで表示できます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセス  
 サーバーに格納されているパッケージの一覧を表示するには、ビュー [catalog.packages (SSISDB データベース)](../../integration-services/system-views/catalog-packages-ssisdb-database.md) に対してクエリを実行します。  
  
 In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーを使用して、サーバーに格納されているパッケージを表示するには、次の手順を実行します。  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>パッケージを表示するには - [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。 つまり、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] データベースをホストする [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。  
  
3.  **[Integration Services カタログ]** ノードを展開して、 **[SSISDB]** ノードを表示します。  
  
4.  **[SSISDB]** ノードを展開して、1 つ以上のフォルダーの一覧を表示します。 各フォルダーの **[プロジェクト]** フォルダーには、1 つ以上のプロジェクトが格納されています。各プロジェクトの **[パッケージ]** フォルダーには、1 つ以上のパッケージが格納されています。  
  
  
