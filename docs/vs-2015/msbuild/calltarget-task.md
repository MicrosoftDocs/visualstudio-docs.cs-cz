---
title: Calltarget – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc3c5822732a4ae584500bfe1c48d7ba9e29b038
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307674"
---
# <a name="calltarget-task"></a>CallTarget – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vyvolá zadané cílů v rámci souboru projektu.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `CallTarget` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Volitelné `Boolean` výstupní parametr.<br /><br /> Pokud `true`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] modul se volá jednou pro každý cíl. Pokud `false`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] modul se volá jednou pro všechny cíle sestavení. Výchozí hodnota je `false`.|  
|`TargetOutputs`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje výstupy sestavených cílů všechny.|  
|`Targets`|Volitelné `String[]` parametru.<br /><br /> Určuje cíl nebo cíle sestavení.|  
|`UseResultsCache`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, výsledky uložené v mezipaměti je vrácena, pokud jsou k dispozici.<br /><br /> **Poznámka:** při MSBuild – úloha běží, výstup se uloží do mezipaměti v oboru (ProjectFileName, GlobalProperties) [TargetNames] jako seznam položek sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadaný cíl v `Targets` selže a `RunEachTargetSeparately` je `true`, úloha pokračuje na zbývající cíle sestavení.  
  
 Pokud chcete k sestavení výchozích cílů, použijte [úlohy nástroje MSBuild](../msbuild/msbuild-task.md) a nastavit `Projects` parametr roven `$(MSBuildProjectFile)`.  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad volá `TargetA` z uvnitř `CallOtherTargets`.  
  
```  
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
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Cíle](../msbuild/msbuild-targets.md)



