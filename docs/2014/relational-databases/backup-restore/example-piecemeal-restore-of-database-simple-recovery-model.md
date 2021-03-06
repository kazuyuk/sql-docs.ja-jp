---
title: データベースの段階的な部分復元 (単純復旧モデル) の例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], simple recovery model
- restore sequences [SQL Server], piecemeal
- simple recovery model [SQL Server], RESTORE examples
ms.assetid: 9834b14a-4e56-4654-b190-c2a38624b6b4
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 12cbb85f6fc335fcb944bee8eb270315dca4957e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37170923"
---
# <a name="example-piecemeal-restore-of-database-simple-recovery-model"></a>データベースの段階的な部分復元 (単純復旧モデル) の例
  段階的な部分復元シーケンスでは、プライマリ ファイル グループからすべての読み取り/書き込みセカンダリ ファイル グループの順に、ファイル グループ レベルで段階的にデータベースが復元および復旧されます。  
  
 この例では、障害発生後、データベース `adb` を新しいコンピューターに復元します。 このデータベースでは、単純復旧モデルが使用されています。 障害が発生する前は、すべてのファイル グループがオンラインです。 ファイル グループ `A` とファイル グループ `C` は読み取り/書き込みが可能で、ファイル グループ `B` は読み取り専用です。 ファイル グループ `B` は、最新の部分バックアップを実行する前に読み取り専用になりました。この部分バックアップには、プライマリ ファイル グループと読み取りと書き込みが可能なセカンダリ ファイル グループ `A` と `C`が含まれています。 ファイル グループ `B` が読み取り専用になった後、ファイル グループ `B` の別のファイル バックアップが作成されました。  
  
## <a name="restore-sequences"></a>復元シーケンス  
  
1.  プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C`の部分復元を行います。  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='A',FILEGROUP='C'   
       FROM partial_backup   
       WITH PARTIAL, RECOVERY;  
  
    ```  
  
     この時点で、プライマリ ファイル グループ、ファイル グループ `A` 、およびファイル グループ `C` はオンラインです。 ファイル グループ `B` のすべてのファイルは復旧待ち状態なので、このファイル グループはオフラインです。  
  
2.  ファイル グループ `B`をオンライン復元します。  
  
    ```  
    RESTORE DATABASE adb FILEGROUP='B' FROM backup WITH RECOVERY;  
  
    ```  
  
     すべてのファイル グループがオンラインになります。  
  
## <a name="additional-examples"></a>その他の例  
  
-   [例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;Simple Recovery Model&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [例: 読み取り専用ファイルのオンライン復元 &#40;Simple Recovery Model&#41;](example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;](example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;](example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [例 : 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;](example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## <a name="see-also"></a>参照  
 [Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [段階的な部分復元 &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
