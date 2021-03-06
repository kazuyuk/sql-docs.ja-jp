---
title: Transact-SQL 構文表記規則 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sql13.TSQLExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- conventions [SQL Server]
- Applies to section in Transact-SQL topics
- code example conventions [SQL Server]
- objects [SQL Server], names
- code [SQL Server], conventions
- multipart names [SQL Server]
- Transact-SQL syntax conventions
- syntax conventions [SQL Server]
- code [SQL Server]
- Transact-SQL
- naming conventions [SQL Server]
- syntax [SQL Server], Transact-SQL
ms.assetid: 35fbcf7f-8b55-46cd-a957-9b8c7b311241
caps.latest.revision: 55
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: c30e69fc5fb07281e3e3ffa3a926907b73e09419
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39457456"
---
# <a name="transact-sql-syntax-conventions-transact-sql"></a>Transact-SQL 構文表記規則 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  次の表は、[!INCLUDE[tsql](../../includes/tsql-md.md)] リファレンスの構文で使用している表記規則について示しています。  
  
|表記|使用目的|  
|----------------|--------------|  
|大文字|[!INCLUDE[tsql](../../includes/tsql-md.md)] キーワードを示します。|  
|*斜体*|ユーザーが指定する [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文のパラメーターを示します。|  
|**太字**|記載されているとおりに入力する必要があるデータベース名、テーブル名、列名、インデックス名、ストアド プロシージャ、ユーティリティ、データ型名、テキストを示します。|  
|_underline_|下線が引かれている値を含む句がステートメントから省略されているときに適用される既定値を示します。|  
|(& a) #124 です。(縦棒)|角かっこ、または中かっこで囲まれた構文項目を区切ります。 使用できる項目は 1 つだけです。|  
|`[ ]` (角かっこ)|省略可能な構文項目。 角かっこは入力しません。|  
|{} (中かっこ)|必須の構文項目を示します。 中かっこは入力しません。|  
|[**,**...*n*]|先行する項目を *n* 回繰り返せることを示します。 項目はコンマで区切ります。|  
|[...*n*]|先行する項目を *n* 回繰り返せることを示します。 項目は空白で区切ります。|  
|;|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのターミネータを示します。セミコロンは、このバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のほとんどのステートメントでは必須ではありませんが、将来のバージョンでは必須となる予定です。|  
|\<label> ::=|構文のブロックの名前を示します。 この表記規則は、1 つのステートメント内の複数の箇所で使用できる長い構文の一部、または構文の 1 単位について、グループ化してラベルを付ける際に使用します。 構文のブロックを使用できる箇所は、不等号で囲まれたラベル (\<label>) で示します。<br /><br /> セットとは、式のコレクションです (たとえば \<grouping set>)。リストとは、セットのコレクションです (たとえば \<composite element list>)。|  
  
## <a name="multipart-names"></a>マルチパート名  
 特に指定のない限り、データベース オブジェクトの名前に対するすべての [!INCLUDE[tsql](../../includes/tsql-md.md)] 参照は、次のような 4 部構成の名前の形式をとります。  
  
*server_name* **.**[*database_name*]**.**[*schema_name*]**.***object_name*  
  
 | *database_name***.**[* schema_name *]**.***object_name*  
  
 | *schema_name ***.*** object_name*  
  
 | *object_name*  
  
*server_name*  
リンク サーバー名またはリモート サーバー名を示します。  
  
*database_name*  
オブジェクトが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに存在するときは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの名前を指定します。 オブジェクトがリンク サーバーに存在するとき、*database_name* には OLE DB カタログを指定します。  
  
*schema_name*  
オブジェクトが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに存在する場合は、そのオブジェクトを含むスキーマの名前を示します。 オブジェクトがリンク サーバーに存在するとき、*schema_name* には OLE DB スキーマ名を指定します。  
  
*object_name*  
オブジェクトの名前を示します。  
  
特定のオブジェクトを参照する場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] にオブジェクトを識別させるために、必ずしもサーバー、データベース、所有者を指定する必要はありません。 ただし、オブジェクトが見つからない場合は、エラーが返されます。  
  
> [!NOTE]  
> 名前解決のエラーを回避するために、スキーマ スコープ オブジェクトを指定するときは、常にスキーマ名を指定することをお勧めします。  
  
中間のノードを省略するには、ピリオドを使用してそれらの位置を示します。 次の表に、オブジェクト名の有効な形式を示します。  
  
|オブジェクト参照形式|[説明]|  
|-----------------------------|-----------------|  
|*server* **.** *database* **.** *schema* **.** *object*|4 部構成の名前です。|  
|*server* **.** *database* **..** *object*|スキーマ名を省略しています。|  
|*server* **..** *schema* **.** *object*|データベース名を省略しています。|  
|*server* **...** *object*|データベースとスキーマ名を省略しています。|  
|*database* **.** *schema* **.** *object*|サーバー名を省略しています。|  
|*database* **..** *object*|サーバーとスキーマ名を省略しています。|  
|*schema* **.** *object*|サーバーとデータベース名を省略しています。|  
|*object*|サーバー、データベース、およびスキーマ名を省略しています。|  
  
## <a name="code-example-conventions"></a>コード例の規則  
特に断りのない限り、[!INCLUDE[tsql](../../includes/tsql-md.md)] リファレンスで提供されている例は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用し、次のオプションを既定の設定にしてテストされています。  
  
-   ANSI_NULLS  
-   ANSI_NULL_DFLT_ON  
-   ANSI_PADDING  
-   ANSI_WARNINGS  
-   CONCAT_NULL_YIELDS_NULL  
-   QUOTED_IDENTIFIER  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] リファレンスのほとんどのコード例は、大文字と小文字を区別する並べ替え順を使用するサーバーでテストされています。 通常、テスト サーバーでは、ANSI/ISO 1252 コード ページが使用されています。  
  
多くのコード例では、Unicode 文字列定数に **N** という文字をプレフィックスとして加えています。プレフィックス **N** がない場合、文字列はデータベースの既定のコード ページに変換されます。 この既定のコード ページでは、一部の文字が認識されない場合があります。  
  
## <a name="applies-to-references"></a>"適用対象" リファレンス  
[!INCLUDE[tsql](../../includes/tsql-md.md)] リファレンスには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] まで)、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、および [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] に関連する記事が含まれています。   

各記事の上部近くには、記事の主題をサポートする製品を示すセクションがあります。 製品が省略されている場合は、記事で説明されている機能は、その製品では使用できません。 たとえば、可用性グループは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で導入されました。 **CREATE AVAILABILITY GROUP** の記事には、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] に適用されないため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで) が適用対象と記載されています。  
  
場合によっては、記事の一般的な主題は製品に使用できますが、すべての引数はサポートされていません。 たとえば、包含データベース ユーザーは [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] で導入されました。 **CREATE USER** ステートメントはすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 製品に使用できますが、**WITH PASSWORD** 構文は以前のバージョンでは使用できません。 この場合、「**適用対象**」セクションが、トピックの本文の適切な引数の説明に挿入されます。  
  
## <a name="see-also"></a>参照  
[TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](../../t-sql/transact-sql-reference-database-engine.md)    
[予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)      
[Transact-SQL の設計の問題](http://msdn.microsoft.com/library/dd193411.aspx)    
[Transact-SQL の名前付けの問題](http://msdn.microsoft.com/library/dd193246.aspx)        
[Transact-SQL のパフォーマンスの問題](http://msdn.microsoft.com/library/dd172117.aspx)    


