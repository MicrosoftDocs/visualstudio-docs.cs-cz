---
title: Úloha UnregisterAssembly – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ef7ef7f4ec930b8aa338a8be33c4009b3009b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193239"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zruší registraci zadaných sestavení pro účely zprostředkovatele komunikace s objekty COM. Provede obrácenou [úlohu RegisterAssembly –](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `UnregisterAssembly` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje sestavení, která mají být odregistrována.|  
|`AssemblyListFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Obsahuje informace o stavu mezi `RegisterAssembly` úkolem a `UnregisterAssembly` úkolem. To brání úloze v pokusu o zrušení registrace sestavení, které selhalo při registraci v `RegisterAssembly` úloze.<br /><br /> Pokud je tento parametr zadán, `Assemblies` parametry a `TypeLibFiles` jsou ignorovány.|  
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Zruší registraci zadané knihovny typů ze zadaného sestavení. **Poznámka:**  Tento parametr je nezbytný pouze v případě, že název souboru knihovny typů je jiný než název sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Není nutné, aby sestavení existovalo pro úspěšnou úlohu. Pokud se pokusíte zrušit registraci sestavení, které neexistuje, úloha bude úspěšně provedena s upozorněním. K tomu dochází, protože se jedná o úlohu této úlohy, která odebere registraci sestavení z registru. Pokud sestavení neexistuje, není v registru, a proto úloha byla úspěšná.  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> třídy, která sama dědí z <xref:System.MarshalByRefObject> třídy. `MarshalByRefObject`Třída poskytuje stejné funkce jako <xref:Microsoft.Build.Utilities.Task> třída, ale je možné ji vytvořit ve své vlastní doméně aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `UnregisterAssembly` úlohu k zrušení registrace sestavení v cestě určené `OutputPath` `FileName` vlastnostmi a, pokud existuje.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [RegisterAssembly – – úloha](../msbuild/registerassembly-task.md)   
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
