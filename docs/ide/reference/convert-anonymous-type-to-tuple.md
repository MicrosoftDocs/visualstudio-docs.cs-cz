---
title: Převést anonymní typ na řazenou kolekci členů
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést anonymní typ na řazenou kolekci členů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 452ba826a2765ef624e6c3d04bb20915a26c51fb
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040859"
---
# <a name="convert-anonymous-type-to-tuple"></a>Převedení anonymního typu na řazenou kolekci členů

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Převeďte anonymní typ na řazenou kolekci členů.

**Když:** Máte anonymní typ, který se může vyvažovat za řazenou kolekci členů.

**Proč:** [řazené kolekce členů](/dotnet/csharp/tuples) jsou užitečné v případě, že je vaše syntaxe odlehčená. Tato rychlá akce usnadňuje využití této funkce jazyka C#.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do anonymního typu.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Převést anonymní typ na řazenou kolekci členů](media/convert-anon-to-tuple.png)

2. Stisknutím klávesy **ENTER** přijměte refaktoring.

   ![Převést anonymní typ na přijatou řazenou kolekci členů](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
