---
title: レポートでのカスタム アセンブリの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ef7579e104fecc5d73e35398f9e54b7b9d8bd7e8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301742"
---
# <a name="using-custom-assemblies-with-reports"></a>レポートでのカスタム アセンブリの使用
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート アイテムの値、スタイル、および書式設定に関するカスタム コードを記述できます。 たとえば、カスタム コードを使用して、ロケールに基づいて通貨を書式設定したり、特殊な書式設定の特定の値にフラグを設定したり、または企業で実際に使用している他のビジネス ルールを適用したりすることができます。 このコードをレポートに含める方法の 1 つは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用してレポート定義ファイル内から参照できるカスタム コード アセンブリを作成することです。 サーバーは、レポートを実行するときにカスタム アセンブリの関数を呼び出します。 カスタム アセンブリは、レポートで使用する特別な関数を取得するときに使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [RDL ファイルのアセンブリの参照](referencing-assemblies-in-an-rdl-file.md)  
 レポート定義言語ファイルのカスタム アセンブリを参照する方法について説明します。  
  
 [カスタム アセンブリの配置](deploying-a-custom-assembly.md)  
 カスタム アセンブリをレポート デザイナーとレポート サーバーに配置する方法について説明します。  
  
 [複雑な名前を持つカスタム アセンブリの使用](using-strong-named-custom-assemblies.md)  
 複雑な名前を持つカスタム アセンブリの使用方法について説明します。  
  
 [カスタム アセンブリでの権限のアサート](asserting-permissions-in-custom-assemblies.md)  
 カスタム アセンブリの権限を限定して配置する方法と権限をコード内でアサートする方法について説明します。  
  
 [式を使用したカスタム アセンブリへのアクセス](accessing-custom-assemblies-through-expressions.md)  
 カスタム アセンブリ メソッドをレポート定義のレポート式として呼び出す方法について説明します。  
  
 [カスタム アセンブリ オブジェクトの初期化](initializing-custom-assembly-objects.md)  
 レポートから呼び出されたカスタム アセンブリ オブジェクトの値を初期化する方法について説明します。  
  
 [カスタム アセンブリをデバッグする方法](how-to-debug-custom-assemblies.md)  
 カスタム アセンブリ コードのデバッグ方法について説明します。  
  
## <a name="see-also"></a>参照  
 [レポート定義言語 &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md)  
  
  
