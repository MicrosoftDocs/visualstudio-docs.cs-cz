---
title: Úloha UnregisterAssembly – | Microsoft Docs
description: Zjistěte, jak MSBuild pomocí úlohy UnregisterAssembly – zruší registraci zadaných sestavení pro účely zprostředkovatele komunikace s objekty COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 068073b2d84d95ad3d86abe582691be0dd4af895
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046924"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly – úloha

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

```xml
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

- [RegisterAssembly – úloha](../msbuild/registerassembly-task.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)