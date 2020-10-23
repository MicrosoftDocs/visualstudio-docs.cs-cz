---
title: Úloha FormatVersion – | Microsoft Docs
description: Přečtěte si o různých způsobech, kterými FormatVersion – úlohy MSBuild připojí číslo revize k číslu verze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16da018e49e6cb456074ebabac52a8768d06c1c6
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436711"
---
# <a name="formatversion-task"></a>FormatVersion – úloha

Připojí číslo revize k číslu verze.

- Případ #1: vstup: verze = \<undefined> ;  Revize = \<don't care> ;   Výstup: OutputVersion = "1.0.0.0"

- Case #2: vstup: Version = "1.0.0. *" Revision = "5" Output: OutputVersion = "1.0.0.5"

- Případ #3: vstup: verze = "1.0.0.0" revize = \<don't care> ;  Výstup: OutputVersion = "1.0.0.0"

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `FormatVersion` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`FormatType`|Volitelný `String` parametr.<br /><br /> Určuje typ formátu.<br /><br /> -"Version" = Version.<br />-"Path" = Replace "." s "_";|
|`OutputVersion`|Volitelný `String` výstupní parametr.<br /><br /> Určuje výstupní verzi, která obsahuje číslo revize.|
|`Revision`|Volitelný `Int32` parametr.<br /><br /> Určuje revizi, která se má připojit k verzi.|
|`Version`|Volitelný `String` parametr.<br /><br /> Určuje řetězec čísla verze, který má být zformátován.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
