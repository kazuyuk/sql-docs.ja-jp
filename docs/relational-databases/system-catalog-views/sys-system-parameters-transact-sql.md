---
title: sys.system_parameters (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.system_parameters
- sys.system_parameters_TSQL
- system_parameters_TSQL
- system_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_parameters catalog view
ms.assetid: 0d135c5f-68b5-4009-a0da-35e6abfee0ff
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: b98410a8938d01586933ee896b0e67058e1896b0
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559632"
---
# <a name="syssystemparameters-transact-sql"></a>sys.system_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  パラメーターを持つシステム オブジェクトごとに 1 行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|パラメーターが属しているオブジェクトの ID。|  
|**name**|**sysname**|パラメーターの名前。 オブジェクト内で一意です。<br /><br /> オブジェクトがスカラー関数の場合、パラメーター名は、戻り値を表す行の空の文字列になります。|  
|**parameter_id**|**int**|パラメーターの ID。 オブジェクト内で一意です。 場合は、オブジェクトがスカラー関数、 **parameter_id**戻り値 0 を = です。|  
|**system_type_id**|**tinyint**|パラメーターのシステム型の ID です。|  
|**user_type_id**|**int**|ユーザーが定義されているパラメーターの型の ID。<br /><br /> 型の名前を返すには、この列で [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログ ビューに結合します。|  
|**max_length**|**smallint**|パラメーターの最大長 (バイト単位)。 値は列のデータ型の場合に達すると-1 になります**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**します。|  
|**有効桁数**|**tinyint**|数値ベースの場合は、パラメーターの有効桁数です。それ以外の場合は、0 です。|  
|**scale**|**tinyint**|数値ベースの場合は、パラメーターの小数点以下桁数です。それ以外の場合は、0 です。|  
|**is_output**|**bit**|1 = パラメーターが出力 (または、返す)。それ以外の場合、0 を返します。|  
|**is_cursor_ref**|**bit**|1 = パラメーターはカーソル参照パラメーター。|  
|**has_default_value**|**bit**|1 = パラメーターに既定値。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] このカタログ ビュー内の CLR オブジェクトの既定値のみが保持されます。そのため、この列は値 0 を常に[!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクト。 内のパラメーターの既定値を表示する、[!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクト、クエリ、**定義**の列、 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビュー、またはを使用して、 [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)システム関数。|  
|**is_xml_document**|**bit**|1 = 内容が完全な XML ドキュメントです。<br /><br /> 0 = 内容がドキュメントの一部か、列のデータ型でない**xml**します。|  
|**default_value**|**sql_variant**|場合**has_default_value**は 1 です。 この列の値は、パラメーターの既定の値。 それ以外の場合は NULL です。|  
|**xml_collection_id**|**int**|非ゼロの場合は、パラメーターのデータ型は**xml** XML が型指定されたとします。 この値は、パラメーターの評価 XML スキーマ名前空間に含まれるコレクションの ID です。<br /><br /> 0 = XML スキーマ コレクションはありません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys.all_parameters &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-parameters-transact-sql.md)  
  
  
