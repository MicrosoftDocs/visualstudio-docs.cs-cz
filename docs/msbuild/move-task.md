---
title: Přesunout úlohu | Microsoft Docs
description: Přečtěte si o parametrech a nastaveních úlohy přesunutí pro MSBuild, která přesouvá soubory do nových umístění.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9121c14037ac1bc5740d1f0684f92226a361e6d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918190"
---
# <a name="move-task"></a>Move – úloha

Přesune soubory do nového umístění.

## <a name="parameters"></a>Parametry

 Tabulka tato popisuje parametry `Move` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DestinationFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje seznam souborů, do kterých se mají přesunout zdrojové soubory. V tomto seznamu se očekává mapování 1:1 na seznam, který je zadaný v `SourceFiles` parametru. To znamená, že první soubor zadaný v `SourceFiles` bude přesunut do prvního umístění určeného v a `DestinationFiles` tak dále.|
|`DestinationFolder`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje adresář, do kterého chcete soubory přesunout.|
|`MovedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje položky, které byly úspěšně přesunuty.|
|`OverwriteReadOnlyFiles`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` , přepíše soubory i v případě, že jsou označeny jako soubory jen pro čtení.|
|`SourceFiles`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které se mají přesunout.|

## <a name="remarks"></a>Poznámky

 `DestinationFolder` `DestinationFiles` Musí být zadán buď parametr, nebo parametr, ale ne oba. Jsou-li zadány oba parametry, úloha se nezdaří a je zaznamenána chyba.

 `Move`Úloha vytvoří složky požadované pro požadované cílové soubory.

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
