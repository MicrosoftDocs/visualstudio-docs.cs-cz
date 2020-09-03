---
title: Úloha ResolveNonMSBuildProjectOutput – | Microsoft Docs
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
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aaf99affe9c29762aa8b47ea76419da429089b7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156148"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje výstupní soubory pro odkazy na projekt, které nejsou v nástroji MSBuild.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `ResolveNonMSBuildProjectOutput` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Volitelný `String` parametr.<br /><br /> Určuje řetězec XML, který obsahuje přeložené výstupy projektu.|  
|`ProjectReferences`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje odkazy na projekt.|  
|`ResolvedOutputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam vyřešených cest odkazů (a zachovává původní referenční atributy projektu).|  
|`UnresolvedProjectReferences`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam položek odkazů projektu, které nelze přeložit pomocí předvyřešeného seznamu výstupů.<br /><br /> Vzhledem k tomu, že aplikace Visual Studio předem vyhodnotí projekty jiného typu než MSBuild, znamená to, že odkazy na projekt v tomto seznamu jsou ve formátu MSBuild.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
