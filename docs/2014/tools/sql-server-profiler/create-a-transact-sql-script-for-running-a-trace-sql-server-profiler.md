---
title: トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], running
- scripts [SQL Server], traces
ms.assetid: 6b0e2519-998d-40d5-b8ba-5e6a773f91a6
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22c6b4b14d1d22dca9e981b1405aed11e432c159
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210422"
---
# <a name="create-a-transact-sql-script-for-running-a-trace-sql-server-profiler"></a>トレースを実行するための Transact-SQL スクリプトの作成 (SQL Server Profiler)
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、既存のトレース ファイルまたはトレース テーブルから Transact-SQL スクリプトを作成する方法について説明します。  
  
### <a name="to-create-a-transact-sql-script-to-run-a-trace"></a>トレースを実行するための Transact-SQL スクリプトを作成するには  
  
1.  トレース ファイルまたはトレース テーブルを開きます。 詳細については、「[トレース ファイルを開く &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)」または「[トレース テーブルを開く &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)」を参照してください。  
  
2.  **[ファイル]** メニューで **[エクスポート]**、**[トレース定義のスクリプト]** の順にポイントし、トレースするサーバーに対応するバージョンをクリックします。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、スクリプト ファイルの名前を入力し、 **[保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SQL Server プロファイラーのテンプレートと権限](sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](sql-server-profiler.md)  
  
  
