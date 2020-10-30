---
title: Element parametru | Microsoft Docs
description: Přečtěte si o elementu parametrů MSBuild, který obsahuje volitelný seznam parametrů přítomných v úloze vygenerované UsingTask TaskFactory.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 104a7313104e194a85d9eb4fee00e84a8facb5b5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048868"
---
# <a name="parametergroup-element"></a>ParameterGroup – element

Obsahuje volitelný seznam parametrů, které budou přítomny u úlohy vygenerované pomocí `UsingTask` `TaskFactory` . Další informace naleznete v tématu [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Parametr](../msbuild/parameter-element.md)|Obsahuje informace o konkrétním parametru pro úkol, který je generován pomocí `UsingTask` `TaskFactory` . Název prvku je název parametru.|

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Poskytuje způsob, jak registrovat úlohy v nástroji MSBuild. V projektu může být nula nebo více `UsingTask` prvků. |

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak použít `ParameterGroup` element.

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
