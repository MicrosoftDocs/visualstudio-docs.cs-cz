---
title: Odstranit úlohu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea1411925c6858bceaea3e2e190ecb1a5f2c7f89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196544"
---
# <a name="delete-task"></a>Delete – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Odstraní zadané soubory.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Delete` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DeletedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje soubory, které se úspěšně odstranily.|  
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které se mají odstranit.|  
|`TreatErrorsAsWarnings`|Volitelný `Boolean` parametr<br /><br /> Pokud `true` jsou chyby protokolovány jako upozornění. Hodnota Defalut je `false` .|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad odstraní soubor `MyApp.pdb` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <AppName>MyApp</AppName>  
    </PropertyGroup>  
  
    <Target Name="DeleteFiles">  
        <Delete Files="$(AppName).pdb" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
