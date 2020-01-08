---
title: Task – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76f808c14b8459abfb3bf9c531cfff496932836c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566355"
---
# <a name="task-element-msbuild"></a>Task – element (MSBuild)
Vytvoří a spustí instanci úlohy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Název elementu je určen názvem vytvářeného úkolu.

 \<projektu > \<Target >

## <a name="syntax"></a>Syntaxe

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut. Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|Nepovinný atribut. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true**. Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue**. Pokud se úloha nezdařila, následné úkoly v prvku `Target` a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nezdařila, zbývající úkoly v prvku `Target` a sestavení nejsou provedeny a celý `Target` element a sestavení se považuje za neúspěšné.<br /><br /> Verze .NET Framework před 4,5 podporují pouze hodnoty `true` a `false`.<br /><br /> Další informace najdete v tématu [Postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Vyžaduje se, pokud třída Task obsahuje jednu nebo více vlastností, které jsou označeny atributem `[Required]`.<br /><br /> Uživatelsky definovaný parametr úkolu, který obsahuje hodnotu parametru jako hodnotu. V prvku `Task` může být libovolný počet parametrů, přičemž každý atribut je mapován na vlastnost .NET ve třídě Task.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Output](../msbuild/output-element-msbuild.md)|Ukládá výstupy z úkolu v souboru projektu. V úloze může být nula nebo více `Output` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [Cíl](../msbuild/target-element-msbuild.md) | Element kontejneru pro úlohy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Poznámky
 Prvek `Task` v souboru projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vytvoří instanci úlohy, nastaví v ní vlastnosti a provede ji. Element `Output` ukládá výstupní parametry do vlastností nebo položek, které mají být použity jinde v souboru projektu.

 Pokud jsou v nadřazené `Target` elementu úlohy nějaké prvky [Errors](../msbuild/onerror-element-msbuild.md) , budou i nadále vyhodnoceny, pokud se úloha nezdaří a `ContinueOnError` má hodnotu `false`. Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Příklad
 Následující příklad kódu vytvoří instanci třídy [úlohy CSC](../msbuild/csc-task.md) , nastaví šest vlastností a spustí úlohu. Po spuštění se hodnota vlastnosti `OutputAssembly` objektu umístí do seznamu položek s názvem `FinalAssemblyName`.

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
