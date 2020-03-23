---
title: Prvek parametru | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: dbf0c25967d84e930ee97a84709c808d3541e733
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263094"
---
# <a name="parameter-element"></a>Element parametru

Obsahuje informace o konkrétním parametru pro úkol, `UsingTask` `TaskFactory`který je generován .  Název prvku je název parametru.  Další informace naleznete [v tématu UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<> \<projektu usingTask \<> \<ParametrSkupina> parametr>

## <a name="syntax"></a>Syntaxe

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`ParameterType`|Nepovinný atribut.<br /><br /> Typ parametru .NET, `System.String`například .|
|`Output`|Volitelný logický atribut.<br /><br /> Pokud `true`je tento parametr výstupním parametrem úlohy. Výchozí hodnota je `false`.|
|`Required`|Volitelný logický atribut.<br /><br /> Pokud `true`je tento parametr povinným parametrem pro úlohu. Výchozí hodnota je `false`.|

### <a name="child-elements"></a>Podřízené prvky

 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Skupina parametrů](../msbuild/parametergroup-element.md)|Obsahuje volitelný seznam parametrů, které budou k dispozici na úkolu, který je generován `UsingTask` `TaskFactory`.|

## <a name="example"></a>Příklad

 Následující příklad ukazuje, jak `Parameter` použít prvek.

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
