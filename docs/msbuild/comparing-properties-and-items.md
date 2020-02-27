---
title: Porovnávání vlastností a položek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a86365ffe839b45fcd09862040fb88f0d4148bc
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634406"
---
# <a name="compare-properties-and-items"></a>Porovnat vlastnosti a položky

Vlastnosti a položky nástroje MSBuild se používají k předávání informací úkolům, vyhodnocení podmínek a ukládání hodnot, na které lze odkazovat v rámci souboru projektu.

- Vlastnosti jsou páry název-hodnota. Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

- Položky jsou objekty, které obvykle představují soubory. K objektům položky mohou být přidruženy kolekce metadat. Metadata jsou páry název-hodnota. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Skalární a vektory

Vzhledem k tomu, že vlastnosti MSBuild jsou páry název-hodnota, které mají pouze jednu řetězcovou hodnotu, jsou často popsány jako *skalární*. Vzhledem k tomu, že typy položek MSBuild jsou seznamy položek, jsou často popsány jako *vektor*. V praxi však vlastnosti mohou představovat více hodnot a typy položek mohou mít 0 nebo jednu položku.

### <a name="target-dependency-injection"></a>Vkládání závislostí cíle

Chcete-li zjistit, jak vlastnosti mohou představovat více hodnot, zvažte společný vzor použití pro přidání cíle do seznamu cílů, které mají být sestaveny. Tento seznam je obvykle reprezentován hodnotou vlastnosti s cílovými názvy oddělenými středníky.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Vlastnost `BuildDependsOn` se obvykle používá jako argument cílového atributu `DependsOnTargets` a efektivně ho převádí na seznam položek. Tato vlastnost může být přepsána, pokud chcete přidat cíl nebo změnit pořadí spuštění cíle. Například:

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

Přidá cíl CustomBuild do cílového seznamu a uvede `BuildDependsOn` hodnotu `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.

Počínaje nástrojem MSBuild 4,0 je vkládání závislostí cíle zastaralé. Místo toho použijte atributy `AfterTargets` a `BeforeTargets`. Další informace najdete v tématu [cílové pořadí sestavení](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Převody mezi řetězci a seznamy položek

Nástroj MSBuild provádí převody na typy položek a hodnoty řetězců podle potřeby a z nich. Chcete-li zjistit, jakým způsobem se může seznam položek stát hodnotou řetězce, zvažte, co se stane, když je typ položky použit jako hodnota vlastnosti MSBuild:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Typ položky OutputDir má atribut `Include` s hodnotou "\\soubory"; Certifikáty\\". Nástroj MSBuild analyzuje tento řetězec do dvou položek: souborů a certifikátů\\. Když typ položky OutputDir slouží jako hodnota vlastnosti OutputDirList, nástroj MSBuild převede nebo "sloučí" typ položky do řetězcových souborů s oddělovači středníkem\\; Certifikáty\\".

## <a name="properties-and-items-in-tasks"></a>Vlastnosti a položky v úlohách

Vlastnosti a položky se používají jako vstupy a výstupy pro úlohy MSBuild. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

Vlastnosti jsou předány do úkolů jako atributy. V rámci úlohy je vlastnost MSBuild reprezentovaná typem vlastnosti, jejíž hodnota může být převedena na a z řetězce. Mezi podporované typy vlastností patří `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`a jakýkoli typ, který <xref:System.Convert.ChangeType%2A> může zpracovat.

Položky jsou předány úlohám jako <xref:Microsoft.Build.Framework.ITaskItem> objekty. V rámci úkolu <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> představuje hodnotu položky a <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> načte svá metadata.

Seznam položek typu položky lze předat jako pole objektů `ITaskItem`. Počínaje .NET Framework 3,5 lze položky odebrat ze seznamu položek v cíli pomocí atributu `Remove`. Protože položky lze odebrat ze seznamu položek, je možné, že typ položky má nulové položky. Pokud je seznam položek předán úkolu, kód v úloze by měl tuto možnost kontrolovat.

## <a name="property-and-item-evaluation-order"></a>Pořadí vyhodnocení vlastností a položek

Během zkušební fáze sestavení jsou importované soubory začleněny do sestavení v pořadí, ve kterém se zobrazí. Vlastnosti a položky jsou definovány ve třech průchodech v následujícím pořadí:

- Vlastnosti jsou definovány a upraveny v pořadí, ve kterém jsou zobrazeny.

- Definice položek jsou definovány a upraveny v pořadí, ve kterém jsou zobrazeny.

- Položky jsou definovány a upraveny v pořadí, ve kterém jsou zobrazeny.

Během fáze provádění sestavení se vlastnosti a položky, které jsou definovány v rámci cílů, vyhodnocují společně v jedné fázi v pořadí, ve kterém jsou uvedeny.

Nejedná se však o úplný příběh. Je-li definována vlastnost, definice položky nebo položka, je vyhodnocena její hodnota. Vyhodnocovací filtr výrazů rozbalí řetězec, který určuje hodnotu. Rozšíření řetězce je závislé na fázi sestavení. Tady je podrobnější pořadí vyhodnocení vlastností a položek:

- Během zkušební fáze sestavení:

  - Vlastnosti jsou definovány a upraveny v pořadí, ve kterém jsou zobrazeny. Funkce vlastností jsou spuštěny. Hodnoty vlastností ve formě $ (PropertyName) jsou v rámci výrazů rozbaleny. Hodnota vlastnosti je nastavena na rozbalený výraz.

  - Definice položek jsou definovány a upraveny v pořadí, ve kterém jsou zobrazeny. Funkce vlastností již byly v rámci výrazů rozbaleny. Hodnoty metadat jsou nastaveny na rozbalené výrazy.

  - Typy položek jsou definovány a upraveny v pořadí, ve kterém jsou zobrazeny. Hodnoty položek ve formuláři @ (ItemType) jsou rozbaleny. Transformace položek jsou také rozbaleny. Funkce vlastností a hodnoty již byly rozšířeny v rámci výrazů. Hodnoty v seznamu položek a metadatech jsou nastaveny na rozbalené výrazy.

- Během fáze provádění sestavení:

  - Vlastnosti a položky, které jsou definovány v rámci cílů, jsou vyhodnocovány v pořadí, ve kterém jsou zobrazeny. Funkce vlastností jsou spouštěny a hodnoty vlastností jsou v rámci výrazů rozbaleny. Také se rozbalí hodnoty položek a transformace položek. Hodnoty vlastností, hodnoty typu položky a hodnoty metadat jsou nastaveny na rozbalené výrazy.

### <a name="subtle-effects-of-the-evaluation-order"></a>Malé efekty pořadí vyhodnocování

Ve fázi vyhodnocení sestavení předchází vyhodnocení vlastnosti před vyhodnocením položky. Vlastnosti však mohou mít hodnoty, které jsou závislé na hodnotách položek. Vezměte v úvahu následující skript.

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Spuštění úlohy zprávy zobrazí tuto zprávu:

```
KeyFileVersion: 1.0.0.3
```

Důvodem je skutečnost, že hodnota `KeyFileVersion` je řetězec "\@(KeyFile->"% (verze) ")". Transformace položek a položek nebyly při prvním definování vlastnosti rozbaleny, takže vlastnost `KeyFileVersion` byla přiřazena k hodnotě nerozbaleného řetězce.

Během fáze provádění sestavení při zpracovávání úlohy nástroj MSBuild rozbalí řetězec "\@(KeyFile-> '% (verze) ')", aby vydával "1.0.0.3".

Všimněte si, že stejná zpráva by se zobrazila i v případě, že skupiny vlastností a položek byly vráceny v daném pořadí.

V druhém příkladu zvažte, co se může stát, když se skupiny vlastností a položek nacházejí v rámci cílů:

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Tato zpráva se zobrazí v úloze zprávy:

```
KeyFileVersion:
```

Důvodem je, že během fáze provádění sestavení, vlastností a skupin položek definovaných v rámci cílů jsou vyhodnocovány shora dolů ve stejnou dobu. Je-li definována `KeyFileVersion`, `KeyFile` je neznámá. Proto se transformace položky rozbalí do prázdného řetězce.

V tomto případě převrácení pořadí vlastností a skupin položek obnoví původní zprávu:

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Hodnota `KeyFileVersion` je nastavená na "1.0.0.3", a ne na "\@(KeyFile->% (verze)"). Tato zpráva se zobrazí v úloze zprávy:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Viz také

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
