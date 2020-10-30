---
title: Error – element (MSBuild) | Microsoft Docs
description: Přečtěte si, jak MSBuild používá element Error k provedení jednoho nebo více cílů, pokud má atribut ContinueOnError hodnotu false pro neúspěšnou úlohu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c3793dddf62f67d1c2ff75d8df863dadfdadb7a1
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048945"
---
# <a name="onerror-element-msbuild"></a>Error – element (MSBuild)

Způsobí provedení jednoho nebo více cílů, pokud `ContinueOnError` je atribut `false` pro neúspěšnou úlohu.

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Syntax

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Požadovaný atribut.<br /><br /> Cíle, které se mají provést, pokud se úloha nezdařila Více cílů oddělte středníkem. V zadaném pořadí je spuštěno více cílů.|

### <a name="child-elements"></a>Podřízené prvky

 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

| Element | Popis |
| - | - |
| [Cílové](../msbuild/target-element-msbuild.md) | Element kontejneru pro úlohy MSBuild |

## <a name="remarks"></a>Poznámky

 Nástroj MSBuild spustí `OnError` prvek v případě, že jedna z `Target` úkolů elementu se nezdařila s `ContinueOnError` atributem nastaveným na `ErrorAndStop` (nebo `false` ). Pokud se úloha nezdařila, cíle zadané v `ExecuteTargets` atributu se spustí. Pokud je v cíli více než jeden `OnError` prvek, `OnError` prvky jsou spouštěny postupně, pokud se úloha nezdařila.

 Informace o atributu naleznete `ContinueOnError` v tématu [element Task (MSBuild)](../msbuild/task-element-msbuild.md). Informace o cílech najdete v tématu [cíle](../msbuild/msbuild-targets.md).

## <a name="example"></a>Příklad

 Následující kód provede `TaskOne` `TaskTwo` úlohy a. Pokud `TaskOne` se operace nezdařila, MSBuild vyhodnotí `OnError` prvek a provede `OtherTarget` cíl.

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

- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Targets](../msbuild/msbuild-targets.md)
