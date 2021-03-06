---
title: Ibcpsession::bcpcolfmt (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPColFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColFmt method
ms.assetid: 2852f4ba-f1c6-4c4c-86b2-b77e4abe70de
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea0872d071893e7d88a5d52d677702a984e49f02
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426721"
---
# <a name="ibcpsessionbcpcolfmt-ole-db"></a>IBCPSession::BCPColFmt (OLE DB)
  プログラム変数と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列のバインドを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPColFmt(   
DBORDINALidxUserDataCol,  
inteUserDataType,  
intcbIndicator,  
intcbUserData,  
BYTE *pbUserDataTerm,  
intcbUserDataTerm,  
DBORDINALidxServerCol);  
```  
  
## <a name="remarks"></a>コメント  
 **BCPColFmt** BCP データ ファイルのフィールド間のバインディングを作成するメソッドを使用し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列。 このメソッドは、列の長さ、型、ターミネータ、およびプレフィックス長をパラメーターとして受け取り、個々のフィールドの対応するプロパティに設定します。  
  
 ユーザーが対話モードを選択すると、このメソッドが 2 回呼び出されます。1 回は既定値 (サーバーの列の型によって異なります) に応じて列形式を設定するために呼び出され、もう 1 回はクライアントが対話モードで選択した列の型に応じて各列の形式を設定するために呼び出されます。  
  
 対話モード以外の場合、このメソッドは列ごとに 1 回だけ呼び出され、各列の型を文字型またはネイティブ型に設定し、列ターミネータと行ターミネータを設定します。  
  
 **BCPColFmt**メソッドでは、一括コピーのユーザー ファイル形式を指定できます。 次に、一括コピーに使用するフォーマットの内容を示します。  
  
-   ユーザー ファイルのフィールドからデータベース列へのマッピング  
  
-   ユーザー ファイルの各フィールドのデータ型  
  
-   各フィールドの省略可能なインジケーターの長さ  
  
-   ユーザー ファイルの各フィールドにおけるデータの最大長  
  
-   各フィールドの省略可能なターミネータ バイト シーケンス  
  
-   省略可能なターミネータ バイト シーケンスの長さ  
  
 呼び出しごとに**BCPColFmt**ユーザー ファイルの 1 つのフィールドの形式を指定します。 たとえば、5 つのフィールドのユーザーのデータ ファイル内の 3 つのフィールドの既定の設定を変更するに最初に呼び出す`BCPColumns(5)`を呼び出して**BCPColFmt**の 5 回の呼び出しで独自の形式の 3 つです。 残りの 2 つの呼び出しでは、設定*eUserDataType*を設定し、BCP_TYPE_DEFAULT *cbIndicator*、 *cbUserData*、および*cbUserDataTerm*0、BCP_VARIABLE_LENGTH、0、それぞれします。 このプロシージャでは、5 つの列すべてをコピーします。それらの列のうち 3 つはカスタマイズされた形式でコピーされ、2 つは既定の形式でコピーされます。  
  
> [!NOTE]  
>  [Ibcpsession::bcpcolumns](ibcpsession-bcpcolumns-ole-db.md)呼び出しの前にメソッドを呼び出す必要があります**BCPColFmt**します。 呼び出す必要があります**BCPColFmt**ユーザー ファイル内の各列に対して 1 回です。 呼び出す**BCPColFmt** 1 回以上のユーザー ファイルの任意の列、エラーが発生します。  
  
 ユーザー ファイル内のすべてのデータをコピーする必要はありません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 列をスキップするには、列のデータの形式を指定する際に idxServerCol パラメーターを 0 に設定します。 一方、フィールドをスキップする場合は、メソッドを正しく機能させるためにすべての情報が必要になります。  
  
 **注**、 [ibcpsession::bcpwritefmt](ibcpsession-bcpwritefmt-ole-db.md)によって提供される形式指定を保存する関数を使用できます**BCPColFmt**します。  
  
## <a name="arguments"></a>引数  
 *idxUserDataCol*[in]  
 ユーザー データ ファイル内のフィールドのインデックス。  
  
 *eUserDataType*[in]  
 ユーザー データ ファイル内のフィールドのデータ型。 使用できるデータ型が記載されて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_type_xxx というで Native Client ヘッダー ファイル (sqlncli.h) 形式、たとえば、BCP_TYPE_SQLINT4 します。 BCP_TYPE_DEFAULT 値を指定すると、プロバイダーはテーブルやビューの列と同じ型を使用します。 一括コピー操作の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルにときに、`eUserDataType`引数に BCP_TYPE_SQLDECIMAL または BCP_TYPE_SQLNUMERIC:  
  
-   コピー元の列が decimal 型または numeric 型以外の場合は、既定の有効桁数と小数点以下桁数が使用されます。  
  
-   コピー元の列が decimal 型または numeric 型の場合は、コピー元の列の有効桁数と小数点以下桁数が使用されます。  
  
 *cbIndicator*[in]  
 フィールドのプレフィックス長。 既定値は BCP_PREFIX_DEFAULT です。 有効なプレフィックス長は、0、1、2、4、および 8 です。 フィールドがチャンク分割される場合に頻繁に使用されるプレフィックスのサイズは 8 です。 チャンク分割は、大きい値になっている列を効率的に一括コピーするために使用します。  
  
 *cbUserData*[in]  
 ユーザー ファイル内にあるフィールド データの最大長 (バイト単位)。長さのインジケーターやターミネータの長さは含まれません。  
  
 設定`cbUserData`BCP_LENGTH_ には、ファイルのフィールドをデータ内のすべての値を示しますが、または NULL に設定する必要があります。 設定`cbUserData`BCP_LENGTH_VARIABLE を示しますが、各フィールドのデータの長さがシステムによって決定されます。 これは、フィールドによっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーされるデータの前に長さのインジケーターや NULL インジケーターを生成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするデータにインジケーターが必要になる場合があることを意味します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字やバイナリ データ型、 `cbUserData` BCP_LENGTH_VARIABLE、BCP_LENGTH_、0 または正の値を指定できます。 場合`cbUserData`BCP_LENGTH_VARIABLE は、システムは存在する場合は、長さのインジケーターやターミネータ シーケンスのいずれかを使用して、データの長さを決定します。 長さのインジケーターとターミネータ シーケンスの両方を指定した場合、一括コピーはコピーするデータ量が少なくなる方法を使用します。 場合`cbUserData`BCP_LENGTH_VARIABLE、データは、型が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文字またはバイナリの型と長さのインジケーターとターミネータ シーケンスのどちらが指定されている場合、システムがエラー メッセージを返します。  
  
 場合`cbUserData`が 0 または正の値をシステムを使用して`cbUserData`最大データ長として。 ただし、正の値の場合、`cbUserData`長さのインジケーターとターミネータ シーケンスの提供、コピーするデータ量が少なくなる方法を使用してデータの長さを決定します。  
  
 `cbUserData`値は、データのバイト数を表します。 文字データが Unicode ワイド文字では、正の値で表されている場合`cbUserData`パラメーターの値は、各文字のバイト単位でサイズを乗算する文字数を表します。  
  
 *pbUserDataTerm*[size_is] [in]  
 フィールドに使用するターミネータ シーケンス。 このパラメーターは主に文字データ型に対して有効です。これは、他のすべての型は固定長であったり、バイト数を正確に記録するために長さのインジケーターが必要になる (バイナリ データの場合) ためです。  
  
 抽出されるデータが途中で終了されないようにしたり、ユーザー ファイル内のデータが途中で終了していないことを示すには、このパラメーターに NULL を設定します。  
  
 複数の方法 (ターミネータと長さのインジケーター、ターミネータと列の最大長など) を使用してユーザー ファイルの列長を指定すると、一括コピーはコピーするデータの量が最も少なくなる方法を使用します。  
  
 一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。 このため、ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定するように注意する必要があります。  
  
 *cbUserDataTerm*[in]  
 列に使用するターミネータ シーケンスの長さ、(バイト単位)。 データ内にターミネータが存在しないか不要な場合は、この値を 0 に設定します。  
  
 *idxServerCol*[in]  
 データベース テーブル内での列の序数位置。 最初の列の序数は 1 です。 列の序数位置がによって報告された**icolumnsinfo::getcolumninfo**または同様の方法です。 この値が 0 の場合、一括コピーではデータ ファイル内のこのフィールドは無視されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 詳細な情報を使用するためのプロバイダー固有のエラーが発生しました、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイス。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](ibcpsession-bcpinit-ole-db.md)メソッドは、このメソッドを呼び出す前に呼び出されませんでした。  
  
 E_INVALIDARG  
 引数が無効です。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)  
  
  
