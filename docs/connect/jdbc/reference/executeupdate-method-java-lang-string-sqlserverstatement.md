---
title: executeUpdate メソッド (java.lang.String) (SQLServerStatement) |Microsoft ドキュメント
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
- SQLServerStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85e7c3a2-f2da-49bf-9d90-5fd246fd60e1
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 148f2887e01d5238ac7461f4922eea77af599bdd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833627"
---
# <a name="executeupdate-method-javalangstring-sqlserverstatement"></a>executeUpdate (java.lang.String) メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された SQL ステートメントを実行します。ステートメントは INSERT、UPDATE、DELETE、または SQL DDL ステートメントのような何も返さない SQL ステートメントが可能です。 以降で[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 では、executeUpdate は正しい数のマージ操作で更新された行を返すはします。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int executeUpdate(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
## <a name="return-value"></a>戻り値  
 **Int** DDL ステートメントを使用する場合、影響を受ける行または 0 の数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この executeUpdate メソッドは、java.sql.Statement インターフェイスの executeUpdate メソッドによって指定されます。  
  
 更新数が 1 より大きくなる (または複数の結果セットが生成される) ストアド プロシージャは [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) メソッドを使用して実行してください。  
  
## <a name="see-also"></a>参照  
 [executeUpdate メソッド&#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
