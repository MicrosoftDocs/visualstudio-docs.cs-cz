---
title: Calltarget – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4546fc47ddb38fabcd0ff84926d942f6ae10d59e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874680"
---
# <a name="calltarget-task"></a>CallTarget – úloha
Vyvolá zadané cílů v rámci souboru projektu.  

## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `CallTarget` úloh.  


| Parametr | Popis |
|---------------------------| - |
| `RunEachTargetSeparately` | Volitelné `Boolean` vstupního parametru.<br /><br /> Pokud `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] modul se volá jednou pro každý cíl. Pokud `false`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] modul se volá jednou pro všechny cíle sestavení. Výchozí hodnota je `false`. |
| `TargetOutputs` | Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupy sestavených cílů všechny. |
| `Targets` | Volitelné `String[]` parametru.<br /><br /> Určuje cíl nebo cíle sestavení. |
| `UseResultsCache` | Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, výsledky uložené v mezipaměti je vrácena, pokud jsou k dispozici.<br /><br /> **Poznámka:** při MSBuild – úloha běží, výstup se uloží do mezipaměti v oboru (ProjectFileName, GlobalProperties) [TargetNames] jako seznam položek sestavení. |

## <a name="remarks"></a>Poznámky  
 Pokud zadaný cíl v `Targets` selže a `RunEachTargetSeparately` je `true`, úloha pokračuje na zbývající cíle sestavení.  

 Pokud chcete k sestavení výchozích cílů, použijte [úlohy nástroje MSBuild](../msbuild/msbuild-task.md) a nastavit `Projects` parametr roven `$(MSBuildProjectFile)`.  

 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  

## <a name="example"></a>Příklad  
 Následující příklad volá `TargetA` z uvnitř `CallOtherTargets`.  

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
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Cíle](../msbuild/msbuild-targets.md)