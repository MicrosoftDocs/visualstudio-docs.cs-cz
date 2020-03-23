---
title: Přesunout text na odpovídající refaktoring souboru
description: Přesuňte typ do samostatného souboru se stejným názvem. Klikněte pravým tlačítkem myši na typ, vyberte Rychlé <TypeName>akce a Refaktoringy a vyberte Přesunout typ na .cs.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba082e90c2447d1da7510ce16f888f67a52b5ac0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585268"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Přesunutí typu na odpovídající refaktoring souboru

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje přesunout vybraný typ do samostatného souboru se stejným názvem.

**Kdy:** Máte více tříd, struktury, rozhraní, atd ve stejném souboru, který chcete oddělit.

**Proč:** Umístění více typů do stejného souboru může ztížit nalezení těchto typů. Přesunutím typů do souborů se stejným názvem se kód stává čitelnějším a snadněji se naviguje.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu typu, kde je definován. Například:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Dále proveďte jeden z následujících akcí:

   - Stiskněte **klávesu Ctrl**+**.**
   - Klikněte pravým tlačítkem myši na název typu a vyberte **Rychlé akce a Refaktoringy.**

1. V nabídce vyberte **Přesunout typ na *TypeName*.cs,** kde *TypeName* je název vybraného typu.

   Typ je přesunut do nového souboru v projektu, který má stejný název jako typ.

   - C#:

      ![Inline výsledek - C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Vsazený výsledek – Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
