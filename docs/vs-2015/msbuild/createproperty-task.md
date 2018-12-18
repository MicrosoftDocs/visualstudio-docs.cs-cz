---
title: CreateProperty – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 3c18288e5088871703605da4915786486e2e864b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267654"
---
# <a name="createproperty-task"></a>CreateProperty – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Naplní hodnoty předané vlastnosti. Díky tomu hodnoty zkopírovány z jedné vlastnosti nebo řetězec do druhého.  
  
## <a name="attributes"></a>Atributy  
 Následující tabulka popisuje parametry `CreateProperty` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Value`|Volitelné `String` výstupní parametr.<br /><br /> Určuje hodnotu zkopírujte do nové vlastnosti.|  
|`ValueSetByTask`|Volitelné `String` výstupní parametr.<br /><br /> Obsahuje stejnou hodnotu jako `Value` parametru. Tento parametr použijte jenom v případě, že chcete, abyste se vyhnuli nutnosti nastavit vlastnost výstupu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] při vynechává ohraničující cíl protože výstupy jsou aktuální.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `CreateProperty` úkolu k vytvoření `NewFile` vlastnost pomocí kombinace hodnot `SourceFilename` a `SourceFileExtension` vlastnost.  
  
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
  
 Po spuštění projektu, hodnota `NewFile` vlastnost `Module1.vb`.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)



