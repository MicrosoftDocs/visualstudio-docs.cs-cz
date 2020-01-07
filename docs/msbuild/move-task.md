---
title: Přesunout úlohu | Microsoft Docs
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
ms.openlocfilehash: 8adfa75964959e2cce61779914a52f03319ed314
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592136"
---
# <a name="move-task"></a>Move – úloha
Přesune soubory do nového umístění.

## <a name="parameters"></a>Parametry
 Tabulka tato popisuje parametry úkolu `Move`.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Určuje seznam souborů, do kterých se mají přesunout zdrojové soubory. V tomto seznamu se očekává mapování 1:1 na seznam, který je zadaný v parametru `SourceFiles`. To znamená, že první soubor zadaný v `SourceFiles` bude přesunut do prvního umístění zadaného v `DestinationFiles`a tak dále.|
|`DestinationFolder`|Volitelný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje adresář, do kterého chcete soubory přesunout.|
|`MovedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje položky, které byly úspěšně přesunuty.|
|`OverwriteReadOnlyFiles`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, přepíše soubory i v případě, že jsou označeny jako soubory jen pro čtení.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které se mají přesunout.|

## <a name="remarks"></a>Poznámky
 Musí být zadán buď parametr `DestinationFolder`, nebo parametr `DestinationFiles`, ale ne oba. Jsou-li zadány oba parametry, úloha se nezdaří a je zaznamenána chyba.

 Úloha `Move` vytváří složky podle požadavků pro požadované cílové soubory.

 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také:
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
