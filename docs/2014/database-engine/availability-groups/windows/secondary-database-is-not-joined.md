---
title: セカンダリ データベースが参加していない | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 053ffeaa176eafd6b56c6db29ad7db95d794dfd9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278008"
---
# <a name="secondary-database-is-not-joined"></a>セカンダリ データベースが参加していない
    
## <a name="introduction"></a>概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性データベースの参加状態|  
|**問題点**|セカンダリ データベースが参加していません。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性データベース|  
  
## <a name="description"></a>説明  
 このポリシーは、セカンダリ データベース ("セカンダリ データベース レプリカ" とも呼ばれます) の参加状態をチェックします。 データセット レプリカが参加していない場合、ポリシーは通常とは異なる状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Secondary database is not joined](http://go.microsoft.com/fwlink/p/?LinkId=220862) 」 (セカンダリ データベースが参加していない) に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 このセカンダリ データベースは可用性グループに参加していません。 このセカンダリ データベースの構成が不完全です。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 Transact-SQL、PowerShell、または SQL Server Management Studio を使用して、セカンダリ レプリカを可用性グループに参加させます。 セカンダリ レプリカを可用性グループに参加させる方法の詳細については、「 [可用性グループへのセカンダリ レプリカの参加 (SQL Server)](http://msdn.microsoft.com/en-sg/library/ff878473\(en-us,SQL.110\).aspx)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
