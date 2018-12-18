---
title: Delete – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd4e0d4aa2567656e8aa37f88b59128bb60a786c
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946183"
---
# <a name="delete-task"></a>Delete – úloha
Odstraní zadané soubory.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Delete` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DeletedFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje soubory, které byly úspěšně odstraněny.|  
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které chcete odstranit.|  
|`TreatErrorsAsWarnings`|Volitelné `Boolean` parametr<br /><br /> Pokud `true`, chyby jsou protokolovány jako upozornění. Výchozí hodnota je `false`.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad odstraní soubor *MyApp.pdb*.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <AppName>MyApp</AppName>  
    </PropertyGroup>  
  
    <Target Name="DeleteFiles">  
        <Delete Files="$(AppName).pdb" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
