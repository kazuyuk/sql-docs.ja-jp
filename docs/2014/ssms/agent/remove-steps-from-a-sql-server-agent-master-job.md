---
title: SQL Server エージェントのマスター ジョブからのステップの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 871e6162-1221-464d-8f7f-7e454dcd9edb
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 701b8fa7be6b8cf17099b6b8999d7d69357d2980
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278328"
---
# <a name="remove-steps-from-a-sql-server-agent-master-job"></a>Remove Steps from a SQL Server Agent Master Job
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]で SQL Server エージェントのマスター ジョブからステップを削除する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **以下を使用して SQL Server エージェントのマスター ジョブからステップを削除するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのマスター ジョブの対象サーバーを、ローカル サーバーとリモート サーバーの両方に設定することはできません。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 **sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか変更できません。 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブからステップを削除するには  
  
1.  **オブジェクト エクスプローラー** で、ステップを削除するジョブを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[ジョブ]** フォルダーを展開します。  
  
4.  ステップを削除するジョブを右クリックし、 **[プロパティ]** をクリックします。  
  
5.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスで、**[ページの選択]** の **[ステップ]** を選択します。  
  
6.  **[ジョブ ステップの一覧]** で削除するジョブ ステップを選択し、 **[削除]** をクリックします。  
  
7.  完了したら、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a>SQL Server エージェントのマスター ジョブからステップを削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- removes job step 1 from the job Weekly Sales Data Backup   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1 ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_delete_jobstep &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)します。  
  
  
