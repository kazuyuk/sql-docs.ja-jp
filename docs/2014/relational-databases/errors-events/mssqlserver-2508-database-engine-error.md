---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ac343cb92828e16cb87bc6e6f979a73a2a4adf47
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407401"
---
# <a name="mssqlserver2508"></a>MSSQLSERVER_2508
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2508|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|メッセージ テキスト|オブジェクト "%.\*ls"、インデックス ID %d、パーティション ID %I64d、アロケーション ユニット ID %I64d (型 %.\*ls) の %.*ls のカウントが正しくありません。 DBCC UPDATEUSAGE を実行してください。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、テーブルおよびインデックスの行やページのカウント値が正しくならないことがあります。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンで作成したデータベースはカウントが誤っている場合があります。 DBCC CHECKDB は、これらのエラーを検出するように拡張されており、エラーが見つかるとこの警告メッセージを返します。  
  
## <a name="user-action"></a>ユーザーの操作  
 指定したオブジェクトやインデックス、またはオブジェクトが格納されているデータベースに対して DBCC UPDATEUSAGE を実行し、無効なカウントを修正します。  
  
  
