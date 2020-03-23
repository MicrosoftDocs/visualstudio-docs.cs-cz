---
title: Přesunout úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b9f83fa7c80769ea3c584e2885c8fb1db24176
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633457"
---
# <a name="move-task"></a>Move – úloha

Přesune soubory do nového umístění.

## <a name="parameters"></a>Parametry

 Listová tabulka popisuje parametry úlohy. `Move`

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje seznam souborů, do kterých se mají zdrojové soubory přesunout. Očekává se, že tento seznam bude mapování 1:1 do `SourceFiles` seznamu, který je zadán v parametru. To znamená, že první `SourceFiles` soubor zadaný v písmenu a) bude přesunut do prvního umístění určeného v aplikace `DestinationFiles`a tak dále.|
|`DestinationFolder`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje adresář, do kterého chcete soubory přesunout.|
|`MovedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které byly úspěšně přesunuty.|
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`přepíše soubory, i když jsou označeny jako soubory jen pro čtení.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které se mají přesunout.|

## <a name="remarks"></a>Poznámky

 `DestinationFolder` Parametr nebo `DestinationFiles` parametr musí být zadán, ale ne obojí. Jsou-li zadány oba parametry, úloha se nezdaří a je zaznamenána chyba.

 Úloha `Move` vytvoří složky podle potřeby pro požadované cílové soubory.

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
