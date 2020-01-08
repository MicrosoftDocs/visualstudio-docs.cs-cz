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
ms.openlocfilehash: 1bad6ab828af1f62818636b3af11232294256c03
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593379"
---
# <a name="calltarget-task"></a>CallTarget – úloha
Vyvolá zadané cíle v rámci souboru projektu.

## <a name="task-parameters"></a>Parametry úlohy
 Následující tabulka popisuje parametry úlohy `CallTarget`.

| Parametr | Popis |
|---------------------------| - |
| `RunEachTargetSeparately` | Volitelný vstupní parametr `Boolean`.<br /><br /> Pokud `true`, modul [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se pro každý cíl zavolá jednou. Pokud `false`, modul [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se volá jednou pro sestavení všech cílů. Výchozí hodnota je `false`. |
| `TargetOutputs` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje výstupy všech sestavených cílů. |
| `Targets` | Volitelný parametr `String[]`.<br /><br /> Určuje cíl nebo cíle, které se mají sestavit. |
| `UseResultsCache` | Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, vrátí výsledek uložený v mezipaměti, pokud je k dispozici.<br /><br /> **Poznámka:** Je-li spuštěn úkol MSBuild, jeho výstup je uložen do mezipaměti v oboru (ProjectFileName, GlobalProperties) [Cílový_názevs] jako seznam položek sestavení. |

## <a name="remarks"></a>Poznámky
 Pokud cíl zadaný v `Targets` selhává a `RunEachTargetSeparately` je `true`, úloha pokračuje v sestavování zbývajících cílů.

 Pokud chcete sestavit výchozí cíle, použijte [úlohu MSBuild](../msbuild/msbuild-task.md) a nastavte parametr `Projects` na hodnotu `$(MSBuildProjectFile)`.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad volá `TargetA` zevnitř `CallOtherTargets`.

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

## <a name="see-also"></a>Viz také:
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Cíle](../msbuild/msbuild-targets.md)
