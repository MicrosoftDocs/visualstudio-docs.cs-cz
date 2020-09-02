---
title: Úloha AssignTargetPath – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7bf12e9f6c90ce544205370a8ed26440388b0a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187014"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato úloha přijme seznam souborů a přidá `<TargetPath>` atributy, pokud již nejsou zadány.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `AssignTargetPath` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`RootFolder`|Volitelný `string` vstupní parametr.<br /><br /> Obsahuje cestu ke složce, která obsahuje cílové odkazy.|  
|`Files`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` vstupní parametr.<br /><br /> Obsahuje seznam příchozích souborů.|  
|`AssignedFiles`|Volitelné<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`výstupní parametr<br /><br /> Obsahuje výsledný seznam souborů.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad spustí `AssignTargetPath` úlohu pro konfiguraci projektu.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
