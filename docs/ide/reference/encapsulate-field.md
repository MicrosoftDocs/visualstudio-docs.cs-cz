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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569709"
---
# <a name="encapsulate-a-field-refactoring"></a>Zapouzdření refaktoringu pole

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje změnit pole na vlastnost a aktualizovat všechna použití tohoto pole tak, aby používalo nově vytvořenou vlastnost.

**Kdy:** Chcete přesunout pole do vlastnosti a aktualizovat všechny odkazy na toto pole.

**Proč:** Chcete udělit přístup k poli ostatním třídám, ale nechcete, aby tyto třídy měly přímý přístup.  Zabalením pole do vlastnosti můžete napsat kód pro ověření hodnoty, která je přiřazena, například.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do názvu pole, které chcete zapouzdřit:

   - C#:

       ![Zvýrazněný kód - C #](media/encapsulate-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/encapsulate-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves Ctrl+R**a potom **kombinaci kláves Ctrl+E**.  (Všimněte si, že klávesová zkratka se může lišit podle vybraného profilu.)
      - Stiskněte **klávesu Ctrl**+**.** aktivujte nabídku **Rychlé akce a Refaktoringy** a vyberte buď **položku pole Zapouzdřit** z vyskakovacího okna Náhled.
   - **Myš**
      - Vyberte **Upravit > Refaktorovat > zapouzdřit pole**.
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a vyberte buď **položku poli Zapouzdření** z vyskakovacího okna Náhled.

   Výběr | Popis
   --------- | -----------
   **Zapouzdřit pole (a použít vlastnost)** | Zapouzdřuje pole s vlastností a aktualizuje všechna použití pole tak, aby se vygenerovaná vlastnost používala.
   **Zapouzdřit pole (ale stále používat pole)** | Zapouzdřuje pole s vlastností, ale ponechá všechna použití pole nedotčená.

   Vlastnost je vytvořena a odkazy na pole jsou aktualizovány, pokud je vybráno.

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v vyskakovacím okně [zjistíte, jaký bude výsledek](../../ide/preview-changes.md) před potvrzením.

   - C#:

      ![Výsledek zapouzdření vlastnosti - C #](media/encapsulate-result-cs.png)

   - Visual Basic:

      ![Výsledek vlastnosti zapouzdření – visual basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
