---
title: Analysis Services のスキーマ行セットの |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d01770593787032d96ab869dd59cd40658eca4b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153233"
---
# <a name="analysis-services-schema-rowsets"></a>Analysis Services のスキーマ行セット
  スキーマ行セットは、Analysis Services オブジェクトとサーバーの状態に関する情報 (データベース スキーマ、アクティブ セッション、接続、コマンド、サーバー上で実行されるジョブなど) を格納する定義済みのテーブルです。 スキーマ行セットのテーブルに対しては、SQL Server Management Studio の XML/A スクリプト ウィンドウでクエリを実行できます。また、スキーマ行セットに対して DMV クエリを実行したり、スキーマ行セットの情報を保持するカスタム アプリケーションを作成したりできます (レポートの作成に使用できるディメンションの一覧を取得するレポート アプリケーションなど)。  
  
> [!NOTE]  
>  XML/A スキーマ行セットを使用する場合のスクリプトをで返される情報、*結果*のパラメーター、 [Discover](../xmla/xml-elements-methods-discover.md)メソッドはこれで説明されている行セット列のレイアウトに従って構成されています。セクション。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーでは、「XML for Analysis 仕様」で定められた行セットがサポートされています。 XMLA プロバイダーでは、OLE DB、OLE DB for OLAP、および OLE DB for Data Mining の各データ ソース プロバイダーに対する標準のスキーマ行セットも一部サポートされています。 サポートされている行セットについては、次の各トピックを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[XML for Analysis Schema 行セット](xml/xml-for-analysis-schema-rowsets.md)|XMLA プロバイダーによってサポートされている XMLA 行セットについて説明します。|  
|[OLE DB Schema 行セット](ole-db/ole-db-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB スキーマ行セットについて説明します。|  
|[OLE DB for OLAP Schema 行セット](ole-db-olap/ole-db-for-olap-schema-rowsets.md)|XMLA プロバイダーによってサポートされている OLE DB for OLAP スキーマ行セットについて説明します。|  
|[データ マイニング スキーマ行セット](data-mining/data-mining-schema-rowsets.md)|XMLA プロバイダーによってサポートされているデータ マイニング スキーマ行セットについて説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのデータ アクセス&#40;Analysis Services - 多次元データ&#41;](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [動的管理ビューを使用して&#40;Dmv&#41;サービス モニターは分析するには](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
