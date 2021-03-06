---
title: 複数の優先順位制約 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
caps.latest.revision: 44
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 60cd55a656849f3cb5eee9cac879a88d8d85ad4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231465"
---
# <a name="multiple-precedence-constraints"></a>複数の優先順位制約
  優先順位制約は、2 つのタスク、2 つのコンテナー、1 つのタスクと 1 つのコンテナーなど、2 つの実行可能ファイルを連結します。 これらは優先順位付き実行可能ファイル、および制約付き実行可能ファイルと呼ばれています。 制約付き実行可能ファイルには、複数の優先順位制約を含めることができます。 優先順位制約の詳細については、「[優先順位制約](control-flow/precedence-constraints.md)」を参照してください。  
  
 制約をグループ化して複雑な制約シナリオを組み立てると、複雑な制御フローをパッケージに実装できます。 などの次の図では、タスク D はリンクによってタスク A に、`Success`制約によってタスク B にリンク、`Failure`制約、およびタスク D がによってタスク C にリンクされている、`Success`制約。 タスク D とタスク A の間、タスク D とタスク B の間、およびタスク D とタスク C の間の優先順位制約は、論理 *AND* リレーションシップになります。 したがって、タスク D を実行するには、タスク A の実行が成功し、タスク B が失敗し、タスク C の実行が成功する必要があります。  
  
 ![優先順位制約によってリンクされているタスク](media/precedenceconstraints.gif "優先順位制約によってリンクされているタスク")  
  
## <a name="logicaland-property"></a>LogicalAnd プロパティ  
 タスクまたはコンテナーに複数の制約がある場合、`LogicalAnd` プロパティにより、優先順位制約を単独で評価するか、別の制約と組み合わせて評価するかを指定します。  
  
 設定することができます、`LogicalAnd`プロパティを使用して、**優先順位制約エディター**で[!INCLUDE[ssIS](../includes/ssis-md.md)]デザイナー、または [プロパティ] ウィンドウを[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を提供します。  
  
## <a name="related-tasks"></a>Related Tasks  
 [優先順位制約のプロパティを設定する](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
