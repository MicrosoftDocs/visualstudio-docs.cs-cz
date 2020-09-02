---
title: Úloha GetFrameworkSdkPath – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d527b00e8cbfe6a6f4ad5d112a23e46d4edb8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149560"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Načte cestu k [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] .  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `GetFrameworkSdkPath` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k sadě .NET SDK verze 2,0, pokud je k dispozici. V opačném případě vrátí `String.Empty` .|  
|`FrameworkSdkVersion35Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k sadě .NET SDK verze 3,5, pokud je k dispozici. V opačném případě vrátí `String.Empty` .|  
|`FrameworkSdkVersion40Path`|Volitelný `String` výstupní parametr jen pro čtení.<br /><br /> Vrátí cestu k sadě .NET SDK verze 4,0, pokud je k dispozici. V opačném případě vrátí `String.Empty` .|  
|`Path`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje cestu k nejnovější sadě .NET SDK, pokud je k dispozici nějaká verze. V opačném případě vrátí `String.Empty` .|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GetFrameworkSdkPath` úlohu k uložení cesty do [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] `SdkPath` Vlastnosti.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
