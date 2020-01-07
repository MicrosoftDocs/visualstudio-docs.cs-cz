---
title: Error – element (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: b2ddf970225d96291f76935838a743ba358eff0f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594874"
---
# <a name="onerror-element-msbuild"></a>Error – element (MSBuild)
Způsobí provedení jednoho nebo více cílů, pokud je atribut `ContinueOnError` `false` pro neúspěšnou úlohu.

 \<projektu > \<Target > \<chyba >

## <a name="syntax"></a>Syntaxe

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

| Prvek | Popis |
| - | - |
| [Cíl](../msbuild/target-element-msbuild.md) | Element kontejneru pro úlohy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Poznámky
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spustí prvek `OnError` v případě, že jeden z úkolů `Target` elementu se nezdařil s atributem `ContinueOnError` nastaveným na `ErrorAndStop` (nebo `false`). V případě, že se úloha nezdařila, cíle zadané v atributu `ExecuteTargets` jsou provedeny. Pokud je v cíli více než jeden `OnError` element, `OnError` prvky jsou spouštěny postupně, pokud se úloha nezdařila.

 Informace o atributu `ContinueOnError` naleznete v tématu [Task element (MSBuild)](../msbuild/task-element-msbuild.md). Informace o cílech najdete v tématu [cíle](../msbuild/msbuild-targets.md).

## <a name="example"></a>Příklad
 Následující kód spustí `TaskOne` a `TaskTwo` úkoly. Pokud `TaskOne` dojde k chybě, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vyhodnotí prvek `OnError` a provede cíl `OtherTarget`.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Cíle](../msbuild/msbuild-targets.md)
