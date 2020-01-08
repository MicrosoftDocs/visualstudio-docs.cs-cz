---
title: Úloha ResolveNativeReference – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 417c4536f13aa90505ec5e69b2719219af0d7e81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595160"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference – úloha
Přeloží nativní odkazy. Implementuje třídu <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Tato třída podporuje infrastrukturu .NET Framework, která není určena pro použití přímo v kódu.

## <a name="task-parameters"></a>Parametry úlohy
 Následující tabulka popisuje parametry úlohy `ResolveNativeReference`.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalSearchPaths`|Požadovaný parametr <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Získá nebo nastaví cesty hledání pro překlad identit sestavení nativních odkazů.|
|`ContainedComComponents`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Získá nebo nastaví komponenty modelu COM v nativním sestavení.|
|`ContainedLooseEtcFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Získá nebo nastaví volné soubory ( *atd* .), které jsou uvedeny v nativním manifestu.|
|`ContainedLooseTlbFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Získá nebo nastaví volné soubory *. tlb* nativního sestavení.|
|`ContainedPrerequisiteAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Získá nebo nastaví sestavení, která musí být přítomna, aby bylo možné použít manifest.|
|`ContainedTypeLibraries`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Získá nebo nastaví knihovny typů nativního sestavení.|
|`ContainingReferenceFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Získá nebo nastaví referenční soubory.|
|`NativeReferences`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Získá nebo nastaví odkazy na nativní sestavení Win32.|

## <a name="remarks"></a>Poznámky
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
