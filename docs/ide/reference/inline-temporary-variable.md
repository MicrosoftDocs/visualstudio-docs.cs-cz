---
title: Nahraďte dočasnou proměnnou s hodnotou
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
ms.openlocfilehash: a6fea50f3cceb907cb014d29bb46988ab07dad6c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066860"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Vložená dočasná proměnná refaktoring

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** umožňuje odebrat dočasné proměnné a nahraďte ji metodou jeho hodnotu.

**Kdy:** použijte dočasné proměnné díky těžší porozumět kódu.

**Důvod, proč:** odebrání dočasná proměnná může být kód lépe čitelný.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístit textový kurzor myši do dočasné proměnné se nedá vložit:

   - C#:

       ![Zvýrazněný kód:C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/inline-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem na kód a vybrat **rychlé akce a Refaktoringy** nabídky.

3. Vyberte **dočasná proměnná na řádku** z automaticky otevíraného okna okno náhledu.

   Odebrat proměnnou a její použití nahrazuje hodnotu proměnné.

   - C#:

      ![Výsledek inline-C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Výsledek inline - jazyka Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)