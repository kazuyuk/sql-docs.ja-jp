---
title: '手順 4: は PHP で SQL に弾性的に接続 |Microsoft Docs'
ms.custom: ''
ms.date: 01/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8013474f-48e9-43d5-ab89-7b0504044468
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da5c3b99eab34afded5fd92c19f53f3868517d43
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983025"
---
# <a name="step-4-connect-resiliently-to-sql-with-php"></a>ステップ 4: PHP で SQL に弾性的に接続する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

  
デモ プログラムの目的はように一時的なエラー (エラー コードは '08'」の一覧にこのプレフィックスを持つ[付録](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)) 再試行に潜在顧客を接続の試行中にします。 ただし、クエリ コマンドの実行中の一時的なエラーが原因で接続が破棄され、クエリ コマンドを再試行する前に、新しい接続を作成するプログラム。 この設計の選択を推奨します。 デモ プログラムは、使用できる柔軟にデザインの一部を示しています。  
  
このサンプル コードの長さが例外キャッチ ロジックにほとんどの場合です。   
  
[Sqlsrv_query()](../../connect/php/sqlsrv-query.md) SQL Database に対するクエリのセットの結果を取得する関数を使用できます。 この関数は、基本的にクエリと接続オブジェクトをすべて受け入れます、使用して反復処理できる結果セットを返します[sqlsrv_fetch_array()](../../connect/php/sqlsrv-fetch-array.md)します。 
  
```php

    <?php  
        // Variables to tune the retry logic.    
        $connectionTimeoutSeconds = 30;  // Default of 15 seconds is too short over the Internet, sometimes.  
        $maxCountTriesConnectAndQuery = 3;  // You can adjust the various retry count values.  
        $secondsBetweenRetries = 4;  // Simple retry strategy.  
        $errNo = 0;  
        $serverName = "tcp:yourdatabase.database.windows.net,1433";  
        $connectionOptions = array("Database"=>"AdventureWorks",  
           "Uid"=>"yourusername", "PWD"=>"yourpassword", "LoginTimeout" => $connectionTimeoutSeconds);  
        $conn = null;  
        $arrayOfTransientErrors = array('08001', '08002', '08003', '08004', '08007', '08S01'); 
        for ($cc = 1; $cc <= $maxCountTriesConnectAndQuery; $cc++) {  
            // [A.2] Connect, which proceeds to issue a query command.  
            $conn = sqlsrv_connect($serverName, $connectionOptions);    
            if ($conn === true) {  
                echo "Connection was established";  
                echo "<br>";  
  
                $tsql = "SELECT Name FROM Production.ProductCategory";  
                $stmt = sqlsrv_query($conn, $tsql);  
                if ($stmt === false) {
                    echo "Error in query execution";  
                    echo "<br>";  
                    die(print_r(sqlsrv_errors(), true));  
                }
                while($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {     
                    echo $row['Name'] . "<br/>" ;
                }  
                sqlsrv_free_stmt($stmt);  
                sqlsrv_close( $conn); 
                break;  
            } else {    
                // [A.4] Check whether the error code is on the whitelist of transients.  
                $isTransientError = false;  
                $errorCode = '';
                if (($errors = sqlsrv_errors()) != null) {
                    foreach ($errors as $error) {  
                        $errorCode = $error['code'];
                        $isTransientError = in_array($errorCode, $arrayOfTransientErrors);
                        if ($isTransientError) {
                            break;
                        }
                    }
                }  
                if (!$isTransientError) { 
                    // it is a static persistent error...
                    echo("Persistent error suffered with error code = $errorCode. Program will terminate.");  
                    echo "<br>";  
                    // [A.5] Either the connection attempt or the query command attempt suffered a persistent error condition.  
                    // Break the loop, let the hopeless program end.  
                    exit(0);  
                }  
                // [A.6] It is a transient error from an attempt to issue a query command.  
                // So let this method reloop and try again. However, we recommend that the new query  
                // attempt should start at the beginning and establish a new connection.  
                if ($cc >= $maxCountTriesConnectAndQuery) {  
                    echo "Transient errors suffered in too many retries - $cc. Program will terminate.";  
                    echo "<br>";  
                    exit(0);  
                }  
                echo("Transient error encountered with error code = $errorCode. Program might retry by itself.");    
                echo "<br>";  
                echo "$cc attempts so far. Might retry.";  
                echo "<br>";  
                // A very simple retry strategy, a brief pause before looping.  
                sleep(1*$secondsBetweenRetries);  
            }  
            // [A.3] All has gone well, so let the program end.  
        }  
    ?>
```
