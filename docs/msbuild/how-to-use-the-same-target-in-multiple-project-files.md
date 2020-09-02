---
title: 'Postupy: použití stejného cíle ve více souborech projektu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bc8f3c95c687244162cb3bd977ca40031cd8f39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82255570"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Postupy: použití stejného cíle ve více souborech projektu

Pokud jste vytvořili několik souborů projektu MSBuild, možná jste zjistili, že je nutné použít stejné úlohy a cíle v různých souborech projektu. Místo zahrnutí úplný popis těchto úkolů nebo cílů do každého souboru projektu můžete uložit cíl do samostatného souboru projektu a pak tento projekt importovat do jakéhokoli jiného projektu, který potřebuje použít cíl.

## <a name="use-the-import-element"></a>Použití elementu import

`Import`Element se používá k vložení jednoho souboru projektu do jiného souboru projektu. Soubor projektu, který se má importovat, musí být platný soubor projektu MSBuild a obsahovat kód XML ve správném formátu. `Project`Atribut určuje cestu k importovanému souboru projektu. Další informace o elementu naleznete `Import` v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Import projektu

1. Definujte v importovaném souboru projektu všechny vlastnosti a položky, které jsou používány jako parametry pro vlastnosti a položky v importovaném projektu.

2. Použijte `Import` prvek pro import projektu. Příklad:

     `<Import Project="MyCommon.targets"/>`

3. Po `Import` elementu definujte všechny vlastnosti a položky, které musí přepsat výchozí definice vlastností a položek v importovaném projektu.

## <a name="order-of-evaluation"></a>Pořadí vyhodnocení

 Když nástroj MSBuild dosáhne `Import` prvku, importovaný projekt je efektivně vložen do importu projektu v umístění `Import` elementu. Proto umístění `Import` elementu může ovlivnit hodnoty vlastností a položek. Je důležité porozumět vlastnostem a položkám, které jsou nastaveny v importovaném projektu, a vlastnosti a položky, které používá importovaný projekt.

 Při sestavení projektu všechny vlastnosti jsou vyhodnoceny jako první, následované položkami. Například následující kód XML definuje importovaný soubor projektu *MyCommon. targets*:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Následující kód XML definuje *MyApp. proj*, který importuje *MyCommon. targets*:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Při sestavení projektu se zobrazí následující zpráva:

 `Name="MyCommon"`

 Vzhledem k tomu, že projekt je importován poté, co byla vlastnost `Name` definována v *MyApp. proj*, definice `Name` v *MyCommon. targets* přepíše definici v *MyApp. proj*. Pokud je projekt importován před definováním názvu vlastnosti, sestavení zobrazí následující zprávu:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Při importu projektů použijte následující postup.

1. V souboru projektu definujte všechny vlastnosti a položky, které jsou používány jako parametry pro vlastnosti a položky v importovaném projektu.

2. Importujte projekt.

3. V souboru projektu definujte všechny vlastnosti a položky, které musí přepsat výchozí definice vlastností a položek v importovaném projektu.

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje soubor *MyCommon. targets* , který naimportuje druhý příklad kódu. Soubor *. targets* vyhodnocuje vlastnosti z importu projektu pro konfiguraci sestavení.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>Příklad

 Následující příklad kódu importuje soubor *MyCommon. targets* .

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Viz také

- [Import – element (MSBuild)](../msbuild/import-element-msbuild.md)
- [Targets](../msbuild/msbuild-targets.md)
