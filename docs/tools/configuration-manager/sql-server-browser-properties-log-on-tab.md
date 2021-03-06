---
title: SQL Server Browser のプロパティ ([ログオン] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 814b8f9f6c94e0c0907ee662565fd5377455a5a9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38022620"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>[SQL Server Browser のプロパティ] ダイアログ ボックス ([ログオン] タブ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser プログラムはサーバー上のサービスとして実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各種リソースに関する着信要求を受信し、このコンピューター上にインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに関する情報を提供します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser は、UDP ポートでリッスンし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resolution Protocol (SSRP) を使用して未認証の要求を受け入れます。  
  
 アカウントのパスワードを変更した場合、サービスを再起動しなくても、すぐにその変更が有効になります。  
  
## <a name="options"></a>[変数]  
 **[ローカル システム アカウント]**  
 ローカル システム アカウントのセキュリティ コンテキストで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを実行します。 可能な場合は、この代わりに低い権限を設定したアカウントを使用してください。  
  
 **[このアカウント]**  
 Windows 認証を使用するローカル ユーザー アカウントまたはドメイン ユーザー アカウントを指定します。 サービスを実行できる必要最小限の権限が設定されたドメイン ユーザー アカウントを使用することをお勧めします。 アカウントの選択の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
 **[参照]**  
 ユーザーまたは組み込みのセキュリティ プリンシパルを表示します。  
  
> [!IMPORTANT]  
>  低い権限を設定したアカウントを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスに必要な権限の詳細については、「 [SQL Server Browser サービス](../../tools/configuration-manager/sql-server-browser-service.md)」の「セキュリティ」セクションを参照してください。  
  
 **Password**  
 セキュリティ プリンシパルのパスワードを入力します。  
  
 **[パスワードの確認入力]**  
 セキュリティ プリンシパルのパスワードを確認入力します。  
  
 **サービスの状態**  
 このサービスが実行中か、停止しているか、無効になっているかが表示されます。 **[...]** の場合は、状態の変更が保留になっています。  
  
 **コントロール パネルの  ◆セグ : 文が分断されているため、訳の位置が入れ替わっています◇**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを開始します。  
  
 **[停止]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを停止します。  
  
 **[一時停止]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを一時停止します。  
  
 **[再開]**  
 一時停止した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser サービスを再開します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Browser サービス](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
