---
title: Přesunout typ do odpovídajícího refaktoringu souboru
description: Přesuňte typ do samostatného souboru se stejným názvem. Klikněte pravým tlačítkem na typ, vyberte rychlé akce a refaktoring a vyberte přesunout typ do <TypeName> . cs.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 728b9e176a40d2bfd7ae36a329409cb27f80fc86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927951"
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

   - Stiskněte klávesu **CTRL** + **.**
   - Klikněte pravým tlačítkem myši na název typu a vyberte **rychlé akce a refaktoring** .

1. Z nabídky vyberte **přesunout typ na *TypeName*. cs** , kde *TypeName* je název typu, který jste vybrali.

   Typ je přesunut do nového souboru v projektu, který má stejný název jako typ.

   - C#:

      ![Vložený výsledek – C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Vložený výsledek – Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
