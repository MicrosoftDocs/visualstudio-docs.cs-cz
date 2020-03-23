---
title: Úkol MSBuild | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 4a312bfe8c88b0ac523666779970cc28e3a7c798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633171"
---
# <a name="msbuild-task"></a>MSBuild – úloha

Vytvoří projekty MSBuild z jiného projektu MSBuild.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `MSBuild` úkolu.

| Parametr | Popis |
|-----------------------------------| - |
| `BuildInParallel` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`jsou projekty `Projects` zadané v parametru sestaveny paralelně, pokud je to možné. Výchozí je `false`. |
| `Projects` | Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory projektu, které mají být sestavovány. |
| `Properties` | Volitelný `String` parametr.<br /><br /> Středník-oddělený seznam párů název/hodnota vlastnosti použít jako globální vlastnosti podřízeného projektu. Pokud zadáte tento parametr, je funkčně ekvivalentní nastavení vlastností, které mají přepínač **vlastnosti -při** vytváření pomocí [*msbuild.exe*](../msbuild/msbuild-command-line-reference.md). Například:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Při předání vlastností projektu `Properties` prostřednictvím parametru MSBuild může vytvořit novou instanci projektu i v případě, že soubor projektu již byla načtena. MSBuild vytvoří jednu instanci projektu pro danou cestu projektu a jedinečnou sadu globálních vlastností. Toto chování například umožňuje vytvořit více úkolů MSBuild, které volají *myproject.proj*, s Configuration=Release a získáte jednu instanci *myproject.proj* (pokud nejsou zadány žádné jedinečné vlastnosti v úkolu). Pokud zadáte vlastnost, která ještě nebyla vidět MSBuild, MSBuild vytvoří novou instanci projektu, který může být sestaven paralelně s jinými instancemi projektu. Například konfigurace vydání můžete sestavit současně s konfigurací ladění.|
| `RebaseOutputs` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`mají relativní cesty cílových výstupních položek ze sestavovaných projektů své cesty upraveny tak, aby byly relativní vzhledem k volajícímu projektu. Výchozí je `false`. |
| `RemoveProperties` | Volitelný `String` parametr.<br /><br /> Určuje sadu globálních vlastností, které chcete odebrat. |
| `RunEachTargetSeparately` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol MSBuild vyvolá každý cíl v seznamu předaný msbuild jeden po druhém, namísto ve stejnou dobu. Nastavení tohoto `true` parametru na záruky, že následné cíle jsou vyvolány i v případě, že dříve vyvolané cíle se nezdařilo. V opačném případě by chyba sestavení zastavit vyvolání všech následných cílů. Výchozí je `false`. |
| `SkipNonexistentProjects` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`budou přeskočeny soubory projektu, které na disku neexistují. V opačném případě tyto projekty způsobí chybu. |
| `StopOnFirstFailure` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, když jeden z projektů se nezdaří sestavit, žádné další projekty budou vytvořeny. V současné době to není podporováno při vytváření paralelně (s více procesory). |
| `TargetAndPropertyListSeparators` | Volitelný `String[]` parametr.<br /><br /> Určuje seznam cílů a vlastností jako `Project` metadata položky). Oddělovače budou un-escaped před zpracováním. například %3B (uvozené ';') bude zacházeno, jako by se jednalo o un-escaped ';'. |
| `TargetOutputs` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr jen pro čtení.<br /><br /> Vrátí výstupy vytvořených cílů ze všech souborů projektu. Jsou vráceny pouze výstupy z cílů, které byly zadány, nikoli všechny výstupy, které mohou existovat na cíle, které tyto cíle závisí na.<br /><br /> Parametr `TargetOutputs` také obsahuje následující metadata:<br /><br /> -   `MSBuildSourceProjectFile`: Soubor projektu MSBuild, který obsahuje cíl, který nastavuje výstupy.<br />-   `MSBuildSourceTargetName`: Cíl, který nastavuje výstupy. **Poznámka:**  Pokud chcete identifikovat výstupy z každého souboru projektu `MSBuild` nebo cíle samostatně, spusťte úkol samostatně pro každý soubor nebo cíl projektu. Pokud spustíte `MSBuild` úlohu pouze jednou k sestavení všech souborů projektu, výstupy všech cílů jsou shromážděny do jednoho pole. |
| `Targets` | Volitelný `String` parametr.<br /><br /> Určuje cíl nebo cíle, které mají být v souborech projektu vytvářeny. Pomocí středníku oddělte seznam cílových názvů. Pokud v úkolu nejsou `MSBuild` zadány žádné cíle, jsou vytvořeny výchozí cíle zadané v souborech projektu. **Poznámka:**  Cíle musí dojít ve všech souborech projektu. Pokud tomu tak není, dojde k chybě sestavení. |
| `ToolsVersion` | Volitelný `String` parametr.<br /><br /> Určuje, `ToolsVersion` který se má použít při vytváření projektů předanejch na tento úkol.<br /><br /> Umožňuje úkolu MSBuild vytvořit projekt, který se zaměřuje na jinou verzi rozhraní .NET Framework než ta, která je zadána v projektu. Platné hodnoty `2.0` `3.0` jsou `3.5`a . Výchozí hodnota `3.5`je . |

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

 Na rozdíl od použití [exec úkol](../msbuild/exec-task.md) ke spuštění *MSBuild.exe*, tento úkol používá stejný proces MSBuild k vytvoření podřízených projektů. Seznam již vytvořených cílů, které lze přeskočit, je sdílen mezi nadřazeným a podřízeným sestavením. Tato úloha je také rychlejší, protože není vytvořen žádný nový proces MSBuild.

 Tento úkol může zpracovávat nejen soubory projektu, ale také soubory řešení.

 Jakákoli konfigurace, kterou msbuild vyžaduje, aby projekty mohly být vytvářeny současně, i když konfigurace zahrnuje vzdálenou infrastrukturu (například porty, protokoly, časové režimy, opakování atd.), musí být konfigurovatelná pomocí konfiguračního souboru. Pokud je to možné, měly by být položky konfigurace možné zadat jako parametry úkolu na `MSBuild` úkolu.

 Počínaje MSBuild 3.5, projekty řešení nyní povrch TargetOutputs ze všech dílčích projektů, které vytváří.

## <a name="pass-properties-to-projects"></a>Předat vlastnosti projektům

 Ve verzích MSBuild před MSBuild 3.5 předávání různých sad vlastností různým projektům uvedeným v položce MSBuild bylo náročné. Pokud jste použili atribut Vlastnosti [úlohy MSBuild](../msbuild/msbuild-task.md), bylo jeho nastavení použito pro všechny vytvářené projekty, pokud jste nedávkovali [úkol MSBuild](../msbuild/msbuild-task.md) a podmíněně nezadali různé vlastnosti pro každý projekt v seznamu položek.

 MSBuild 3.5 však poskytuje dvě nové položky vyhrazených metadat, Vlastnosti a AdditionalProperties, které poskytují flexibilní způsob, jak předat různé vlastnosti pro různé projekty vytvářené pomocí [úkolu MSBuild](../msbuild/msbuild-task.md).

> [!NOTE]
> Tyto nové položky metadat se vztahují pouze na položky předané v atributu Projekty [úlohy MSBuild](../msbuild/msbuild-task.md).

## <a name="multi-processor-build-benefits"></a>Výhody sestavení s více procesory

 K hlavní výhodě použití těchto nových metadat dochází při paralelním vytváření projektů v systému s více procesory. Metadata umožňují konsolidovat všechny projekty do jednoho volání [úkolu MSBuild](../msbuild/msbuild-task.md) bez nutnosti provádět jakékoli dávkové nebo podmíněné úlohy MSBuild. A když zavoláte pouze jeden [úkol MSBuild](../msbuild/msbuild-task.md), všechny projekty uvedené v projects atribut bude sestaven paralelně. (Pouze pokud je `BuildInParallel=true` atribut přítomen v [úloze MSBuild](../msbuild/msbuild-task.md).) Další informace naleznete [v tématu Sestavení více projektů paralelně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="properties-metadata"></a>Metadata vlastností

 Když je zadán, metadata Vlastnosti přepíše parametr Vlastnosti úlohy, zatímco metadata [AdditionalProperties](#additionalproperties-metadata) se připojí k definicím parametru.

 Běžným scénářem je, když vytváříte více souborů řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), pouze pomocí různých konfigurací sestavení. Možná budete chtít vytvořit řešení a1 pomocí konfigurace ladění a řešení a2 pomocí konfigurace vydání. V msbuild 2.0 by tento soubor projektu vypadal takto:

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

 Pomocí metadat vlastnosti však můžete zjednodušit použití jedné [úlohy MSBuild](../msbuild/msbuild-task.md), jak ukazuje následující:

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

 \-nebo -

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

## <a name="additionalproperties-metadata"></a>Metadata Vlastností AdditionalProperties

 Zvažte následující scénář, kde vytváříte dva soubory řešení pomocí [úlohy MSBuild](../msbuild/msbuild-task.md), a to jak pomocí konfigurace release, ale jeden pomocí architektury x86 a druhý pomocí architektury ia64. V MSBuild 2.0 budete muset vytvořit více instancí [úlohy MSBuild](../msbuild/msbuild-task.md): jeden k sestavení projektu pomocí konfigurace vydání s architekturou x86, druhý pomocí konfigurace release s architekturou ia64. Soubor projektu bude vypadat takto:

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

 Pomocí metadat AdditionalProperties to můžete zjednodušit tak, abyste mohli použít jednu [úlohu MSBuild](../msbuild/msbuild-task.md) pomocí následujících možností:

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

 Následující příklad používá `MSBuild` úkol k sestavení projektů `ProjectReferences` určených kolekcí položek. Výsledné cílové výstupy jsou uloženy v kolekci `AssembliesBuiltByChildProjects` položek.

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
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
