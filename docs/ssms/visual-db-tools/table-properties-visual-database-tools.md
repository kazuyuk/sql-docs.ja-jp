---
title: '[テーブルのプロパティ]\(Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.tabledesigner
- vdt.designers.properties.Table
ms.assetid: cc392987-1aab-45f5-b5af-a26be53409bf
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ace32c9a58718e567b7b4dd77b201a3f6a60775
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981034"
---
# <a name="table-properties-visual-database-tools"></a>[テーブルのプロパティ] \(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
以下のプロパティは、テーブル デザイナーで右クリックして [プロパティ] をクリックすると開く [プロパティ] ウィンドウに表示されます。 特に断りのない限り、テーブルが選択されているときにこれらのプロパティを [プロパティ] ウィンドウで編集できます。  
  
> [!NOTE]  
> テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](http://msdn.microsoft.com/f1745145-182d-4301-a334-18f799d361d1) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。 テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。 パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。  
  
## <a name="show-table-properties-in-table-designer"></a>テーブル デザイナーでのテーブル プロパティの表示  
  
> [!NOTE]  
> このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。  
  
**[IDENTITY] カテゴリ**  
展開して **[名前]**、 **[説明]**、および **[スキーマ]** の各プロパティを表示します。  
  
**名前**  
テーブルの名前を表示します。 名前を編集するには、テキスト ボックスに入力します。  
  
> [!CAUTION]  
> テーブルを参照するクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムがある場合は、テーブル名を変更すると、各オブジェクトが無効になります。  
  
**データベース名**  
選択したテーブルのデータ ソースの名前を表示します。  
  
**[説明]**  
選択したテーブルの説明を表示します。 説明全体を表示したり、説明を編集したりするには、説明をクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。  
  
**[スキーマ]**  
このテーブルが所属するスキーマの名前を表示します。 Microsoft SQL Server だけに適用されます。  
  
**[サーバー名]**  
データ ソースのサーバーの名前を表示します。  
  
**[テーブル デザイナー] カテゴリ**  
展開して **[IDENTITY 列]**、 **[Indexable]**、および **[Replicated]** の各プロパティを表示します。  
  
**[IDENTITY 列]**  
テーブルの ID 列として使用されている列を表示します。 ID 列を変更するには、ドロップダウン リストから列を選択します。 数値データ型の列だけが一覧に表示されます。  
  
**[Indexable]**  
テーブルにインデックスを付けることができるかどうかを表示します。 テーブルにインデックスを付けることができない場合、テーブルの所有者でないか、データ型が text、ntext、または image の列がテーブルに含まれている可能性があります。  
  
**[Replicated]**  
テーブルが別の場所でレプリケートされているかどうかを表示します。  
  
**[標準データ スペースの指定] カテゴリ**  
展開して **[(データ スペースの種類)]**、 **[ファイル グループまたはパーティション スキーム名]**、および **[パーティション列の一覧]** の各プロパティを表示します。  
  
**[(データ スペースの種類)]**  
テーブルがファイル グループまたはパーティション スキームを使用して保存されるかどうかを表示します。  
  
**[ファイル グループまたはパーティション スキーム名]**  
ファイル グループまたはパーティション スキームの名前を表示します。  
  
**[パーティション列の一覧]**  
**[パーティション列の一覧]** ダイアログ ボックスにアクセスできます。  
  
**[行 GUID 列]**  
Microsoft SQL Server がテーブルの ROWGUID 列として使用する列を表示します。 ROWGUID 列を変更するには、ドロップダウン リストから列を選択します。 SQL Server 7.0 以降だけに適用されます。  
  
**[テキスト/イメージのファイル グループ]**  
text データ型、または image データ型の列について、ファイル グループを選択できるドロップダウン リストを表示します。 パーティション スキームを使用してテーブルを保存する場合は、このフィールドを空白のままにします。  
  
## <a name="see-also"></a>参照  
[テーブルのデザイン (Visual Database Tools)](../../ssms/visual-db-tools/design-tables-visual-database-tools.md)  
  
