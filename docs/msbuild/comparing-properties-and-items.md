---
title: Porovnání vlastností a položek | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634406"
---
# <a name="compare-properties-and-items"></a>Porovnání vlastností a položek

Vlastnosti a položky MSBuild se používají k předání informací úkolům, vyhodnocení podmínek a ukládání hodnot, na které lze odkazovat v celém souboru projektu.

- Vlastnosti jsou dvojice název-hodnota. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

- Položky jsou objekty, které obvykle představují soubory. Objekty položek mohou mít přidružené kolekce metadat. Metadata jsou dvojice název-hodnota. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Skalára a vektory

Vzhledem k tomu, že msbuild vlastnosti jsou dvojice název hodnota, které mají pouze jednu hodnotu řetězce, jsou často popisovány jako *skalární*. Vzhledem k tomu, že typy položek MSBuild jsou seznamy položek, jsou často popisovány jako *vektor*. V praxi však vlastnosti mohou představovat více hodnot a typy položek mohou mít nulu nebo jednu položku.

### <a name="target-dependency-injection"></a>Cílová injekce závislostí

Chcete-li zjistit, jak vlastnosti mohou představovat více hodnot, zvažte běžný vzor použití pro přidání cíle do seznamu cílů, které mají být vytvořeny. Tento seznam je obvykle reprezentován hodnotou vlastnosti, přičemž cílové názvy jsou odděleny středníky.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Vlastnost `BuildDependsOn` se obvykle používá jako argument `DependsOnTargets` cílového atributu, který efektivně převádí na seznam položek. Tato vlastnost může být přepsána přidat cíl nebo změnit cíl pořadí provádění. Například:

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

přidá cíl CustomBuild do cílového `BuildDependsOn` seznamu `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`a uvede hodnotu .

Počínaje MSBuild 4.0, cíl vkládání závislostí je zastaralé. Místo `AfterTargets` toho `BeforeTargets` použijte atributy a. Další informace naleznete v [tématu Target build order](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Převody mezi řetězci a seznamy položek

MSBuild provádí převody do a z typů položek a řetězcové hodnoty podle potřeby. Chcete-li zjistit, jak se může seznam položek stát hodnotou řetězce, zvažte, co se stane, když se jako hodnota vlastnosti MSBuild použije typ položky:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Typ položky OutputDir `Include` má atribut s\\hodnotou "KeyFiles ; Certifikáty\\". MSBuild analyzuje tento řetězec do dvou položek: KeyFiles\ a Certifikáty\\. Pokud je jako hodnota vlastnosti OutputDirList použit typ položky OutputDir, MSBuild převede nebo "sloučí" typ\\položky na řetězec oddělený středníkem "KeyFiles ; Certifikáty\\".

## <a name="properties-and-items-in-tasks"></a>Vlastnosti a položky v úkolech

Vlastnosti a položky se používají jako vstupy a výstupy úloh MSBuild. Další informace naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

Vlastnosti jsou předávány úkolům jako atributy. V rámci úlohy msbuild vlastnost je reprezentována typ vlastnosti, jehož hodnotu lze převést do a z řetězce. Podporované typy vlastností `char` `DateTime`zahrnují `Decimal` `bool` `Double`, , , `int`, , `string`, a jakýkoli typ, který <xref:System.Convert.ChangeType%2A> může zpracovat.

Položky jsou předávány úkolům jako <xref:Microsoft.Build.Framework.ITaskItem> objekty. V rámci <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> úkolu představuje hodnotu <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> položky a načte její metadata.

Seznam položek typu položky lze předat jako `ITaskItem` pole objektů. Počínaje rozhraním .NET Framework 3.5 lze položky odebrat ze `Remove` seznamu položek v cíli pomocí atributu. Vzhledem k tomu, že položky mohou být odebrány ze seznamu položek, je možné, že typ položky má nulové položky. Pokud je seznam položek předán úkolu, kód v úloze by měl tuto možnost zkontrolovat.

## <a name="property-and-item-evaluation-order"></a>Pořadí hodnocení vlastností a položek

Během fáze vyhodnocení sestavení importované soubory jsou začleněny do sestavení v pořadí, ve kterém se zobrazí. Vlastnosti a položky jsou definovány ve třech průchodech v následujícím pořadí:

- Vlastnosti jsou definovány a upraveny v pořadí, ve kterém se zobrazí.

- Definice položek jsou definovány a změněny v pořadí, ve kterém se zobrazují.

- Položky jsou definovány a upraveny v pořadí, ve kterém se zobrazují.

Během fáze provádění sestavení jsou vlastnosti a položky, které jsou definovány v rámci cílů, vyhodnocovány společně v jedné fázi v pořadí, ve kterém se zobrazují.

Nicméně, toto není celý příběh. Když je definována vlastnost, definice položky nebo položka, je vyhodnocena její hodnota. Vyhodnocení výrazu rozbalí řetězec, který určuje hodnotu. Rozšíření řetězce je závislé na fázi sestavení. Zde je podrobnější vlastnost a pořadí hodnocení položek:

- Během fáze hodnocení sestavení:

  - Vlastnosti jsou definovány a upraveny v pořadí, ve kterém se zobrazí. Funkce vlastností jsou prováděny. Hodnoty vlastností ve formuláři $(PropertyName) jsou rozbaleny v rámci výrazů. Hodnota vlastnosti je nastavena na rozbalený výraz.

  - Definice položek jsou definovány a změněny v pořadí, ve kterém se zobrazují. Funkce vlastností již byly rozbaleny v rámci výrazů. Hodnoty metadat jsou nastaveny na rozbalené výrazy.

  - Typy položek jsou definovány a upraveny v pořadí, ve kterém se zobrazí. Hodnoty položek ve formuláři @(ItemType) jsou rozbaleny. Transformace položek jsou také rozbaleny. Funkce a hodnoty vlastností již byly rozbaleny v rámci výrazů. Hodnoty seznamu položek a metadat jsou nastaveny na rozbalené výrazy.

- Během fáze provádění sestavení:

  - Vlastnosti a položky, které jsou definovány v rámci cílů, jsou vyhodnocovány společně v pořadí, ve kterém se zobrazují. Funkce vlastností jsou spouštěny a hodnoty vlastností jsou rozbaleny v rámci výrazů. Hodnoty položek a transformace položek jsou také rozbaleny. Hodnoty vlastností, hodnoty typu položky a hodnoty metadat jsou nastaveny na rozbalené výrazy.

### <a name="subtle-effects-of-the-evaluation-order"></a>Jemné efekty pořadí hodnocení

Ve fázi hodnocení sestavení hodnocení vlastností předchází hodnocení položky. Vlastnosti však mohou mít hodnoty, které se zdají záviset na hodnotách položek. Zvažte následující skript.

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

Spuštění úlohy Zpráva zobrazí tuto zprávu:

```
KeyFileVersion: 1.0.0.3
```

Důvodem `KeyFileVersion` je, že hodnota je\@vlastně řetězec " (KeyFile->'%(Version)')". Transformace položek a položek nebyly rozbaleny při první `KeyFileVersion` definici vlastnosti, takže vlastnosti byla přiřazena hodnota nerozbaleného řetězce.

Během fáze provádění sestavení, když zpracovává message úlohu, MSBuild\@rozbalí řetězec " (KeyFile->'%(Version)')" výnos "1.0.0.3".

Všimněte si, že stejná zpráva se zobrazí i v případě, že vlastnost a skupiny položek byly stornovány v pořadí.

Jako druhý příklad zvažte, co se může stát, když jsou skupiny vlastností a položek umístěny v rámci cílů:

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

Úloha Zpráva zobrazí tuto zprávu:

```
KeyFileVersion:
```

Důvodem je, že během fáze provádění sestavení, vlastnosti a položky skupiny definované v rámci cíle jsou vyhodnocovány shora dolů ve stejnou dobu. Kdy `KeyFileVersion` je `KeyFile` definován, je neznámý. Proto transformace položky rozbalí na prázdný řetězec.

V tomto případě stornování pořadí skupin vlastností a položek obnoví původní zprávu:

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

Hodnota `KeyFileVersion` je nastavena na "1.0.0.3"\@a ne na " (KeyFile->'%(Version)')". Úloha Zpráva zobrazí tuto zprávu:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Viz také

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
