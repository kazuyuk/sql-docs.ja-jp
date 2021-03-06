---
title: PDOStatement::fetchAll |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: be74188a-77cd-4d19-b16e-77278373c979
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 639ff09c2c739e99b974c1b4df7d4963b7959e94
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37983022"
---
# <a name="pdostatementfetchall"></a>PDOStatement::fetchAll
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

結果セットの行を配列で返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array PDOStatement::fetchAll([ $fetch_style[, $column_index ][, ctor_args]] );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*fetch_style*: 行データの形式を指定する (整数の) シンボル。 値の一覧については、「 [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) 」を参照してください。 PDO::FETCH_COLUMN も使用できます。 PDO::FETCH_BOTH が既定値です。  
  
$*column_index*: $*fetch_style* が PDO::FETCH_COLUMN の場合に取得する列を表す整数値。 0 は既定値です。  
  
$*ctor_args*: $*fetch_style* が PDO::FETCH_CLASS または PDO::FETCH_OBJ のとき、クラス コンストラクターのパラメーターの配列。  
  
## <a name="return-value"></a>戻り値  
結果セットの残りの行の配列、またはメソッドの呼び出しが失敗した場合は false。  
  
## <a name="remarks"></a>Remarks  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_BOTH);  
   print_r( $result );  
   print "\n-----------\n";  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_NUM);  
   print_r( $result );  
   print "\n-----------\n";  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_COLUMN, 1);  
   print_r( $result );  
   print "\n-----------\n";  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg\n";  
      }  
  
      function __toString() {  
         echo "To string\n";  
      }  
   };  
  
   $stmt = $conn->query( 'SELECT TOP(2) * FROM Person.ContactType' );  
   $all = $stmt->fetchAll( PDO::FETCH_CLASS, 'cc', array( 'Hi!' ));  
   var_dump( $all );  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
