---
title: Úloha GetFrameworkPath – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149494"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Načte cestu k [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sestavením.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `GetFrameworkPath` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 1,1, pokud je k dispozici. V opačném případě vrátí `null` .|  
|`FrameworkVersion20Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 2,0, pokud je k dispozici. V opačném případě vrátí `null` .|  
|`FrameworkVersion30Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,0, pokud je k dispozici. V opačném případě vrátí `null` .|  
|`FrameworkVersion35Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 3,5, pokud je k dispozici. V opačném případě vrátí `null` .|  
|`FrameworkVersion40Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k sestavením rozhraní .NET Framework verze 4,0, pokud je k dispozici. V opačném případě vrátí `null` .|  
|`Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k nejnovějším sestavením rozhraní, pokud jsou k dispozici. V opačném případě vrátí `null` .|  
  
## <a name="remarks"></a>Poznámky  
 Pokud [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] je nainstalováno několik verzí nástroje, vrátí tato úloha verzi, která [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] je určena ke spuštění.  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GetFrameworkPath` úlohu k uložení cesty do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `FrameworkPath` Vlastnosti.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
