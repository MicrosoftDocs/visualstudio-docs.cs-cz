---
title: Generovat pole, vlastnost, místní proměnná
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b554aa5586150942c0fc7d7aeada9356a67029ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595602"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generovat pole, vlastnost nebo místní proměnnou v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě vygenerovat kód pro dříve nedeklarované pole, vlastnost nebo místní.

**Kdy:** Při psaní zavádíte nové pole, vlastnost nebo místní a chcete je správně deklarovat automaticky.

**Proč:** Před použitím můžete deklarovat pole, vlastnost nebo místní, ale tato funkce vygeneruje deklaraci a zadá automaticky.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na čáru, kde je červená vlnovka. Červená vlnovka označuje pole, místní nebo vlastnost, která ještě neexistuje.

   - C#:

       ![Zvýrazněný kód C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód VB](media/field-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**
      - Najeďte přes červenou vlnovku a klikněte na ![chybová žárovka](media/error-bulb.png) ikona, která se zobrazí.
      - Klikněte na ![chybová žárovka](media/error-bulb.png) se zobrazí na levém okraji, pokud je textový kurzor již na řádku s červenou vlnovkou.

      ![Generovat pole/vlastnost/místní náhled](media/field-preview-cs.png)

3. V rozevírací nabídce vyberte jednu z možností generování.

   > [!TIP]
   > Pomocí odkazu **Náhled změn** v dolní části okna náhledu [zobrazíte všechny změny,](../../ide/preview-changes.md) které budou provedeny před provedením výběru.

   Pole, vlastnost nebo místní je vytvořen, s typem odvodit z jeho použití.

   - C#:

       ![Generovat výsledek metody C #](media/field-result-cs.png)

   - Visual Basic:

       ![Generovat výsledek metody VB](media/field-result-vb.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
