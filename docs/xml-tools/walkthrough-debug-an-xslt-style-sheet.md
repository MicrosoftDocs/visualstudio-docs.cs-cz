---
title: Ladit šablony stylů XSLT
description: Naučte se používat ladicí program XSLT v aplikaci Visual Studio k ladění šablony stylů XSLT pomocí kroků v tomto návodu.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a6f1efc85366bc74206dc8637c992f249c4eb44
ms.sourcegitcommit: e443866e3468f838bc3655ad56a83a552013ceed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2021
ms.locfileid: "98925884"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Návod: Ladění šablony stylů XSLT

Kroky v tomto návodu ukazují, jak používat ladicí program XSLT. Postup zahrnuje proměnné pro zobrazení, nastavení zarážek a krokování kódu. Ladicí program umožňuje spustit kód po jednotlivých řádcích.

Pro přípravu k tomuto návodu nejdřív zkopírujte dva [ukázkové soubory](#sample-files) do místního počítače. Jedna je předloha se styly a jedna je soubor XML, který použijeme jako vstup do šablon stylů. V tomto návodu se v šabloně stylů používá vyhledáváme všechny knihy, jejichž cena je nižší než průměrná cena za knihu.

> [!NOTE]
> Ladicí program XSLT je k dispozici pouze v edicích Professional a Enterprise sady Visual Studio.

## <a name="start-debugging"></a>Spustit ladění

1. V nabídce **soubor** klikněte na příkaz **otevřít**  >  **soubor**.

2. Vyhledejte soubor *below-Average. xsl* a klikněte na tlačítko **otevřít**.

   Šablona stylů se otevře v editoru XML.

3. Klikněte na tlačítko pro procházení (**...**) v poli **input** okna vlastností dokumentu. (Pokud se okno **vlastnosti** nezobrazí, klikněte pravým tlačítkem myši kamkoli na otevřený soubor v editoru a pak zvolte **vlastnosti**.)

4. Vyhledejte soubor *books.xml* a pak zvolte možnost **otevřít**.

   Tím se nastaví zdrojový soubor dokumentu, který se používá pro transformaci XSLT.

5. Nastavte [zarážku](../debugger/using-breakpoints.md) na řádku 12 souboru *below-Average. xsl*. Můžete to udělat jedním z několika způsobů:

   - Klikněte na okraj editoru na řádku 12.

   - Klikněte kamkoli na řádek 12 a pak stiskněte **F9**.

   - Klikněte pravým tlačítkem na `xsl:if` značku Start a pak zvolte **zarážka**  >  **Vložit zarážku**.

      ![Vložit zarážku v souboru XSL v aplikaci Visual Studio](media/insert-breakpoint.PNG)

6. Na panelu nabídek vyberte **XML**  >  **Spustit ladění XSLT** (nebo stiskněte klávesu **ALT** + **F5**).

   Spustí se proces ladění.

   V editoru je ladicí program umístěn na `xsl:if` prvku v šabloně stylů. V editoru se otevře jiný soubor s názvem *below-average.xml* . Toto je výstupní soubor, který se naplní jako každý uzel ve vstupním souboru, *books.xml* se zpracovává.

   Okna **Automatické** hodnoty, **místní** hodnoty a **kukátko 1** se zobrazí v dolní části okna sady Visual Studio. V okně **místní** hodnoty se zobrazí všechny místní proměnné a jejich aktuální hodnoty. To zahrnuje proměnné definované v šabloně stylů a také proměnné, které ladicí program používá ke sledování uzlů, které jsou aktuálně v kontextu.

## <a name="watch-window"></a>Kukátko – okno

Do okna **kukátko 1** přidáte dvě proměnné, abychom mohli analyzovat jejich hodnoty, když se zpracuje vstupní soubor. (Můžete také použít okno **místní** hodnoty k prohlédnutí hodnot, pokud proměnné, které chcete sledovat, již existují.)

1. V nabídce **ladění** vyberte možnost sledování **kukátko**  >    >  **1**.

   Okno **kukátko 1** se zobrazí.

2. `$bookAverage`Do pole **název** zadejte a stiskněte klávesu **ENTER**.

   Hodnota `$bookAverage` proměnné se zobrazí v poli **hodnota** .

3. Do dalšího řádku zadejte `self::node()` pole **název** a stiskněte klávesu **ENTER**.

   `self::node()` je výraz XPath, který je vyhodnocen na aktuální kontextový uzel. Hodnota `self::node()` výrazu XPath je první uzel knihy. Tím se změny provedou v průběhu transformace.

4. Rozbalte `self::node()` uzel a potom rozbalte položku uzel, který je jeho hodnotou `price` .

   ![okno Kukátko při ladění XSLT v aplikaci Visual Studio](media/xslt-debugging-watch-window.png)

   Můžete zobrazit hodnotu ceny za knihu pro aktuální uzel knihy a porovnat ji s `$bookAverage` hodnotou. Vzhledem k tomu, že se cena za knihu nachází pod průměrem, `xsl:if` při pokračování procesu ladění by podmínka měla být úspěšná.

## <a name="step-through-the-code"></a>Krokovat kód

1. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že první uzel knihy splnil `xsl:if` podmínku, uzel Book se přidá do výstupního souboru *below-average.xml* . Ladicí program bude pokračovat, dokud nebude znovu umístěn u `xsl:if` prvku v šabloně stylů. Ladicí program je nyní umístěn na druhém uzlu Book v souboru *books.xml* .

   V okně **kukátko 1** se `self::node()` hodnota změní na druhý uzel Book. Prozkoumáním hodnoty cenového prvku můžete zjistit, že cena je nad průměrem, takže `xsl:if` Podmínka by měla selhat.

2. Pokračujte stisknutím **F5**.

   Vzhledem k tomu, že druhý uzel knihy nesplňuje `xsl:if` podmínky, uzel Book není přidán do výstupního souboru *below-average.xml* . Ladicí program bude pokračovat, dokud nebude znovu umístěn u `xsl:if` prvku v šabloně stylů. Ladicí program je nyní umístěn na třetím `book` uzlu v souboru *books.xml* .

   V okně **kukátko 1** se `self::node()` hodnota změní na uzel třetí knihy. Prozkoumáním hodnoty `price` elementu můžete určit, že cena je nižší než průměr. `xsl:if`Podmínka by měla být úspěšná.

3. Pokračujte stisknutím **F5**.

   Vzhledem k tomu `xsl:if` , že podmínka byla splněna, je do výstupního souboru *below-average.xml* přidána třetí kniha. Všechny knihy v dokumentu XML byly zpracovány a ladicí program se zastaví.

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

### <a name="booksxml"></a>books.xml

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
