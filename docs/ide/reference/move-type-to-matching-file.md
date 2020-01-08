---
title: Přesun typu do odpovídajícího souboru refaktoring
description: Přesuňte typ do samostatného souboru se stejným názvem. Klikněte pravým tlačítkem na typ, vyberte rychlé akce a refaktoring a vyberte přesunout typ do <TypeName>. cs.
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585268"
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

   - Stisknutím klávesy **Ctrl**+ **.**
   - Klikněte pravým tlačítkem na název typu a vyberte **rychlé akce a Refaktoringy**

1. Vyberte **přesunutí typu do *TypeName*.cs** z nabídky kde *TypeName* je název typu, který jste vybrali.

   Typ se přesune do nového souboru v projektu, který má stejný název jako typ.

   - C#:

      ![Výsledek inline-C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Výsledek inline - jazyka Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
