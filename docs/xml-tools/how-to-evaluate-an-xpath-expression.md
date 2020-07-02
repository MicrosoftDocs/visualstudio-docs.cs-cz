---
title: Vyhodnotit výraz XPath při ladění
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64113461cd081eb97e2eb927119f1cd67f8a8d6e
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816251"
---
# <a name="evaluate-xpath-expressions"></a>Vyhodnotit výrazy XPath

Výrazy XPath můžete vyhodnotit pomocí okna **QuickWatch** během ladění. Výraz XPath musí být platný podle doporučení jazyka W3C XPath 1,0. Aktuální kontext XSLT (to znamená, že `self::node()` uzel v okně **místní** hodnoty) poskytuje kontext vyhodnocení pro výraz XPath.

Při vyhodnocování výrazu XPath:

- Jsou podporovány předdefinované funkce XPath.

- Integrované funkce XSLT a uživatelsky definované funkce nejsou podporovány.

> [!NOTE]
> Ladění XSLT je k dispozici pouze v edici Enterprise sady Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Vyhodnocení výrazu XPath

Následující postup používá soubory *below-Average. xsl* a *books.xml* z [návodu: ladění stránky stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) .

1. Vložte zarážku na `xsl:if` počáteční značku.

2. Chcete-li spustit ladění, zvolte možnost **XML**  >  **Spustit ladění XSLT** na řádku nabídek (nebo stiskněte klávesu **ALT** + **F5**).

   Ladicí program se spustí a přeruší na `xsl:if` značku.

3. Klikněte pravým tlačítkem a vyberte **QuickWatch**.

   Otevře se okno **QuickWatch** .

4. `./price/text()`Do pole **výraz** v dialogovém okně **QuickWatch** zadejte a pak zvolte **přehodnocení**.

   V poli **hodnota** se zobrazí cena aktuálního uzlu knihy.

   ![Vyhodnocení výrazu XPath v okně QuickWatch](media/quickwatch-price.png)

5. Změňte výraz XPath na `./price/text() < $bookAverage` a klikněte na znovu **vyhodnotit**.

   Pole **hodnota** ukazuje, že výraz XPath je vyhodnocen jako `true` .

## <a name="see-also"></a>Viz také:

- [Ladění XSLT](../xml-tools/debugging-xslt.md)
