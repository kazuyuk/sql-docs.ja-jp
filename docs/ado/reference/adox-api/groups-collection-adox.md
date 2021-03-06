---
title: コレクション (ADOX) をグループ化 |Microsoft ドキュメント
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
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 253cf76adf8f32734b4bd878cb2f623e79489ccb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285971"
---
# <a name="groups-collection-adox"></a>グループのコレクション (ADOX)
すべてを含むストアド[グループ](../../../ado/reference/adox-api/group-object-adox.md)カタログまたはユーザーのオブジェクト。  
  
## <a name="remarks"></a>コメント  
 **グループ**のコレクション、[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)のすべてのカタログのグループ アカウントを表します。 **グループ**のコレクション、[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)ユーザーが所属するグループのみを表します。  
  
 [Append](../../../ado/reference/adox-api/append-method-adox-groups.md)のメソッド、**グループ**コレクションは ADOX に一意です。 可能な代替手段としては以下の方法があります。  
  
-   新しいセキュリティ グループを使用して、コレクションに追加、 **Append**メソッドです。  
  
 残りのプロパティとメソッドは、standard ADO コレクションには、 可能な代替手段としては以下の方法があります。  
  
-   使用して、コレクション内のグループへのアクセス、[項目](../../../ado/reference/ado-api/item-property-ado.md)プロパティです。  
  
-   使用して、コレクションに含まれるグループの数を返す、[カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティです。  
  
-   グループを使用して、コレクションから削除、[削除](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドです。  
  
-   現在のデータベース スキーマを反映するようにコレクション内のオブジェクトを更新、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドです。  
  
> [!NOTE]
>  追加の前に、**グループ**オブジェクトを**グループ**のコレクション、**ユーザー**オブジェクト、**グループ**が同じオブジェクト[名前](../../../ado/reference/adox-api/name-property-adox.md)追加する 1 つに既に存在すると、**グループ**のコレクション、**カタログ**です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [Groups コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Group オブジェクト (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
