---
title: Úloha CreateProperty – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea16950e47760e89204503413fd98811e781d059
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184048"
---
# <a name="createproperty-task"></a>CreateProperty – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Naplní vlastnosti pomocí předaných hodnot. To umožňuje zkopírování hodnot z jedné vlastnosti nebo řetězce do jiného.  
  
## <a name="attributes"></a>Atributy  
 Následující tabulka popisuje parametry `CreateProperty` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Value`|Volitelný `String` výstupní parametr.<br /><br /> Určuje hodnotu, která má být zkopírována do nové vlastnosti.|  
|`ValueSetByTask`|Volitelný `String` výstupní parametr.<br /><br /> Obsahuje stejnou hodnotu jako `Value` parametr. Tento parametr použijte pouze v případě, že chcete zabránit tomu, aby vlastnost Output byla nastavena, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] když přeskočí nadřazený cíl, protože výstupy jsou aktuální.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `CreateProperty` úlohu k vytvoření `NewFile` vlastnosti pomocí kombinace hodnot `SourceFilename` `SourceFileExtension` vlastnosti a.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Po spuštění projektu `NewFile` je hodnota vlastnosti `Module1.vb` .  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)
