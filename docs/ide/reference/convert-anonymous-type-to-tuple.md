---
title: Převést anonymní typ na řazenou kolekci členů
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést anonymní typ na řazenou kolekci členů v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6486b771207722c64993d5a880894fe07beb99c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907663"
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
