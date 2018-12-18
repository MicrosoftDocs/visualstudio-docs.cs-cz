---
title: Generování přepisu – metoda
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bb4a35c1f7c9e2752148e54f934a3fcbfb974136
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063639"
---
# <a name="generate-an-override-in-visual-studio"></a>Generovat přepsání v sadě Visual Studio

Tato generace kód platí pro:

- C#

- Visual Basic

**Co:** umožňuje okamžitě generování kódu pro libovolnou metodu, která se dá přepsat ze základní třídy.

**Kdy:** chcete přepsat metodu základní třídy a automaticky generovat podpis.

**Důvod, proč:** můžete napsat podpis metody sami, ale tato funkce bude automaticky generovat podpis.

## <a name="how-to"></a>Postupy

1. Typ `override` v C# nebo `Overrides` v jazyce Visual Basic, za nímž následuje mezera, pokud chcete vložit to metoda override.

   - C#:

      ![Přepsat technologie IntelliSenseC#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Přepsat IntelliSense VB](media/override-intellisense-vb.png)

2. Vyberte metodu, kterou chcete přepsat ze základní třídy.

   > [!TIP]
   > - Vlastnosti ikony ![Ikona vlastnost](media/override-property-cs.png) Chcete-li zobrazit nebo skrýt vlastnosti v seznamu.
   > - Automaticky otevírané ikony – metoda ![Ikona metody](media/override-method-cs.png) Chcete-li zobrazit nebo skrýt metod v seznamu.

   Vybrané metody nebo vlastnosti se přidá do třídy jako přepsání, připraveno k implementaci.

   - C#:

       ![Přepsat výsledkuC#](media/override-result-cs.png)

   - Visual Basic:

       ![Přepsat výsledek VB](media/override-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)