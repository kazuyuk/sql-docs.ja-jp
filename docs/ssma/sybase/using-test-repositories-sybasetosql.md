---
title: テスト リポジトリ (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Test Repositories
ms.assetid: c359c25c-db2a-4a20-afa9-62d87a62df72
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 880262cf0342c66a91a1f88e50477e0685e1d1e0
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779538"
---
# <a name="using-test-repositories-sybasetosql"></a>テスト リポジトリ (SybaseToSQL) を使用します。
SSMA テスト リポジトリ ストア SSMA Tester テスト_ケースとテスト結果を後で使用します。 リポジトリのデータは、SQL Server テーブルに保存されます**TestCaseRepository**と**RunTestCaseResultRepository**スキーマ**ssma_sybase_utilities**の**ssmatesterdb_syb**データベース。  
  
次のボタンは、[テスト_ケース リポジトリ] ダイアログ ボックスを使用できます。  
  
-   クリックして、**更新**テスト_ケースまたはテスト結果の一覧を更新するボタンをクリックします。  
  
-   をクリックして、**閉じる**テスト_ケース リポジトリ ダイアログ ボックスを閉じるボタンをクリックします。  
  
## <a name="test-cases-repository"></a>テスト_ケース リポジトリ  
クリックして、Test Cases リポジトリを表示する**テスト_ケースしています.** **Tester**メニュー。 SSMA は、表示、**テスト_ケース リポジトリ**ダイアログ ウィンドウに保存されているテスト_ケースのリストを持つ、**テスト_ケース**ページ。  
  
グリッドは、各テスト・ケースは、次の情報を示しています。  
  
-   名前: テスト_ケース名。  
  
-   作成されます。 テスト_ケース作成日。  
  
-   更新日時: テスト_ケース最終変更日。  
  
-   説明: テスト ケース説明です。  
  
テスト_ケース ページで、次のボタンがあります。  
  
-   クリックして、**追加**テスト_ケース ウィザードを実行し、新しいテストを作成するボタンをクリックします。  
  
-   をクリックして、**削除**リポジトリから、選択したテストを削除するボタンをクリックします。テスト_ケースを削除すると、関連するすべてのテスト結果も削除されます。  
  
-   をクリックして、**編集**テスト_ケース ウィザードを実行し、選択したテストを変更するボタンをクリックします。  
  
-   をクリックして、**実行** を開きます、[テスト_ケースを実行している&#40;SybaseToSQL&#41; ](../../ssma/sybase/running-test-cases-sybasetosql.md)ダイアログと、選択したテストを実行します。  
  
## <a name="test-results-repository"></a>テストの結果リポジトリ  
テストの結果リポジトリを表示することができます、**テスト結果**のページ、**テスト_ケース リポジトリ**ウィンドウです。 クリックして開く**テスト結果しています.** **Tester**メニュー。  
  
2 つのフィルターを使用するには**テスト結果**ページ。  
  
-   名前のテスト ケース フィルター: テスト_ケース名でテスト結果を選択できます。 このフィルターの**すべてのテスト ケース**値により、すべてのテスト_ケースのテスト結果を表示します。  
  
-   テスト_ケースの実行の日付フィルター: 保存の日付でテスト結果をフィルターします。このフィルターの**すべて期間**保存の任意の日付のテスト結果を表示する値を使用します。  
  
テスト結果に関する次の情報がグリッドに表示されます。  
  
-   名前: テスト_ケースの名前。  
  
-   作業の開始: 実行中のケースの日付をテストします。  
  
-   結果: (このセルのツールヒントには、テストの実行の全体的な概要が表示されます) テスト実行の概要です。  
  
次のボタンは、テスト結果 ページで入手できます。  
  
-   をクリックして、**ビュー**  を開きます[テスト_ケース レポートを表示する&#40;SybaseToSQL&#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)の現在のテスト_ケースの結果。  
  
-   クリックして、**削除**を選択したテスト結果を削除するボタン  
  
## <a name="see-also"></a>参照  
[テスト_ケースを実行する&#40;SybaseToSQL&#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[データベース オブジェクトを移行テスト&#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
