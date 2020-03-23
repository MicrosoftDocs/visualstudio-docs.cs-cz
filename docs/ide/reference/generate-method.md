---
title: Generovat metodu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f166c31a1615c951170367223a5b19ab93811b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595589"
---
# <a name="generate-a-method-in-visual-studio"></a>Generovat metodu v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě přidat metodu do třídy.

**Kdy:** Zavedete novou metodu a chcete ji správně deklarovat automaticky.

**Proč:** Můžete deklarovat metodu a parametry před použitím, ale tato funkce bude generovat deklaraci automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na čáru, kde je červená vlnovka. Červená vlnovka označuje metodu, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kód C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/method-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

      ![Generovat náhled metody](media/method-preview-cs.png)

3. V rozevírací nabídce vyberte **Generovat metodu.**

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.

   Metoda je vytvořena s libovolnými parametry odvozenými z jejího použití.

   - C#:

       ![Generovat výsledek metody C #](media/method-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
