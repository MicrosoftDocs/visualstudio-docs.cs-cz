---
title: Úlohy nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 3782db2b2c3fb3cdc5d0cc9ed21459c2b2215250
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878255"
---
# <a name="msbuild-task"></a>MSBuild – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sestaví [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty z jiného [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektu.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `MSBuild` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`BuildInParallel`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, v zadaných projektů `Projects` parametru jsou vytvořeny paralelně, pokud je to možné. Výchozí hodnota je `false`.|  
|`Projects`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory projektu k sestavení.|  
|`Properties`|Volitelné `String` parametru.<br /><br /> Seznam oddělený středníkem dvojice název/hodnota vlastnosti použít jako globální vlastnosti podřízený projekt. Pokud tento parametr zadán, je funkčně srovnatelný s nastavením vlastnosti, které mají **/property** přepnout při sestavení s [MSBuild.exe](../msbuild/msbuild-command-line-reference.md). Příklad:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Při předání vlastnosti projektu prostřednictvím `Properties` parametr [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vytvoří novou instanci projektu i v případě, že už je načtený soubor projektu. Po vytvoření nové instance projektu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] považuje za jiný projekt, který má jiné globální vlastnosti a, který může být sestaven paralelně s jinými instancemi projektu. Například může vytvořit konfiguraci vydané verze ve stejnou dobu jako konfigurace ladění.|  
|`RebaseOutputs`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, relativní cesty cílové výstupní položky ze sestavených projektech mají jejich cesty, upraví se vzhledem k volání projektu. Výchozí hodnota je `false`.|  
|`RemoveProperties`|Volitelné `String` parametru.<br /><br /> Určuje sadu globálních vlastností k odebrání.|  
|`RunEachTargetSeparately`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úloha vyvolá každý cíl v seznamu předán [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] postupně, místo ve stejnou dobu. Nastavení tohoto parametru na `true` zaručuje, že další cíle jsou vyvolány i v případě, že dříve vyvolaný cíle se nezdařilo. V opačném případě chybu sestavení zastaví vyvolání všechny následné cíle. Výchozí hodnota je `false`.|  
|`SkipNonexistentProjects`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, soubory projektu, které neexistuje na disku se přeskočí. V opačném případě takových projektů způsobí chybu.|  
|`StopOnFirstFailure`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, při selhání jednoho z projektů k sestavení, budou vytvořeny žádné další projekty. Aktuálně to není podporováno při sestavování paralelně (s více procesory).|  
|`TargetAndPropertyListSeparators`|Volitelné `String[]` parametru.<br /><br /> Určuje seznam cíle a vlastnosti jako `Project` metadata položky). Oddělovače budou uvozeny řídicími znaky před zpracováním. třeba % 3B (uvozený uvozovacím znakem ";") bude zacházeno, jako by šlo uvozeny řídicími znaky ";".|  
|`TargetOutputs`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` jen pro čtení výstupního parametru.<br /><br /> Vrátí výstupy sestavených cílů ze všech vygenerovaných souborů projektu. Výstupy z cíle, které se zadaly nezobrazí, není žádné výstupy, které mohou existovat na cíle, které tyto cíle závisí na.<br /><br /> `TargetOutputs` Parametr obsahuje také následující metadata:<br /><br /> -   `MSBuildSourceProjectFile`: [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Soubor projektu, který obsahuje cíl, nastavte výstupy.<br />-   `MSBuildSourceTargetName`: Cíl, který nastavit výstupy. **Poznámka:** Pokud chcete identifikovat výstupy z každého souboru projektu nebo cílové samostatně, spusťte `MSBuild` úkol samostatně pro každý projekt soubor nebo cíl. Pokud spustíte `MSBuild` úkolů pouze jednou, pokud chcete sestavit všechny soubory projektu, výstupy všechny cíle se shromáždí do jednoho pole.|  
|`Targets`|Volitelné `String` parametru.<br /><br /> Určuje cíl nebo cíle sestavení v souborech projektu. K oddělení seznam cílových názvů použijte středník. Pokud nejsou zadány žádné cíle v `MSBuild` úkolu, jsou integrované výchozí cíle zadané v souborech projektu. **Poznámka:** cíle, které se musí vyskytovat ve všech souborech projektu. Pokud tomu tak není, dojde k chybě sestavení.|  
|`ToolsVersion`|Volitelné `String` parametru.<br /><br /> Určuje, `ToolsVersion` pro použití při sestavování projektů předaný k tomuto úkolu.<br /><br /> Umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úkolů k sestavení projektu, který se zaměřuje na jinou verzi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] než verze zadaná v projektu. Platné hodnoty jsou `2.0`, `3.0` a `3.5`. Výchozí hodnota je `3.5`.|  
|`UnloadProjectsOnCompletion`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, projekt bude zrušeno po dokončení operace.|  
|`UseResultsCache`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, výsledky uložené v mezipaměti bude vrácen, pokud jsou k dispozici. Pokud je spuštěn úkol theMSBuild, výsledek bude v oboru (ProjectFileName, GlobalProperties) do mezipaměti [TargetNames]<br /><br /> jako seznam položek sestavení|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
 Na rozdíl od použití [Exec – úloha](../msbuild/exec-task.md) spustit MSBuild.exe, tato úloha používá stejná [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] procesu k vytvoření podřízené projekty. Seznam již vytvořených cílů, které mohly být přeskočeny, jsou sdílena mezi nadřazenými a podřízenými sestavení. Tato úloha je také rychlejší, protože žádná nová [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proces je vytvořen.  
  
 Tato úloha může zpracovat pouze soubory projektu, ale také soubory řešení.  
  
 Všechny konfigurace, který vyžaduje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] umožňující projektů k sestavení ve stejnou dobu, i v případě, že konfigurace zahrnuje vzdálené infrastruktury (třeba portů, protokolů, vypršení časového limitu, opakování a tak dále), musí provést konfigurovatelné pomocí konfigurační soubor. Pokud je to možné, položky konfigurace budou moci být zadány jako parametry úkolu na `MSBuild` úloh.  
  
 Počínaje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, řešení, projekty teď surface TargetOutputs ze všech dílčích projektů sestavení.  
  
## <a name="passing-properties-to-projects"></a>Předávání vlastností do projektů  
 Ve verzích [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] před [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, předávání různých nastaví vlastnosti uvedené v různých projektech [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] položka už byla náročná. Pokud jste použili atribut vlastnosti [úlohy nástroje MSBuild](../msbuild/msbuild-task.md), pak jeho nastavení bylo použito na všechny projekty jsou sestaveny, pokud jste v dávce [úlohy nástroje MSBuild](../msbuild/msbuild-task.md) a podmíněně k dispozici různé vlastnosti pro každý projekt v seznamu položek.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, ale nabízí dvě nové vyhrazené položky metadat, vlastnosti a AdditionalProperties, které poskytují flexibilní způsob, jak předat různé vlastnosti pro různé projekty jsou sestaveny [úlohy nástroje MSBuild](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Tyto nové položky metadat se vztahují pouze na položek předaných v atributu projektů [úlohy nástroje MSBuild](../msbuild/msbuild-task.md).  
  
## <a name="multi-processor-build-benefits"></a>Výhody víceprocesorového sestavení  
 Jeden z největších výhod používání tato nová metadata nastane, pokud sestavujete svoje projekty paralelně na systému s více procesory. Metadata vám umožňuje konsolidovat všechny projekty do jednoho [úlohy nástroje MSBuild](../msbuild/msbuild-task.md) volání bez nutnosti provádět všechny dávkování nebo podmíněné [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úlohy. A při volání jedné [úlohy nástroje MSBuild](../msbuild/msbuild-task.md), všechny projekty, které jsou uvedené v atributu projekty budou vytvořeny paralelně. (Pouze, ale pokud `BuildInParallel=true` atribut nachází v [úlohy nástroje MSBuild](../msbuild/msbuild-task.md).) Další informace najdete v tématu [sestavování více projektů současně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="properties-metadata"></a>Vlastnosti metadat  
 Běžný scénář, kdy je při vytváření více souborů řešení pomocí [úlohy nástroje MSBuild](../msbuild/msbuild-task.md), různé konfigurace sestavení používá se jenom. Možná budete chtít vytvořit a1 řešení pomocí a2 řešení a konfigurace ladění pomocí konfigurace vydané verze. V [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, tento soubor projektu by vypadat nějak takto:  
  
> [!NOTE]
>  V následujícím příkladu "..." představuje soubory další řešení.  
  
### <a name="aproj"></a>a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Pomocí vlastností metadat však můžete zjednodušit této možnosti pomocí jediného [úlohy nástroje MSBuild](../msbuild/msbuild-task.md), jak je znázorněno v následující:  
  
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
  
 \- nebo –  
  
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
 Vezměte v úvahu následující scénář, ve kterém vytváříte dva soubory řešení pomocí [úlohy nástroje MSBuild](../msbuild/msbuild-task.md), jak pomocí konfigurace vydané verze, ale jeden x86 pomocí architektury a druhou architekturou ia64. V [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, je třeba vytvořit více instancí [úlohy nástroje MSBuild](../msbuild/msbuild-task.md): z nich se má sestavit projekt pomocí x86 konfiguraci vydané verze architektury, druhý konfiguraci vydané verze pomocí ia64 Architektura. Váš soubor projektu by vypadat nějak takto:  
  
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
  
 Pomocí AdditionalProperties metadata může zjednodušit této možnosti pomocí jediného [úlohy nástroje MSBuild](../msbuild/msbuild-task.md) pomocí následujících:  
  
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
 V následujícím příkladu `MSBuild` úkolů k sestavení projektů určeného `ProjectReferences` kolekci položek. Cíl výsledného výstupy jsou uloženy v `AssembliesBuiltByChildProjects` kolekci položek.  
  
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
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



