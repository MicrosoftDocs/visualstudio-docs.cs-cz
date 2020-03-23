---
title: Zrušit registraci Úloha sestavení | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631494"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly – úloha

Zruší registraci zadaných sestavení pro účely interop com. Provede opak [úlohy RegisterAssembly](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `UnregisterAssembly` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Assemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje sestavení, která mají být neregistrována.|
|`AssemblyListFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Obsahuje informace o stavu `RegisterAssembly` mezi `UnregisterAssembly` úkolem a úkolem. To zabrání úlohy z pokusu o zrušení registrace sestavení, které se nepodařilo zaregistrovat v úloze. `RegisterAssembly`<br /><br /> Pokud je tento parametr `Assemblies` `TypeLibFiles` zadán, a parametry jsou ignorovány.|
|`TypeLibFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Zruší registraci zadané knihovny typů ze zadaného sestavení. **Poznámka:**  Tento parametr je nutný pouze v případě, že název souboru knihovny typů se liší od názvu sestavení.|

## <a name="remarks"></a>Poznámky

 Není nutné, aby sestavení existuje pro tento úkol, aby byl úspěšný. Pokud se pokusíte zrušit registraci sestavení, které neexistuje, úloha bude úspěšná s upozorněním. K tomu dochází, protože je úlohou tohoto úkolu odebrat registraci sestavení z registru. Pokud sestavení neexistuje, není v registru, a proto úkol proběhl úspěšně.

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> parametry z třídy, <xref:System.MarshalByRefObject> která sama dědí z třídy. Třída `MarshalByRefObject` poskytuje stejné funkce jako <xref:Microsoft.Build.Utilities.Task> třída, ale může být vytvořena instance ve vlastní doméně aplikace.

## <a name="example"></a>Příklad

 Následující příklad používá `UnregisterAssembly` úkol k zrušení registrace sestavení na `OutputPath` `FileName` cestě určené vlastnostmi a, pokud existuje.

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

- [Úkol RegisterAssembly](../msbuild/registerassembly-task.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)