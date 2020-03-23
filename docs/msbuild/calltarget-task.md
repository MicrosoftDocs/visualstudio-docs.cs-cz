---
title: Úkol CallTarget | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094556"
---
# <a name="calltarget-task"></a>CallTarget – úloha

Vyvolá zadané cíle v rámci souboru projektu.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `CallTarget` úkolu.

| Parametr | Popis |
|---------------------------| - |
| `RunEachTargetSeparately` | Volitelný `Boolean` vstupní parametr.<br /><br /> Pokud `true`je modul MSBuild volán jednou za cíl. Pokud `false`je modul MSBuild volán jednou k sestavení všech cílů. Výchozí hodnota je `false`. |
| `TargetOutputs` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupy všech vytvořených cílů. |
| `Targets` | Volitelný `String[]` parametr.<br /><br /> Určuje cíl nebo cíle, které chcete sestavit. |
| `UseResultsCache` | Volitelný `Boolean` parametr.<br /><br /> Pokud `true`je výsledek uložený v mezipaměti vrácen, pokud je k dispozici.<br /><br /> **Poznámka:** Při spuštění úlohy MSBuild je její výstup uložen do mezipaměti v oboru (ProjectFileName, GlobalProperties)[TargetNames] jako seznam položek sestavení. |

## <a name="remarks"></a>Poznámky

 Pokud cíl zadaný v aplikaci `Targets` se nezdaří a `RunEachTargetSeparately` je `true`, úkol pokračuje v vytváření zbývajících cílů.

 Pokud chcete vytvořit výchozí cíle, použijte [úlohu MSBuild](../msbuild/msbuild-task.md) a nastavte `Projects` parametr rovný . `$(MSBuildProjectFile)`

Při `CallTarget`použití MSBuild vyhodnotí volaný cíl v novém oboru, na rozdíl od stejného oboru, ze který je volán. To znamená, že všechny změny položky a vlastnosti v volaný cíl nejsou viditelné pro volající cíl.  Chcete-li předat informace volajícímu `TargetOutputs` cíli, použijte výstupní parametr.

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad `TargetA` volání `CallOtherTargets`zevnitř .

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Cíle](../msbuild/msbuild-targets.md)
