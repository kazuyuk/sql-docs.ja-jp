---
title: Red Hat Enterprise Linux 上の SQL Server 2017 の概要 |Microsoft Docs
description: このクイック スタートでは、Red Hat Enterprise Linux に SQL Server 2017 をインストールし、作成および sqlcmd を使用したデータベースを照会する方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 4438184f6e14af1097ff05ea6e463f626025bb46
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103745"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>クイック スタート: SQL Server をインストールし、Red Hat でデータベースを作成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このクイック スタートで最初にインストールする SQL Server 2017 で Red Hat Enterprise Linux (RHEL) 7.3 以降。 その後 **sqlcmd** で接続して最初のデータベースを作成し、クエリを実行します。

> [!TIP]
> このチュートリアルでは、ユーザー入力と、インターネット接続が必要です。 [無人](sql-server-linux-setup.md#unattended) または [オフライン](sql-server-linux-setup.md#offline) インストール手順に興味のある場合、[Linux 上の SQL Server のインストールのガイダンス](sql-server-linux-setup.md) を参照してください。

## <a name="prerequisites"></a>前提条件

RHEL 7.3 または 7.4 マシンで **少なくとも 2 GB** のメモリが必要です。

自分のコンピューターで Red Hat Enterprise Linux をインストールするには[ http://access.redhat.com/products/red-hat-enterprise-linux/evaluation](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)します。 Azure で RHEL 仮想マシンを作成することもできます。 参照してください[の作成と Azure CLI を使用した Linux Vm の管理](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)、および使用`--image RHEL`への呼び出しで`az vm create`します。

その他のシステム要件については、[SQL Server on Linux のシステム要件](sql-server-linux-setup.md#system) を参照してください。

## <a id="install"></a>SQL Server をインストールします。

RHEL で SQL Server を構成するためには、ターミナルで次のコマンドを実行して **mssql サーバー** パッケージをインストールします。

> [!IMPORTANT]
> 既に SQL Server 2017 の CTP または RC リリースをインストールしている場合は、GA リポジトリを登録する前に、古いリポジトリを削除する必要があります。  詳細については、「[プレビュー リポジトリからリポジトリを GA リポジトリに変更](sql-server-linux-change-repo.md)」を参照してください。

1. Microsoft SQL Server の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > これは、累積的な更新プログラム (CU) リポジトリです。 リポジトリ オプションとそれらの相違点についての詳細は、次を参照してください。 [Linux に SQL Server 用のリポジトリを構成する](sql-server-linux-change-repo.md)です。

1. SQL Server をインストールするには、次のコマンドを実行します。

   ```bash
   sudo yum install -y mssql-server
   ```

1. パッケージのインストールが完了したら、**mssql-conf setup** の実行後に、SA パスワードの設定とエディションを選択する指示に従います。

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```
   > [!TIP]
   > このチュートリアルで SQL Server 2017 を試す場合、次のエディションはライセンスフリーです: Evaluation、Developer、および Express

   > [!NOTE]
   > SA アカウントは強力なパスワードを指定していることを確認してください。(最小長さが 8 文字で、大文字と小文字のアルファベット、10 進数の数字や英数字以外の記号を含む)。

1. 構成を完了したら、サービスが実行されていることを確認します。

   ```bash
   systemctl status mssql-server
   ```
   
1. リモート接続を許可するには、RHEL 上のファイアウォールで SQL Server のポートを開きます。 SQL Server の既定ポートは、TCP 1433 です。 ファイアウォールとして **FirewallD** を使用している場合、次のコマンドを使用することができます。

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

この時点で、SQL Server はRHEL コンピューター上で実行されており、使用する準備ができました!

## <a id="tools"></a>SQL Server コマンド ライン ツールをインストールします。

データベースを作成するには、SQL Server で TRANSACT-SQL ステートメントを実行できるツールを使用して接続する必要があります。 次の手順で、SQL Server コマンド ライン ツール: [sqlcmd](../tools/sqlcmd-utility.md) と [bcp](../tools/bcp-utility.md) をインストールします。

1. Microsoft の Red Hat リポジトリの構成ファイルをダウンロードします。

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. インストールされている **mssql ツール** の以前のバージョンがあれば、古い unixODBC パッケージを削除します。

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. 次のコマンドを実行して **mssql-tools** を unixODBC 開発者パッケージとともにインストールします。

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. 利便性のために、`/opt/mssql-tools/bin/` を **PATH** 環境変数に追加します。 これにより、完全なパスを指定せずに、ツールを実行することができます。 次のコマンドを実行し、**PATH** をログイン セッションと対話型/非ログイン セッションの両方に変更します。

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
