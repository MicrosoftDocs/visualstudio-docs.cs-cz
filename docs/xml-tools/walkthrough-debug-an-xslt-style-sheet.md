---
title: Ladění šablon stylů XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301718"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Návod: Ladění šablony stylů XSLT

Kroky v tomto návodu ukazují, jak používat ladicí program XSLT. Kroky zahrnují zobrazení proměnných, nastavení zarážek a krokování kódu. Ladicí program umožňuje spustit kód po jednom řádku.

Chcete-li se připravit na tento návod, nejprve zkopírujte dva [ukázkové soubory](#sample-files) do místního počítače. Jedním z nich je šablona stylů a jedna je soubor XML, který použijeme jako vstup do šablony stylů. V tomto návodu šablona stylů, kterou používáme, najde všechny knihy, jejichž cena je nižší než průměrná cena knihy.

> [!NOTE]
> Ladicí program XSLT je k dispozici pouze v edici Enterprise sady Visual Studio.

## <a name="start-debugging"></a>Zahájit ladění

1. V nabídce **Soubor** zvolte **Otevřít** > **soubor**.

2. Vyhledejte soubor *podprůměrem.xsl* a zvolte **Otevřít**.

   Šablona stylů se otevře v editoru XML.

3. Klepněte na tlačítko procházet (**...**) v poli **Vstup** v okně vlastností dokumentu. (Pokud okno **Vlastnosti** není viditelné, klepněte pravým tlačítkem myši na libovolné místo v otevřeném souboru v editoru a pak zvolte **Vlastnosti**.)

4. Vyhledejte soubor *books.xml* a pak zvolte **Otevřít**.

   Tím nastavíte soubor zdrojového dokumentu, který se používá pro transformaci XSLT.

5. Nastavte [zarážku](../debugger/using-breakpoints.md) na řádku 12 *podprůměrem.xsl*. Můžete to provést jedním z několika způsobů:

   - Klikněte na okraj editoru na řádku 12.

   - Klikněte na libovolné místo na řádku 12 a stiskněte **klávesu F9**.

   - Klikněte pravým `xsl:if` tlačítkem myši na značku start a pak zvolte**Zarážka vložení zarážky zarážky** **zarážky** > .

      ![Vložení zarážky do souboru XSL v sadě Visual Studio](media/insert-breakpoint.PNG)

6. Na řádku nabídek zvolte **Xml** > **Start XSLT Debugging** (nebo stiskněte **Alt**+**F5**).

   Spustí se proces ladění.

   V editoru ladicí program je `xsl:if` umístěn na prvek šablony stylů. V editoru se otevře jiný soubor s názvem *podprůměrem.xml.* Jedná se o výstupní soubor, který bude naplněn při zpracování každého uzlu ve vstupním souboru *books.xml.*

   Okna **Autos**, **Locals**a **Watch 1** se zobrazí v dolní části okna sady Visual Studio. V okně **Locals** se zobrazí všechny místní proměnné a jejich aktuální hodnoty. To zahrnuje proměnné definované v šabloně stylů a také proměnné, které ladicí program používá ke sledování uzlů, které jsou aktuálně v kontextu.

## <a name="watch-window"></a>Kukátko – okno

Přidáme dvě proměnné do okna **Sledovat 1,** abychom mohli zkoumat jejich hodnoty při zpracování vstupního souboru. (Okno **Locals** můžete také použít ke kontrole hodnot, pokud proměnné, které chcete sledovat, již existují.)

1. Z nabídky **Ladění** zvolte **Windows** > **Watch** > **Watch 1**.

   Okno **Sledovat 1** se zobrazí.

2. Zadejte `$bookAverage` do pole **Název** a stiskněte **Enter**.

   Hodnota proměnné `$bookAverage` se zobrazí v poli **Hodnota.**

3. Na dalším řádku `self::node()` zadejte pole **Název** a stiskněte **Enter**.

   `self::node()`je výraz XPath, který vyhodnocuje aktuální kontextový uzel. Hodnota výrazu `self::node()` XPath je prvním uzlou knihou. To se mění, jak postupujeme transformací.

4. Rozbalte `self::node()` uzel a potom rozbalte hodnotu uzlu, kdo je `price`.

   ![Okno sledování během ladění XSLT v sadě Visual Studio](media/xslt-debugging-watch-window.png)

   Můžete zobrazit hodnotu ceny knihy pro aktuální uzel knihy a `$bookAverage` porovnat ji s hodnotou. Vzhledem k tomu, že `xsl:if` cena knihy je pod průměrem, podmínka by měla být úspěšná, když budete pokračovat v procesu ladění.

## <a name="step-through-the-code"></a>Krokovat kódem

1. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že `xsl:if` první uzel knihy splnil podmínku, je uzel knihy přidán do výstupního souboru *podprůměrem.xml.* Ladicí program pokračuje v provádění, dokud `xsl:if` není znovu umístěn na prvku v šabloně stylů. Ladicí program je nyní umístěn na druhém uzlu knihy v souboru *books.xml.*

   V okně **Sledovat** 1 `self::node()` se hodnota změní na druhý uzel knihy. Zkoumáním hodnoty cenového prvku můžete určit, že cena je nad `xsl:if` průměrem, proto by měla podmínka selhat.

2. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že `xsl:if` druhý uzel knihy nesplňuje podmínku, uzel knihy není přidán do výstupního souboru *podprůměrem.xml.* Ladicí program pokračuje v provádění, dokud `xsl:if` není znovu umístěn na prvku v šabloně stylů. Ladicí program je nyní `book` umístěn na třetím uzlu v souboru *books.xml.*

   V okně **Kukátko 1** se `self::node()` hodnota změní na třetí uzel knihy. Prozkoumáním hodnoty `price` prvku můžete určit, že cena je pod průměrem. Podmínka `xsl:if` by měla být úspěšná.

3. Pokračujte stisknutím **F5**.

   Vzhledem `xsl:if` k tomu, že podmínka byla splněna, třetí kniha je přidána do výstupního souboru *podprůměrem.xml.* Všechny knihy v dokumentu XML byly zpracovány a ladicí program se zastaví.

## <a name="sample-files"></a>Ukázkové soubory

Následující dva soubory jsou používány v návodu.

### <a name="below-averagexsl"></a>pod-average.xsl

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
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>Books.xml

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

## <a name="see-also"></a>Viz také

- [Ladění XSLT](../xml-tools/debugging-xslt.md)
