---
title: Prvek úlohy usingtask (MSBuild) | Dokumenty společnosti Microsoft
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
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263185"
---
# <a name="task-element-of-usingtask-msbuild"></a>Prvek úlohy UsingTask (MSBuild)

Obsahuje data, která je `UsingTask` `TaskFactory`předána . Další informace naleznete [v tématu UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Projekt \<> pomocí \<> úkolu> úkolů

## <a name="syntax"></a>Syntaxe

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Evaluate`|Volitelný logický atribut.<br /><br /> Pokud `true`, MSBuild vyhodnotí všechny vnitřní prvky a rozbalí `TaskFactory` položky a vlastnosti před tím, než předá informace při vytvoření instance úlohy.|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Data|Text mezi `Task` značkami je doslovně `TaskFactory`odeslán do .|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Poskytuje způsob, jak zaregistrovat úkoly v MSBuild. V projektu může `UsingTask` být nula nebo více prvků. |

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak `Task` používat `Evaluate` prvek s atributem.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
