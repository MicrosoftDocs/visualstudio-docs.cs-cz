---
title: Implementace rozhraní
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 7abe20831c920a0d4fd74f60a75e6112c480ab39
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068471"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementovat rozhraní v sadě Visual Studio

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** umožňuje okamžitě generovat kód potřebný k implementaci rozhraní.

**Kdy:** chcete dědit z rozhraní.

**Důvod, proč:** ručně může implementovat všechny rozhraní jeden po druhém, ale tato funkce automaticky vygeneruje všechny podpisy metod.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek níž se nachází červená vlnovka, která určuje neodkazujete rozhraní, ale neimplementovali všechny požadované členy.

   - C#:

       ![Zvýrazněný kód jazyka C#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód jazyka Visual Basic](media/interface-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky.
   - **Myši**
      - Klikněte pravým tlačítkem a vyberte **rychlé akce a Refaktoringy** nabídky.
      - Červená vlnovka ukazatel myši a klikněte ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí.
      - Klikněte na ![Žárovka](media/bulb-cs.png) ikona, která se zobrazí u levého okraje, pokud textový kurzor na řádek s červená vlnovka.

3. Vyberte **implementovat rozhraní** z rozevírací nabídky.

   ![Implementovat rozhraní ve verzi preview](media/interface-preview-cs.png)

   > [!TIP]
   > - Použití **náhled změn** odkaz v dolní části okna náhledu [zobrazíte všechny změny](../../ide/preview-changes.md) , který bude proveden před zvolení požadované možnosti.
   > - Použití **dokumentu**, **projektu**, a **řešení** odkazy v dolní části okna ve verzi preview vytvořit správnou metodu podpisy v rámci více tříd, které implementují rozhraní.

   Podpisy metod rozhraní je vytvořen a připraven k implementaci.

   - C#:

       ![Implementovat rozhraní výsledek C#](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementovat rozhraní výsledek VB](media/interface-result-vb.png)

   > [!TIP]
   > (C# jenom) Použití **implementovat rozhraní explicitně** možnost používaly každý vygeneruje metodu s názvem rozhraní, aby se zabránilo kolize názvů.
   >
   > ![Implementovat rozhraní explicitně způsobit.](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)