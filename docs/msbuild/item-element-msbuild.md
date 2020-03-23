---
title: Prvek položky (MSBuild) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169349"
---
# <a name="item-element-msbuild"></a>Prvek položky (MSBuild)

Obsahuje uživatelem definovanou položku a její metadata. Každá položka, která se používá v projektu MSBuild, `ItemGroup` musí být zadána jako podřízený prvek.

\<> \<položky \<> položky položky položky položky skupiny položky> projektu

## <a name="syntax"></a>Syntaxe

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Určení metadat jako atributů

V MSBuild 15.1 nebo novější, všechna metadata s názvem, který není v konfliktu s aktuální seznam atributů může volitelně vyjádřit jako atribut.

Chcete-li například zadat seznam balíčků NuGet, obvykle byste použili něco jako následující syntaxe.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Nyní však můžete předat `Version` metadata jako atribut, například v následující syntaxi:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Include`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který chcete zahrnout do seznamu položek.|
|`Exclude`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak, který chcete vyloučit ze seznamu položek.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|
|`Remove`|Nepovinný atribut.<br /><br /> Soubor nebo zástupný znak odebrat ze seznamu položek.<br /><br />|
|`KeepDuplicates`|Nepovinný atribut.<br /><br /> Určuje, zda má být položka přidána do cílové skupiny, pokud se jedná o přesný duplikát existující položky. Pokud má zdrojová a `Include` cílová položka stejnou hodnotu, ale `KeepDuplicates` jiná `false`metadata, bude položka přidána i v případě, že je nastavena na hodnotu . Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, `ItemGroup` že je určen `Target`pro položku v aplikaci .|
|`KeepMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, které chcete přidat do cílových položek. Ze zdrojové položky do cílové položky jsou přenesena pouze metadata, jejichž názvy jsou zadány v seznamu oddělených středníkem. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, `ItemGroup` že je určen `Target`pro položku v aplikaci .|
|`RemoveMetadata`|Nepovinný atribut.<br /><br /> Metadata pro zdrojové položky, které nemají být přeneseny na cílové položky. Všechna metadata jsou přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).<br /><br /> Tento atribut je platný pouze v případě, `ItemGroup` že je určen `Target`pro položku v aplikaci .|
|`Update`|Nepovinný atribut. (K dispozici pouze pro projekty .NET Core v sadě Visual Studio 2017 nebo novější.)<br /><br /> Umožňuje upravit metadata souboru, který byl zahrnut pomocí glob.<br /><br /> Tento atribut je platný pouze v případě, `ItemGroup` že je určen `Target`pro položku, která není v .|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Metadata položky](../msbuild/itemmetadata-element-msbuild.md)|Uživatelem definovaný klíč metadat položky, který obsahuje hodnotu metadat položky. V položce může `ItemMetadata` být nula nebo více prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Skupina položek](../msbuild/itemgroup-element-msbuild.md)|Seskupování elementu pro položky.|

## <a name="remarks"></a>Poznámky

`Item`elementy definují vstupy do systému sestavení a jsou seskupeny do kolekcí položek na základě jejich uživatelem definovaných názvů kolekcí. Tyto kolekce položek lze použít jako parametry pro [úkoly](../msbuild/msbuild-tasks.md), které používají jednotlivé položky v kolekcích k provedení kroků procesu sestavení. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

Pomocí notace\<@( myType>) umožňuje \<kolekci položek typu myType> rozbalit do seznamu řetězců oddělených středníkem a předat parametru. Pokud je parametr `string`typu , pak hodnota parametru je seznam prvků, oddělený středníky. Pokud je parametrem pole řetězců`string[]`( ), pak je každý prvek vložen do pole na základě umístění středníků. Pokud je parametr úlohy typu <xref:Microsoft.Build.Framework.ITaskItem> `[]`, pak hodnota je obsah kolekce položek spolu s všechna metadata připojena. Chcete-li vymezit každou položku pomocí jiného znaku než středník, použijte syntaxi @(\<myType>, '\<oddělovač>').

Modul MSBuild může vyhodnotit `*` zástupné znaky, například `?` a rekurzivní zástupné znaky, například * / \* \* / \*.cs*. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

## <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak deklarovat dvě položky typu `CSFile`. Druhá deklarovaná položka `MyMetadata` obsahuje `HelloWorld`metadata, která byla nastavena na .

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

Následující příklad kódu ukazuje, `Update` jak použít atribut k úpravě metadat v souboru s názvem *somefile.cs,* který byl zahrnut prostřednictvím glob. (K dispozici pouze pro projekty .NET Core v sadě Visual Studio 2017 nebo novější.)

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Items](../msbuild/msbuild-items.md)
- [Běžné položky projektu MSBuild](../msbuild/common-msbuild-project-items.md)
- [Vlastnosti MSBuild](../msbuild/msbuild-properties.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
