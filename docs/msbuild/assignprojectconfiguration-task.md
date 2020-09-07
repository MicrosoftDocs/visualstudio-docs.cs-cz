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
ms.openlocfilehash: b543af39cbcd0301da7d0d353f8f7b6fa006f7ac
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508519"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration – úloha

Tato úloha přijme konfigurační řetězce seznamu a přiřadí je zadaným projektům.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `AssignProjectConfiguration` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`ProjectReferences`|Povinný <xref:Microsoft.Build.Framework.ITaskItem> `[]` vstupní parametr.<br /><br /> Projekty, které mají být nakonfigurovány.|
|`SolutionConfigurationContents`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje řetězec XML obsahující konfiguraci projektu pro každý projekt. Konfigurace jsou přiřazeny k pojmenovaným projektům.|
|`DefaultToVcxPlatformMapping`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje seznam mapování z názvů platforem používaných většinou středníkem oddělených typů na ty, které jsou používány soubory *vcxproj* .<br /><br /> Příklad:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Nepovinné<br /><br /> `string` výstupní parametr<br /><br /> Obsahuje seznam mapování od středníkem oddělených názvů platforem z *. vcxproj* názvy platforem, které používá většina typů.<br /><br /> Příklad:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje konfiguraci pro aktuální projekt.|
|`CurrentProjectPlatform`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje platformu pro aktuální projekt.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Volitelný `bool` výstupní parametr.<br /><br /> Obsahuje příznak označující, že by měly být vytvořeny odkazy i v případě, že byly zakázány v konfiguraci projektu.|
|`ShouldUnsetParentConfigurationAndPlatform`|Volitelný `bool` výstupní parametr.<br /><br /> Obsahuje příznak označující, zda by měla být nastavená nadřazená konfigurace a platforma.|
|`OutputType`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje typ výstupu projektu.|
|`ResolveConfigurationPlatformUsingMappings`|Volitelný `bool` výstupní parametr.<br /><br /> Obsahuje příznak označující, zda má sestavení použít výchozí mapování k překladu konfigurace a platformy předaných odkazů na projekt.|
|`AssignedProjects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam vyřešených cest odkazů.|
|`UnassignedProjects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam položek odkazů projektu, které nelze přeložit pomocí předem vyřešeného seznamu výstupů.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
