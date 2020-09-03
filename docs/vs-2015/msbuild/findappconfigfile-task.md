---
title: Úloha FindAppConfigFile – | Microsoft Docs
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
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb9e1f3fbdc1a6f4d7c4e2c589f620f331a904ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179613"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vyhledá soubor app.config, pokud existuje, v zadaných seznamech.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `FindAppConfigFile` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AppConfigFile`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje první vyhovující položku, která se nachází v seznamu, pokud existuje.|  
|`PrimaryList`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje primární seznam, pomocí kterého se bude hledat.|  
|`SecondaryList`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje sekundární seznam, přes který se má prohledat.|  
|`TargetPath`|Požadovaný parametr `String`.<br /><br /> Určuje hodnotu, která se má přidat jako metadata.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
