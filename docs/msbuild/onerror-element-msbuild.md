---
title: OnError Element (MSBuild) | Dokumenty společnosti Microsoft
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18edfe06a4f2cb98fcb41e93c920b03c53daea8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633080"
---
# <a name="onerror-element-msbuild"></a>Prvek OnError (MSBuild)

Způsobí, že jeden nebo více `ContinueOnError` cílů `false` provést, pokud je atribut pro neúspěšný úkol.

 \<\<> \<>>> cíl> projektu

## <a name="syntax"></a>Syntaxe

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributy a prvky

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Požadovaný atribut.<br /><br /> Cíle, které mají být provedeny, pokud se úloha nezdaří. Oddělte více cílů středníky. Více cílů jsou prováděny v zadaném pořadí.|

### <a name="child-elements"></a>Podřízené prvky

 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Cíl](../msbuild/target-element-msbuild.md) | Element kontejneru pro úlohy MSBuild. |

## <a name="remarks"></a>Poznámky

 MSBuild provede `OnError` prvek, pokud `Target` jeden z úkolů prvku `ContinueOnError` selže `ErrorAndStop` s `false`atributem nastaveným na (nebo ). Pokud se úloha nezdaří, `ExecuteTargets` jsou provedeny cíle zadané v atributu. Pokud je více `OnError` než jeden prvek `OnError` v cíli, prvky jsou prováděny postupně při selhání úlohy.

 Informace o `ContinueOnError` atributu naleznete v tématu [Task element (MSBuild)](../msbuild/task-element-msbuild.md). Informace o cílech naleznete v tématu [Cíle](../msbuild/msbuild-targets.md).

## <a name="example"></a>Příklad

 Následující kód provede `TaskOne` a `TaskTwo` úkoly. Pokud `TaskOne` se nezdaří, MSBuild vyhodnotí `OnError` prvek a provede `OtherTarget` cíl.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Viz také

- [Odkaz na schéma souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Cíle](../msbuild/msbuild-targets.md)
