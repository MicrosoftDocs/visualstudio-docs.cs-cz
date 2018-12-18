---
title: 'Postupy: vyhodnocení výrazu jazyka XPath'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02492f2e1760df3ce5cd6751808303bae75577e2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549048"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Postupy: vyhodnocení výrazu jazyka XPath

Je možné vyhodnotit výraz XPath s **QuickWatch** dialogové okno. Výraz XPath musí být platná souladu s doporučením W3C XPath 1.0. Aktuální kontext XSLT – to znamená, `self::node()` uzlu **místní hodnoty –** okno – poskytuje kontext vyhodnocení pro výraz XPath.

 Následující seznam popisuje, které funkce jsou podporovány při vyhodnocování výrazu jazyka XPath:

-   Jsou podporovány integrované funkce jazyka XPath.

-   Integrované funkce XSLT nejsou podporovány.

-   Uživatelem definované funkce nejsou podporovány.

> [!NOTE]
> Následující postup používá *belowAvg.xsl* a *books.xml* souborů z [návod: ladění stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tématu.

## <a name="to-evaluate-an-xpath-expression"></a>Vyhodnocení výrazu jazyka XPath

1.  Vložit zarážka v `xsl:if` počáteční značka.

2.  Klikněte **ladění XSL** tlačítka na panelu nástrojů editoru XML.

     Ladicí program spustí a dělí na `xsl:if` značky.

3.  Klikněte pravým tlačítkem a vyberte **QuickWatch**.

     **QuickWatch** se zobrazí dialogové okno.

4.  Zadejte `./price/text()` v **výraz** pole z **QuickWatch** dialogové okno a klikněte na tlačítko **přehodnocovat**.

     Cena na aktuální uzel adresáře se zobrazí v **hodnotu** pole.

5.  Změnit výraz XPath pro `./price/text() < $bookAverage` a klikněte na tlačítko **přehodnocovat**.

     **Hodnotu** pole ukazuje, že výraz XPath vyhodnocuje `true`.

## <a name="see-also"></a>Viz také

- [Ladění XSLT](../xml-tools/debugging-xslt.md)