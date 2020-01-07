---
title: Ladit šablony stylů XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592474"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Návod: ladění šablony stylů XSLT

Kroky v tomto návodu ukazují, jak používat ladicí program XSLT. Postup zahrnuje proměnné pro zobrazení, nastavení zarážek a krokování kódu. Ladicí program umožňuje spustit kód po jednotlivých řádcích.

Pro přípravu k tomuto návodu nejdřív zkopírujte dva [ukázkové soubory](#sample-files) do místního počítače. Jedna je předloha se styly a jedna je soubor XML, který použijeme jako vstup do šablon stylů. V tomto návodu se v šabloně stylů používá vyhledáváme všechny knihy, jejichž cena je nižší než průměrná cena za knihu.

> [!NOTE]
> Ladicí program XSLT je k dispozici pouze v edici Enterprise sady Visual Studio.

## <a name="start-debugging"></a>Spustit ladění

1. V nabídce **soubor** klikněte na příkaz **otevřít** > **soubor**.

2. Vyhledejte soubor *below-Average. xsl* a klikněte na tlačítko **otevřít**.

   Šablona stylů se otevře v editoru XML.

3. Klikněte na tlačítko pro procházení ( **...** ) v poli **input** okna vlastností dokumentu. (Pokud se okno **vlastnosti** nezobrazí, klikněte pravým tlačítkem myši kamkoli na otevřený soubor v editoru a pak zvolte **vlastnosti**.)

4. Vyhledejte soubor *Books. XML* a pak zvolte **otevřít**.

   Tím se nastaví zdrojový soubor dokumentu, který se používá pro transformaci XSLT.

5. Nastavte [zarážku](../debugger/using-breakpoints.md) na řádku 12 souboru *below-Average. xsl*. Můžete to udělat jedním z několika způsobů:

   - Klikněte na okraj editoru na řádku 12.

   - Klikněte kamkoli na řádek 12 a pak stiskněte **F9**.

   - Klikněte pravým tlačítkem na značku `xsl:if` Start a pak zvolte **zarážku** > **Vložit zarážku**.

      ![Vložit zarážku v souboru XSL v aplikaci Visual Studio](media/insert-breakpoint.PNG)

6. Na panelu nabídek vyberte **XML** > **Spustit ladění XSLT** (nebo stiskněte klávesu **ALT**+**F5**).

   Spustí se proces ladění.

   V editoru je ladicí program umístěn v prvku `xsl:if` v šabloně stylů. V editoru se otevře jiný soubor s názvem *below-Average. XML* . Toto je výstupní soubor, který se naplní jako každý uzel ve vstupních *knihách souborů. XML* .

   Okna **Automatické**hodnoty, **místní**hodnoty a **kukátko 1** se zobrazí v dolní části okna sady Visual Studio. V okně **místní** hodnoty se zobrazí všechny místní proměnné a jejich aktuální hodnoty. To zahrnuje proměnné definované v šabloně stylů a také proměnné, které ladicí program používá ke sledování uzlů, které jsou aktuálně v kontextu.

## <a name="watch-window"></a>Okno kukátka

Do okna **kukátko 1** přidáte dvě proměnné, abychom mohli analyzovat jejich hodnoty, když se zpracuje vstupní soubor. (Můžete také použít okno **místní** hodnoty k prohlédnutí hodnot, pokud proměnné, které chcete sledovat, již existují.)

1. V nabídce **ladění** vyberte možnost **Windows** > **sledovat** > **kukátko 1**.

   Okno **kukátko 1** se zobrazí.

2. Do pole **název** zadejte `$bookAverage` a potom stiskněte klávesu **ENTER**.

   Hodnota proměnné `$bookAverage` se zobrazí v poli **hodnota** .

3. Na dalším řádku zadejte do pole **název** `self::node()` a potom stiskněte klávesu **ENTER**.

   `self::node()` je výraz XPath, který je vyhodnocen na aktuální kontextový uzel. Hodnota výrazu XPath `self::node()` je první uzel knihy. Tím se změny provedou v průběhu transformace.

4. Rozbalte uzel `self::node()` a poté rozbalte položku uzel, který je hodnotou `price`.

   ![okno Kukátko při ladění XSLT v aplikaci Visual Studio](media/xslt-debugging-watch-window.png)

   Můžete zobrazit hodnotu ceny za knihu pro aktuální uzel knihy a porovnat ji s `$bookAverage` hodnotou. Vzhledem k tomu, že se cena za knihu nachází pod průměrem, `xsl:if` podmínka by měla být při pokračování procesu ladění úspěšná.

## <a name="step-through-the-code"></a>Krokovat kód

1. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že první uzel knihy splnil stav `xsl:if`, uzel Book se přidá do výstupního souboru *below-Average. XML* . Ladicí program bude pokračovat, dokud nebude znovu umístěn v prvku `xsl:if` v šabloně stylů. Ladicí program je nyní umístěn na druhém uzlu Book v souboru *Books. XML* .

   V okně **kukátko 1** se hodnota `self::node()` změní na druhý uzel Book. Prozkoumáním hodnoty cenového prvku můžete zjistit, že cena je nad průměrem, takže `xsl:if` podmínka by měla selhat.

2. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že druhý uzel knihy nesplňuje podmínky `xsl:if`, uzel Book není přidán do výstupního souboru *below-Average. XML* . Ladicí program bude pokračovat, dokud nebude znovu umístěn v prvku `xsl:if` v šabloně stylů. Ladicí program je nyní umístěn na třetím `book` uzlu v souboru *Books. XML* .

   V okně **kukátko 1** se hodnota `self::node()` změní na uzel třetí knihy. Prozkoumáním hodnoty `price` elementu můžete určit, že cena je nižší než průměr. Podmínka `xsl:if` by měla být úspěšná.

3. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že podmínka `xsl:if` byla splněna, třetí kniha je přidána do výstupního souboru *below-Average. XML* . Všechny knihy v dokumentu XML byly zpracovány a ladicí program se zastaví.

## <a name="sample-files"></a>Ukázkové soubory

Následující dva soubory jsou používány v tomto návodu.

### <a name="below-averagexsl"></a>Below-Average. xsl

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

### <a name="booksxml"></a>Books. XML

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
