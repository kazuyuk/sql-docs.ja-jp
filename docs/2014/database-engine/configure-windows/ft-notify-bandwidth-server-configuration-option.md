---
title: ft notify bandwidth サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 68b6bda063c9bcbb2eb938c5310b91233ef7a866
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287908"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>ft notify bandwidth サーバー構成オプション
  **ft notify bandwidth** オプションは、小規模メモリ バッファーのプールの最大サイズを指定する際に使用します。 小規模メモリ バッファーのサイズは 64 KB です。 *max* パラメーターの値によって、小規模バッファー プールでフルテキスト メモリ マネージャーが保持する必要があるバッファーの最大数が指定されます。 場合、`max`値が 0 の場合、小規模バッファー プールに保持できるバッファー数に上限はありません。  
  
 **min** パラメーターによって、小規模メモリ バッファーのプールで保持する必要があるメモリ バッファーの最少数が指定されます。  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ マネージャーからの要求時に、余分なバッファー プールがすべて解放されますが、このバッファーの最少数は保持されます。 ただし、 **min** の値にゼロ (0) が指定されている場合は、すべてのメモリ バッファーが解放されます。  
  
 特定の状況では、その時点で割り当てられるバッファーの数が **min** パラメーターによって指定された値よりも少なくなることがあります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [ft crawl bandwidth サーバー構成オプション](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
