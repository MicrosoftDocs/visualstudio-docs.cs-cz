---
title: Generatetrustinfo – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: a20a50e74f702c1c015f29abde81b2e24a5551b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208692"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Generuje důvěryhodnost aplikace z manifestu základní a `TargetZone` a `ExcludedPermissions` parametry.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GenerateTrustInfo` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ApplicationDependencies`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje závislá sestavení.|  
|`BaseManifest`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje základní manifest generovat důvěryhodnost aplikace z.|  
|`ExcludedPermissions`|Volitelné `String` parametru.<br /><br /> Určuje jednu nebo více hodnot identity oddělených středníkem oprávnění mají být vyloučeny ze sady zóny výchozí oprávnění.|  
|`TargetZone`|Volitelné `String` parametru.<br /><br /> Určuje výchozí oprávnění sadě, který získáte od zásady počítače.|  
|`TrustInfoFile`|Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje soubor, který obsahuje informace o vztahu důvěryhodnosti zabezpečení aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě s parametry, které jsou uvedené v tabulce, zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



