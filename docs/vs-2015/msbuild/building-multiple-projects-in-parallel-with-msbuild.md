---
title: Paralelní sestavování více projektů pomocí MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f80f0898167de133d78d27d26f97d0ab8ced0b31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843953"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Paralelní sestavování více projektů současně pomocí nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj MSBuild lze použít pro rychlejší sestavení více projektů tak, že budou tyto projekty spuštěny paralelně. Pro paralelní spuštění sestavení je možné na počítači s více jádry nebo s více procesory použít následující nastavení:  
  
- Přepínač příkazového řádku `/maxcpucount`.  
  
- Parametr úlohy <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> na úlohu nástroje MSBuild.  
  
> [!NOTE]
> Výkon sestavení může také ovlivnit přepínač **/Verbosity** (**/v**) na příkazovém řádku. Výkon sestavení se může snížit, je-li podrobnost informací protokolu sestavení nastavena na možnosti podrobné nebo diagnostické, které se používají pro řešení potíží. Další informace najdete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [odkazů na příkazový řádek](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Přepínač /maxcpucount  
 Použitím přepínače `/maxcpucount` nebo pomocí zkratky `/m` může nástroj MSBuild vytvořit zadaný počet procesů MSBuild.exe, které probíhají souběžně. Tyto procesy jsou známé také jako „pracovní procesy“. Každý pracovní proces používá samostatné jádro nebo procesor – je-li nějaký k dispozici – pro sestavení projektu ve stejnou dobu, kdy ostatní procesory provádějí sestavení ostatních projektů. Například nastavení tohoto přepínače na hodnotu „4“ způsobí, že nástroj MSBuild vytvoří čtyři pracovní procesy pro sestavení projektu.  
  
 Při použití přepínače `/maxcpucount` bez zadání hodnoty použije nástroj MSBuild číslo odpovídající počtu procesorů v počítači.  
  
 Další informace o tomto přepínači, který byl představen v MSBuild 3,5, najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
 Následující příklad nastaví nástroj MSBuild pro použití tří pracovních procesů. Použitím této konfigurace může nástroj MSBuild provádět souběžné sestavení tří projektů.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>Parametr úlohy BuildInParallel  
 `BuildInParallel` je volitelný logický parametr pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úlohu. Když `BuildInParallel` je nastavená na `true` (výchozí hodnota), vygenerují se několik pracovních procesů, aby se sestavilo co nejvíce projektů. Aby tento postup správně fungoval, musí být přepínač `/maxcpucount` nastaven na hodnotu větší než 1 a systém musí být alespoň dvoujádrový nebo mít dva nebo více procesorů.  
  
 Následuje příklad z webu microsoft.common.targets o tom, jak nastavit parametr `BuildInParallel`.  
  
```  
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
 [Použití více procesorů k sestavení projektů](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Zápis protokolovacích nástrojů podporujících více procesorů](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Ladění blogu pro paralelní sestavení C++](https://blogs.msdn.com/b/visualstudio/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)
