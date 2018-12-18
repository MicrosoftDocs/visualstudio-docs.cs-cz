---
title: Položka – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e33f057f3184a9a9bb19311f7206c6ab273dab8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081017"
---
# <a name="item-element-msbuild"></a>Item – element (MSBuild)
Obsahuje uživatelem definovanou položku a jeho metadata. Všechny položky, který se používá v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu musí být zadán jako podřízený objekt `ItemGroup` elementu.  

 \<Project>  
 \<ItemGroup >  
 \<Položka >  

## <a name="syntax"></a>Syntaxe  

```xml  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Zadejte metadat jako atributy
V MSBuild 15.1 nebo novější může být jakékoli metadat s názvem, který není v konfliktu s aktuální seznam atributů volitelně vyjádřený jako atribut.

Například pokud chcete zadat seznam balíčků NuGet, běžně používáte něco jako následující syntaxi.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Teď, ale můžete předat `Version` metadat jako atribut, jako je například následující syntax:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  

### <a name="attributes"></a>Atributy  

|Atribut|Popis|  
|---------------|-----------------|  
|`Include`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak a v seznamu položek zahrnují.|  
|`Exclude`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak a vyloučit ze seznamu položek.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínku, která má být vyhodnocen. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`Remove`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak a odebrat ze seznamu položek.<br /><br />|  
|`KeepDuplicates`|Nepovinný atribut.<br /><br /> Určuje, zda položky by měl přidat do cílové skupiny, jde přesnou kopii existující položku. Pokud zdrojové a cílové položky mají stejné `Include` hodnota, ale rozdílná metadata, položka je přidaná i v případě `KeepDuplicates` je nastavena na `false`. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
|`KeepMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, které chcete přidat do cílové položky. Jenom metadata, jejichž názvy jsou určené v seznam oddělený středníkem jsou přeneseny z položky zdroje do cílové položky. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
|`RemoveMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky není přenést na cílí na položky. Všechna metadata se přenesou z položky zdrojové do cílové položky s výjimkou metadat jejichž názvy jsou obsaženy v středníkem oddělený seznam názvů. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
|`Update`|Nepovinný atribut. (K dispozici pouze pro projekty .NET Core v sadě Visual Studio 2017 nebo novější).<br /><br /> Umožňuje upravit metadata, která byla zahrnuta glob pomocí souboru.<br /><br />  Tento atribut je platný jenom v případě, že je zadané pro položku v `ItemGroup` , který se nepoužívá `Target`.|  

### <a name="child-elements"></a>Podřízené prvky  

|Prvek|Popis|  
|-------------|-----------------|  
|[Itemmetadata](../msbuild/itemmetadata-element-msbuild.md)|Klíč metadat uživatelem definovanou položku katalogu, který obsahuje hodnotu metadat položky. Může být nula nebo více `ItemMetadata` prvky v položce.|  

### <a name="parent-elements"></a>Nadřazené prvky  

|Prvek|Popis|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element Grouping pro položky.|  

## <a name="remarks"></a>Poznámky  
 `Item` elementy definovat vstupy do systému sestavení a jsou seskupené do kolekcí položek na základě jejich uživatelem definované kolekci názvů. Tyto položky kolekce se dají použít jako parametry pro [úlohy](../msbuild/msbuild-tasks.md), které používají jednotlivé položky v kolekci k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  

 Pomocí notace @(\<myType >) umožňuje kolekci položek typu \<myType > rozbalí do seznam řetězců oddělených středníkem, a předat parametr. Pokud je parametr typu `string`, hodnota parametru se bude seznam prvků, oddělené středníky. Pokud je parametr pole řetězců (`string[]`), pak každý prvek se vloží do pole na základě umístění středníky. Pokud je parametr úlohy typu <xref:Microsoft.Build.Framework.ITaskItem> `[]`, pak hodnota je obsah kolekce položek spolu s veškerá metadata připojené. K oddělení jednotlivých položek s použitím znaku jiného než středník, použijte syntaxi @(<myType>, "<separator>").  

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Modul vyhodnocení zástupné znaky, jako `*` a `?` a rekurzivní zástupné znaky, jako  */ \* \* / \*.cs*. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje, jak deklarovat dvě položky typu `CSFile`. Deklarována druhá položka obsahuje metadata, která má `MyMetadata` nastavena na `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
Následující příklad kódu ukazuje, jak používat `Update` atribut k úpravě metadat v souboru s názvem *somefile.cs* , která byla zahrnuta prostřednictvím glob. (K dispozici pouze pro projekty .NET Core v sadě Visual Studio 2017 nebo novější).

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>Viz také:  
 [Položky](../msbuild/msbuild-items.md)   
 [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
