---
title: '[SQL Server エージェント エラー ログの構成] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 30feef171974f2ec1dedb9da842f103b08122671
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33040189"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a>[SQL Server エージェント エラー ログの構成] \([全般] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

この画面を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのエラー ログ設定の表示と更新を行うことができます。  
  
## <a name="options"></a>および  
**[エラー ログ ファイル]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがエラー ログを書き込むファイルを指定します。  
  
**[...]**  
エラー ログ ファイルを参照します。  
  
**[OEM エラー ログを書き込む]**  
エラー ログ ファイルを非 Unicode ファイルとして書き込みます。 これにより、ログ ファイルによって消費されるディスク領域が減少します。 ただし、このオプションを有効にすると Unicode データを含むメッセージが読み取りにくくなる場合があります。  
  
**エラー**  
ログ ファイルにエラーおよび情報メッセージのみを書き込みます。  
  
**Warnings**  
ログ ファイルに警告および情報メッセージのみを書き込みます。  
  
**情報**  
ログ ファイルに情報メッセージのみを書き込みます。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント エラー ログ](../../ssms/agent/sql-server-agent-error-log.md)  
  
