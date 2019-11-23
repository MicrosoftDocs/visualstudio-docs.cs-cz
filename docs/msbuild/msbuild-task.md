---
title: Úloha MSBuild | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d0b2b0c4cee2a372bccb8ad461ed195fc5519d7
ms.sourcegitcommit: 0554b59a2a251661e56824fb9cd6e9b1f326cef1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71831857"
---
# <a name="msbuild-task"></a>MSBuild – úloha

Vytvoří [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty z jiného projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `MSBuild`.

| Parametr | Popis |
|-----------------------------------| - |
| `BuildInParallel` | Volitelný parametr `Boolean`.<br /><br /> Pokud je to `true`, projekty zadané v parametru `Projects` jsou sestaveny paralelně, pokud je to možné. Výchozí hodnota je `false`. |
| `Projects` | Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory projektu, které se mají sestavit. |
| `Properties` | Volitelný parametr `String`.<br /><br /> Čárkami oddělený seznam párů název/hodnota vlastnosti, které se použijí jako globální vlastnosti podřízeného projektu. Pokud zadáte tento parametr, je funkčně ekvivalentní nastavení vlastností, které mají přepínač **-Property** při sestavení pomocí nástroje [*MSBuild. exe*](../msbuild/msbuild-command-line-reference.md). Příklad:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Při předání vlastností projektu prostřednictvím parametru `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] může vytvořit novou instanci projektu i v případě, že soubor projektu již byl načten. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vytvoří jednu instanci projektu pro danou cestu projektu a jedinečnou sadu globálních vlastností. Například toto chování umožňuje vytvořit více úloh nástroje MSBuild, které volají *MyProject. proj*s konfigurací = Release, a získáte jednu instanci *MyProject. proj* (Pokud v úloze nejsou zadány žádné jedinečné vlastnosti). Pokud zadáte vlastnost, která ještě nebyla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]a, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vytvoří novou instanci projektu, která může být sestavena paralelně s jinými instancemi projektu. Například konfigurace vydané verze může sestavovat ve stejnou dobu jako konfigurace ladění.|
| `RebaseOutputs` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, relativní cesty cílového výstupních položek z sestavených projektů mají své cesty upraveny tak, aby byly relativní vzhledem k volajícímu projektu. Výchozí hodnota je `false`. |
| `RemoveProperties` | Volitelný parametr `String`.<br /><br /> Určuje sadu globálních vlastností, které mají být odebrány. |
| `RunEachTargetSeparately` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, úloha [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vyvolá každý cíl v seznamu předaném do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] v jednom okamžiku místo ve stejnou dobu. Nastavením tohoto parametru na `true` zajistíte, aby se další cíle vyvolaly i v případě, že se dřív vyvolaný cíl nezdařil V opačném případě chyba sestavení by zastavila vyvolání všech dalších cílů. Výchozí hodnota je `false`. |
| `SkipNonexistentProjects` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, soubory projektu, které na disku neexistují, se přeskočí. Jinak takové projekty způsobí chybu. |
| `StopOnFirstFailure` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, pokud se jeden z projektů nepovede sestavit, nebudou sestaveny žádné další projekty. V současné době není tato podpora podporována při paralelním sestavování (s více procesory). |
| `TargetAndPropertyListSeparators` | Volitelný parametr `String[]`.<br /><br /> Určuje seznam cílů a vlastností jako metadata `Project` položky). Oddělovače budou před zpracováním uvozeny řídicími znaky. například% 3B (řídicí znak '; ') bude považován za, jako by šlo o neřídicí znak '; '. |
| `TargetOutputs` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` výstupní parametr jen pro čtení.<br /><br /> Vrátí výstupy sestavených cílů ze všech souborů projektu. Vrátí se jenom výstupy z určených cílů, ne všechny výstupy, které můžou existovat na cílících, na kterých jsou tyto cíle závislé.<br /><br /> Parametr `TargetOutputs` obsahuje také následující metadata:<br /><br /> -   `MSBuildSourceProjectFile`: soubor projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], který obsahuje cíl, který nastaví výstupy.<br />-   `MSBuildSourceTargetName`: cíl, který nastaví výstupy. **Poznámka:**  Chcete-li identifikovat výstupy z každého souboru projektu nebo cíle samostatně, spusťte úlohu `MSBuild` samostatně pro každý soubor projektu nebo cíl. Pokud spustíte úlohu `MSBuild` pouze jednou pro sestavení všech souborů projektu, výstupy všech cílů jsou shromažďovány do jednoho pole. |
| `Targets` | Volitelný parametr `String`.<br /><br /> Určuje cíl nebo cíle, které se mají sestavit v souborech projektu. K oddělení seznamu cílových názvů použijte středník. Pokud nejsou zadány žádné cíle v úloze `MSBuild`, jsou vytvořeny výchozí cíle zadané v souborech projektu. **Poznámka:**  Cíle musí být provedeny ve všech souborech projektu. Pokud ne, dojde k chybě sestavení. |
| `ToolsVersion` | Volitelný parametr `String`.<br /><br /> Určuje `ToolsVersion`, který se má použít při vytváření projektů předaných do této úlohy.<br /><br /> Umožňuje úloze [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sestavit projekt, který se zaměřuje na jinou verzi .NET Framework než v projektu, který je zadaný v projektu. Platné hodnoty jsou `2.0`, `3.0` a `3.5`. Výchozí hodnota je `3.5`. |

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

 Na rozdíl od použití [úlohy exec](../msbuild/exec-task.md) ke spuštění nástroje *MSBuild. exe*Tato úloha používá stejný proces [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k sestavení podřízených projektů. Seznam již sestavených cílů, které lze přeskočit, je sdílen mezi nadřazeným a podřízeným sestavením. Tato úloha je také rychlejší, protože se nevytvoří žádný nový proces [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

 Tato úloha může zpracovat nejen soubory projektu, ale také soubory řešení.

 Jakákoli konfigurace, která je požadována [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k tomu, aby bylo možné projekty současně sestavit, i když konfigurace zahrnuje vzdálenou infrastrukturu (například porty, protokoly, vypršení časového limitu, opakování a tak dále), je nutné provést konfiguraci pomocí konfiguračního souboru. Pokud je to možné, měly by být položky konfigurace možné zadat jako parametry úkolu `MSBuild` úlohy.

 Počínaje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 projekty řešení nyní surfují TargetOutputs ze všech dílčích projektů, které sestavení vytvoří.

## <a name="pass-properties-to-projects"></a>Předat vlastnosti projektům

 Ve verzích [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] před [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 předávání různých sad vlastností různým projektům uvedeným v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] položce bylo náročné. Pokud jste použili atribut Properties (vlastnosti) [úlohy MSBuild](../msbuild/msbuild-task.md), pak se jeho nastavení použilo pro všechny projekty, které jsou sestaveny, pokud jste nedávkují [úlohu MSBuild](../msbuild/msbuild-task.md) a podmíněně neposkytly různé vlastnosti pro každý projekt v seznamu položek.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3,5 však poskytuje dvě nové rezervované položky metadat, vlastnosti a AdditionalProperties, které poskytují flexibilní způsob, jak předat různé vlastnosti pro různé projekty sestavené pomocí [úlohy MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Tyto nové položky metadat platí pouze pro položky předané v atributu Projects [úlohy MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Výhody sestavení s více procesory

 Jednou z hlavních výhod používání těchto nových metadat nastane při sestavování projektů paralelně v systému s více procesory. Metadata umožňují konsolidovat všechny projekty do jednoho volání [úlohy MSBuild](../msbuild/msbuild-task.md) bez nutnosti provádět úlohy dávkování nebo podmíněného [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. A při volání pouze jedné [úlohy MSBuild](../msbuild/msbuild-task.md)budou všechny projekty, které jsou uvedeny v atributu Projects, sestaveny paralelně. (Pokud je však atribut `BuildInParallel=true` přítomen v [úloze MSBuild](../msbuild/msbuild-task.md).) Další informace najdete v tématu [sestavení více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadata vlastností

 Po zadání vlastnosti metadata Přepisuje parametr vlastností úlohy, zatímco metadata [AdditionalProperties](#additionalproperties-metadata) jsou připojena k definicím parametru.

 Běžným scénářem je, když vytváříte více souborů řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to pouze pomocí různých konfigurací sestavení. Můžete chtít sestavit řešení a1 pomocí konfigurace ladění a řešení a2 pomocí konfigurace vydané verze. V [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 by tento soubor projektu vypadal jako následující:

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

 \- nebo –

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

 Vezměte v úvahu následující scénář, kde vytváříte dva soubory řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to pomocí konfigurace vydané verze, ale jednoho pomocí architektury x86 a druhé pomocí architektury IA64. V [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2,0 byste museli vytvořit více instancí [úlohy MSBuild](../msbuild/msbuild-task.md): jeden pro sestavení projektu pomocí konfigurace vydané verze s architekturou x86, druhá pomocí konfigurace vydané verze s architekturou ia64. Váš soubor projektu by vypadal jako následující:

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

 Následující příklad používá úlohu `MSBuild` k sestavení projektů určených `ProjectReferences` kolekce položek. Výsledné výstupy jsou uloženy v kolekci `AssembliesBuiltByChildProjects`ch položek.

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

## <a name="see-also"></a>Viz také:

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
