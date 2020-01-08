---
title: Přepsání nastavení ToolsVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1706d0e82139da5962fbb43610cdecd6b1477ad1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590485"
---
# <a name="override-toolsversion-settings"></a>Přepsat nastavení ToolsVersion
Sadu nástrojů pro projekty a řešení můžete změnit jedním ze tří způsobů:

1. Při sestavování projektu nebo řešení z příkazového řádku pomocí přepínače `-ToolsVersion` (při krátkém `-tv`).

2. Nastavením parametru `ToolsVersion` v úloze MSBuild.

3. Nastavením vlastnosti `$(ProjectToolsVersion)` v projektu v rámci řešení. To umožňuje sestavit projekt v řešení s verzí sady nástrojů, která se liší od pro ostatní projekty.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Přepsat nastavení ToolsVersion projektů a řešení v sestaveních příkazového řádku
 I když projekty sady Visual Studio obvykle sestavují s ToolsVersion, které jsou zadány v souboru projektu, můžete použít přepínač `-ToolsVersion` (nebo `-tv`) na příkazovém řádku pro přepsání této hodnoty a sestavení všech projektů a jejich závislostí typu projekt-projekt s jinou sadou nástrojů. Příklad:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 V tomto příkladu jsou všechny projekty sestaveny pomocí ToolsVersion 12,0. (Ale další informace najdete v části [pořadí priorit](#order-of-precedence) dále v tomto tématu.)

 Při použití přepínače `-tv` v příkazovém řádku můžete volitelně použít vlastnost `$(ProjectToolsVersion)` v jednotlivých projektech pro jejich sestavení s jinou hodnotou ToolsVersion než ostatní projekty v řešení.

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Přepsat nastavení ToolsVersion pomocí parametru ToolsVersion úlohy MSBuild
 Úloha MSBuild je primárním prostředkem pro jeden projekt k sestavení jiného. Chcete-li povolit úlohu MSBuild pro sestavení projektu s jiným ToolsVersion, než je zadáno v projektu, poskytuje volitelný parametr úlohy s názvem `ToolsVersion`. Následující příklad ukazuje, jak použít tento parametr:

1. Vytvořte soubor s názvem *Project. proj* , který obsahuje následující kód:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go" >
            <Message Text="projectA.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />

            <MSBuild Projects="projectB.proj"
                ToolsVersion="2.0"
                Targets="go" />
        </Target>
    </Project>
    ```

2. Vytvořte další soubor s názvem *projectB. proj* , který obsahuje následující kód:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    ToolsVersion="12.0">

        <Target Name="go">
            <Message Text="projectB.proj" />
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />
        </Target>
    </Project>
    ```

3. Do příkazového řádku zadejte následující příkaz:

    ```cmd
    msbuild projectA.proj -t:go -toolsversion:3.5
    ```

4. Zobrazí se následující výstup. Pro `projectA`nastavení `-toolsversion:3.5` na příkazovém řádku přepisuje nastavení `ToolsVersion=12.0` ve značce `Project`.

     `ProjectB` je volána úlohou v `projectA`. Tato úloha má `ToolsVersion=2.0`, která přepíše ostatní nastavení `ToolsVersion` pro `projectB`.

    ```
    Output:
      projectA.proj
      MSBuildToolsVersion: 3.5
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5

      projectB.proj
      MSBuildToolsVersion: 2.0
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727
    ```

## <a name="order-of-precedence"></a>Pořadí priorit
 Pořadí priorit od nejvyšších po nejnižší, které slouží k určení `ToolsVersion`:

1. Atribut `ToolsVersion` v úloze MSBuild, který se používá k sestavení projektu, pokud existuje.

2. Přepínač `-toolsversion` (nebo `-tv`), který je použit v příkazu MSBuild. exe, pokud existuje.

3. Pokud je nastavená proměnná prostředí `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`, použijte aktuální `ToolsVersion`.

4. Pokud je proměnná prostředí `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` nastavena a `ToolsVersion` definována v souboru projektu je větší než aktuální `ToolsVersion`, použijte aktuální `ToolsVersion`.

5. Pokud je nastavená proměnná prostředí `MSBUILDLEGACYDEFAULTTOOLSVERSION` nebo pokud `ToolsVersion` není nastavená, použijí se tyto kroky:

    1. Atribut `ToolsVersion` prvku [projektu](../msbuild/project-element-msbuild.md) v souboru projektu. Pokud tento atribut neexistuje, předpokládá se, že se jedná o aktuální verzi.

    2. Výchozí verze nástrojů v souboru *MSBuild. exe. config* .

    3. Výchozí verze nástrojů v registru. Další informace najdete v tématu [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md).

6. Pokud není nastavená proměnná prostředí `MSBUILDLEGACYDEFAULTTOOLSVERSION`, použijí se tyto kroky:

    1. Pokud je proměnná prostředí `MSBUILDDEFAULTTOOLSVERSION` nastavená na `ToolsVersion`, která existuje, použijte ji.

    2. Pokud je v *souboru MSBuild. exe. config*nastavena `DefaultOverrideToolsVersion`, použijte ji.

    3. Pokud je v registru nastavená `DefaultOverrideToolsVersion`, použijte ji.

    4. V opačném případě použijte aktuální `ToolsVersion`.

## <a name="see-also"></a>Viz také:
- [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)
