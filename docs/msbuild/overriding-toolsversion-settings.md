---
title: Přepsání nastavení parametru ToolsVersion | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f0abe9db7178678c4ffda7f4179117817b3add6
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879297"
---
# <a name="override-toolsversion-settings"></a>Přepsání nastavení parametru ToolsVersion
Můžete změnit sadu nástrojů pro projekty a řešení jedním ze tří způsobů:  
  
1.  S použitím `-ToolsVersion` přepnout (nebo `-tv`, zkráceně) při sestavení projektu nebo řešení z příkazového řádku.  
  
2.  Tím, že nastavíte `ToolsVersion` parametr úlohy MSBuild.  
  
3.  Tím, že nastavíte `$(ProjectToolsVersion)` vlastnosti na projektu v rámci řešení. To umožňuje sestavení projektu v řešení s verzí sady nástrojů, které se liší od ostatních projektů.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Přepsání nastavení ToolsVersion v projektech a řešeních při sestavení na příkazovém řádku  
 Ačkoli projekty aplikace Visual Studio obvykle sestavení pomocí parametru ToolsVersion zadané v souboru projektu, můžete použít `-ToolsVersion` (nebo `-tv`) přepněte na příkazovém řádku k přepsání této hodnoty a sestavení všech projektů a jejich typu projekt projekt závislosti s různými sadami nástrojů. Příklad:  
  
```cmd  
msbuild.exe someproj.proj -tv:12.0 -p:Configuration=Debug  
```  
  
 V tomto příkladu jsou všechny projekty sestaveny pomocí ToolsVersion 12.0. (Ale najdete v části [pořadí priorit](#order-of-precedence) dále v tomto tématu.)  
  
 Při použití `-tv` přepnout na příkazovém řádku, můžete volitelně použít `$(ProjectToolsVersion)` vlastnost v jednotlivých projektech k sestavení s jinou hodnotou ToolsVersion než ostatní projekty v řešení.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Přepsání nastavení ToolsVersion pomocí parametru ToolsVersion úlohy nástroje MSBuild  
 Úloha MSBuild představuje primární prostředek jednoho projektu pro sestavení dalšího. Zapnutí úlohy nástroje MSBuild k sestavení projektu s jinými ToolsVersion, než verze zadaná v projektu, poskytuje volitelný parametr úlohy s názvem `ToolsVersion`. Následující příklad ukazuje, jak tento parametr použijte:  
  
1.  Vytvořte soubor s názvem *projectA.proj* , který obsahuje následující kód:  
  
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
  
2.  Vytvořte jiný soubor, který je pojmenován *projectB.proj* , který obsahuje následující kód:  
  
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
  
3.  Zadejte následující příkaz z příkazového řádku:  
  
    ```cmd  
    msbuild projectA.proj -t:go -toolsversion:3.5  
    ```  
  
4.  Zobrazí se následující výstup. Pro `projectA`, `-toolsversion:3.5` přepíše nastavení na příkazovém řádku `ToolsVersion=12.0` nastavení `Project` značky.  
  
     `ProjectB` je volán úlohou v `projectA`. Tento úkol byl `ToolsVersion=2.0`, který přepíše další `ToolsVersion` nastavení `projectB`.  
  
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
 Pořadí priorit od nejvyšší po nejnižší, umožňuje určit, `ToolsVersion` je:  
  
1.  `ToolsVersion` Atribut úlohy MSBuild použité k sestavení projektu, pokud existuje.  
  
2.  `-toolsversion` (Nebo `-tv`) přepínač, který se používá v příkazu msbuild.exe, pokud existuje.  
  
3.  Pokud proměnná prostředí `MSBUILDTREATALLTOOLSVERSIONSASCURRENT` je nastavena, pak použijte aktuální `ToolsVersion`.  
  
4.  Pokud proměnná prostředí `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` nastavena a `ToolsVersion` definované v projektu soubor je větší než aktuální `ToolsVersion`, použijte aktuální `ToolsVersion`.  
  
5.  Pokud proměnná prostředí `MSBUILDLEGACYDEFAULTTOOLSVERSION` nastaven, nebo pokud `ToolsVersion` není nastavena, pak se použijí následující kroky:  
  
    1.  `ToolsVersion` Atribut [projektu](../msbuild/project-element-msbuild.md) prvek souboru projektu. Pokud tento atribut neexistuje, předpokládá se, že se aktuální verze.  
  
    2.  Výchozí verze nástroje v *MSBuild.exe.config* souboru.  
  
    3.  Výchozí verze nástroje v registru. Další informace najdete v tématu [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Pokud proměnná prostředí `MSBUILDLEGACYDEFAULTTOOLSVERSION` není nastavena, pak se použijí následující kroky:  
  
    1.  Pokud proměnná prostředí `MSBUILDDEFAULTTOOLSVERSION` je nastavena na `ToolsVersion` , který existuje, použijte ji.  
  
    2.  Pokud `DefaultOverrideToolsVersion` je nastavena v *MSBuild.exe.config*, použijte ji.  
  
    3.  Pokud `DefaultOverrideToolsVersion` je nastaven v registru, použijte ho.  
  
    4.  Jinak použijte aktuální `ToolsVersion`.  
  
## <a name="see-also"></a>Viz také:  
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)