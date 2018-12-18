---
title: Položka – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dfec558a9958d980d25d4160c4b7f2ce269cbb5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270024"
---
# <a name="item-element-msbuild"></a>Item – prvek (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Obsahuje uživatelem definovanou položku a jeho metadata. Všechny položky, který se používá v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu musí být zadán jako podřízený objekt `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup >  
 \<Položka >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Include`|Požadovaný atribut.<br /><br /> Soubor nebo zástupný znak a v seznamu položek zahrnují.|  
|`Exclude`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak a vyloučit ze seznamu položek.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínku, která má být vyhodnocen. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`Remove`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak a odebrat ze seznamu položek.<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
|`KeepMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, které chcete přidat do cílové položky. Jenom metadata, jejichž názvy jsou určené v seznam oddělený středníkem jsou přeneseny z položky zdroje do cílové položky. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
|`RemoveMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky není přenést na cílí na položky. Všechna metadata se přenesou z položky zdrojové do cílové položky s výjimkou metadat jejichž názvy jsou obsaženy v středníkem oddělený seznam názvů. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
|`KeepDuplicates`|Nepovinný atribut.<br /><br /> Určuje, zda položky by měl přidat do cílové skupiny, jde přesnou kopii existující položku. Pokud zdrojové a cílové položky mají stejné `Include` hodnota, ale rozdílná metadata, položka je přidaná i v případě `KeepDuplicates` je nastavena na `false`. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný jenom v případě, že je zadané pro položku `ItemGroup` , který je ve `Target`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Itemmetadata](../msbuild/itemmetadata-element-msbuild.md)|Klíč metadat uživatelem definovanou položku katalogu, který obsahuje hodnotu metadat položky. Může být nula nebo více `ItemMetadata` prvky v položce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Element Grouping pro položky.|  
  
## <a name="remarks"></a>Poznámky  
 `Item` elementy definovat vstupy do systému sestavení a jsou seskupené do kolekcí položek na základě jejich uživatelem definované kolekci názvů. Tyto položky kolekce se dají použít jako parametry pro [úlohy](../msbuild/msbuild-tasks.md), které používají jednotlivé položky v kolekci k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
 Pomocí notace `@(` *myType* `)` umožňuje kolekci položek typu *myType* rozbalí do seznam řetězců oddělených středníkem, a předat parametr. Pokud je parametr typu `string`, hodnota parametru se bude seznam prvků, oddělené středníky. Pokud je parametr pole řetězců (`string[]`), pak každý prvek se vloží do pole na základě umístění středníky. Pokud je parametr úlohy typu <xref:Microsoft.Build.Framework.ITaskItem> `[]`, pak hodnota je obsah kolekce položek spolu s veškerá metadata připojené. K oddělení jednotlivých položek s použitím znaku jiného než středník, použijte syntaxi `@(` *myType*`, '`*oddělovač*`')`.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Modul vyhodnocení zástupné znaky, jako `*` a `?` a rekurzivní zástupné znaky, jako `/**/*.cs`. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak deklarovat dvě položky typu `CSFile`. Deklarována druhá položka obsahuje metadata, která má `MyMetadata` nastavena na `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Viz také  
 [Položky](../msbuild/msbuild-items.md)   
 [Vlastnosti nástroje MSBuild](msbuild-properties1.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)



