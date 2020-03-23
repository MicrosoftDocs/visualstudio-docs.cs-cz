---
title: Úloha formatversion | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634107"
---
# <a name="formatversion-task"></a>Úloha FormatVersion

Připojí číslo revize k číslu verze.

- Případ #1: Vstup:\<Verze = nedefinovaná>;  Revize\<= nezajímá>;   Výstup: OutputVersion="1.0.0.0"

- Případ #2: Vstup: Version="1.0.0.*" Revision="5" Výstup: OutputVersion="1.0.0.5"

- Případ #3: Vstup: Version="1.0.0.0" Revize =\<nestarám se>;  Výstup: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `FormatVersion` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`FormatType`|Volitelný `String` parametr.<br /><br /> Určuje typ formátu.<br /><br /> - "Verze" = verze.<br />- "Cesta" = nahradit "." s "_";|
|`OutputVersion`|Volitelný `String` výstupní parametr.<br /><br /> Určuje výstupní verzi, která obsahuje číslo revize.|
|`Revision`|Volitelný `Int32` parametr.<br /><br /> Určuje revizi, která se připojí k verzi.|
|`Version`|Volitelný `String` parametr.<br /><br /> Určuje číselné řetězce verze, které chcete formátovat.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
