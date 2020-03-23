---
title: Položky MSBuild | Dokumenty společnosti Microsoft
description: Pomocí atributu MSBuild Include skupiny ItemGroup určete soubory, které mají být zahrnuty do sestavení.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7c41539ec50cb166dfe60690a4722992b29a47a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093974"
---
# <a name="msbuild-items"></a>Položky MSBuild

Položky MSBuild jsou vstupy do systému sestavení a obvykle představují `Include` soubory (soubory jsou zadány v atributu). Položky jsou seskupeny do typů položek na základě jejich názvů prvků. Typy položek jsou pojmenované seznamy položek, které lze použít jako parametry pro úkoly. Úkoly používají hodnoty položek k provedení kroků procesu sestavení.

 Vzhledem k tomu, že položky jsou pojmenovány podle typu položky, ke které patří, lze zaměnitelné termíny "položka" a "hodnota položky".

## <a name="create-items-in-a-project-file"></a>Vytvoření položek v souboru projektu

 Deklarujete položky v souboru projektu jako podřízené prvky prvku [ItemGroup.](../msbuild/itemgroup-element-msbuild.md) Název podřízeného prvku je typ položky. Atribut `Include` prvku určuje položky (soubory), které mají být zahrnuty do tohoto typu položky. Například následující jazyk XML vytvoří typ položky s názvem `Compile`, který obsahuje dva soubory.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Položka *file2.cs* nenahrazuje položku *file1.cs*; místo toho je název souboru připojen k `Compile` seznamu hodnot pro typ položky.

 Následující jazyk XML vytvoří stejný typ položky `Include` deklarováním obou souborů v jednom atributu. Všimněte si, že názvy souborů jsou odděleny středníkem.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

Atribut `Include` je cesta, která je interpretována vzhledem ke složce souboru projektu ,(MSBuildProjectPath), i když je položka v importovaném souboru, například *souboru .targets.*

## <a name="create-items-during-execution"></a>Vytvořit položky během provádění

 Položky, které jsou mimo [Target](../msbuild/target-element-msbuild.md) prvky jsou přiřazeny hodnoty během fáze hodnocení sestavení. Během fáze následného provádění lze položky vytvořit nebo upravit následujícími způsoby:

- Libovolný úkol může vyzařovat položku. Chcete-li vyzařovat položku, [Task](../msbuild/task-element-msbuild.md) element musí mít `ItemName` podřízený [Output](../msbuild/output-element-msbuild.md) prvek, který má atribut.

- Úloha [CreateItem](../msbuild/createitem-task.md) může vyzařovat položku. Tento způsob využití je zastaralý.

- Počínaje rozhraním .NET Framework `Target` 3.5 mohou prvky obsahovat prvky [ItemGroup,](../msbuild/itemgroup-element-msbuild.md) které mohou obsahovat prvky položky.

## <a name="reference-items-in-a-project-file"></a>Odkaz na položky v souboru projektu

 Chcete-li odkazovat na typy položek v\<celém souboru projektu, použijte syntaxi @( ItemType>). Například byste odkazovat na typ položky `@(Compile)`v předchozím příkladu pomocí . Pomocí této syntaxe můžete předat položky úkolům zadáním typu položky jako parametru tohoto úkolu. Další informace naleznete v [tématu Postup: Vyberte soubory, které chcete vytvořit](../msbuild/how-to-select-the-files-to-build.md).

 Ve výchozím nastavení jsou položky typu položky odděleny středníky (;) když se rozbalí. Syntaxi @(\<ItemType>,\<' oddělovač>' ) můžete použít k určení jiného oddělovače než výchozího. Další informace naleznete v [tématu Postup: Zobrazení seznamu položek oddělených čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Použití zástupných znaků k určení položek

Znaky `**`, `*`a `?` zástupné znaky můžete použít k určení skupiny souborů jako vstupů pro sestavení namísto zápisu každého souboru zvlášť.

- Zástupný `?` znak odpovídá jednomu znaku.
- Zástupný `*` znak odpovídá nule nebo více znaků.
- Sekvence `**` zástupných znaků odpovídá částečné cestě.

Můžete například zadat všechny `.cs` soubory v adresáři, který obsahuje soubor projektu, pomocí následujícího prvku v souboru projektu.

```xml
<CSFile Include="*.cs"/>
```

Následující prvek vybere `.vb` všechny soubory `D:` na jednotce:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Pokud chcete do položky `*` `?` zahrnout literál nebo znaky bez rozšíření zástupných znaků, je nutné [uniknout zástupným znakům](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Další informace o zástupných znacích naleznete v [tématu Postup: Vyberte soubory, které chcete vytvořit](../msbuild/how-to-select-the-files-to-build.md).

## <a name="use-the-exclude-attribute"></a>Použití atributu Vyloučit

 Prvky položky `Exclude` mohou obsahovat atribut, který vylučuje určité položky (soubory) z typu položky. Atribut `Exclude` se obvykle používá společně se zástupnými znaky. Například následující xml přidá každý soubor *CS* v adresáři do typu položky CSFile, s výjimkou *DoNotBuild.cs* souboru.

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 Atribut `Exclude` ovlivňuje pouze položky, které `Include` jsou přidány atributem v elementu položky, který je obsahuje oba. Následující příklad by nevyloučil *Form1.cs*souboru , který byl přidán do předchozího prvku položky.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Další informace naleznete v [tématu How to: Exclude files from the build](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Metadata položky

 Položky mohou obsahovat metadata kromě `Include` `Exclude` informací v atributy a. Tato metadata mohou používat úkoly, které vyžadují další informace o položkách nebo dávkové úkoly a cíle. Další informace naleznete v [tématu Batching](../msbuild/msbuild-batching.md).

 Metadata je kolekce párů klíč hodnota, které jsou deklarovány v souboru projektu jako podřízené prvky prvku položky. Název podřízeného prvku je název metadat a hodnota podřízeného prvku je hodnota metadat.

 Metadata jsou přidružena k prvku položky, který jej obsahuje. Například následující XML `Culture` přidá metadata, `Fr` která má hodnotu jak pro *one.cs,* tak *two.cs* položek typu položky CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Položka může mít nulové nebo více hodnot metadat. Hodnoty metadat můžete kdykoli změnit. Pokud nastavíte metadata na prázdnou hodnotu, efektivně odeberte z sestavení.

### <a name="reference-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a>Metadata odkazované položky v souboru projektu

 Metadata položky v celém souboru projektu můžete\<odkazovat pomocí syntaxe %( ItemMetadataName>). Pokud nejednoznačnost existuje, můžete kvalifikovat odkaz pomocí názvu typu položky. Můžete například zadat %(\<ItemType.ItemMetaDataName>). Následující příklad používá zobrazit metadata k dávkování úlohy Zpráva. Další informace o použití metadat položky pro dávkování naleznete [v tématu Metadata položky v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Stuff Include="One.cs" >
            <Display>false</Display>
        </Stuff>
        <Stuff Include="Two.cs">
            <Display>true</Display>
        </Stuff>
    </ItemGroup>
    <Target Name="Batching">
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>
    </Target>
</Project>
```

### <a name="well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a>Známá metadata položek

 Při přidání položky do typu položky je této položce přiřazena některá známá metadata. Například všechny položky mají dobře známá\<metadata %( Název souboru>), jehož hodnota je název souboru položky (bez přípony). Další informace naleznete v [tématu Známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="transform-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a>Transformace typů položek pomocí metadat

 Seznamy položek můžete transformovat do nových seznamů položek pomocí metadat. Můžete například transformovat `CppFiles` typ položky, který obsahuje položky, které představují soubory *CPP,* do odpovídajícího seznamu souborů *OBJ* pomocí výrazu `@(CppFiles -> '%(Filename).obj')`.

 Následující kód vytvoří `CultureResource` typ položky, `EmbeddedResource` který `Culture` obsahuje kopie všech položek s metadaty. Hodnota `Culture` metadat se stane hodnotou nových `CultureResource.TargetDirectory`metadat .

```xml
<Target Name="ProcessCultureResources">
    <ItemGroup>
        <CultureResource Include="@(EmbeddedResource)"
            Condition="'%(EmbeddedResource.Culture)' != ''">
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>
        </CultureResource>
    </ItemGroup>
</Target>
```

 Další informace naleznete v [tématu Transformace](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Definice položek

 Počínaje rozhraním .NET Framework 3.5 můžete přidat výchozí metadata do libovolného typu položky pomocí [elementu ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Stejně jako známá metadata je výchozí metadata přidružena ke všem položkám zadaného typu položky. V definici položky můžete explicitně přepsat výchozí metadata. Například následující XML poskytuje `Compile` položky *one.cs* a `BuildDay` *three.cs* metadata s hodnotou "Pondělí". Kód poskytuje položku *two.cs* `BuildDay` metadata s hodnotou "úterý".

```xml
<ItemDefinitionGroup>
    <Compile>
        <BuildDay>Monday</BuildDay>
    </Compile>
</ItemDefinitionGroup>
<ItemGroup>
    <Compile Include="one.cs;three.cs" />
    <Compile Include="two.cs">
        <BuildDay>Tuesday</BuildDay>
    </Compile>
</ItemGroup>
```

 Další informace naleznete v [tématu Definice položek](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Atributy pro položky v ItemGroup cíle

 Počínaje rozhraním .NET Framework `Target` 3.5 mohou prvky obsahovat prvky [ItemGroup,](../msbuild/itemgroup-element-msbuild.md) které mohou obsahovat prvky položky. Atributy v této části jsou platné, pokud jsou `ItemGroup` určeny pro `Target`položku v aplikaci .

### <a name="remove-attribute"></a><a name="BKMK_RemoveAttribute"></a>Odebrat atribut

 Atribut `Remove` odebere určité položky (soubory) z typu položky. Tento atribut byl zaveden v rozhraní .NET Framework 3.5 (pouze vnitřní cíle). Vnitřní i vnější cíle jsou podporovány počínaje MSBuild 15.0.

 Následující příklad odebere každý soubor *.config* z typu compile položky.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a>Atribut KeepMetadata

 Pokud je položka generována v rámci cíle, `KeepMetadata` prvek položky může obsahovat atribut. Pokud je tento atribut zadán, budou ze zdrojové položky do cílové položky přenesena pouze metadata, která jsou zadána v seznamu názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní nezadání. Atribut `KeepMetadata` byl zaveden v rozhraní .NET Framework 4.5.

 Následující příklad ukazuje, jak `KeepMetadata` použít atribut.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0">

    <ItemGroup>
        <FirstItem Include="rhinoceros">
            <Class>mammal</Class>
            <Size>large</Size>
        </FirstItem>

    </ItemGroup>
    <Target Name="MyTarget">
        <ItemGroup>
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />
        </ItemGroup>

        <Message Text="FirstItem: %(FirstItem.Identity)" />
        <Message Text="  Class: %(FirstItem.Class)" />
        <Message Text="  Size:  %(FirstItem.Size)"  />

        <Message Text="SecondItem: %(SecondItem.Identity)" />
        <Message Text="  Class: %(SecondItem.Class)" />
        <Message Text="  Size:  %(SecondItem.Size)"  />
    </Target>
</Project>

<!--
Output:
  FirstItem: rhinoceros
    Class: mammal
    Size:  large
  SecondItem: rhinoceros
    Class: mammal
    Size:
-->
```

### <a name="removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a>Atribut RemoveMetadata

 Pokud je položka generována v rámci cíle, `RemoveMetadata` prvek položky může obsahovat atribut. Pokud je tento atribut zadán, všechna metadata jsou přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní nezadání. Atribut `RemoveMetadata` byl zaveden v rozhraní .NET Framework 4.5.

 Následující příklad ukazuje, jak `RemoveMetadata` použít atribut.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <MetadataToRemove>Size;Material</MetadataToRemove>
    </PropertyGroup>

    <ItemGroup>
        <Item1 Include="stapler">
            <Size>medium</Size>
            <Color>black</Color>
            <Material>plastic</Material>
        </Item1>
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />
        </ItemGroup>

        <Message Text="Item1: %(Item1.Identity)" />
        <Message Text="  Size:     %(Item1.Size)" />
        <Message Text="  Color:    %(Item1.Color)" />
        <Message Text="  Material: %(Item1.Material)" />
        <Message Text="Item2: %(Item2.Identity)" />
        <Message Text="  Size:     %(Item2.Size)" />
        <Message Text="  Color:    %(Item2.Color)" />
        <Message Text="  Material: %(Item2.Material)" />
    </Target>
</Project>

<!--
Output:
  Item1: stapler
    Size:     medium
    Color:    black
    Material: plastic
  Item2: stapler
    Size:
    Color:    black
    Material:
-->
```

### <a name="keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a>Zachovat duplikáty, atribut

 Pokud je položka generována v rámci cíle, `KeepDuplicates` prvek položky může obsahovat atribut. `KeepDuplicates`je `Boolean` atribut, který určuje, zda má být položka přidána do cílové skupiny, pokud je položka přesným duplikátem existující položky.

 Pokud má zdrojová a cílová položka stejnou hodnotu Include, `KeepDuplicates` ale jiná `false`metadata, bude položka přidána, i když je nastavena na . Prázdná hodnota pro tento atribut je ekvivalentní nezadání. Atribut `KeepDuplicates` byl zaveden v rozhraní .NET Framework 4.5.

 Následující příklad ukazuje, jak `KeepDuplicates` použít atribut.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Item1 Include="hourglass;boomerang" />
        <Item2 Include="hourglass;boomerang" />
    </ItemGroup>

    <Target Name="MyTarget">
        <ItemGroup>
            <Item1 Include="hourglass" KeepDuplicates="false" />
            <Item2 Include="hourglass" />
        </ItemGroup>

        <Message Text="Item1: @(Item1)" />
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />
        <Message Text="Item2: @(Item2)" />
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />
    </Target>
</Project>

<!--
Output:
  Item1: hourglass;boomerang
    hourglass  Count: 1
    boomerang  Count: 1
  Item2: hourglass;boomerang;hourglass
    hourglass  Count: 2
    boomerang  Count: 1
-->
```

## <a name="see-also"></a>Viz také

- [Prvek položky (MSBuild)](../msbuild/item-element-msbuild.md)
- [Běžné položky projektu MSBuild](../msbuild/common-msbuild-project-items.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Postup: Vyberte soubory, které chcete sestavit.](../msbuild/how-to-select-the-files-to-build.md)
- [Postup: Vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)
- [Postup: Zobrazení seznamu položek oddělených čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definice položek](../msbuild/item-definitions.md)
- [Dávkování](../msbuild/msbuild-batching.md)
