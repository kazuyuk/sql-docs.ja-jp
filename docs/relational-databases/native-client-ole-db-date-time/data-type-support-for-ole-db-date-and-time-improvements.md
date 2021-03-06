---
title: OLE DB の日付/時刻の強化に対するデータ型のサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], data type support
- OLE DB, date/time improvements
ms.assetid: d40e3fd6-9057-4371-8236-95cef300603e
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 57447d0d15ceaf5cb3d6ab72654a595c8e3e952a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39557252"
---
# <a name="data-type-support-for-ole-db-date-and-time-improvements"></a>OLE DB の日付/時刻の強化に対するデータ型のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付および時刻データ型をサポートする OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) の型について説明します。  
  
## <a name="data-type-mapping-in-rowsets-and-parameters"></a>行セットとパラメーターでのデータ型マッピング  
 OLE DB には、新しいサーバーの種類をサポートする 2 つの新しいデータ型 (DBTYPE_DBTIME2 と DBTYPE_DBTIMESTAMPOFFSET) が用意されています。 次の表に、完全なサーバーの型マッピングを示します。  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型|OLE DB データ型|値|  
|-----------------------------------------|----------------------|-----------|  
|DATETIME|DBTYPE_DBTIMESTAMP|135 (oledb.h)|  
|smalldatetime|DBTYPE_DBTIMESTAMP|135 (oledb.h)|  
|日付|DBTYPE_DBDATE|133 (oledb.h)|  
|time|DBTYPE_DBTIME2|145 (sqlncli.h)|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|146 (sqlncli.h)|  
|datetime2|DBTYPE_DBTIMESTAMP|135 (oledb.h)|  
  
## <a name="data-formats-strings-and-literals"></a>データ形式 : 文字列とリテラル  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型|OLE DB データ型|クライアントで変換した場合の文字列の形式|  
|-----------------------------------------|----------------------|------------------------------------------|  
|DATETIME|DBTYPE_DBTIMESTAMP|'yyyy-mm-dd hh:mm:ss[.999]'<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、datetime における秒の小数部の桁数を 3 桁までサポートします。|  
|smalldatetime|DBTYPE_DBTIMESTAMP|'yyyy-mm-dd hh:mm:ss'<br /><br /> このデータ型の精度は 1 分です。 秒の部分は、出力時には 0 になり、入力時にはサーバーによって丸められます。|  
|日付|DBTYPE_DBDATE|'yyyy-mm-dd'|  
|time|DBTYPE_DBTIME2|'hh:mm:ss[.9999999]'<br /><br /> 秒の小数部には、必要に応じて最大 7 桁まで指定できます。|  
|datetime2|DBTYPE_DBTIMESTAMP|'yyyy-mm-dd hh:mm:ss[.fffffff]'<br /><br /> 秒の小数部には、必要に応じて最大 7 桁まで指定できます。|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'<br /><br /> 秒の小数部には、必要に応じて最大 7 桁まで指定できます。|  
  
 日付リテラルまたは時刻リテラルのエスケープ シーケンスに変更はありません。  
  
 結果に含まれる秒の小数部にはコロン (:) ではなくドット (.) を使用します。  
  
 アプリケーションに返される文字列値は、指定された列に対して常に同じ長さになります。 年、月、日、時、分、および秒の各部分は、最大幅に合わせて先頭にゼロが埋め込まれます。 日付と時間の間、および時間とタイムゾーン オフセットの間には空白が 1 つずつ入ります。 タイム ゾーン オフセットの前には常に符号を指定します。 オフセットが 0 の場合は、正符号 (+) になります。 符号とオフセット値の間に空白はありません。 秒の小数部では、必要に応じて、列に定義されている有効桁数になるまで後ろにゼロが埋め込まれますが、その有効桁数を超過することはありません。 datetime 列の場合、秒の小数部は 3 桁になります。 smalldatetime 列の場合、秒の小数部がなく、秒は常にゼロになります。  
  
 アプリケーションによって指定された文字列値を変換すると、柔軟性が向上し、各部分の値を最大幅より小さくすることができます。 年は 1 ～ 4 桁になります。 月、日、時、分、および秒は 1 桁または 2 桁になります。 日付と時刻の間および時刻とタイムゾーン オフセットの間には、任意の空白を含めることができます。 0 時 0 分のオフセットの符号は、正符号と負符号のどちらでもかまいません。 秒の小数部では、最大 9 桁になるように末尾にゼロを含めることができます。 時刻部分は、小数点で終了して、秒の小数部を省略することができます。  
  
 空の文字列は、有効な日付リテラルまたは時間リテラルではありません。また、NULL 値を表すものでもありません。 空の文字列を日付または時刻の値に変換しようとすると、SQLState 22018 のエラーが発生し、"キャストした文字コードが正しくありません" というメッセージが表示されます。  
  
## <a name="data-formats-data-structures"></a>データ形式 : データ構造体  
 次に説明する OLE DB 固有の構造体では、OLE DB は ODBC と同じ制約に準拠しています。 これらはグレゴリオ暦から取得されます。  
  
-   月の範囲は 1 ～ 12 です。  
  
-   日フィールドの範囲は 1 からその月の日数までです。この範囲は、うるう年を考慮して、年フィールドおよび月フィールドと一貫性を保つ必要があります。  
  
-   時刻の範囲は 0 ～ 23 です。  
  
-   分の範囲は 0 ～ 59 です。  
  
-   秒の範囲は 0 ～ 59 です。 この範囲では、恒星時との同期を維持するために最大 2 秒のうるう秒が許可されています。  
  
 次の既存の OLE DB 構造体の実装は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しい日付と時刻のデータ型をサポートするように変更されました。 ただし、定義は変更されていません。  
  
-   DBTYPE_DATE (オートメーション DATE 型です。 内部では **double** として表されます。 整数部分は 1899 年 12 月 30 日からの日数で、小数部分は 1 日の端数になります。 この型の精度は 1 秒なので、有効な小数点以下桁数は 0 です。)  
  
-   DBTYPE_DBDATE  
  
-   DBTYPE_DBTIME  
  
-   DBTYPE_DBTIMESTAMP (小数フィールドは、OLE DB で 10 億分の 1 秒 (ナノ秒) 単位の数値として定義され、範囲は 0 ～ 999,999,999 になります。)  
  
-   DBTYPE_FILETIME  
  
### <a name="dbtypedbtime2"></a>DBTYPE_DBTIME2  
 この構造体では、32 ビットと 64 ビットの両方のオペレーティング システムで、12 バイトまで埋め込みが行われます。  
  
```  
typedef struct tagDBTIME2 {  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    } DBTIME2;  
```  
  
### <a name="dbtype-dbtimestampoffset"></a>DBTYPE_ DBTIMESTAMPOFFSET  
  
```  
typedef struct tagDBTIMESTAMPOFFSET {  
    SHORT year;  
    USHORT month;  
    USHORT day;  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    SHORT timezone_hour;  
    SHORT timezone_minute;  
    } DBTIMESTAMPOFFSET;  
```  
  
 場合`timezone_hour`が負の値、`timezone_minute`負の値である必要がありますまたは 0。 場合`timezone_hour`が正の値、`timezone minute`正である必要がありますまたは 0。 `timezone_hour` が 0 の場合、`timezone minute` は -59 ～ +59 の値を保持できます。  
  
### <a name="ssvariant"></a>SSVARIANT  
 この構造体は、新しい構造体 DBTYPE_DBTIME2 と DBTYPE_DBTIMESTAMPOFFSET を含み、適切な型に対しては秒の小数部の桁数が追加されています。  
  
```  
struct SSVARIANT {  
   SSVARTYPE vt;  
   DWORD dwReserved1;  
   DWORD dwReserved2;  
   union {  
// ...  
      DBTIMESTAMP tsDateTimeVal;  
      DBDATE dDateVal;  
      struct _Time2Val {  
         DBTIME2 tTime2Val;  
         BYTE bScale;  
      } Time2Val;  
      struct _DateTimeVal {  
         DBTIMESTAMP tsDateTimeVal;  
         BYTE bScale;  
      } DateTimeVal;  
      struct _DateTimeOffsetVal {   
         DBTIMESTAMPOFFSET tsoDateTimeOffsetVal;  
         BYTE bScale;  
      } DateTimeOffsetVal;  
// ...  
   };  
};  
```  
  
 さらに、列挙の型を決定する、SSVARIANT の型のエンコーディングに関連付けられた列挙は、次のように拡張されます。  
  
```  
enum SQLVARENUM {  
// ...  
   // Datetime  
   VT_SS_DATETIME      = DBTYPE_DBTIMESTAMP,  
   VT_SS_SMALLDATETIME = 206,  
  
   VT_SS_DATE = DBTYPE_DBDATE,  
   VT_SS_TIME2 = DBTYPE_DBTIME2,  
   VT_SS_DATETIME2 = 212  
   VT_SS_DATETIMEOFFSET = DBTYPE_DBTIMESTAMPOFFSET  
};  
```  
  
 アプリケーションへの移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client を使用する**sql_variant**の制限された有効桁数に依存し、 **datetime** を使用する基になるスキーマが更新された場合に、更新する必要があります**datetime2**なく**datetime**します。  
  
 また、SSVARIANT へのアクセス マクロが拡張され、次の部分が追加されました。  
  
```  
#define V_SS_DATETIME2(X)       V_SS_UNION(X, DateTimeVal)  
#define V_SS_TIME2(X)           V_SS_UNION(X, Time2Val)  
#define V_SS_DATE(X)            V_SS_UNION(X, dDateVal)  
#define V_SS_DATETIMEOFFSET(X)  V_SS_UNION(X, DateTimeOffsetVal)  
```  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>ITableDefinition::CreateTable でのデータ型マッピング  
 Itabledefinition::createtable で使用される DBCOLUMNDESC 構造体で、次の型マッピングが使用されます。  
  
|OLE DB データ型 (*wType*)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型|注|  
|----------------------------------|-----------------------------------------|-----------|  
|DBTYPE_DBDATE|日付||  
|DBTYPE_DBTIMESTAMP|**datetime2**(p)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの検査、DBCOLUMDESC *bScale*メンバーに秒の小数部の精度を確認します。|  
|DBTYPE_DBTIME2|**time**(p)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの検査、DBCOLUMDESC *bScale*メンバーに秒の小数部の精度を確認します。|  
|DBTYPE_DBTIMESTAMPOFFSET|**datetimeoffset**(p)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの検査、DBCOLUMDESC *bScale*メンバーに秒の小数部の精度を確認します。|  
  
 アプリケーションに DBTYPE_DBTIMESTAMP を指定するときに*wType*へのマッピングをオーバーライドできます**datetime2**で型名を指定することによって*pwszTypeName*します。 場合**datetime**が指定されている*bScale* 3 である必要があります。 場合**smalldatetime**が指定されている*bScale* 0 にする必要があります。 場合*bScale*と整合性がありません*wType*と*pwszTypeName*DB_E_BADSCALE が返されます。  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化機能 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
