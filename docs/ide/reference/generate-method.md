---
title: Vygenerovat metodu
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c85e3f849d7d74f326c1cf330b0e2c338d78fc6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668336"
---
# <a name="generate-a-method-in-visual-studio"></a>Generování metody v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě přidat metodu do třídy.

**Když:** Zavádíte novou metodu a chcete ji správně deklarovat automaticky.

**Proč:** Metodu a parametry můžete deklarovat před jejím použitím, ale tato funkce bude tuto deklaraci generovat automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na řádek, kde je červená vlnovka. Červená vlnovka označuje metodu, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kódC#](media/method-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/method-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

      ![Vygenerovat ukázkovou metodu](media/method-preview-cs.png)

3. V rozevírací nabídce vyberte **generovat metodu** .

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.

   Metoda je vytvořena s parametry odvozenými z jejího použití.

   - C#:

       ![Generovat výsledek metodyC#](media/method-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)