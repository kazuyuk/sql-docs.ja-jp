---
title: EntityType 要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4f2697b3616e2a47e32b87913c49f76e009153a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277598"
---
# <a name="entitytype-element-csdlbi"></a>EntityType 要素 (CSDLBI)
  `EntityType` 要素は、データ モデルで顧客や注文などの高レベル エンティティの構造を表す複合型です。 `bi:EntityType`要素の定義を拡張する[EntityType](http://msdn.microsoft.com/library/bb399206.aspx)で使用される、 [Entity Data Framework](http://msdn.microsoft.com/library/bb399567.aspx)します。  
  
 EntityType 要素は、データ モデルに含まれる各エンティティに対して指定される必要があります。 EntityType のサブ要素では、テーブルの列とメジャーが記述されます。 テーブル間のリレーションシップは `EntityContainer` に含まれます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、`EntityType` 要素を定義する要素と属性を示します。 関連項目に適用される属性、 [EntityType](http://msdn.microsoft.com/library/bb399206.aspx)要素。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|目次|いいえ|列内のデータの種類を含む文字列です。 値は、データ モデルの DimensionAttributeTypeEnumType の値から取得されます。<br /><br /> DimensionAttributeTypeEnumType の値が ExtendedType の場合は、Contents の値は DimensionAttribute の ExtendedType 要素から取得されます。 クライアントはこれらの値に対応する必要はありません。|  
|DefaultDetails|いいえ|プロパティ参照のリスト。テーブル内の列のセットを表します。<br /><br /> 参照してください[DefaultDetails 要素&#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)します。|  
|DefaultImage|いいえ|エンティティを示すイメージを含む列への参照。<br /><br /> 多次元モデルでは、この要素は、ディメンション属性のバイナリ属性に対応します。 この属性が存在する場合、要素にはただ 1 つの MemberRef 要素が必ず含まれます。<br /><br /> 参照してください[MemberRef 要素&#40;CSDLBI&#41;](memberref-element-csdlbi.md)します。|  
|DefaultMeasure|いいえ|エンティティ上での計算時に既定として使用されるエンティティのメジャーへの参照です。 指定しない場合は、SUM が既定値です。<br /><br /> 参照してください[MemberRef 要素&#40;CSDLBI&#41;](memberref-element-csdlbi.md)します。|  
|DisplayKey|いいえ|列またはロール エンドに対する参照のリスト。エンティティ インスタンスを一意に識別する強い識別子を構成します。<br /><br /> 参照してください[DisplayKey 要素&#40;CSDLBI&#41;](displaykey-element-csdlbi.md)します。|  
|Hieararchy|いいえ|モデルの階層のリスト。<br /><br /> 参照してください[Hierarchy 要素&#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)します。|  
|ReferenceName|はい|Data Analysis Expressions (DAX) クエリでこのエンティティを参照するために使用できる識別子。<br /><br /> この属性が存在しない場合は、エンティティの完全修飾されたフィールド名が使用されます。|  
|SortMembers|いいえ|並べ替えるの基準となるプロパティの一覧です。 SortDirection 属性が昇順または降順を示します。|  
  
## <a name="contents-element"></a>Contents 要素  
 `Contents` 要素は、エンティティのデータの種類を示す単純型です。  
  
 エンティティ (列) のコンテンツは次の値のいずれかです。  
  
|値|説明|  
|-----------|-----------------|  
|Regular|特に定義されていない場合。|  
|[時刻]|年、半期、四半期、月、日などの時間間隔を表す属性。|  
|Geography|市区町村や郵便番号などの地理情報を表す属性。|  
|Organization|従業員や子会社などの組織情報を表す属性。|  
|BillOfMaterials|製品の部品表などの在庫情報や製造情報を表す属性。|  
|Accounts|財務報告用の勘定科目一覧表を表す属性。|  
|Customers|顧客情報や連絡先情報を表す属性。|  
|Products|製品情報を表す属性。|  
|シナリオ|計画的または戦略的な分析情報を表す属性。|  
|Quantitative|量的な情報を表す属性。|  
|Utility|その他の情報を表す属性。|  
|通貨|通貨のデータとメタデータが含まれます。|  
|Rates|通貨レート情報を表す属性。|  
|Channel|チャネル情報を表す属性。|  
|Promotion|マーケティング関連のプロモーション情報を表す属性。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 次の例は、AdventureWorks のテーブル モデルで使用される Geography テーブルの CSDLBI Version 1.1 による表現の一部です。 RowNumber 列は、テーブル モデルの行識別子 (ROWID) として自動的に生成される非表示の列で、Contents 属性の `RowNumber` を持ちます。  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 次の例は、Contoso Operations キューブからの時間ディメンションの一部を表す、CSDLBI Version 1.1 で表現した EntityType 要素を示します。  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>参照  
 [CSDL への BI 注釈のテクニカル リファレンス](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
