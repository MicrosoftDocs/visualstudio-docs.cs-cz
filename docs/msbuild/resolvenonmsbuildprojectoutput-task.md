---
title: ResolveNonMSBuildProjectOutput Úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604ed91d32140c3b037e6ddef21e996f72ef8439
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632573"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput – úloha

Určuje výstupní soubory pro odkazy na projekt y jiné než MSBuild.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `ResolveNonMSBuildProjectOutput` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Volitelný `String` parametr.<br /><br /> Určuje řetězec XML, který obsahuje přeložené výstupy projektu.|
|`ProjectReferences`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje odkazy na projekt.|
|`ResolvedOutputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam vyřešených referenčních cest (a zachová původní atributy odkazu projektu).|
|`UnresolvedProjectReferences`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam položek odkazu na projekt, které nebylo možné vyřešit pomocí předem vyřešeného seznamu výstupů.<br /><br /> Vzhledem k tomu, že Visual Studio pouze předresolves nemsbuild projekty, to znamená, že odkazy na projekt v tomto seznamu jsou ve formátu MSBuild.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)