---
title: Úloha AssignProjectConfiguration – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95f61858bfcdf0f54c4f786e1b1064707b57c68c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593444"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration – – úloha
Tato úloha přijme konfigurační řetězce seznamu a přiřadí je zadaným projektům.

## <a name="task-parameters"></a>Parametry úlohy
 Následující tabulka popisuje parametry úlohy `AssignProjectConfiguration`.

|Parametr|Popis|
|---------------|-----------------|
|`SolutionConfigurationContents`|Volitelný výstupní parametr `string`.<br /><br /> Obsahuje řetězec XML obsahující konfiguraci projektu pro každý projekt. Konfigurace jsou přiřazeny k pojmenovaným projektům.|
|`DefaultToVcxPlatformMapping`|Volitelný výstupní parametr `string`.<br /><br /> Obsahuje seznam mapování z názvů platforem používaných většinou středníkem oddělených typů na ty, které jsou používány soubory *vcxproj* .<br /><br /> Příklad:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Volitelné<br /><br /> výstupní parametr `string`.<br /><br /> Obsahuje seznam mapování od středníkem oddělených názvů platforem z *. vcxproj* názvy platforem, které používá většina typů.<br /><br /> Příklad:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Volitelný výstupní parametr `string`.<br /><br /> Obsahuje konfiguraci pro aktuální projekt.|
|`CurrentProjectPlatform`|Volitelný výstupní parametr `string`.<br /><br /> Obsahuje platformu pro aktuální projekt.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Volitelný výstupní parametr `bool`.<br /><br /> Obsahuje příznak označující, že by měly být vytvořeny odkazy i v případě, že byly zakázány v konfiguraci projektu.|
|`ShouldUnsetParentConfigurationAndPlatform`|Volitelný výstupní parametr `bool`.<br /><br /> Obsahuje příznak označující, zda by měla být nastavená nadřazená konfigurace a platforma.|
|`OutputType`|Volitelný výstupní parametr `string`.<br /><br /> Obsahuje typ výstupu projektu.|
|`ResolveConfigurationPlatformUsingMappings`|Volitelný výstupní parametr `bool`.<br /><br /> Obsahuje příznak označující, zda má sestavení použít výchozí mapování k překladu konfigurace a platformy předaných odkazů na projekt.|
|`AssignedProjects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje seznam vyřešených cest odkazů.|
|`UnassignedProjects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje seznam položek odkazů projektu, které nelze přeložit pomocí předem vyřešeného seznamu výstupů.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
