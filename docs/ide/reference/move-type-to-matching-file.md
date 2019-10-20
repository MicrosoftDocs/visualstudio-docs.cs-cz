---
title: Přesunout typ do odpovídajícího refaktoringu souboru
description: Přesuňte typ do samostatného souboru se stejným názvem. Klikněte pravým tlačítkem na typ, vyberte rychlé akce a refaktoring a vyberte přesunout typ do <TypeName>. cs.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba822981ade5ebdc191732e0a32b02a9a4005fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666478"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Přesunutí typu na vyhovující refaktoring souboru

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje přesunout vybraný typ do samostatného souboru se stejným názvem.

**Když:** Máte více tříd, struktur, rozhraní atd. ve stejném souboru, který chcete oddělit.

**Proč:** Umístěním více typů do stejného souboru může být obtížné tyto typy najít. Přesunutím typů do souborů se stejným názvem se kód bude čitelnější a snáze se naviguje.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu typu, kde je definován. Příklad:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Dále proveďte jednu z následujících akcí:

   - Stiskněte klávesu **Ctrl** + **.**
   - Klikněte pravým tlačítkem myši na název typu a vyberte **rychlé akce a refaktoring** .

1. Z nabídky vyberte **přesunout typ na *TypeName*. cs** , kde *TypeName* je název typu, který jste vybrali.

   Typ je přesunut do nového souboru v projektu, který má stejný název jako typ.

   - C#:

      ![Vložený výsledek –C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Vložený výsledek – Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
