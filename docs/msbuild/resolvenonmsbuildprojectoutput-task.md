---
title: Úloha ResolveNonMSBuildProjectOutput – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu ResolveNonMSBuildProjectOutput – k určení výstupních souborů pro odkazy na projekt, které nejsou určené pro MSBuild.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98d8e483b8ad03f02283620f65ec0351d9d64051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912457"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput – úloha

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

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)