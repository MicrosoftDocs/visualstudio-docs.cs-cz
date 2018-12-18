---
title: Sestavování více projektů současně pomocí nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c375f9af63f1622df995ca28315048f682c1ca4
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879002"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>Sestavování více projektů současně pomocí nástroje MSBuild
Nástroj MSBuild lze použít pro rychlejší sestavení více projektů tak, že budou tyto projekty spuštěny paralelně. Pro paralelní spuštění sestavení je možné na počítači s více jádry nebo s více procesory použít následující nastavení:  
  
-   Přepínač příkazového řádku `-maxcpucount`.  
  
-   Parametr úlohy <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> na úlohu nástroje MSBuild.  
  
> [!NOTE]
>  **-Podrobností** (**- v**) přepínač pomocí nástroje příkazového řádku může také ovlivnit výkon sestavení. Výkon sestavení se může snížit, je-li podrobnost informací protokolu sestavení nastavena na možnosti podrobné nebo diagnostické, které se používají pro řešení potíží. Další informace najdete v tématu [získat protokoly o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="-maxcpucount-switch"></a>-maxcpucount přepínače  
 Pokud používáte `-maxcpucount` přepnout, nebo `-m` zkráceně, může nástroj MSBuild vytvořit zadaný počet *MSBuild.exe* procesy, které můžou běžet paralelně. Tyto procesy jsou známé také jako „pracovní procesy“. Každý pracovní proces používá samostatné jádro nebo procesor – je-li nějaký k dispozici – pro sestavení projektu ve stejnou dobu, kdy ostatní procesory provádějí sestavení ostatních projektů. Například nastavení tohoto přepínače na hodnotu „4“ způsobí, že nástroj MSBuild vytvoří čtyři pracovní procesy pro sestavení projektu.  
  
 Při použití přepínače `-maxcpucount` bez zadání hodnoty použije nástroj MSBuild číslo odpovídající počtu procesorů v počítači.  
  
 Další informace o tomto přepínači, která byla zavedena v MSBuild 3.5, naleznete v tématu [odkaz na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  
  
 Následující příklad nastaví nástroj MSBuild pro použití tří pracovních procesů. Použitím této konfigurace může nástroj MSBuild provádět souběžné sestavení tří projektů.  
  
```cmd  
msbuild.exe myproj.proj -maxcpucount:3   
```  

## <a name="buildinparallel-task-parameter"></a>Parametr úlohy BuildInParallel  
 `BuildInParallel` je volitelný logický parametr úlohy nástroje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Když `BuildInParallel` je nastavena na `true` (výchozí hodnota je `false`), více procesů, kolik je vytvořeno pro sestavení tolik projekty ve stejnou dobu jako možný. Aby tento postup správně fungoval, musí být přepínač `-maxcpucount` nastaven na hodnotu větší než 1 a systém musí být alespoň dvoujádrový nebo mít dva nebo více procesorů.  
  
 Následuje příklad, na základě *cílů microsoft.common.targets*, o tom, jak nastavit `BuildInParallel` parametru.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Použití více procesorů k sestavení projektů](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Zápis více procesorů protokolovacích](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Ladění blogu paralelismu sestavení C++](http://go.microsoft.com/fwlink/?LinkId=251457)
