---
title: Resolvemanifestfiles – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82b265bc46e4d8edac666b4f73d5256e524f5b08
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151547"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles – úloha
Řeší následující položky v procesu sestavení k souborům pro generování manifestu: vytvořené položky, závislosti, satelity, obsah, symboly ladění a dokumentaci.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `ResolveManifestFiles` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje název manifestu nasazení.|  
|`EntryPoint`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje spravované sestavení nebo odkaz na manifest ClickOnce, která je vstupním bodem k manifestu.|  
|`ExtraFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje další soubory.|  
|`ManagedAssemblies`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje spravovaná sestavení.|  
|`NativeAssemblies`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje nativní sestavení.|  
|`OutputAssemblies`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje vygenerované sestavení.|  
|`OutputDeploymentManifestEntryPoint`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje výstupní nasazení manifestu vstupní bod.|  
|`OutputEntryPoint`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje výstupní vstupní bod.|  
|`OutputFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje výstupní soubory.|  
|`PublishFiles`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje soubory publikovat.|  
|`SatelliteAssemblies`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje, že satelitní sestavení.|  
|`SigningManifests`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, jsou podepsané manifesty.|  
|`TargetCulture`|Volitelné `String` parametru.<br /><br /> Určuje cílové jazykové verzi pro satelitní sestavení.|  
|`TargetFrameworkVersion`|Volitelné `String` parametru.<br /><br /> Určuje cílovou verzi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě s parametry, které jsou uvedené v tabulce, zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)