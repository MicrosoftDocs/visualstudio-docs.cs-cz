---
title: 'Postupy: vyhodnocení výrazu XPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670870"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Postupy: Vyhodnocení výrazu XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vyhodnotit výrazy XPath pomocí dialogového okna **QuickWatch** . Výraz XPath musí být platný podle doporučení jazyka W3C XPath 1,0. Aktuální kontext XSLT – to znamená, že `self::node()` uzel v okně **místní** hodnoty – poskytuje kontext vyhodnocení pro výraz XPath.

 Následující seznam popisuje, které funkce jsou podporovány při vyhodnocování výrazu XPath:

- Jsou podporovány předdefinované funkce XPath.

- Integrované funkce XSLT nejsou podporovány.

- Uživatelsky definované funkce nejsou podporovány.

> [!NOTE]
> Následující postup používá soubory belowAvg. XSL a books.xml z [návodu: ladit šablonu stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Vyhodnocení výrazu XPath

1. Vložte zarážku na `xsl:if` počáteční značku.

2. Klikněte na tlačítko **LADIT XSL** na panelu nástrojů editoru XML.

     Ladicí program se spustí a přeruší na `xsl:if` značku.

3. Klikněte pravým tlačítkem a vyberte **QuickWatch**.

     Zobrazí se dialogové okno **QuickWatch** .

4. `./price/text()`Do pole **výraz** v dialogovém okně **QuickWatch** zadejte a klikněte na znovu **vyhodnotit**.

     V poli **hodnota** se zobrazí cena aktuálního uzlu knihy.

5. Změňte výraz XPath na `./price/text() < $bookAverage` a klikněte na znovu **vyhodnotit**.

     Pole **hodnota** ukazuje, že výraz XPath je vyhodnocen jako `true` .

## <a name="see-also"></a>Viz také
 [Ladění XSLT](../xml-tools/debugging-xslt.md)
