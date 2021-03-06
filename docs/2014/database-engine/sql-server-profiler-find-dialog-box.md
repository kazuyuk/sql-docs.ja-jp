---
title: SQL Server Profiler - [検索] ダイアログ ボックス |Microsoft Docs
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
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 311d248acae2b64d106c57f5c7f92024c4174e5c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199992"
---
# <a name="sql-server-profiler---find-dialog-box"></a>[SQL Server Profiler] - [検索] ダイアログ ボックス
  **[検索]** ダイアログ ボックスを使用すると、トレース内で特定の文字や単語を検索できます。 検索の実行中に取り消すには、<localizedText>Esc</localizedText> キーを押します。  
  
 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]でこのダイアログ ボックスを開くには、 **[編集]** メニューの **[検索]** をクリックします。  
  
## <a name="options"></a>および  
 **[検索する文字列]**  
 検索するテキストを入力します。 指定した文字列を含むすべての文字列が検索されます。 たとえば、検索文字列として "Completed" を指定すると、一致する文字列として "SQL:BatchCompleted" が検索されます。 ワイルドカード文字 (*、? など) はサポートされません。  
  
 **[検索する列]**  
 検索するデータ列をクリックします。トレース内のすべてのデータ列を検索するには、**\<すべての列>** をクリックします。  
  
 **[大文字と小文字を区別する]**  
 **[検索する文字列]** ボックスで指定したテキストと、大文字と小文字の違いまで一致するテキストを検索します。 このチェック ボックスをオフにすると、大文字と小文字の違いが一致しないテキストも含めてトレースを検索します。  
  
 **[単語単位]**  
 単語全体に一致する対象のみを検索します。 **[単語単位]** チェック ボックスをオフにすると、単語内の文字列も検索対象になります。  
  
 **[次を検索]**  
 次に出現する **[検索する文字列]** ボックスの文字列を検索します。  
  
 **[前を検索]**  
 トレース内をさかのぼって、前に出現する **[検索する文字列]** ボックスの文字列を検索します。  
  
## <a name="see-also"></a>参照  
 [値またはトレース中にデータ列の検索&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [トレースを作成する&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [トレース テーブルを開く &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [トレース ファイルを開く &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [SQL Server プロファイラーのテンプレートと権限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
