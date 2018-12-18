---
title: Sestavování více projektů současně pomocí nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98444a8af0dfd231d63748a1dd0e9b62ca54b651
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285373"
---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Paralelní sestavování více projektů současně pomocí nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Nástroj MSBuild lze použít pro rychlejší sestavení více projektů tak, že budou tyto projekty spuštěny paralelně. Pro paralelní spuštění sestavení je možné na počítači s více jádry nebo s více procesory použít následující nastavení:  
  
-   Přepínač příkazového řádku `/maxcpucount`.  
  
-   Parametr úlohy <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> na úlohu nástroje MSBuild.  
  
> [!NOTE]
>  **/Verbosity** (**/v**) přepínač pomocí nástroje příkazového řádku může také ovlivnit výkon sestavení. Výkon sestavení se může snížit, je-li podrobnost informací protokolu sestavení nastavena na možnosti podrobné nebo diagnostické, které se používají pro řešení potíží. Další informace najdete v tématu [získávání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Přepínač /maxcpucount  
 Použitím přepínače `/maxcpucount` nebo pomocí zkratky `/m` může nástroj MSBuild vytvořit zadaný počet procesů MSBuild.exe, které probíhají souběžně. Tyto procesy jsou známé také jako „pracovní procesy“. Každý pracovní proces používá samostatné jádro nebo procesor – je-li nějaký k dispozici – pro sestavení projektu ve stejnou dobu, kdy ostatní procesory provádějí sestavení ostatních projektů. Například nastavení tohoto přepínače na hodnotu „4“ způsobí, že nástroj MSBuild vytvoří čtyři pracovní procesy pro sestavení projektu.  
  
 Při použití přepínače `/maxcpucount` bez zadání hodnoty použije nástroj MSBuild číslo odpovídající počtu procesorů v počítači.  
  
 Další informace o tomto přepínači, která byla zavedena v MSBuild 3.5, naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
 Následující příklad nastaví nástroj MSBuild pro použití tří pracovních procesů. Použitím této konfigurace může nástroj MSBuild provádět souběžné sestavení tří projektů.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>Parametr úlohy BuildInParallel  
 `BuildInParallel` je volitelný logický parametr úlohy nástroje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Když `BuildInParallel` je nastavena na `true` (výchozí hodnota), více procesů, kolik je vytvořeno pro sestavení tolik projekty ve stejnou dobu jako možný. Aby tento postup správně fungoval, musí být přepínač `/maxcpucount` nastaven na hodnotu větší než 1 a systém musí být alespoň dvoujádrový nebo mít dva nebo více procesorů.  
  
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
 [Zápis více procesorů protokolovacích](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Blog o optimalizaci paralelního sestavení v C++](http://go.microsoft.com/fwlink/?LinkId=251457)



