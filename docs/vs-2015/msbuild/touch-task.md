---
title: Dotyková úloha | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf68bf5dada310a23136e431fdaecad3e738d4bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144273"
---
# <a name="touch-task"></a>Touch – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastaví dobu přístupu a úprav souborů.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Touch` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AlwaysCreate`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vytvoří všechny soubory, které ještě neexistují.|  
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje kolekci souborů, které se mají kontaktovat.|  
|`ForceTouch`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , vynutí soubor dotykového ovládání, i když jsou soubory jen pro čtení.|  
|`Time`|Volitelný `String` parametr.<br /><br /> Určuje jiný čas než aktuální čas. Formát musí být formát, který je přijatelný pro <xref:System.DateTime.Parse%2A> metodu.|  
|`TouchedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje kolekci položek, které byly úspěšně změněny.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Touch` úlohu ke změně doby přístupu a úprav souborů zadaných v `Files` kolekci položek a umístí seznam úspěšně se retušných souborů v `FilesTouched` kolekci položek.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
