---
title: Úloha ResolveNonMSBuildProjectOutput – | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632573"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput – úloha

Určuje výstupní soubory pro odkazy na projekt, které nejsou v nástroji MSBuild.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `ResolveNonMSBuildProjectOutput`.

|Parametr|Popis|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Volitelný parametr `String`.<br /><br /> Určuje řetězec XML, který obsahuje přeložené výstupy projektu.|
|`ProjectReferences`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje odkazy na projekt.|
|`ResolvedOutputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje seznam vyřešených cest odkazů (a zachovává původní referenční atributy projektu).|
|`UnresolvedProjectReferences`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje seznam položek odkazů projektu, které nelze přeložit pomocí předvyřešeného seznamu výstupů.<br /><br /> Vzhledem k tomu, že aplikace Visual Studio předem vyhodnotí projekty jiného typu než MSBuild, znamená to, že odkazy na projekt v tomto seznamu jsou ve formátu MSBuild.|

## <a name="remarks"></a>Poznámky

 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)