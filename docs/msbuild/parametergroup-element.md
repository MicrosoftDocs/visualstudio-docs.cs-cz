---
title: Element parametru | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28d6def203a819d41a420899663d1a974612c631
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632989"
---
# <a name="parametergroup-element"></a>Element Parameter

Obsahuje volitelný seznam parametrů, které budou k dispozici u úlohy vygenerované `TaskFactory``UsingTask`. Další informace naleznete v tématu [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<projektu > \<UsingTask > \<parametru >

## <a name="syntax"></a>Syntaxe

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[Ukazatele](../msbuild/parameter-element.md)|Obsahuje informace o konkrétním parametru pro úkol, který je generován `TaskFactory``UsingTask`. Název prvku je název parametru.|

### <a name="parent-elements"></a>Nadřazené prvky

| Prvek | Popis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Poskytuje způsob, jak registrovat úlohy v nástroji MSBuild. V projektu může být nula nebo více `UsingTask` prvků. |

## <a name="example"></a>Příklad

 Následující příklad ukazuje použití prvku `ParameterGroup`.

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
