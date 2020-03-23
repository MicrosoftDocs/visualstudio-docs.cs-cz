---
title: Přiřazení úlohy Konfigurace projektu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: b5159b73058c73c925cae644c2e3ddd2bc84ac41
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634549"
---
# <a name="assignprojectconfiguration-task"></a>Přiřazení úkolu Konfigurace projektu

Tato úloha přijme konfigurační řetězce seznamu a přiřadí je k určeným projektům.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `AssignProjectConfiguration` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`SolutionConfigurationContents`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje řetězec XML obsahující konfiguraci projektu pro každý projekt. Konfigurace jsou přiřazeny k pojmenovaným projektům.|
|`DefaultToVcxPlatformMapping`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje seznam mapování oddělených středníkem z názvů platforem používaných většinou typů na názvy používanými soubory *.vcxproj.*<br /><br /> Například:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Nepovinné<br /><br /> `string`výstupního parametru.<br /><br /> Obsahuje seznam mapování oddělených středníkem od názvů platformy *.vcxproj* až po názvy platforem, které používá většina typů.<br /><br /> Například:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje konfiguraci pro aktuální projekt.|
|`CurrentProjectPlatform`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje platformu pro aktuální projekt.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Volitelný `bool` výstupní parametr.<br /><br /> Obsahuje příznak označující, že odkazy by měly být vytvořeny i v případě, že byly zakázány v konfiguraci projektu.|
|`ShouldUnsetParentConfigurationAndPlatform`|Volitelný `bool` výstupní parametr.<br /><br /> Obsahuje příznak označující, pokud by měla být odstavena nadřazená konfigurace a platforma.|
|`OutputType`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje typ výstupu pro projekt.|
|`ResolveConfigurationPlatformUsingMappings`|Volitelný `bool` výstupní parametr.<br /><br /> Obsahuje příznak označující, pokud sestavení by měl použít výchozí mapování k vyřešení konfigurace a platformy předané v odkazech na projekt.|
|`AssignedProjects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam vyřešených referenčních cest.|
|`UnassignedProjects`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam položek odkazu na projekt, které nebylo možné vyřešit pomocí předem vyřešeného seznamu výstupů.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
