---
title: SQL Server Profiler の再生の構成 (基本再生オプション) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cef06029d3ac1af86955f7a2df89fbe570c15245
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178379"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a>SQL Server Profiler - [構成の再生] ([再生オプションの基本設定])
  **[構成の再生]** ダイアログ ボックスの **[再生オプションの基本設定]** ページを使用すると、トレース ファイルまたはテーブルの再生方法を指定できます。  
  
 このウィンドウを表示するには、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を使用して、再生するイベントを含むトレース ファイルまたはテーブルを開きます。 詳細については、「 [再生を実行するための必要条件](../tools/sql-server-profiler/replay-requirements.md)」を参照してください。 トレース ファイルまたはテーブルが開いている状態で、 **[再生]** メニューの **[開始]** をクリックした後、トレースを再生する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。  
  
## <a name="options"></a>および  
 **[再生サーバー]**  
 再生のために接続する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを表示します。  
  
 **[変更]**  
 **[サーバーへの接続]** ダイアログ ボックスを表示して、別のサーバーへ接続します。  
  
 **[ファイルに保存]**  
 再生結果をファイルに保存します。 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] ファイルを保存する場所を指定する、標準ファイル ダイアログが表示されます。  
  
 **[テーブルに保存]**  
 再生結果をテーブルに保存します。 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] により、テーブルを保存する場所を指定するためのテーブル選択ダイアログが表示されます。  
  
 **[再生スレッドの数]**  
 同時に使用する再生スレッドの数を指定します。 値を大きくするほど、再生時にはより多くのリソースが消費されますが、再生が高速になり、同時実行性が高くなります。  
  
 **[トレースされた順番にイベントを再生します。このオプションはデバッグを有効にします。]**  
 イベントを順番に再生します。 このオプションは、デバッグのためにトレースを再生する場合に使用します。  
  
 **[複数のスレッドを使用してイベントを再生します。このオプションはパフォーマンスを最適にし、デバッグを無効にします。]**  
 イベントを同時に再生します。 このオプションを選択した場合は、イベントを順番に再生するよりも処理が高速になりますが、デバッグができなくなります。 イベントは、システム プロセス識別子 (SPID) 内で順序付けられます。  
  
 **[再生結果を表示する]**  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]に再生結果を表示します。  
  
## <a name="see-also"></a>参照  
 [トレース テーブルを再生&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [トレース ファイルを再生する &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [トレースの再生](../tools/sql-server-profiler/replay-traces.md)  
  
  
