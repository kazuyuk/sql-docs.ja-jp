---
title: テスト_ケース (OracleToSQL) の作成 |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: e2bf49da49e6b7e79ee62b18925aa60401e4e2a4
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777228"
---
# <a name="creating-test-cases-oracletosql"></a>テスト_ケース (OracleToSQL) の作成
テストを作成するのにには、テスト ケース ウィザードを使用します。 このウィザードでは、テストおよび検証済みのオブジェクトを選択して、テストのパラメーターを指定して、テスト_ケースを作成できます。  
  
## <a name="starting-the-test-case-wizard"></a>テスト ケース ウィザードの開始  
テスト_ケースのウィザードを起動する**新しいテスト_ケースしています.** **Tester**メニュー。  
  
起動すると、ウィザードは、そのスキーマ SSMATESTER_ORACLE ソース Oracle サーバーでを探します。 テスト担当者拡張機能のスキーマの補助オブジェクトの格納に使用することをお勧めします。 テスト_ケースが見つかりません SSMATESTER_ORACLE、スキーマを作成することを提案するダイアログ ウィンドウが表示されます。 (この状況で通常実行される SSMA テスターの最初の実行中にします。)  
  
ダイアログ ウィンドウが表示された場合にをクリックして**はい**を移行元サーバーで SSMATESTER_ORACLE スキーマを作成します。 新しいユーザーを作成し、このユーザーのスキーマでオブジェクトを作成する Oracle 特権が必要に注意してください。  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>ウィザードを使用してテスト_ケースの作成の概要  
テスト_ケースを作成するプロセスは、5 つの手順で構成されます。  
  
1.  [テスト_ケースの初期化&#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [選択して、テストするオブジェクトを構成&#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [影響を受けたオブジェクトの選択と構成&#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [呼び出し順序のカスタマイズ&#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [テスト_ケース準備を完了&#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>参照  
[データベース オブジェクトを移行テスト&#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
