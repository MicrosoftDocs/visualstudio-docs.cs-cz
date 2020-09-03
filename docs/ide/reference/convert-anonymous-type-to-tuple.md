---
title: Převést anonymní typ na řazenou kolekci členů
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
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094271"
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

   ![Převést anonymní typ na řazenou kolekci členů](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
