---
title: SQL Server インデックスの削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 148565f2866e571ba783c58d1ff10413510ef6db
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422231"
---
# <a name="dropping-a-sql-server-index"></a>SQL Server インデックスの削除
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **iindexdefinition::dropindex**関数。 これにより、コンシューマーからインデックスを削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、複数公開されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックスと主キーと UNIQUE 制約。 テーブルの所有者、データベース所有者、およびいくつかの管理ロールのメンバーを変更できる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]制約を削除するテーブル。 既定では、テーブル所有者だけが既存のインデックスを削除できます。 そのため、 **DropIndex**成功または失敗が示されるインデックスの種類も、アプリケーション ユーザーのアクセス権でだけでなく依存します。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* DBKIND_NAME にする必要があります。  
  
 コンシューマーで Unicode 文字の文字列としてインデックスの名前を指定する、 *pwszName*のメンバー、 *uName*共用体の*pIndexID*パラメーター。 *EKind*のメンバー *pIndexID* DBKIND_NAME にする必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがテーブルのすべてのインデックスを削除するの OLE DB の機能をサポートしていないときに*pIndexID*が null です。 場合*pIndexID*が null の場合、E_INVALIDARG が返されます。  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
