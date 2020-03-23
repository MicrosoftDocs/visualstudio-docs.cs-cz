---
title: Přepsání nástrojeNastavení verze | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 13c33f0ef43707390aa32d4c26c0380a8a32883e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633015"
---
# <a name="override-toolsversion-settings"></a>Přepsat nastavení ToolsVersion

Sadu nástrojů pro projekty a řešení můžete změnit jedním ze tří způsobů:

1. Pomocí přepínače `-ToolsVersion` (nebo `-tv`, zkráceně) při vytváření projektu nebo řešení z příkazového řádku.

2. Nastavením `ToolsVersion` parametru na úlohě MSBuild.

3. Nastavením `$(ProjectToolsVersion)` vlastnosti na projektu v rámci řešení. To umožňuje vytvořit projekt v řešení s verzí sady nástrojů, která se liší od ostatních projektů.

## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Přepsat nastavení ToolsVersion projektů a řešení na sestavení příkazového řádku

 Přestože projekty sady Visual Studio obvykle sestavení s ToolsVersion `-ToolsVersion` zadané `-tv`v souboru projektu, můžete použít přepínač (nebo ) na příkazovém řádku přepsat tuto hodnotu a sestavit všechny projekty a jejich závislosti projektu na projekt s jinou sadou nástrojů. Například:

```cmd
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug
```

 V tomto příkladu jsou všechny projekty sestaveny pomocí ToolsVersion 12.0. (V tomto tématu však naleznete v části [Pořadí priorit](#order-of-precedence) dále.)

 Při použití `-tv` přepínače na příkazovém řádku, `$(ProjectToolsVersion)` můžete volitelně použít vlastnost v jednotlivých projektech k jejich sestavení s jinou ToolsVersion hodnotu než ostatní projekty v řešení.

## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Přepsat nastavení ToolsVersion pomocí toolsversion parametr úlohy MSBuild

 Úkol MSBuild je primární mašita pro jeden projekt k sestavení jiného projektu. Chcete-li povolit úkol MSBuild k sestavení projektu s jinou ToolsVersion než zadaný `ToolsVersion`v projektu, poskytuje volitelný parametr úkolu s názvem . Následující příklad ukazuje, jak použít tento parametr:

1. Vytvořte soubor s názvem *projectA.proj,* který obsahuje následující kód:

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

2. Vytvořte jiný soubor s názvem *projectB.proj* a který obsahuje následující kód:

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

3. Na příkazovém řádku zadejte následující příkaz:

    ```cmd
    msbuild projectA.proj -t:go -toolsversion:3.5
    ```

4. Zobrazí se následující výstup. V `projectA`případě `-toolsversion:3.5` , nastavení na příkazovém řádku přepíše `ToolsVersion=12.0` nastavení ve značce. `Project`

     `ProjectB`je volána úkolem v aplikaci `projectA`. Tento úkol `ToolsVersion=2.0`má , který `ToolsVersion` přepíše ostatní nastavení pro `projectB`.

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

 Pořadí priorit, od nejvyšší k nejnižší, slouží `ToolsVersion` k určení je:

1. Atribut `ToolsVersion` úkolu MSBuild, který se používá k sestavení projektu, pokud existuje.

2. Přepínač `-toolsversion` (nebo), `-tv`který se používá v příkazu msbuild.exe, pokud existuje.

3. Pokud je `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` nastavena proměnná prostředí, použijte aktuální `ToolsVersion`.

4. Pokud je `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` nastavena proměnná prostředí a `ToolsVersion` definice v `ToolsVersion`souboru projektu `ToolsVersion`je větší než aktuální , použijte aktuální .

5. Pokud je `MSBUILDLEGACYDEFAULTTOOLSVERSION` nastavena proměnná `ToolsVersion` prostředí nebo není nastavena, použijí se následující kroky:

    1. Atribut `ToolsVersion` [Project](../msbuild/project-element-msbuild.md) prvek souboru projektu. Pokud tento atribut neexistuje, předpokládá se, že se jedná o aktuální verzi.

    2. Výchozí verze nástrojů v souboru *MSBuild.exe.config.*

    3. Výchozí verze nástrojů v registru. Další informace naleznete [v tématu Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md).

6. Pokud proměnná `MSBUILDLEGACYDEFAULTTOOLSVERSION` prostředí není nastavena, použijí se následující kroky:

    1. Pokud je `MSBUILDDEFAULTTOOLSVERSION` proměnná prostředí `ToolsVersion` nastavena na existující, použijte ji.

    2. Pokud `DefaultOverrideToolsVersion` je nastavena v *MSBuild.exe.config*, použijte ji.

    3. Pokud `DefaultOverrideToolsVersion` je nastavena v registru, použijte ji.

    4. V opačném případě `ToolsVersion`použijte aktuální .

## <a name="see-also"></a>Viz také

- [Multicílení](../msbuild/msbuild-multitargeting-overview.md)
- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
- [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)
