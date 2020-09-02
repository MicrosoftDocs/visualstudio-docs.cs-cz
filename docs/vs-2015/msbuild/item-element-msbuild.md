---
title: Item – Element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: cc3d606bb890b5f95089bfc7b1e83b2d34cd56ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192603"
---
# <a name="item-element-msbuild"></a>Item – prvek (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje uživatelem definovanou položku a její metadata. Každá položka, která se používá v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu, musí být zadána jako podřízený `ItemGroup` elementu.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Syntax  
  
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
|`Include`|Požadovaný atribut.<br /><br /> Soubor nebo zástupný znak, který má být zahrnut do seznamu položek.|  
|`Exclude`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který se má vyloučit ze seznamu položek.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`Remove`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který se má odebrat ze seznamu položek<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|  
|`KeepMetadata`|Nepovinný atribut.<br /><br /> Metadata zdrojových položek, které mají být přidány do cílových položek. Ze zdrojové položky do cílové položky jsou předávána pouze metadata, jejichž názvy jsou zadány v seznamu středníkem oddělených. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|  
|`RemoveMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, která se nepřenášejí do cílových položek. Všechna metadata jsou přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|  
|`KeepDuplicates`|Nepovinný atribut.<br /><br /> Určuje, zda má být položka přidána do cílové skupiny, pokud se jedná o přesný duplikát existující položky. Pokud má zdrojová a cílová položka stejnou `Include` hodnotu, ale odlišná metadata, je položka přidána i v případě, že `KeepDuplicates` je nastavena na `false` . Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[ItemMetadata –](../msbuild/itemmetadata-element-msbuild.md)|Klíč metadat položky definovaný uživatelem, který obsahuje hodnotu metadat položky. Položka může obsahovat nula nebo více `ItemMetadata` prvků.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Seskupení elementu pro položky|  
  
## <a name="remarks"></a>Poznámky  
 `Item` prvky definují vstupy do systému sestavení a jsou seskupeny do kolekcí položek na základě jejich uživatelsky definovaných názvů kolekcí. Tyto kolekce položek lze použít jako parametry pro [úlohy](../msbuild/msbuild-tasks.md), které používají jednotlivé položky v kolekcích k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
 Použití notace Notation `@(` *MyType* `)` umožňuje rozšířit kolekci položek typu *MyType* na seznam řetězců oddělených středníkem a předat parametru. Pokud je parametr typu `string` , pak hodnota parametru je seznam elementů, které jsou odděleny středníky. Pokud je parametr pole řetězců ( `string[]` ), pak je každý element vložen do pole na základě umístění středníků. Pokud je parametr úlohy typu <xref:Microsoft.Build.Framework.ITaskItem> `[]` , pak je hodnota obsahem kolekce položek společně s připojenými metadaty. K vymezení každé položky pomocí jiného znaku než středníku použijte `@(` *myType* `, '` *oddělovač*MyType syntaxe `')` .  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Modul může vyhodnotit zástupné znaky, například `*` a `?` a rekurzivní zástupné znaky, jako například `/**/*.cs` . Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak deklarovat dvě položky typu `CSFile` . Druhá deklarovaná položka obsahuje metadata, která jsou `MyMetadata` nastavena na `HelloWorld` .  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Viz také  
 [Položek](../msbuild/msbuild-items.md)   
 [Vlastnosti nástroje MSBuild](msbuild-properties1.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
