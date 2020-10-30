---
title: Úloha MSBuild | Microsoft Docs
description: Přečtěte si, jak úloha MSBuild používá stejný proces MSBuild k sestavení podřízených projektů z jiného projektu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4d1f9fe79ae5092992ff66ddaf5e10729e8b19a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049065"
---
# <a name="msbuild-task"></a>MSBuild – úloha

Vytvoří projekty MSBuild z jiného projektu MSBuild.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `MSBuild` úkolu.

| Parametr | Popis |
|-----------------------------------| - |
| `BuildInParallel` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je to možné, projekty zadané v `Projects` parametru jsou sestaveny paralelně. Výchozí je `false`. |
| `Projects` | Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory projektu, které se mají sestavit. |
| `Properties` | Volitelný `String` parametr.<br /><br /> Čárkami oddělený seznam párů název/hodnota vlastnosti, které se použijí jako globální vlastnosti podřízeného projektu. Pokud zadáte tento parametr, je funkčně ekvivalentní nastavení vlastností, které mají přepínač **-Property** při sestavování pomocí [*MSBuild.exe*](../msbuild/msbuild-command-line-reference.md). Příklad:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Když předáte vlastnosti projektu prostřednictvím `Properties` parametru, MSBuild může vytvořit novou instanci projektu i v případě, že soubor projektu již byl načten. Nástroj MSBuild vytvoří jednu instanci projektu pro danou cestu projektu a jedinečnou sadu globálních vlastností. Například toto chování umožňuje vytvořit více úloh nástroje MSBuild, které volají *MyProject. proj* s konfigurací = Release, a získáte jednu instanci *MyProject. proj* (Pokud v úloze nejsou zadány žádné jedinečné vlastnosti). Pokud zadáte vlastnost, která ještě nebyla v nástroji MSBuild zjištěna, nástroj MSBuild vytvoří novou instanci projektu, která může být sestavena paralelně s jinými instancemi projektu. Například konfigurace vydané verze může sestavovat ve stejnou dobu jako konfigurace ladění.|
| `RebaseOutputs` | Volitelný `Boolean` parametr.<br /><br /> Pokud jsou `true` relativní cesty cílových výstupních položek z sestavených projektů upraveny tak, aby byly relativní vzhledem k volajícímu projektu. Výchozí je `false`. |
| `RemoveProperties` | Volitelný `String` parametr.<br /><br /> Určuje sadu globálních vlastností, které mají být odebrány. |
| `RunEachTargetSeparately` | Volitelný `Boolean` parametr.<br /><br /> V případě `true` , úloha MSBuild vyvolá každý cíl v seznamu předaného do nástroje MSBuild v jednom okamžiku, nikoli ve stejnou dobu. Nastavením tohoto parametru `true` zajistíte, aby se vyvolaly další cíle i v případě, že se dřív vyvolaný cíl nezdařil V opačném případě chyba sestavení by zastavila vyvolání všech dalších cílů. Výchozí je `false`. |
| `SkipNonexistentProjects` | Volitelný `Boolean` parametr.<br /><br /> Pokud se `true` soubory projektu, které na disku neexistují, přeskočí. Jinak takové projekty způsobí chybu. |
|`SkipNonexistentTargets`|Volitelný `Boolean` parametr.<br /><br /> `true`V případě, že soubory projektu, které existují, ale neobsahují název, se `Targets` přeskočí. Jinak takové projekty způsobí chybu. Představeno v MSBuild 15,5.|
| `StopOnFirstFailure` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true` je v případě, že se jeden z projektů nepovede sestavit, nebudou sestaveny žádné další projekty. V současné době není tato podpora podporována při paralelním sestavování (s více procesory). |
| `TargetAndPropertyListSeparators` | Volitelný `String[]` parametr.<br /><br /> Určuje seznam cílů a vlastností jako `Project` metadata položky. Oddělovače budou před zpracováním uvozeny řídicími znaky. například% 3B (řídicí znak '; ') bude považován za, jako by šlo o neřídicí znak '; '. |
| `TargetOutputs` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Vrátí výstupy sestavených cílů ze všech souborů projektu. Vrátí se jenom výstupy z určených cílů, ne všechny výstupy, které můžou existovat na cílících, na kterých jsou tyto cíle závislé.<br /><br /> `TargetOutputs`Parametr obsahuje také následující metadata:<br /><br /> -   `MSBuildSourceProjectFile`: Soubor projektu MSBuild obsahující cíl, který nastaví výstupy.<br />-   `MSBuildSourceTargetName`: Cíl, který nastavuje výstupy. **Poznámka:**  Chcete-li identifikovat výstupy z každého souboru projektu nebo cíle samostatně, spusťte `MSBuild` úlohu samostatně pro každý soubor projektu nebo cíl. Pokud úlohu spouštíte `MSBuild` pouze jednou pro sestavení všech souborů projektu, výstupy všech cílů jsou shromažďovány do jednoho pole. |
| `Targets` | Volitelný `String` parametr.<br /><br /> Určuje cíl nebo cíle, které se mají sestavit v souborech projektu. K oddělení seznamu cílových názvů použijte středník. Nejsou-li v úloze zadány žádné cíle `MSBuild` , jsou vytvořeny výchozí cíle zadané v souborech projektu. **Poznámka:**  Cíle musí být provedeny ve všech souborech projektu. Pokud ne, dojde k chybě sestavení. |
| `ToolsVersion` | Volitelný `String` parametr.<br /><br /> Určuje, `ToolsVersion` který má být použit při sestavování projektů předaných této úloze.<br /><br /> Umožňuje úloze MSBuild sestavit projekt, který cílí na jinou verzi .NET Framework než v projektu, který je zadaný v projektu. Platné hodnoty jsou `2.0` `3.0` a `3.5` . Výchozí hodnota je `3.5`. |

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

 Na rozdíl od použití [úlohy exec](../msbuild/exec-task.md) ke spuštění *MSBuild.exe* používá tato úloha stejný proces MSBuild pro sestavení podřízených projektů. Seznam již sestavených cílů, které lze přeskočit, je sdílen mezi nadřazeným a podřízeným sestavením. Tato úloha je taky rychlejší, protože se nevytvoří žádný nový proces MSBuild.

 Tato úloha může zpracovat nejen soubory projektu, ale také soubory řešení.

 Jakákoli konfigurace, kterou nástroj MSBuild vyžaduje k tomu, aby bylo možné projekty současně sestavit, i když konfigurace zahrnuje vzdálenou infrastrukturu (například porty, protokoly, vypršení časového limitu, opakování a tak dále), je nutné provést konfiguraci pomocí konfiguračního souboru. Pokud je to možné, měly by být položky konfigurace možné zadat jako parametry úkolu v `MSBuild` úloze.

 Počínaje nástrojem MSBuild 3,5 projekty řešení nyní surfují TargetOutputs ze všech dílčích projektů, které sestavení vytvoří.

## <a name="pass-properties-to-projects"></a>Předat vlastnosti projektům

 Ve verzích MSBuild před nástrojem MSBuild 3,5 předávání různých sad vlastností různým projektům uvedeným v položce MSBuild bylo náročné. Pokud jste použili atribut Properties (vlastnosti) [úlohy MSBuild](../msbuild/msbuild-task.md), pak se jeho nastavení použilo pro všechny projekty, které jsou sestaveny, pokud jste nedávkují [úlohu MSBuild](../msbuild/msbuild-task.md) a podmíněně neposkytly různé vlastnosti pro každý projekt v seznamu položek.

 Nástroj MSBuild 3,5 však poskytuje dvě nové rezervované položky metadat, vlastnosti a AdditionalProperties, které poskytují flexibilní způsob, jak předat různé vlastnosti pro různé projekty sestavené pomocí [úlohy MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Tyto nové položky metadat platí pouze pro položky předané v atributu Projects [úlohy MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Výhody sestavení s více procesory

 Jednou z hlavních výhod používání těchto nových metadat nastane při sestavování projektů paralelně v systému s více procesory. Metadata umožňují konsolidovat všechny projekty do jednoho volání [úlohy MSBuild](../msbuild/msbuild-task.md) bez nutnosti provádět žádné dávkové nebo podmíněné úlohy MSBuild. A při volání pouze jedné [úlohy MSBuild](../msbuild/msbuild-task.md)budou všechny projekty, které jsou uvedeny v atributu Projects, sestaveny paralelně. (Nicméně pokud `BuildInParallel=true` je atribut přítomen v [úloze MSBuild](../msbuild/msbuild-task.md).) Další informace najdete v tématu [sestavení více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadata vlastností

 Po zadání vlastnosti metadata Přepisuje parametr vlastností úlohy, zatímco metadata [AdditionalProperties](#additionalproperties-metadata) jsou připojena k definicím parametru.

 Běžným scénářem je, když vytváříte více souborů řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to pouze pomocí různých konfigurací sestavení. Můžete chtít sestavit řešení a1 pomocí konfigurace ladění a řešení a2 pomocí konfigurace vydané verze. V MSBuild 2,0 by tento soubor projektu vypadal jako následující:

> [!NOTE]
> V následujícím příkladu "..." představuje další soubory řešení.

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>
    </Target>
</Project>
```

 Pomocí vlastností metadat však můžete zjednodušit použití jedné [úlohy MSBuild](../msbuild/msbuild-task.md), jak je znázorněno v následujícím příkladu:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
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

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln..."/>
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

 Vezměte v úvahu následující scénář, kde vytváříte dva soubory řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to pomocí konfigurace vydané verze, ale jednoho pomocí architektury x86 a druhé pomocí architektury IA64. V MSBuild 2,0 byste museli vytvořit více instancí [úlohy MSBuild](../msbuild/msbuild-task.md): jeden pro sestavení projektu pomocí konfigurace vydané verze s architekturou x86, druhá pomocí konfigurace vydané verze s architekturou ia64. Váš soubor projektu by vypadal jako následující:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Build">
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;
          Architecture=x86"/>
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;
          Architecture=ia64"/>
    </Target>
</Project>
```

 Pomocí metadat AdditionalProperties můžete zjednodušit použití jedné [úlohy MSBuild](../msbuild/msbuild-task.md) pomocí následujících kroků:

### <a name="aproj"></a>a.proj

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ProjectToBuild Include="a1.sln...">
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

```xml
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

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
