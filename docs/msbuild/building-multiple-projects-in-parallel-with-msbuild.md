---
title: Souběžné vytváření více projektů s msbuildem | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1723fba810450fe5e31a43d63f3704ab74f455f4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634497"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>Souběžné vytváření více projektů s msbuildem

Nástroj MSBuild lze použít pro rychlejší sestavení více projektů tak, že budou tyto projekty spuštěny paralelně. Pro paralelní spuštění sestavení je možné na počítači s více jádry nebo s více procesory použít následující nastavení:

- Přepínač příkazového řádku `-maxcpucount`.

- Parametr úlohy <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> na úlohu nástroje MSBuild.

> [!NOTE]
> Přepínač **-verbosity** (**-v**) v příkazovém řádku může také ovlivnit výkon sestavení. Výkon sestavení se může snížit, je-li podrobnost informací protokolu sestavení nastavena na možnosti podrobné nebo diagnostické, které se používají pro řešení potíží. Další informace naleznete v [tématu Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [odkazu na příkazový řádek](../msbuild/msbuild-command-line-reference.md).

## <a name="-maxcpucount-switch"></a>-maxcpucount přepínač

Pokud použijete `-maxcpucount` přepínač `-m` nebo zkráceně, MSBuild můžete vytvořit zadaný počet procesů *MSBuild.exe,* které mohou být spuštěny paralelně. Tyto procesy jsou známé také jako „pracovní procesy“. Každý pracovní proces používá samostatné jádro nebo procesor – je-li nějaký k dispozici – pro sestavení projektu ve stejnou dobu, kdy ostatní procesory provádějí sestavení ostatních projektů. Například nastavení tohoto přepínače na hodnotu „4“ způsobí, že nástroj MSBuild vytvoří čtyři pracovní procesy pro sestavení projektu.

Při použití přepínače `-maxcpucount` bez zadání hodnoty použije nástroj MSBuild číslo odpovídající počtu procesorů v počítači.

Další informace o tomto přepínači, který byl zaveden v MSBuild 3.5, naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md).

Následující příklad nastaví nástroj MSBuild pro použití tří pracovních procesů. Použitím této konfigurace může nástroj MSBuild provádět souběžné sestavení tří projektů.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>Parametr úlohy BuildInParallel

`BuildInParallel`je volitelný logický parametr úlohy MSBuild. Když `BuildInParallel` je `true` nastavena na `true`(jeho výchozí hodnota je ) více pracovních procesů jsou generovány k sestavení co nejvíce projektů ve stejnou dobu, jak je to možné. Aby tento postup správně fungoval, musí být přepínač `-maxcpucount` nastaven na hodnotu větší než 1 a systém musí být alespoň dvoujádrový nebo mít dva nebo více procesorů.

Následuje příklad převzatý z *microsoft.common.targets*o nastavení `BuildInParallel` parametru.

```xml
<PropertyGroup>
    <BuildInParallel Condition="'$(BuildInParallel)' ==
        ''">true</BuildInParallel>
</PropertyGroup>
<MSBuild
    Projects="@(_MSBuildProjectReferenceExistent)"
    Targets="GetTargetPath"
    BuildInParallel="$(BuildInParallel)"
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);
        %(_MSBuildProjectReferenceExistent.SetPlatform)"
    Condition="'@(NonVCProjectReference)'!='' and
        ('$(BuildingSolutionFile)' == 'true' or
        '$(BuildingInsideVisualStudio)' == 'true' or
        '$(BuildProjectReferences)' != 'true') and
        '@(_MSBuildProjectReferenceExistent)' != ''"
    ContinueOnError="!$(BuildingProject)">
    <Output TaskParameter="TargetOutputs"
        ItemName="_ResolvedProjectReferencePaths"/>
</MSBuild>
```

## <a name="see-also"></a>Viz také

- [Použití více procesorů k vytváření projektů](../msbuild/using-multiple-processors-to-build-projects.md)
- [Zápis víceprocesorových úhozů](../msbuild/writing-multi-processor-aware-loggers.md)
- [Tuning C++ sestavení paralelismu blog](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
