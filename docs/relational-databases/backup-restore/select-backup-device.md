---
title: '[バックアップ デバイスの選択] | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c743a249373317a83096c311916a94d7e68607d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32919007"
---
# <a name="select-backup-device"></a>[バックアップ デバイスの選択]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[バックアップ デバイスの選択]** ダイアログ ボックスを使用すると、復元操作で使用する論理バックアップ デバイスを選択できます。  
  
 論理バックアップ デバイスは、オペレーティング システムによって提供される物理デバイス (テープ ドライブまたはディスク ドライブ) に対応するユーザー定義の論理デバイスです。  
  
> [!NOTE]  
>  バックアップで複数のバックアップ デバイスを使用する場合、すべてのバックアップ デバイスが 1 つの種類のデバイスに対応する必要があります。  
  
 **SQL Server Management Studio を使用してバックアップ デバイスの内容を表示するには**  
  
-   [バックアップ テープまたはバックアップ ファイルの内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>および  
 **バックアップ デバイス**  
 復元操作で使用する論理バックアップ デバイスの名前を、このリスト ボックスから選択します。  
  
 バックアップデバイスのコンテンツの表示方法の詳細については、「 [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 探していたバックアップを含む論理バックアップ デバイスが一覧に表示されない場合、バックアップが 1 つ以上のファイルまたはテープ ドライブに直接書き込まれている可能性があります。 この場合、 **[バックアップ デバイスの選択]** ダイアログ ボックスを取り消し、 **[バックアップの指定]** ダイアログ ボックスの **[バックアップ メディア]** ボックスで **[ファイル]** または **[テープ]** を選択します。  
  
## <a name="see-also"></a>参照  
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  
