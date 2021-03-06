---
title: sys.server_event_notifications (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_event_notifications
- sys.server_event_notifications
- sys.server_event_notifications_TSQL
- server_event_notifications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_notifications catalog view
ms.assetid: 1a83a044-3130-4551-95ca-162525846ff5
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 7736946316131a6760d7bd9d9f2ab7b258b560ed
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222123"
---
# <a name="sysservereventnotifications-transact-sql"></a>sys.server_event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー レベルのイベント通知オブジェクトごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|サーバーのイベント通知名です。 すべてのサーバー レベルのイベント通知で一意です。|  
|**object_id**|**int**|オブジェクト ID 番号。 内で一意では、**マスター**データベース。|  
|**parent_class**|**tinyint**|親のクラスです。 常に 100 = サーバーです。|  
|**parent_class_desc**|**nvarchar(60)**|親のクラスの説明です。 常に SERVER です。|  
|**parent_id**|**int**|常に 0 です。|  
|**create_date**|**datetime**|作成された日付。|  
|**modify_date**|**datetime**|オブジェクトが ALTER ステートメントを使用して最後に変更された日付です。|  
|**service_name**|**nvarchar (256)**|通知の送信先のサービスの名前です。|  
|**broker_instance**|**nvarchar(128)**|指定された通知先サービスが定義されている Service Broker です。|  
|**creator_sid**|**varbinary(85)**|イベント通知を作成するステートメントを実行するログインの SID です。 イベント通知の定義で WITH FAN_IN が指定されていない場合は NULL です。|  
|**principal_id**|**int**|これを所有しているサーバー プリンシパルの ID です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
