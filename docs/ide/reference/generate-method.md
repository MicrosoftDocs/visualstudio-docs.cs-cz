---
title: Vygenerovat metodu
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring hned přidat metodu do třídy.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c6f4a25e3cda10e74c344cb7eef879b78f60a1de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903902"
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

       ![Zvýrazněný kód C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/method-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .
      - Najeďte myší na červenou vlnovkou a klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![žárovka chyby](media/error-bulb.png) ikona, která se zobrazí na levém okraji, pokud se na řádku již nachází textový kurzor s červenou vlnovkou

      ![Vygenerovat ukázkovou metodu](media/method-preview-cs.png)

3. V rozevírací nabídce vyberte **generovat metodu** .

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna Preview [zobrazíte všechny změny](../../ide/preview-changes.md) , které budou provedeny před provedením výběru.

   Metoda je vytvořena s parametry odvozenými z jejího použití.

   - C#:

       ![Generovat výsledek metody C #](media/method-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
