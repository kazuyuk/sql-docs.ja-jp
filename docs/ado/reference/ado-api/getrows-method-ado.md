---
title: GetRows メソッド (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords:
- Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4df52f5ebc2fee80017f284c78cb49e4cb36667b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278801"
---
# <a name="getrows-method-ado"></a>GetRows メソッド (ADO)
複数のレコードを取得、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトを配列にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>戻り値  
 返します、**バリアント**値が 2 次元配列。  
  
#### <a name="parameters"></a>パラメーター  
 *行数*  
 任意。 A [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)を取得するレコードの数を示す値。 既定値は**adGetRowsRest**です。  
  
 *開始*  
 任意。 A**文字列**値または**バリアント**元となるレコードのブックマークに評価される、 **GetRows**の操作を開始する必要があります。 使用することも、 [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)値。  
  
 *Fields*  
 任意。 A**バリアント**を表す単一のフィールド名または序数位置、またはフィールド名または序数位置番号の配列。 ADO では、これらのフィールドのデータのみを返します。  
  
## <a name="remarks"></a>コメント  
 使用して、 **GetRows**にからレコードをコピーする方法、 **Recordset** 2 次元配列にします。 最初の添字は、フィールドを識別し、2 つ目は、レコード番号を識別します。 *配列*変数が正しい次元が自動的にする場合のサイズ、 **GetRows**メソッドは、データを返します。  
  
 値を指定しない場合、*行*引数、 **GetRows**メソッド内のすべてのレコードを自動的に取得する、 **Recordset**オブジェクト。 使用できるよりも多くのレコードを要求した場合は**GetRows**のみ使用可能なレコードの数を返します。  
  
 場合、 **Recordset**オブジェクトは、ブックマークをサポートする、次のようにどのレコードに指定できる、 **GetRows**メソッドがそのレコードの値を渡すことによってデータの取得を開始する必要があります[ブックマーク](../../../ado/reference/ado-api/bookmark-property-ado.md)プロパティに、*開始*引数。  
  
 フィールドを制限する場合、 **GetRows**呼び出しが返された、1 つのフィールドの名前/番号またはフィールド名または番号での配列のいずれかを渡すことができます、*フィールド*引数。  
  
 呼び出した後**GetRows**、未読の次のレコードが現在のレコードまたは[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)プロパティに設定されている**True**レコードがある場合。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [GetRows メソッドの例 (VB)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [GetRows メソッドの例 (VC++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
