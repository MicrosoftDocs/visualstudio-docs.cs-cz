---
title: Úloha CallTarget – | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094556"
---
# <a name="calltarget-task"></a>CallTarget – úloha

Vyvolá zadané cíle v rámci souboru projektu.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `CallTarget` úkolu.

| Parametr | Popis |
|---------------------------| - |
| `RunEachTargetSeparately` | Volitelný `Boolean` vstupní parametr.<br /><br /> Pokud `true` je modul MSBuild volán jednou pro každý cíl. Pokud `false` je modul MSBuild volán jednou pro sestavení všech cílů. Výchozí hodnota je `false`. |
| `TargetOutputs` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupy všech sestavených cílů. |
| `Targets` | Volitelný `String[]` parametr.<br /><br /> Určuje cíl nebo cíle, které se mají sestavit. |
| `UseResultsCache` | Volitelný `Boolean` parametr.<br /><br /> `true`Je-li k dispozici, vrátí výsledek uložený v mezipaměti.<br /><br /> **Poznámka:** Je-li spuštěn úkol MSBuild, jeho výstup je uložen do mezipaměti v oboru (ProjectFileName, GlobalProperties) [Cílový_názevs] jako seznam položek sestavení. |

## <a name="remarks"></a>Poznámky

 Pokud cíl zadaný v poli `Targets` selhává a `RunEachTargetSeparately` je `true` , úloha pokračuje v sestavování zbývajících cílů.

 Pokud chcete sestavit výchozí cíle, použijte [úlohu MSBuild](../msbuild/msbuild-task.md) a nastavte `Projects` parametr Equal `$(MSBuildProjectFile)` .

Při použití nástroje `CallTarget` MSBuild vyhodnotí pojmenovaný cíl v novém oboru, nikoli na stejný obor, ze kterého se volá. To znamená, že jakákoli položka a změny vlastností v volaném cíli nejsou viditelné pro volající cíl.  Chcete-li předat informace do cíle volání, použijte `TargetOutputs` výstupní parametr.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad volá `TargetA` zevnitř `CallOtherTargets` .

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

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Targets](../msbuild/msbuild-targets.md)
