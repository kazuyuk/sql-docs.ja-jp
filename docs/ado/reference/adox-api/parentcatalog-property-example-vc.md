---
title: ParentCatalog プロパティの例 (vc++) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ParentCatalog property [ADOX], VC++ example
ms.assetid: 43ae202e-1972-4aab-9cc1-3b6612bad363
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 686e8a9dff329f4082c83af83d25855d4b30e2f2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286591"
---
# <a name="parentcatalog-property-example-vc"></a>ParentCatalog プロパティの例 (vc++)
次のコードを使用する方法を示しています、 [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md)カタログにテーブルを追加する前に、プロバイダー固有のプロパティにアクセスするプロパティです。 このプロパティは**AutoIncrement**、Microsoft Jet データベースで自動増分 フィールドを作成します。  
  
```  
// BeginCreateAutoIncrColumnCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" rename("EOF", "EndOfFile")  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define and initialize ADOX object pointers. These are in ADODB namespace.  
   _CatalogPtr m_pCatalog = NULL;  
   _TablePtr m_pTable = NULL;  
  
   // Define ADODB object pointers.  
   ADODB::_ConnectionPtr m_pCnn = NULL;  
  
   // Define string variables  
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data Source='c:\\Northwind.mdb';");  
  
   try {  
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));  
      TESTHR(hr = m_pTable.CreateInstance(__uuidof (Table)));  
  
      // Connect the catalog.  
      m_pCnn->Open (strCnn, "", "", NULL);  
  
      m_pCatalog->PutActiveConnection(variant_t((IDispatch *)m_pCnn));  
  
      m_pTable->Name = "MyContacts";  
      m_pTable->ParentCatalog = m_pCatalog;  
  
      // Create fields and append them to the new Table object.  
      m_pTable->Columns->Append("ContactId", adInteger,0);  
  
      // Make the ContactId column and auto incrementing column  
      m_pTable->Columns->GetItem("ContactId")->Properties->GetItem("AutoIncrement")->Value = true;  
      m_pTable->Columns->Append("CustomerID", adVarWChar,0);  
      m_pTable->Columns->Append("FirstName", adVarWChar,0);  
      m_pTable->Columns->Append("LastName", adVarWChar,0);  
      m_pTable->Columns->Append("Phone", adVarWChar, 20);  
      m_pTable->Columns->Append("Notes", adLongVarWChar,0);  
      m_pCatalog->Tables->Append(_variant_t((IDispatch*)m_pTable));  
  
      // Refresh the database.  
      m_pCatalog->Tables->Refresh();  
  
      printf("Table 'MyContacts' is added.\n");  
  
      // Delete new table, since this is only an example  
      m_pCatalog->Tables->Delete("MyContacts");  
  
      printf("Table 'MyContacts' is deleted.\n");  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
   catch(...) {  
      cout << "Error occured in CreateAutoIncrColumnX...."<< endl;  
   }  
  
   m_pCatalog = NULL;  
   ::CoUninitialize();  
}  
```
