---
title: 格納されている XML スキーマ コレクションの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1560eb844657d806862d6a4e85bb9a52682b77d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301789"
---
# <a name="view-a-stored-xml-schema-collection"></a>格納されている XML スキーマ コレクションの表示
  [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)を使用して XML スキーマ コレクションをインポートすると、メタデータにスキーマ コンポーネントが格納されます。 固有の関数 [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)を使用して、XML スキーマ コレクションを再構築できます。 この関数を返します、`xml`データ型のインスタンス。  
  
 たとえば、次のクエリでは、`ProductDescriptionSchemaCollection`データベースの実稼働リレーショナル スキーマから XML スキーマ コレクション ( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ) が取得されます。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 XML スキーマ コレクションからスキーマを 1 つだけを表示する場合は、に対して XQuery を指定できます、`xml`によって返される結果の入力`xml_schema_namespace`します。  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 たとえば、次のクエリでは、 `ProductDescriptionSchemaCollection` XML スキーマ コレクションに含まれる、製品保証書とメンテナンスの XML スキーマ情報を取得しています。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 次のクエリに示すように、省略可能な対象名前空間を 3 番目のパラメーターとして `xml_schema_namespace` 関数に渡すことにより、特定のスキーマをコレクションから取得することもできます。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 CREATE XML SCHEMA COLLECTION を使用してデータベースに XML スキーマ コレクションを作成すると、スキーマ コンポーネントがメタデータに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が理解したスキーマ コンポーネントのみが格納されることに注意してください。 コメント、注釈、または XSD 以外の属性は格納されません。 したがって、 **xml_schema_namespace** によって再構築されたスキーマは、機能的には元のスキーマと同じですが、同じように見えるとは限りません。 たとえば、元のスキーマにあったものと同じプレフィックスはありません。 **xml_schema_namespace** によって返されるスキーマでは、対象名前空間のプレフィックスとして **t** が使用され、他の名前空間には **ns1**、 **ns2**などが使用されています。  
  
 XML スキーマの同一のコピーを保持するには、ファイルまたはデータベース テーブルの `xml` 型の列に XML スキーマを保存する必要があります。  
  
 [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) カタログ ビューでも、XML スキーマ コレクションに関する情報が返されます。 この情報には、コレクションの名前、作成日、およびコレクションの所有者が含まれます。  
  
## <a name="see-also"></a>参照  
 [XML スキーマ コレクション &#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
