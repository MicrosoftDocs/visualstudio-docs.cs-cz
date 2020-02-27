---
title: Úloha FormatVersion – | Microsoft Docs
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
ms.openlocfilehash: 250c73ce0395f278b72c18605f1666290670e20a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634107"
---
# <a name="formatversion-task"></a>FormatVersion – – úloha

Připojí číslo revize k číslu verze.

- Case #1: vstup: verze =\<nedefinovaný >;  Revision =\<nemusíte >;   Výstup: OutputVersion = "1.0.0.0"

- Case #2: vstup: Version = "1.0.0. *" Revision = "5" Output: OutputVersion = "1.0.0.5"

- Případ #3: vstup: verze = "1.0.0.0" revize =\<není důležité >;  Výstup: OutputVersion = "1.0.0.0"

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry úlohy `FormatVersion`.

|Parametr|Popis|
|---------------|-----------------|
|`FormatType`|Volitelný parametr `String`.<br /><br /> Určuje typ formátu.<br /><br /> -"Version" = Version.<br />-"Path" = Replace "." s "_";|
|`OutputVersion`|Volitelný výstupní parametr `String`.<br /><br /> Určuje výstupní verzi, která obsahuje číslo revize.|
|`Revision`|Volitelný parametr `Int32`.<br /><br /> Určuje revizi, která se má připojit k verzi.|
|`Version`|Volitelný parametr `String`.<br /><br /> Určuje řetězec čísla verze, který má být zformátován.|

## <a name="remarks"></a>Poznámky

 Kromě toho, že mají parametry, které jsou uvedeny v tabulce, tato úloha dědí parametry z třídy <xref:Microsoft.Build.Tasks.TaskExtension>, kterou sám dědí z třídy <xref:Microsoft.Build.Utilities.Task>. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
