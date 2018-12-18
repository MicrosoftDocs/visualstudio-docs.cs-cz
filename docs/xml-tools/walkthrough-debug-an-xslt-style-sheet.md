---
title: 'Návod: Ladění šablony stylů XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebc8e8f8700690a2ae74fcc91384fb77b238ea33
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693393"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Návod: Ladění stylů XSLT

Kroky v tomto návodu ukazují, jak používat ladicí program XSLT. Kroky zahrnují zobrazení proměnné, nastavení zarážek a krokování kódu. Šablony stylů vyhledá všechny publikace, které náklady níže průměrnou cenu knih.

## <a name="to-prepare-for-this-walkthrough"></a>Příprava pro Tento názorný postup

1.  Zavřete všechny otevřené řešení.

2.  Zkopírujte dva ukázkové soubory do místního počítače.

## <a name="start-debugging"></a>Spuštění ladění

### <a name="to-start-debugging"></a>Spustit ladění

1.  Z **soubor** nabídky, přejděte na příkaz **otevřete**a klikněte na tlačítko **souboru**.

2.  Vyhledejte *belowAvg.xsl* souboru a klikněte na tlačítko **otevřete**.

     Šablony stylů je otevřen v editoru XML.

3.  Klikněte na tlačítko Procházet (**...** ) na **vstup** pole v okně vlastností dokumentu.

4.  Vyhledejte *books.xml* souboru a klikněte na tlačítko **otevřete**.

     Toto nastaví zdrojový soubor dokumentu, který se používá pro transformace XSLT.

5.  Klikněte pravým tlačítkem myši `xsl:if` počáteční značka, přejděte na **zarážek**a klikněte na tlačítko **vložit zarážku**.

6.  Klikněte **ladění XSL** tlačítka na panelu nástrojů editoru XML.

To spustí proces ladění a několik nových oken, které jsou používány ladicího programu.

Existují dvě windows, které zobrazují vstupní dokument a styly listu. Ladicí program používá tyto windows zobrazit aktuální stav spuštění. Ladicí program je umístěn na `xsl:if` element šablony stylů a na prvním uzlu adresáře v *books.xml* souboru.

**Místní hodnoty –** okně se zobrazí všechny místní proměnné a jejich aktuální hodnoty. To zahrnuje proměnné definované v šabloně stylů a také proměnné, které používá ladicí program ke sledování uzly, které jsou aktuálně v kontextu.

**XSL výstup** okně se zobrazí výstup transformace XSL. Toto okno je oddělená od **Visual Studio výstup** okno.

## <a name="watch-window"></a>Kukátko – okno

### <a name="to-use-the-watch-window"></a>Chcete-li používat okna kukátka

1.  Z **ladění** nabídky, přejděte na příkaz **Windows**, přejděte na příkaz **sledovat**a klikněte na tlačítko **kukátko 1**.

     Díky tomu **kukátko 1** okno viditelné.

2.  Typ `$bookAverage` v **název** pole a stiskněte klávesu **Enter**.

     Hodnota `$bookAverage` proměnné se zobrazí v okně.

3.  Typ `self::node()` v **název** pole a stiskněte klávesu **Enter**.

     `self::node()` je výraz XPath, který vyhodnotí do aktuálního uzlu kontextu. Hodnota `self::node()` výraz XPath je prvním uzlu adresáře. To změní, když jsme průběhu procházení transformace.

4.  Rozbalte `self::node()` uzel a potom rozbalte `price` uzlu.

     To umožňuje zobrazit hodnotu ceny adresáře a jeho snadno porovnat `$bookAverage` hodnotu. Protože ceny adresáře je nižší než průměr, `xsl:if` uspěli podmínku.

## <a name="step-through-the-code"></a>Krok prostřednictvím kódu
 Ladicí program umožňuje provést jeden řádek kódu v čase.

### <a name="to-step-through-the-code"></a>Procházet kód

1.  Stiskněte klávesu **F5** pokračujte.

     Protože splněna prvního uzlu adresáře `xsl:if` podmínku, uzel adresáře je přidán do **XSL výstup** okno. Ladicí program bude pokračovat v provádění, dokud je znovu umístěný na `xsl:if` element v šabloně stylů. Ladicí program je teď nastavený na druhém uzlu adresáře v *books.xml* souboru.

     V **kukátko 1** okno `self::node()` hodnotu změny ve druhém uzlu adresáře. Prověřením hodnota elementu ceny, můžete určit, že cena je vyšší než průměr, proto `xsl:if` podmínka má selhat.

2.  Stiskněte klávesu **F5** pokračujte.

     Protože nesplňuje druhého uzlu adresáře `xsl:if` podmínku uzlu adresáře není přidáno do **XSL výstup** okno. Ladicí program bude pokračovat v provádění, dokud je znovu umístěný na `xsl:if` element v šabloně stylů. Ladicí program je teď nastavený na třetí `book` uzlu *books.xml* souboru.

     V **kukátko 1** okno `self::node()` hodnota změní na uzlu třetí adresáře. Prověřením hodnotu `price` elementu, můžete určit, že cena je nižší než průměr, proto `xsl:if` uspěli podmínku.

3.  Stiskněte klávesu **F5** pokračujte.

     Protože `xsl:if` byla splněna podmínka, třetí adresáře se přidá do **XSL výstup** okno. Zpracování všech knih v dokumentu XML a ladicí program zastaví.

## <a name="sample-files"></a>Ukázkové soubory

Následující dva soubory jsou používány návodu.

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>Books.XML

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Viz také:

- [Ladění XSLT](../xml-tools/debugging-xslt.md)