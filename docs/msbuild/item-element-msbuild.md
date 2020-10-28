---
title: Item – Element (MSBuild) | Microsoft Docs
description: Naučte se, jak MSBuild používá prvek Item k zahrnutí uživatelsky definované položky a jejích metadat. Každá položka musí být podřízenou položkou elementu Item.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51ecf68cacf0edca90893931642cd7fb6064f972
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904644"
---
# <a name="item-element-msbuild"></a>Item – Element (MSBuild)

Obsahuje uživatelem definovanou položku a její metadata. Každá položka, která je použita v projektu MSBuild, musí být zadána jako podřízený `ItemGroup` elementu.

\<Project>
\<ItemGroup>
\<Item>

## <a name="syntax"></a>Syntax

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Zadat metadata jako atributy

V MSBuild 15,1 nebo novější může být jakákoli metadata s názvem, která nejsou v konfliktu s aktuálním seznamem atributů, volitelně vyjádřena jako atribut.

Například pro určení seznamu balíčků NuGet byste obvykle použili něco podobného jako následující syntaxe.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Teď ale můžete `Version` metadata předat jako atribut, například v následující syntaxi:

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
|`Include`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který má být zahrnut do seznamu položek.|
|`Exclude`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který se má vyloučit ze seznamu položek.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|
|`Remove`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který se má odebrat ze seznamu položek<br /><br />|
|`KeepDuplicates`|Nepovinný atribut.<br /><br /> Určuje, zda má být položka přidána do cílové skupiny, pokud se jedná o přesný duplikát existující položky. Pokud má zdrojová a cílová položka stejnou `Include` hodnotu, ale odlišná metadata, je položka přidána i v případě, že `KeepDuplicates` je nastavena na `false` . Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|
|`KeepMetadata`|Nepovinný atribut.<br /><br /> Metadata zdrojových položek, které mají být přidány do cílových položek. Ze zdrojové položky do cílové položky jsou předávána pouze metadata, jejichž názvy jsou zadány v seznamu středníkem oddělených. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|
|`RemoveMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, která se nepřenášejí do cílových položek. Všechna metadata jsou přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v objektu `ItemGroup` , který je v `Target` .|
|`Update`|Nepovinný atribut. (K dispozici pouze pro projekty .NET Core v aplikaci Visual Studio 2017 nebo novější.)<br /><br /> Umožňuje změnit metadata položky; obvykle se používá k přepsání výchozích metadat konkrétních položek po intially určení skupiny položek (například se zástupným znakem).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v `ItemGroup` , která není v `Target` .|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[ItemMetadata –](../msbuild/itemmetadata-element-msbuild.md)|Klíč metadat položky definovaný uživatelem, který obsahuje hodnotu metadat položky. Položka může obsahovat nula nebo více `ItemMetadata` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Seskupení elementu pro položky|

## <a name="remarks"></a>Poznámky

`Item` prvky definují vstupy do systému sestavení a jsou seskupeny do kolekcí položek na základě jejich uživatelsky definovaných názvů kolekcí. Tyto kolekce položek lze použít jako parametry pro [úlohy](../msbuild/msbuild-tasks.md), které používají jednotlivé položky v kolekcích k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

Použití notace @ ( \<myType> ) umožňuje rozšířit kolekci položek typu \<myType> na seznam řetězců oddělených středníkem a předat parametru. Pokud je parametr typu `string` , pak hodnota parametru je seznam elementů, které jsou odděleny středníky. Pokud je parametr pole řetězců ( `string[]` ), pak je každý element vložen do pole na základě umístění středníků. Pokud je parametr úlohy typu <xref:Microsoft.Build.Framework.ITaskItem> `[]` , pak je hodnota obsahem kolekce položek společně s připojenými metadaty. K vymezení každé položky pomocí jiného znaku než středníku použijte syntaxi @ ( \<myType> , ' \<separator> ').

Modul MSBuild může vyhodnotit zástupné znaky, jako jsou `*` a `?` a rekurzivní zástupné znaky, jako je například */ \* \* / \* . cs* . Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak deklarovat dvě položky typu `CSFile` . Druhá deklarovaná položka obsahuje metadata, která jsou `MyMetadata` nastavena na `HelloWorld` .

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Následující příklad kódu ukazuje, jak použít `Update` atribut pro úpravu metadat v souboru s názvem *somefile.cs* , který byl zahrnut prostřednictvím glob. (K dispozici pouze pro projekty .NET Core v aplikaci Visual Studio 2017 nebo novější.)

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Položky](../msbuild/msbuild-items.md)
- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
- [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
