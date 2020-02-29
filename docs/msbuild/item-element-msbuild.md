---
title: Item – Element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: ff7e446c319a08004260125580cdace43412cdba
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169349"
---
# <a name="item-element-msbuild"></a>Item – Element (MSBuild)

Obsahuje uživatelem definovanou položku a její metadata. Každá položka, která je použita v projektu MSBuild, musí být zadána jako podřízený prvku `ItemGroup`.

\<projektu > \<položka > \<položka >

## <a name="syntax"></a>Syntaxe

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

Teď ale můžete metadata `Version` předat jako atribut, jako je například v následující syntaxi:

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
|`KeepDuplicates`|Nepovinný atribut.<br /><br /> Určuje, zda má být položka přidána do cílové skupiny, pokud se jedná o přesný duplikát existující položky. Pokud má zdrojová a cílová položka stejnou `Include` hodnotu, ale odlišná metadata, přidá se tato položka i v případě, že je `KeepDuplicates` nastavená na `false`. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v `ItemGroup`, která je ve `Target`.|
|`KeepMetadata`|Nepovinný atribut.<br /><br /> Metadata zdrojových položek, které mají být přidány do cílových položek. Ze zdrojové položky do cílové položky jsou předávána pouze metadata, jejichž názvy jsou zadány v seznamu středníkem oddělených. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v `ItemGroup`, která je ve `Target`.|
|`RemoveMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, která se nepřenášejí do cílových položek. Všechna metadata jsou přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v `ItemGroup`, která je ve `Target`.|
|`Update`|Nepovinný atribut. (K dispozici pouze pro projekty .NET Core v aplikaci Visual Studio 2017 nebo novější.)<br /><br /> Umožňuje upravit metadata souboru, který byl zahrnutý pomocí glob.<br /><br /> Tento atribut je platný pouze v případě, že je zadán pro položku v `ItemGroup`, která není ve `Target`.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[ItemMetadata –](../msbuild/itemmetadata-element-msbuild.md)|Klíč metadat položky definovaný uživatelem, který obsahuje hodnotu metadat položky. V položce může být nula nebo více `ItemMetadata` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Seskupení elementu pro položky|

## <a name="remarks"></a>Poznámky

prvky `Item` definují vstupní hodnoty do systému sestavení a jsou seskupeny do kolekcí položek na základě jejich uživatelsky definovaných názvů kolekcí. Tyto kolekce položek lze použít jako parametry pro [úlohy](../msbuild/msbuild-tasks.md), které používají jednotlivé položky v kolekcích k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

Použití notace Notation @ (\<myType >) umožňuje rozšířit kolekci položek typu \<myType > na seznam řetězců oddělených středníkem a předaných do parametru. Pokud je parametr typu `string`, pak hodnota parametru je seznam elementů, které jsou odděleny středníky. Pokud je parametr pole řetězců (`string[]`), pak je každý element vložen do pole na základě umístění středníků. Pokud je parametr úlohy typu <xref:Microsoft.Build.Framework.ITaskItem>`[]`, pak je hodnotou obsah kolekce Items spolu s připojenými metadaty. K vymezení jednotlivých položek pomocí znaku jiného než středníku použijte syntaxi @ (\<myType >, '\<oddělovač > ').

Modul MSBuild může vyhodnotit zástupné znaky, například `*` a `?` a rekurzivní zástupné znaky, jako je například */\*\*/\*. cs*. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak deklarovat dvě položky typu `CSFile`. Druhá deklarovaná položka obsahuje metadata, která mají `MyMetadata` nastavená na `HelloWorld`.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Následující příklad kódu ukazuje, jak použít atribut `Update` pro úpravu metadat v souboru s názvem *somefile.cs* , který byl zahrnut prostřednictvím glob. (K dispozici pouze pro projekty .NET Core v aplikaci Visual Studio 2017 nebo novější.)

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
- [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
