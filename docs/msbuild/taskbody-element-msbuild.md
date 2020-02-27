---
title: TaskBody – – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45b255f782390cfc478ac2f7bce58170e4e2b268
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631844"
---
# <a name="taskbody-element-msbuild"></a>TaskBody – – element (MSBuild)

Obsahuje data předávaná `UsingTask` `TaskFactory`. Další informace naleznete v tématu [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<projektu > \<UsingTask > \<TaskBody – >

## <a name="syntax"></a>Syntaxe

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Evaluate`|Volitelný logický atribut.<br /><br /> Pokud `true`, MSBuild vyhodnotí vnitřní prvky a rozbalí položky a vlastnosti před tím, než předává informace do `TaskFactory` při vytváření instance úkolu.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|Data|Text mezi značkami `TaskBody` se do `TaskFactory`pošle jako doslovné.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Poskytuje způsob, jak registrovat úlohy v nástroji MSBuild. V projektu může být nula nebo více `UsingTask` prvků. |

## <a name="example"></a>Příklad

 Následující příklad ukazuje způsob použití prvku `TaskBody` s atributem `Evaluate`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
