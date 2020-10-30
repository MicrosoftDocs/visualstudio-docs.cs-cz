---
title: Element Task cíle (MSBuild) | Microsoft Docs
description: Přečtěte si o elementu Task of MSBuild cíl, který vytvoří a spustí instanci úlohy MSBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 58ac6b02424da40ba1130d8a1b549886c9efd718
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047965"
---
# <a name="task-element-of-target-msbuild"></a>Element Task cíle (MSBuild)

Vytvoří a spustí instanci úlohy MSBuild. Název elementu je určen názvem vytvářeného úkolu.

 \<Project> \<Target>

## <a name="syntax"></a>Syntax

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
|`ContinueOnError`|Nepovinný atribut. Může obsahovat jednu z následujících hodnot:<br /><br /> -   **WarnAndContinue** nebo **true** . Pokud se úloha nezdařila, následné úkoly v [cílovém](../msbuild/target-element-msbuild.md) elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za upozornění.<br />-   **ErrorAndContinue** . Pokud se úloha nezdařila, následné úkoly v `Target` elementu a sestavení se budou dále spouštět a všechny chyby z tohoto úkolu jsou považovány za chyby.<br />-   **ErrorAndStop** nebo **false** (výchozí). Pokud se úloha nepovede, zbývající úkoly v `Target` elementu a sestavení se nezpracují a celý `Target` element a sestavení se považuje za neúspěšné.<br /><br /> Verze .NET Framework před 4,5 podporovaly pouze `true` `false` hodnoty a.<br /><br /> Další informace najdete v tématu [Postupy: ignorování chyb v úlohách](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Vyžaduje se, pokud třída Task obsahuje jednu nebo více vlastností, které jsou označeny `[Required]` atributem.<br /><br /> Uživatelsky definovaný parametr úkolu, který obsahuje hodnotu parametru jako hodnotu. V elementu může být libovolný počet parametrů `Task` , přičemž každý atribut je mapován na vlastnost .NET ve třídě Task.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Výstup](../msbuild/output-element-msbuild.md)|Ukládá výstupy z úkolu v souboru projektu. V úkolu může být nula nebo více `Output` prvků.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Cílové](../msbuild/target-element-msbuild.md) | Element kontejneru pro úlohy MSBuild |

## <a name="remarks"></a>Poznámky

 `Task`Element v souboru projektu MSBuild vytvoří instanci úlohy, nastaví v ní vlastnosti a provede ji. `Output`Element ukládá výstupní parametry do vlastností nebo položek, které mají být použity jinde v souboru projektu.

 Pokud v nadřazeném [OnError](../msbuild/onerror-element-msbuild.md) elementu úlohy existují nějaké prvky Error `Target` , budou vyhodnoceny i v případě, že úloha selže a `ContinueOnError` má hodnotu `false` . Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Příklad

 Následující příklad kódu vytvoří instanci třídy [úlohy CSC](../msbuild/csc-task.md) , nastaví šest vlastností a spustí úlohu. Po spuštění se hodnota `OutputAssembly` vlastnosti objektu umístí do seznamu položek s názvem `FinalAssemblyName` .

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

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
