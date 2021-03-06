---
title: テンプレートを使用したスクリプトの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1890a03b77baa23ea3e87e7894f5f89bf2eee09a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263738"
---
# <a name="create-scripts-using-templates"></a>テンプレートを使用したスクリプトの作成
  Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、一般のさまざまな作業に適した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがスクリプト テンプレートとして多数用意されています。 これらのテンプレートには、テーブル名などのようなユーザーの入力した値に対応するパラメーターが含まれています。 これらのパラメーターを使用して名前を一度入力すると、その名前は、スクリプト内の必要なすべての場所に自動的にコピーされます。 独自のカスタム テンプレートを作成し、頻繁に記述するスクリプトに役立てることができます。 さらに、テンプレートの移動、またはテンプレートを保存する新規フォルダーの作成を行い、テンプレート ツリーを整理できます。 次の実習では、照合テンプレートを指定しつつ、テンプレートを使用してデータベースを作成します。  
  
## <a name="using-templates"></a>テンプレートの使用  
  
#### <a name="to-create-a-script-using-a-template"></a>テンプレートを使用してスクリプトを作成するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  テンプレート エクスプローラーではテンプレートがグループ別に表示されます。 **[Database]** を展開し、 **[Create Database]** をダブルクリックします。  
  
3.  **[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]** をクリックします。 新しいクエリ エディター ウィンドウが開き、 **Create Database** テンプレートの内容が表示されます。  
  
4.  **[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。  
  
5.  **[テンプレート パラメーターの値の指定]** ダイアログ ボックスの **[値]** 列には、 **Database_Name** パラメーターの推奨値が表示されます。 **Database Name** パラメーターの [値] 列のボックスに「 **Marketing**」と入力し、**[OK]** をクリックします。 スクリプトの複数の場所に "Marketing" が挿入されていることを確認します。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [カスタム テンプレートの作成](lesson-3-2-create-custom-templates.md)  
  
  
