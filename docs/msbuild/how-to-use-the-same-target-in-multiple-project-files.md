---
title: 'Postup: Použití stejného cíle ve více souborech projektu | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633756"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Postup: Použití stejného cíle ve více souborech projektu

Pokud jste vytvořili několik souborů projektu MSBuild, pravděpodobně jste zjistili, že je třeba použít stejné úkoly a cíle v různých souborech projektu. Místo zahrnutí úplného popisu těchto úkolů nebo cílů do každého souboru projektu můžete uložit cíl do samostatného souboru projektu a potom importovat tento projekt do jiného projektu, který potřebuje cíl použít.
## <a name="use-the-import-element"></a>Použití prvku Import

 Prvek `Import` se používá k vložení jednoho souboru projektu do jiného souboru projektu. Importovaný soubor projektu musí být platný soubor projektu MSBuild a musí obsahovat dobře formátovaný kód XML. Atribut `Project` určuje cestu k importovanému souboru projektu. Další informace o `Import` prvku naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md).
Prvek `Import` se používá k vložení jednoho souboru projektu do jiného souboru projektu. Importovaný soubor projektu musí být platný soubor projektu MSBuild a musí obsahovat dobře formátovaný kód XML. Atribut `Project` určuje cestu k importovanému souboru projektu. Další informace o `Import` prvku naleznete v tématu [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Import projektu

1. Definujte v importujícím souboru projektu všechny vlastnosti a položky, které se používají jako parametry pro vlastnosti a položky v importovaném projektu.

2. Pomocí `Import` prvku importujte projekt. Například:

     `<Import Project="MyCommon.targets"/>`

3. Po `Import` elementu definujte všechny vlastnosti a položky, které musí přepsat výchozí definice vlastností a položek v importovaném projektu.

## <a name="order-of-evaluation"></a>Pořadí vyhodnocení

 Když MSBuild dosáhne `Import` prvku, importovaný projekt je efektivně vložen do importu projektu `Import` v umístění prvku. Proto umístění `Import` prvku může ovlivnit hodnoty vlastností a položek. Je důležité porozumět vlastnostem a položkám, které jsou nastaveny importovaným projektem, a vlastnostem a položkám, které importovaný projekt používá.

 Při sestavení projektu jsou nejprve vyhodnoceny všechny vlastnosti následované položkami. Například následující xml definuje importovaný soubor projektu *MyCommon.targets*:

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

 Následující kód XML definuje *soubor MyApp.proj*, který importuje *soubor MyCommon.targets*:

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

 Vzhledem k tomu, že `Name` projekt je importován poté, co `Name` byla vlastnost definována v *souboru MyApp.proj*, definice v *souboru MyCommon.targets* přepíše definici v *souboru MyApp.proj*. Pokud je projekt importován před definovanou vlastností Název, sestavení zobrazí následující zprávu:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Při importu projektů použijte následující postup

1. Definujte v souboru projektu všechny vlastnosti a položky, které se používají jako parametry pro vlastnosti a položky v importovaném projektu.

2. Importujte projekt.

3. Definujte v souboru projektu všechny vlastnosti a položky, které musí přepsat výchozí definice vlastností a položek v importovaném projektu.

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje soubor *MyCommon.targets,* který importuje druhý příklad kódu. Soubor *.targets* vyhodnocuje vlastnosti z projektu importu ke konfiguraci sestavení.

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

 Následující příklad kódu importuje soubor *MyCommon.targets.*

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

- [Prvek importu (MSBuild)](../msbuild/import-element-msbuild.md)
- [Cíle](../msbuild/msbuild-targets.md)
