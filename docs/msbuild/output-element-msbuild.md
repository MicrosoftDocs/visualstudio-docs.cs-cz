---
title: Výstupní prvek (MSBuild) | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633028"
---
# <a name="output-element-msbuild"></a>Výstupní prvek (MSBuild)

Ukládá výstupní hodnoty úlohy do položek a vlastností.

 \<> \<výstupu \<> \<>> cíl> úkol projektu

## <a name="syntax"></a>Syntaxe

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`TaskParameter`|Požadovaný atribut.<br /><br /> Název výstupního parametru úlohy.|
|`PropertyName`|Je `PropertyName` vyžadován `ItemName` atribut or.<br /><br /> Vlastnost, která přijímá hodnotu výstupního parametru úlohy. Váš projekt pak můžete odkazovat\<na vlastnost s $( PropertyName>) syntaxe. Tento název vlastnosti může být buď nový název vlastnosti nebo název, který je již definován v projektu.<br /><br /> Tento atribut nelze `ItemName` použít, pokud je také používán.|
|`ItemName`|Je `PropertyName` vyžadován `ItemName` atribut or.<br /><br /> Položka, která obdrží hodnotu výstupního parametru úlohy. Projekt pak může odkazovat na\<položku pomocí syntaxe @( ItemName>). Název položky může být buď název nové položky nebo název, který je již definován v projektu. Pokud je název položky existující položkou, budou k existující položce přidány hodnoty výstupního parametru. <br /><br /> Tento atribut nelze `PropertyName` použít, pokud je také používán.|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Podřízené prvky

 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Úkol](../msbuild/task-element-msbuild.md) | Vytvoří a provede instanci úlohy MSBuild. |

## <a name="example"></a>Příklad

 Následující příklad kódu `Csc` ukazuje úlohu, která `Target` je prováděna uvnitř prvku. Položky a vlastnosti předané parametrům úkolu jsou deklarovány mimo rozsah tohoto příkladu. Hodnota z výstupního `OutputAssembly` parametru `FinalAssemblyName` je uložena v položce `BuildSucceeded` a hodnota `BuildWorked` z výstupního parametru je uložena ve vlastnosti. Další informace naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

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

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
