---
title: Přesun typu do odpovídajícího souboru refaktoring
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 997cf31d14acd65abd003bcb00cce4a9797b394a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059636"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Přesunutí typu do odpovídajícího souboru refaktoring

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** umožňuje vybraného typu přesuňte do samostatného souboru se stejným názvem.

**Kdy:** mít více tříd, struktur, rozhraní a podobně ve stejném souboru, který chcete oddělit.

**Důvod, proč:** umístěním více typů ve stejném souboru může být obtížné najít tyto typy. Přesunutím typů souborů se stejným názvem, bude kód čitelnější a přehlednější a díky tomu.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor mezi název typu, kde je definován. Příklad:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Dále proveďte jednu z následujících akcí:

   - Stisknutím klávesy **Ctrl**+**.**
   - Klikněte pravým tlačítkem na název typu a vyberte **rychlé akce a Refaktoringy**

1. Vyberte **přesunutí typu do *TypeName*.cs** z nabídky kde *TypeName* je název typu, který jste vybrali.

   Typ se přesune do nového souboru v projektu, který má stejný název jako typ.

   - C#:

      ![Výsledek inline-C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Výsledek inline - jazyka Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
