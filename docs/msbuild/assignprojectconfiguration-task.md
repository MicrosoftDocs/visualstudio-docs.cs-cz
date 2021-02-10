---
title: Úloha AssignProjectConfiguration – | Microsoft Docs
description: Pomocí úlohy MSBuild AssignProjectConfiguration – můžete přijmout seznam konfiguračních řetězců a přiřadit je ke zadaným projektům.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18dab3d34f4c1c11fa2c212f12ca875cb1b7f3b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964950"
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
|`VcxToDefaultPlatformMapping`|Volitelné<br /><br /> `string` výstupní parametr<br /><br /> Obsahuje seznam mapování od středníkem oddělených názvů platforem z *. vcxproj* názvy platforem, které používá většina typů.<br /><br /> Příklad:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
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
