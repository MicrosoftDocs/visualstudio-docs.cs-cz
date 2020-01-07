---
title: Nahraďte dočasnou proměnnou s hodnotou
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
ms.openlocfilehash: 8f0199436f5f9b1013a4c49cfb5909e760c73dcc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568864"
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
      - Stisknutím klávesy **Ctrl**+ **.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
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
