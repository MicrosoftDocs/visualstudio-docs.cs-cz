---
title: 'Návod: ladění šablony stylů XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c205ff68ebc51d0b0f5b32038763c1741855d7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656109"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Návod: Ladění šablony stylů XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroky v tomto návodu ukazují, jak používat ladicí program XSLT. Postup zahrnuje proměnné pro zobrazení, nastavení zarážek a krokování kódu. Předloha se styly vyhledá všechny knihy, které jsou náklady pod průměrnou cenou za knihu.

### <a name="to-prepare-for-this-walkthrough"></a>Příprava na tento návod

1. Zavřete všechna otevřená řešení.

2. Zkopírujte dva ukázkové soubory do místního počítače.

## <a name="start-debugging"></a>Spustit ladění

#### <a name="to-start-debugging"></a>Spuštění ladění

1. V nabídce **soubor** přejděte na příkaz **otevřít**a klikněte na možnost **soubor**.

2. Vyhledejte soubor belowAvg. XSL a klikněte na tlačítko **otevřít**.

    Šablona stylů se otevře v editoru XML.

3. Klikněte na tlačítko pro procházení (**...**) v poli **input** okna vlastností dokumentu.

4. Vyhledejte soubor books.xml a klikněte na tlačítko **otevřít**.

    Tím se nastaví zdrojový soubor dokumentu, který se používá pro transformaci XSLT.

5. Klikněte pravým tlačítkem myši na `xsl:if` značku Start, přejděte na **zarážku**a klikněte na **Vložit zarážku**.

6. Klikněte na tlačítko **LADIT XSL** na panelu nástrojů editoru XML.

   Tím se spustí proces ladění a otevře několik nových oken, které používá ladicí program.

   Existují dvě okna, kde je zobrazen vstupní dokument a šablona stylů. Ladicí program používá tato okna k zobrazení aktuálního stavu provádění. Ladicí program je umístěn na `xsl:if` prvku v šabloně stylů a na prvním uzlu knihy v souboru books.xml.

   V okně místní hodnoty se zobrazí všechny místní proměnné a jejich aktuální hodnoty. To zahrnuje proměnné definované v šabloně stylů a také proměnné, které ladicí program používá ke sledování uzlů, které jsou aktuálně v kontextu.

   V okně **výstupu XSL** se zobrazí výstup transformace XSL. Toto okno je nezávislé na okně **výstupu sady Visual Studio** .

## <a name="watch-window"></a>Okno kukátka

#### <a name="to-use-the-watch-window"></a>Použití okno Kukátko

1. V nabídce **ladění** přejděte na **Windows**, přejděte na **sledování**a klikněte na **sledovat 1**.

     Tím se okno kukátko 1 zobrazuje.

2. `$bookAverage`Do pole **název** zadejte a stiskněte klávesu ENTER.

     Hodnota `$bookAverage` proměnné se zobrazí v okně.

3. `self::node()`Do pole **název** zadejte a stiskněte klávesu ENTER.

     `self::node()` je výraz XPath, který je vyhodnocen na aktuální kontextový uzel. Hodnota `self::node()` výrazu XPath je první uzel knihy. Tím se změny provedou v průběhu transformace.

4. Rozbalte `self::node()` uzel a potom rozbalte `price` uzel.

     To vám umožní zobrazit hodnotu ceny za knihu a můžete ji snadno porovnat s `$bookAverage` hodnotou. Vzhledem k tomu, že se cena za knihu nachází pod průměrem, `xsl:if` Podmínka by měla být úspěšná.

## <a name="step-through-the-code"></a>Krokovat kód
 Ladicí program umožňuje spustit kód po jednotlivých řádcích.

#### <a name="to-step-through-the-code"></a>Postup procházení kódu

1. Pokračujte stisknutím **F5**.

     Vzhledem k tomu, že první uzel knihy splnil `xsl:if` podmínku, uzel Book se přidá do okna výstupu XSL. Ladicí program bude pokračovat, dokud nebude znovu umístěn u `xsl:if` prvku v šabloně stylů. Ladicí program je nyní umístěn na druhém uzlu Book v souboru books.xml.

     V okně Watch1 se `self::node()` hodnota změní na druhý uzel Book. Prozkoumáním hodnoty cenového prvku můžete zjistit, že cena je nad průměrem, takže `xsl:if` Podmínka by měla selhat.

2. Pokračujte stisknutím **F5**.

     Vzhledem k tomu, že druhý uzel knihy nesplňuje `xsl:if` podmínky, uzel Book není přidán do okna výstupu XSL. Ladicí program bude pokračovat, dokud nebude znovu umístěn u `xsl:if` prvku v šabloně stylů. Ladicí program je nyní umístěn na třetím `book` uzlu v souboru books.xml.

     V okně Watch1 se `self::node()` hodnota změní na uzel třetí knihy. Prozkoumáním hodnoty `price` elementu můžete určit, že cena je nižší než průměr, takže `xsl:if` Podmínka by měla být úspěšná.

3. Pokračujte stisknutím **F5**.

     Vzhledem k tomu `xsl:if` , že podmínka byla splněna, třetí kniha je přidána do okna výstupu XSL. Všechny knihy v dokumentu XML byly zpracovány a ladicí program se zastaví.

## <a name="sample-files"></a>Ukázkové soubory
 Následující dva soubory jsou používány v tomto návodu.

### <a name="belowavgxsl"></a>belowAvg. xsl

```
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

### <a name="booksxml"></a>books.xml

```
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

## <a name="see-also"></a>Viz také
 [Ladění XSLT](../xml-tools/debugging-xslt.md)
