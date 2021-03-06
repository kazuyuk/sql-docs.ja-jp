---
title: 更新数があるストアド プロシージャの使用 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cebd655a20c49525585cb414cfd7409745391bdc
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662124"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>更新数があるストアド プロシージャの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベース内のデータをストアド プロシージャを使用して変更する用途向けに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) クラスが用意されています。 SQLServerCallableStatement クラスを使用すると、データベース内のデータに変更を加え、影響を受けた行数 (更新数) を返すストアド プロシージャを呼び出すことができます。

SQLServerCallableStatement クラスを使用してストアド プロシージャに対する呼び出しを設定すると、[execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) メソッドまたは [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) メソッドのいずれかを使用して、ストアド プロシージャを呼び出すことができます。 executeUpdate メソッドではストアド プロシージャの影響を受けた行数を示す **int** 値が返されますが、execute メソッドではこの値が返されません。 execute メソッドを使用して影響を受けた行数を取得する場合は、ストアド プロシージャの実行後に [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) メソッドを呼び出すことができます。

> [!NOTE]  
> JDBC ドライバで、発生した可能性があるすべてのトリガが返した更新数を含む、すべての更新数を返す場合、lastUpdateCount 接続文字列プロパティを "false" に設定します。 LastUpdateCount プロパティの詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)します。

たとえば、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースで、次に示すテーブルおよびストアド プロシージャを作成し、サンプル データを挿入します。

```sql
CREATE TABLE TestTable
   (Col1 int IDENTITY,
    Col2 varchar(50),
    Col3 int);  

CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```

次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースに対して開いている接続を関数に渡し、execute メソッドを使用して UpdateTestTable ストアド プロシージャを呼び出し、次に getUpdateCount メソッドを使用して、ストアド プロシージャによって影響を受けた行数を取得しています。

[!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]

## <a name="see-also"></a>参照

[ストアド プロシージャでのステートメントの使用](../../connect/jdbc/using-statements-with-stored-procedures.md)
