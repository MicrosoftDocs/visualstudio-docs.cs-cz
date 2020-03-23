---
title: Úkol ResolveNativeReference | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 64b76b31e96947914c9a641ed4ceb23c7761eb85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632677"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference – úloha

Řeší nativní odkazy. Implementuje <xref:Microsoft.Build.Tasks.ResolveNativeReference> třídu. Tato třída podporuje infrastrukturu rozhraní .NET Framework, která není určena k použití přímo z vašeho kódu.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `ResolveNativeReference` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AdditionalSearchPaths`|Požadovaný parametr <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Získá nebo nastaví vyhledávací cesty pro řešení identity sestavení nativní odkazy.|
|`ContainedComComponents`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Získá nebo nastaví součásti modelu COM nativního sestavení.|
|`ContainedLooseEtcFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Získá nebo nastaví volné *Etc* soubory uvedené v nativním manifestu.|
|`ContainedLooseTlbFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Získá nebo nastaví volné *.tlb* soubory nativní sestavení.|
|`ContainedPrerequisiteAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Získá nebo nastaví sestavení, které musí být k dispozici před manifest lze použít.|
|`ContainedTypeLibraries`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Získá nebo nastaví knihovny typů nativní sestavení.|
|`ContainingReferenceFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Získá nebo nastaví referenční soubory.|
|`NativeReferences`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Získá nebo nastaví odkazy nativní sestavení Win32.|

## <a name="remarks"></a>Poznámky

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
