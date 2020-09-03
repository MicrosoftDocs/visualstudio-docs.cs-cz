---
title: Output – element (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90fbd517608c9c36db0b1035f296b9d9402abddd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633028"
---
# <a name="output-element-msbuild"></a>Output – element (MSBuild)

Ukládá výstupní hodnoty úkolu do položek a vlastností.

 \<Project> \<Target>
 \<Task>
 \<Output>

## <a name="syntax"></a>Syntax

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`TaskParameter`|Požadovaný atribut.<br /><br /> Název výstupního parametru úkolu.|
|`PropertyName`|Buď `PropertyName` `ItemName` je vyžadován atribut nebo.<br /><br /> Vlastnost, která obdrží hodnotu výstupního parametru úkolu. Projekt pak může odkazovat na vlastnost pomocí syntaxe $ ( \<PropertyName> ). Tento název vlastnosti může být buď nový název vlastnosti, nebo název, který je již definován v projektu.<br /><br /> Tento atribut nelze použít `ItemName` , je-li použit také.|
|`ItemName`|Buď `PropertyName` `ItemName` je vyžadován atribut nebo.<br /><br /> Položka, která obdrží hodnotu výstupního parametru úkolu. Projekt pak může odkazovat na položku pomocí syntaxe @ ( \<ItemName> ). Název položky může být buď název nové položky, nebo název, který je již definován v projektu. Pokud je název položky existující položka, hodnoty výstupních parametrů se přidají do existující položky. <br /><br /> Tento atribut nelze použít `PropertyName` , je-li použit také.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Úkol](../msbuild/task-element-msbuild.md) | Vytvoří a spustí instanci úlohy MSBuild. |

## <a name="example"></a>Příklad

 Následující příklad kódu ukazuje úlohu prováděnou `Csc` v rámci `Target` elementu. Položky a vlastnosti předané parametrům úlohy jsou deklarovány mimo rozsah tohoto příkladu. Hodnota z výstupního parametru `OutputAssembly` je uložena v `FinalAssemblyName` položce a hodnota z výstupního parametru `BuildSucceeded` je uložena ve `BuildWorked` Vlastnosti. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
