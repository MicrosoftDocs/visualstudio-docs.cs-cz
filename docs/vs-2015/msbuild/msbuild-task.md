---
title: Úloha MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2349c21d55c20bcb3bcd50ab96f383a9afcc00b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64826942"
---
# <a name="msbuild-task"></a>MSBuild – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty z jiného [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `MSBuild` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BuildInParallel`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je to možné, projekty zadané v `Projects` parametru jsou sestaveny paralelně. Výchozí je `false`.|  
|`Projects`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory projektu, které se mají sestavit.|  
|`Properties`|Volitelný `String` parametr.<br /><br /> Čárkami oddělený seznam párů název/hodnota vlastnosti, které se použijí jako globální vlastnosti podřízeného projektu. Pokud zadáte tento parametr, je funkčně ekvivalentní nastavení vlastností, které mají přepínač **/Property** při sestavování pomocí [MSBuild.exe](../msbuild/msbuild-command-line-reference.md). Příklad:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Při předání vlastností projektu prostřednictvím `Properties` parametru [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vytvoří novou instanci projektu i v případě, že soubor projektu již byl načten. Při vytvoření nové instance projektu se [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] považuje za jiný projekt, který má různé globální vlastnosti a který lze sestavit paralelně s jinými instancemi projektu. Například konfigurace vydané verze by mohla sestavovat ve stejnou dobu jako konfigurace ladění.|  
|`RebaseOutputs`|Volitelný `Boolean` parametr.<br /><br /> Pokud jsou `true` relativní cesty cílových výstupních položek z sestavených projektů upraveny tak, aby byly relativní vzhledem k volajícímu projektu. Výchozí je `false`.|  
|`RemoveProperties`|Volitelný `String` parametr.<br /><br /> Určuje sadu globálních vlastností, které mají být odebrány.|  
|`RunEachTargetSeparately`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úloha vyvolá každý cíl v seznamu předaný do jednoho a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nikoli ve stejnou dobu. Nastavením tohoto parametru `true` zajistíte, aby se vyvolaly další cíle i v případě, že se dřív vyvolaný cíl nezdařil V opačném případě chyba sestavení by zastavila vyvolání všech dalších cílů. Výchozí je `false`.|  
|`SkipNonexistentProjects`|Volitelný `Boolean` parametr.<br /><br /> Pokud se `true` soubory projektu, které na disku neexistují, přeskočí. Jinak takové projekty způsobí chybu.|  
|`StopOnFirstFailure`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je v případě, že se jeden z projektů nepovede sestavit, nebudou sestaveny žádné další projekty. V současné době není tato podpora podporována při paralelním sestavování (s více procesory).|  
|`TargetAndPropertyListSeparators`|Volitelný `String[]` parametr.<br /><br /> Určuje seznam cílů a vlastností jako `Project` metadata položky. Oddělovače budou před zpracováním uvozeny řídicími znaky. například% 3B (řídicí znak '; ') bude považován za, jako by šlo o neřídicí znak '; '.|  
|`TargetOutputs`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Vrátí výstupy sestavených cílů ze všech souborů projektu. Vrátí se jenom výstupy z určených cílů, ne všechny výstupy, které můžou existovat na cílících, na kterých jsou tyto cíle závislé.<br /><br /> `TargetOutputs`Parametr obsahuje také následující metadata:<br /><br /> -   `MSBuildSourceProjectFile`: [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Soubor projektu, který obsahuje cíl, který nastaví výstupy.<br />-   `MSBuildSourceTargetName`: Cíl, který nastavuje výstupy. **Poznámka:**  Chcete-li identifikovat výstupy z každého souboru projektu nebo cíle samostatně, spusťte `MSBuild` úlohu samostatně pro každý soubor projektu nebo cíl. Pokud úlohu spouštíte `MSBuild` pouze jednou pro sestavení všech souborů projektu, výstupy všech cílů jsou shromažďovány do jednoho pole.|  
|`Targets`|Volitelný `String` parametr.<br /><br /> Určuje cíl nebo cíle, které se mají sestavit v souborech projektu. K oddělení seznamu cílových názvů použijte středník. Nejsou-li v úloze zadány žádné cíle `MSBuild` , jsou vytvořeny výchozí cíle zadané v souborech projektu. **Poznámka:**  Cíle musí být provedeny ve všech souborech projektu. Pokud ne, dojde k chybě sestavení.|  
|`ToolsVersion`|Volitelný `String` parametr.<br /><br /> Určuje, `ToolsVersion` který má být použit při sestavování projektů předaných této úloze.<br /><br /> Umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úloze sestavit projekt, který se zaměřuje na jinou verzi, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] než je zadaná v projektu. Platné hodnoty jsou `2.0` `3.0` a `3.5` . Výchozí hodnota je `3.5` .|  
|`UnloadProjectsOnCompletion`|Volitelný `Boolean` parametr.<br /><br /> Pokud dojde k `true` uvolnění projektu po dokončení operace.|  
|`UseResultsCache`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` se vrátí výsledek uložený v mezipaměti, je-li k dispozici. Je-li spuštěn úkol theMSBuild, jeho výsledek bude uložen do mezipaměti v oboru (ProjectFileName, GlobalProperties) [Cílový_názevs]<br /><br /> jako seznam položek sestavení|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
 Na rozdíl od použití [úlohy exec](../msbuild/exec-task.md) ke spuštění MSBuild.exe, tato úloha používá stejný [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proces pro sestavení podřízených projektů. Seznam již sestavených cílů, které lze přeskočit, je sdílen mezi nadřazeným a podřízeným sestavením. Tato úloha je také rychlejší [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , protože není vytvořen žádný nový proces.  
  
 Tato úloha může zpracovat nejen soubory projektu, ale také soubory řešení.  
  
 Jakákoli konfigurace, která je vyžadována nástrojem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] k tomu, aby bylo možné projekty současně sestavit i v případě, že konfigurace zahrnuje vzdálenou infrastrukturu (například porty, protokoly, vypršení časového limitu, opakování a tak dále), je nutné provést konfiguraci pomocí konfiguračního souboru. Pokud je to možné, měly by být položky konfigurace možné zadat jako parametry úkolu v `MSBuild` úloze.  
  
 Počínaje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3,5, projekty řešení nyní TargetOutputs plochu ze všech dílčích projektů, které sestavení vytvoří.  
  
## <a name="passing-properties-to-projects"></a>Předávání vlastností do projektů  
 Ve verzích [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] starších než [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3,5 předávání různých sad vlastností různým projektům uvedeným v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] položce bylo náročné. Pokud jste použili atribut Properties (vlastnosti) [úlohy MSBuild](../msbuild/msbuild-task.md), pak se jeho nastavení použilo pro všechny projekty, které jsou sestaveny, pokud jste nedávkují [úlohu MSBuild](../msbuild/msbuild-task.md) a podmíněně neposkytly různé vlastnosti pro každý projekt v seznamu položek.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3,5 však poskytuje dvě nové rezervované položky metadat, vlastnosti a AdditionalProperties, které poskytují flexibilní způsob, jak předat různé vlastnosti pro různé projekty sestavené pomocí [úlohy MSBuild](../msbuild/msbuild-task.md).  
  
> [!NOTE]
> Tyto nové položky metadat platí pouze pro položky předané v atributu Projects [úlohy MSBuild](../msbuild/msbuild-task.md).  
  
## <a name="multi-processor-build-benefits"></a>Výhody víceprocesorového sestavení  
 Jednou z hlavních výhod používání těchto nových metadat nastane při sestavování projektů paralelně v systému s více procesory. Metadata umožňují konsolidovat všechny projekty do jednoho volání [úlohy MSBuild](../msbuild/msbuild-task.md) bez nutnosti provádět úlohy dávkování nebo podmíněné [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úkoly. A při volání pouze jedné [úlohy MSBuild](../msbuild/msbuild-task.md)budou všechny projekty, které jsou uvedeny v atributu Projects, sestaveny paralelně. (Nicméně pokud `BuildInParallel=true` je atribut přítomen v [úloze MSBuild](../msbuild/msbuild-task.md).) Další informace naleznete v tématu [Souběžné sestavování více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="properties-metadata"></a>Vlastnosti metadat  
 Běžným scénářem je, když vytváříte více souborů řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to pouze pomocí různých konfigurací sestavení. Můžete chtít sestavit řešení a1 pomocí konfigurace ladění a řešení a2 pomocí konfigurace vydané verze. V [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2,0 by tento soubor projektu vypadal jako následující:  
  
> [!NOTE]
> V následujícím příkladu "..." představuje další soubory řešení.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Pomocí vlastností metadat však můžete zjednodušit použití jedné [úlohy MSBuild](../msbuild/msbuild-task.md), jak je znázorněno v následujícím příkladu:  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- ani  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## <a name="additionalproperties-metadata"></a>Metadata AdditionalProperties  
 Vezměte v úvahu následující scénář, kde vytváříte dva soubory řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to pomocí konfigurace vydané verze, ale jednoho pomocí architektury x86 a druhé pomocí architektury IA64. V [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2,0 byste museli vytvořit více instancí [úlohy MSBuild](../msbuild/msbuild-task.md): jeden pro sestavení projektu pomocí konfigurace vydané verze s architekturou x86, druhá používá konfiguraci vydané verze s architekturou ia64. Váš soubor projektu by vypadal jako následující:  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 Pomocí metadat AdditionalProperties můžete zjednodušit použití jedné [úlohy MSBuild](../msbuild/msbuild-task.md) pomocí následujících kroků:  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `MSBuild` úlohu k sestavení projektů určených `ProjectReferences` kolekcí položek. Výsledné výstupní výstupy jsou uloženy v `AssembliesBuiltByChildProjects` kolekci položek.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
