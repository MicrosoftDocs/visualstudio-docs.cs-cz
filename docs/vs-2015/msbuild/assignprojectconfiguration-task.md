---
title: Úloha AssignProjectConfiguration – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e2091fad7e527990e8ed89ea8622cf41c1ae1ac4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187031"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato úloha přijme konfigurační řetězce seznamu a přiřadí je zadaným projektům.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `AssignProjectConfiguration` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje řetězec XML obsahující konfiguraci projektu pro každý projekt. Konfigurace jsou přiřazeny k pojmenovaným projektům.|  
|`DefaultToVcxPlatformMapping`|Volitelný `string` výstupní parametr.<br /><br /> Obsahuje seznam mapování z používaných názvů platforem oddělený středníkem.<br /><br /> podle většiny typů do těch, které jsou používány soubory vcxproj.<br /><br /> Příklad:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Volitelné<br /><br /> `string` výstupní parametr<br /><br /> Obsahuje seznam mapování od středníkem oddělených názvů platforem z. vcxproj názvy platforem, které používá většina typů.<br /><br /> Příklad:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
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
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
