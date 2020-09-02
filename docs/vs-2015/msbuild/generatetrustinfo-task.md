---
title: Úloha GenerateTrustInfo – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccbe11cefa730264e523390a0844086d6fb03ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149575"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Generuje vztah důvěryhodnosti aplikace ze základního manifestu a z `TargetZone` `ExcludedPermissions` parametrů a.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GenerateTrustInfo` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ApplicationDependencies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje závislá sestavení.|  
|`BaseManifest`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje základní manifest, ze kterého se má vygenerovat vztah důvěryhodnosti aplikace.|  
|`ExcludedPermissions`|Volitelný `String` parametr.<br /><br /> Určuje jednu nebo víc hodnot identity oprávnění oddělených středníkem, které se mají vyloučit ze sady výchozích oprávnění zóny.|  
|`TargetZone`|Volitelný `String` parametr.<br /><br /> Určuje výchozí sadu oprávnění zóny, která se získá ze zásad počítače.|  
|`TrustInfoFile`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který obsahuje informace o vztahu důvěryhodnosti zabezpečení aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
