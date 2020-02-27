---
title: Element parametru | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7c4fa5d093952eefc870aded3d3e14a1f5983a7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633002"
---
# <a name="parameter-element"></a>Element parametru

Obsahuje informace o konkrétním parametru pro úkol, který je generován `TaskFactory``UsingTask`.  Název prvku je název parametru.  Další informace naleznete v tématu [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<projektu > \<UsingTask > \<parametru > \<parametr >

## <a name="syntax"></a>Syntaxe

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`ParameterType`|Nepovinný atribut.<br /><br /> Typ rozhraní .NET parametru, například `System.String`.|
|`Output`|Volitelný logický atribut.<br /><br /> Pokud je `true`, tento parametr je parametrem Output pro úlohu. Výchozí hodnota je `false`.|
|`Required`|Volitelný logický atribut.<br /><br /> Pokud `true`, tento parametr je pro úlohu povinný. Výchozí hodnota je `false`.|

### <a name="child-elements"></a>Podřízené prvky

 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|[ParameterGroup –](../msbuild/parametergroup-element.md)|Obsahuje volitelný seznam parametrů, které budou k dispozici u úlohy vygenerované `TaskFactory``UsingTask`.|

## <a name="example"></a>Příklad

 Následující příklad ukazuje použití prvku `Parameter`.

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
