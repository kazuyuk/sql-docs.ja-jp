---
title: updateString (java.lang.String, java.lang.String) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateString (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3a9236bb-a307-45a8-b7d2-c4cbd9b3cb35
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77483ea821bb90c7a386c42a6eaa0dd4fd3ed11d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38039260"
---
# <a name="updatestring-method-javalangstring-javalangstring"></a>updateString (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列を**文字列**の値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateString(java.lang.String columnName,  
                         java.lang.String x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *x*  
  
 A**文字列**オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateString メソッドは、java.sql.ResultSet インターフェイスの updateString メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateString メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
