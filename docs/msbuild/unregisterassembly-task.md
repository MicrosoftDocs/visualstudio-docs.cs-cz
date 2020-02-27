---
title: Úloha UnregisterAssembly – | Microsoft Docs
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
ms.openlocfilehash: 2f8cddcf9bf0632914d1a6de1cc904dbf0f173e6
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631494"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly – úloha

Zruší registraci zadaných sestavení pro účely zprostředkovatele komunikace s objekty COM. Provede obrácenou [úlohu RegisterAssembly –](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `UnregisterAssembly`.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje sestavení, která mají být odregistrována.|
|`AssemblyListFile`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Obsahuje informace o stavu mezi úlohou `RegisterAssembly` a úlohou `UnregisterAssembly`. To brání úloze v pokusu o zrušení registrace sestavení, které selhalo při registraci do úlohy `RegisterAssembly`.<br /><br /> Pokud je tento parametr zadán, parametry `Assemblies` a `TypeLibFiles` jsou ignorovány.|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Zruší registraci zadané knihovny typů ze zadaného sestavení. **Poznámka:**  Tento parametr je nezbytný pouze v případě, že název souboru knihovny typů je jiný než název sestavení.|

## <a name="remarks"></a>Poznámky

 Není nutné, aby sestavení existovalo pro úspěšnou úlohu. Pokud se pokusíte zrušit registraci sestavení, které neexistuje, úloha bude úspěšně provedena s upozorněním. K tomu dochází, protože se jedná o úlohu této úlohy, která odebere registraci sestavení z registru. Pokud sestavení neexistuje, není v registru, a proto úloha byla úspěšná.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> třídy, které sama dědí z <xref:System.MarshalByRefObject> třídy. Třída `MarshalByRefObject` poskytuje stejné funkce jako <xref:Microsoft.Build.Utilities.Task> třída, ale je možné ji vytvořit ve své vlastní doméně aplikace.

## <a name="example"></a>Příklad

 Následující příklad používá úlohu `UnregisterAssembly` k zrušení registrace sestavení v cestě určené vlastností `OutputPath` a `FileName`, pokud existuje.

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

- [RegisterAssembly – – úloha](../msbuild/registerassembly-task.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)