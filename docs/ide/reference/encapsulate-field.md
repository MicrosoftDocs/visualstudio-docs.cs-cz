---
title: Refaktorovat pole na vlastnost
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: db0bd17cd0bead3807f857b2198b8d4ea4c72ffb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569709"
---
# <a name="encapsulate-a-field-refactoring"></a>Zapouzdřit pole refaktoring

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** umožňuje pole do vlastností a aktualizovat všechny použití tohoto pole použít vlastnost nově vytvořený.

**Kdy:** chcete přesunout do vlastnosti pole a aktualizovat všechny odkazy na pole.

**Důvod, proč:** chcete udělit jiným třídy přístup k poli, ale nechcete, aby tyto třídy umožňuje mít přímý přístup.  Obalením pole ve vlastnosti můžete napsat kód pro ověření přiřazené hodnoty, třeba.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte kurzor text mezi název pole k zapouzdření:

   - C#:

       ![Zvýrazněný kód:C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/encapsulate-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl + R**, pak **Ctrl + E**.  (Všimněte si, že klávesová zkratka může být jiný platformě, na který profil vyberete.)
      - Stisknutím klávesy **Ctrl**+ **.** aktivační událost **rychlé akce a Refaktoringy** nabídku a vyberte buď **transakci zapouzdřit pole** položky z automaticky otevíraného okna okno náhledu.
   - **Myši**
      - Vyberte **Upravit > Refaktorovat > pro zapouzdření polí**.
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídku a vyberte buď **transakci zapouzdřit pole** položky z automaticky otevíraného okna okno náhledu.

   Výběr | Popis
   --------- | -----------
   **Zapouzdřit pole (a použít vlastnost)** | Zapouzdřuje pole s vlastností a aktualizuje všechny použití pole pro použití vygenerované vlastnosti
   **Zapouzdřit pole (ale dál používat pole)** | Zapouzdřuje pole s vlastností, ale ponechá beze změny všech použití pole

   Vlastnost je vytvořen a odkazy na pole jsou aktualizovány, pokud vybraná.

   > [!TIP]
   > Použití **náhled změn** odkaz v automaticky otevíraném okně [chcete zobrazit, co bude výsledkem](../../ide/preview-changes.md) před potvrzením do něj.

   - C#:

      ![Zapouzdřit vlastnosti result-C#](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Zapouzdřit vlastnosti result - jazyka Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
