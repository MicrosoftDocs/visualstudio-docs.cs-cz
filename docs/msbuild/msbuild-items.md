---
title: Položky nástroje MSBuild | Microsoft Docs
description: Pro určení souborů, které se mají zahrnout do sestavení, použijte atribut include pro MSBuild.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cebf824785fed39cfd824b9b90f9d19be5df8c64
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251716"
---
# <a name="msbuild-items"></a>Položky nástroje MSBuild
Položky nástroje MSBuild jsou vstupy do systému sestavení a obvykle představují soubory (soubory jsou zadány v `Include` atributu). Položky jsou seskupeny do typů položek na základě jejich názvů prvků. Typy položek jsou pojmenované seznamy položek, které lze použít jako parametry pro úlohy. Úkoly používají hodnoty položek k provedení kroků procesu sestavení.

 Vzhledem k tomu, že položky jsou pojmenovány typem položky, ke kterým patří, je možné použít "položku" a "hodnotu položky", které jsou zaměnitelné.

## <a name="create-items-in-a-project-file"></a>Vytvoření položek v souboru projektu
 Položky v souboru projektu deklarujete jako podřízené prvky elementu [ItemCollection](../msbuild/itemgroup-element-msbuild.md) . Název podřízeného prvku je typ položky. `Include` Atribut elementu určuje položky (soubory), které mají být zahrnuty do daného typu položky. Například následující kód XML vytvoří typ položky s názvem `Compile`, který obsahuje dva soubory.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Položka *File2.cs* nenahrazuje položku *FILE1.cs*; místo toho se název souboru připojí k seznamu hodnot pro daný `Compile` typ položky.

 Následující kód XML vytvoří stejný typ položky deklarováním obou souborů v jednom `Include` atributu. Všimněte si, že názvy souborů jsou oddělené středníkem.

```xml
<ItemGroup>
    <Compile Include = "file1.cs;file2.cs"/>
</ItemGroup>
```

## <a name="create-items-during-execution"></a>Během provádění vytvořit položky
 K položkám, které jsou mimo [cílové](../msbuild/target-element-msbuild.md) prvky, jsou přiřazeny hodnoty během fáze hodnocení sestavení. Během následné fáze provádění lze položky vytvořit nebo upravit následujícími způsoby:

- Libovolný úkol může vygenerovat položku. Chcete-li vygenerovat položku, musí mít element [Task](../msbuild/task-element-msbuild.md) podřízený element [Output](../msbuild/output-element-msbuild.md) `ItemName` , který má atribut.

- Úkol [CreateItem –](../msbuild/createitem-task.md) může vygenerovat položku. Tento způsob využití je zastaralý.

- Počínaje .NET Framework 3,5 `Target` prvky mohou obsahovat prvky [položky](../msbuild/itemgroup-element-msbuild.md) , které mohou obsahovat prvky položky.

## <a name="reference-items-in-a-project-file"></a>Referenční položky v souboru projektu
 Chcete-li odkazovat na typy položek v celém souboru projektu, použijte syntaxi @\<(ItemType >). Například byste odkazovali na typ položky v předchozím příkladu pomocí `@(Compile)`. Pomocí této syntaxe můžete předat položky úkolů zadáním typu položky jako parametru této úlohy. Další informace najdete v tématu [jak: Vyberte soubory, které chcete](../msbuild/how-to-select-the-files-to-build.md)sestavit.

 Ve výchozím nastavení jsou položky typu položky oddělené středníky (;) Když je rozbalený. Můžete použít syntaxi @ (\<ItemType >, '\<oddělovač > ') k určení oddělovače, který je jiný než výchozí. Další informace najdete v tématu [jak: Zobrazí seznam položek oddělený čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md).

## <a name="use-wildcards-to-specify-items"></a>Zadání položek pomocí zástupných znaků

Zástupné znaky `**`, `*`a `?` můžete použít k určení skupiny souborů jako vstupů pro sestavení místo výpisu každého souboru samostatně.

- `?` Zástupný znak odpovídá jednomu znaku.
- `*` Zástupný znak odpovídá žádnému nebo více znakům.
- Sekvence `**` zástupných znaků odpovídá částečné cestě.

Například můžete zadat všechny `.cs` soubory v adresáři, který obsahuje soubor projektu, pomocí následujícího elementu v souboru projektu.

```xml
<CSFile Include="*.cs"/>
```

Následující prvek vybere všechny `.vb` soubory `D:` na jednotce:

```xml
<VBFile Include="D:/**/*.vb"/>
```

Chcete-li zahrnout literály `*` nebo `?` znaky do položky bez rozšíření zástupných znaků, je nutné [řídicí znaky escape](../msbuild/how-to-escape-special-characters-in-msbuild.md).

Další informace o zástupných znacích naleznete [v tématu How to: Vyberte soubory, které chcete](../msbuild/how-to-select-the-files-to-build.md)sestavit.

## <a name="use-the-exclude-attribute"></a>Použití atributu Exclude
 Prvky položky mohou obsahovat `Exclude` atribut, který vylučuje konkrétní položky (soubory) z typu položky. `Exclude` Atribut se obvykle používá společně se zástupnými znaky. Například následující kód XML přidá každý soubor *. cs* v adresáři do typu položky CSFile s výjimkou souboru *DoNotBuild.cs* .

```xml
<ItemGroup>
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>
</ItemGroup>
```

 Atribut ovlivňuje pouze položky, které jsou přidány `Include` atributem v prvku Item, který je obsahuje obě. `Exclude` Následující příklad nevylučuje soubor *Form1.cs*, který byl přidán do předchozí položky elementu.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

 Další informace najdete v tématu [jak: Vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).

## <a name="item-metadata"></a>Metadata položky
 Kromě informací v `Include` atributech a `Exclude` můžou položky obsahovat i metadata. Tato metadata mohou být používána úkoly, které vyžadují další informace o položkách nebo úlohách a cílech Batch. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

 Metadata je kolekce párů klíč-hodnota, které jsou deklarovány v souboru projektu jako podřízené prvky elementu Item. Název podřízeného prvku je název metadat a hodnota podřízeného elementu je hodnota metadat.

 Metadata jsou přidružena k elementu Item, který jej obsahuje. Například následující `Culture` kód XML přidá metadata, která mají hodnotu `Fr` pro *One.cs* a *Two.cs* položky typu položky CSFile.

```xml
<ItemGroup>
    <CSFile Include="one.cs;two.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Položka může mít nula nebo více hodnot metadat. Hodnoty metadat můžete kdykoli změnit. Pokud nastavíte metadata na prázdnou hodnotu, můžete ji efektivně odebrat ze sestavení.

### <a name="BKMK_ReferencingItemMetadata"></a>Metadata položky reference v souboru projektu
 Metadata položky můžete odkazovat v celém souboru projektu pomocí syntaxe%(\<ItemMetaDataName >). Pokud existuje nejednoznačnost, můžete kvalifikovat odkaz pomocí názvu typu položky. Například můžete zadat%(\<ItemType. ItemMetaDataName >). Následující příklad používá metadata zobrazení k dávkování úlohy zprávy. Další informace o tom, jak používat metadata položek pro dávkování, najdete v tématu [Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).

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

### <a name="BKMK_WellKnownItemMetadata"></a>Dobře známá metadata položky
 Když je položka přidána do typu položky, je tato položka přiřazena dobře známým metadatům. Například všechny položky mají dobře známou%(\<název souboru metadat >), jehož hodnota je název souboru položky. Další informace najdete v tématu [známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md).

### <a name="BKMK_Transforming"></a>Transformace typů položek pomocí metadat
 Seznamy položek můžete transformovat do seznamů nové položky pomocí metadat. Například můžete převést `CppFiles` typ položky, který obsahuje položky, které reprezentují soubory *. cpp* , do odpovídajícího seznamu souborů *. obj* pomocí výrazu. `@(CppFiles -> '%(Filename).obj')`

 Následující kód vytvoří `CultureResource` typ položky, který obsahuje kopie všech `EmbeddedResource` položek s `Culture` metadaty. Hodnota metadata se zobrazí jako hodnota nových metadat `CultureResource.TargetDirectory`. `Culture`

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

 Další informace najdete v tématu [transformace](../msbuild/msbuild-transforms.md).

## <a name="item-definitions"></a>Definice položek
 Počínaje .NET Framework 3,5 můžete přidat výchozí metadata k libovolnému typu položky pomocí [elementu ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Podobně jako dobře známá metadata jsou výchozí metadata přidružena ke všem položkám typu položky, které zadáte. Výchozí metadata můžete explicitně přepsat v definici položky. Například následující `Compile` kód XML poskytuje položky *One.cs* a *Three.cs* metadata `BuildDay` s hodnotou "pondělí". Kód umožňuje, aby položka *Two.cs* metadata `BuildDay` s hodnotou "úterý".

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

 Další informace naleznete v tématu [Definice položek](../msbuild/item-definitions.md).

## <a name="attributes-for-items-in-an-itemgroup-of-a-target"></a>Atributy pro položky v instanci položky cíle
 Počínaje .NET Framework 3,5 `Target` prvky mohou obsahovat prvky [položky](../msbuild/itemgroup-element-msbuild.md) , které mohou obsahovat prvky položky. Atributy v této části jsou platné, pokud jsou zadány pro položku v objektu `ItemGroup` , který je `Target`v.

### <a name="BKMK_RemoveAttribute"></a>Odebrat atribut
 `Remove` Atribut odebere konkrétní položky (soubory) z typu položky. Tento atribut byl představen v .NET Framework 3,5 (pouze uvnitř cílů). V MSBuild 15,0 jsou podporovány jak uvnitř, tak mimo cíle.

 Následující příklad odebere každý soubor *. config* z typu položky kompilace.

```xml
<Target>
    <ItemGroup>
        <Compile Remove="*.config"/>
    </ItemGroup>
</Target>
```

### <a name="BKMK_KeepMetadata"></a>KeepMetadata – atribut
 Pokud je položka generována v rámci cíle, element Item může `KeepMetadata` atribut obsahovat. Pokud je tento atribut zadán, budou ze zdrojové položky do cílové položky přenesena pouze metadata, která jsou zadána v seznamu názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní s jeho zadáním. `KeepMetadata` Atribut byl představen v .NET Framework 4,5.

 Následující příklad ukazuje, jak použít `KeepMetadata` atribut.

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

### <a name="BKMK_RemoveMetadata"></a>RemoveMetadata – atribut
 Pokud je položka generována v rámci cíle, element Item může `RemoveMetadata` atribut obsahovat. Je-li tento atribut zadán, jsou všechna metadata přenesena ze zdrojové položky do cílové položky s výjimkou metadat, jejichž názvy jsou obsaženy v seznamu názvů oddělených středníkem. Prázdná hodnota pro tento atribut je ekvivalentní s jeho zadáním. `RemoveMetadata` Atribut byl představen v .NET Framework 4,5.

 Následující příklad ukazuje, jak použít `RemoveMetadata` atribut.

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

### <a name="BKMK_KeepDuplicates"></a>KeepDuplicates – atribut
 Pokud je položka generována v rámci cíle, element Item může `KeepDuplicates` atribut obsahovat. `KeepDuplicates``Boolean` je atribut, který určuje, zda má být položka přidána do cílové skupiny, pokud je položka přesným duplikátem existující položky.

 Pokud má zdrojová a cílová položka stejnou hodnotu zahrnutí, ale odlišná metadata, položka je přidána i v případě `KeepDuplicates` , že je `false`nastavena na. Prázdná hodnota pro tento atribut je ekvivalentní s jeho zadáním. `KeepDuplicates` Atribut byl představen v .NET Framework 4,5.

 Následující příklad ukazuje, jak použít `KeepDuplicates` atribut.

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

## <a name="see-also"></a>Viz také:
- [Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Společné položky projektu nástroje MSBuild](../msbuild/common-msbuild-project-items.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Postupy: Vyberte soubory, které chcete sestavit.](../msbuild/how-to-select-the-files-to-build.md)
- [Postupy: Vyloučit soubory ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md)
- [Postupy: Zobrazit seznam položek oddělený čárkami](../msbuild/how-to-display-an-item-list-separated-with-commas.md)
- [Definice položek](../msbuild/item-definitions.md)
- [Dávkování](../msbuild/msbuild-batching.md)
