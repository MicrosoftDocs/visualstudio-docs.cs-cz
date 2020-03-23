---
title: Změna podpisu metody
description: Odeberte nebo změňte pořadí parametrů metody. Klikněte pravým tlačítkem myši na metodu, vyberte Rychlé akce a Refaktoringy a vyberte Změnit podpis.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711266"
---
# <a name="change-a-method-signature-refactoring"></a>Změna refaktoringu podpisu metody

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje odebrat nebo změnit pořadí parametrů metody.

**Kdy:** Chcete přesunout nebo odebrat parametr metody, který je aktuálně používán v různých umístěních.

**Proč:** Můžete ručně odebrat a změnit pořadí parametrů a potom najít všechna volání této metody a změnit je jeden po druhém, ale to by mohlo vést k chybám.  Tento refaktoring nástroj provede úlohu automaticky.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do názvu metody, kterou chcete upravit, nebo do jednoho z jejích použití:

   - C#:

       ![Zvýrazněný kód C #](media/changesignature-highlight-cs.png)

   - Vb:

       ![Zvýrazněný kód Jazyka](media/changesignature-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **kombinaci kláves Ctrl+R**a potom **kombinaci kláves Ctrl+V**.  (Všimněte si, že klávesová zkratka se může lišit podle vybraného profilu.)
      - Stiskněte **klávesu Ctrl**+**.** aktivujete nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Změnit podpis.**
   - **Myš**
      - Vyberte **možnost Upravit > refaktorovat > odebrat parametry**.
      - Vyberte **možnost Upravit > Přefaktorovat > Parametry přiobjednání**.
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a v automaticky otevíraném okně Náhled vyberte **Změnit podpis.**

3. V dialogovém okně **Změnit podpis,** které se objeví, můžete pomocí tlačítek na pravé straně změnit podpis metody:

   ![Dialogové okno Změnit podpis](media/changesignature-dialog-cs.png)

   | Tlačítko | Popis
   | ------ | ---
   | **Nahoru/dolů** | Přesunutí vybraného parametru nahoru a dolů v seznamu
   | **Odebrat** | Odebrání vybraného parametru ze seznamu
   | **Obnovení** | Obnovení vybraného přeškrtnutého parametru do seznamu

   > [!TIP]
   > Pomocí zaškrtávacího políčka **Změny odkazu náhledu** [zobrazíte, jaký bude výsledek,](../../ide/preview-changes.md) než se k němu odevzdejte.

4. Po dokončení proveďte změny stisknutím tlačítka **OK.**

   - C#:

      ![Výsledek podpisu změny - C #](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Výsledek změny podpisu – visual basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)