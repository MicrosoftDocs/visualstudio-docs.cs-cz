---
title: 'Návod: Používání hierarchie XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9f3fe246189313dcc04176e2971ad448a1b2cff8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604434"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>Návod: použití hierarchie XSLT

Nástroj hierarchie XSLT zjednodušuje mnoho úloh vývoje XML. Šablona stylů XSLT často používá `includes` a `imports` pokyny. Kompilace začíná z hlavní šablony stylů, ale pokud se zobrazí chyba v důsledku kompilování šablony stylů XSLT, může být chyba z jiného zdroje než z hlavní šablony stylů. Oprava chyby nebo úprav šablony stylů může vyžadovat přístup k zahrnutým nebo importovaným šablonám stylů. Rozkrokování přes šablonu stylů v ladicím programu může otevřít zahrnuté a importované šablony stylů a v některých případech můžete chtít přidat zarážku v jedné nebo více zahrnutých šablonách stylů.

Další situací, kdy může být užitečný nástroj hierarchie XSLT, je vložení zarážek na předdefinovaná pravidla šablony. Pravidla šablony jsou speciální šablony vygenerované pro každý režim šablony stylů a volány `xsl:apply-templates`, když se uzel neshoduje s žádnou jinou šablonou. Chcete-li implementovat ladění v předdefinovaných pravidlech šablon, ladicí program XSLT vytvoří soubor s pravidly v dočasné složce a zkompiluje je spolu s hlavní šablonou stylů. Bez krokování kódu z některých `xsl:apply-template` může být obtížné najít šablony stylů, které byly zahrnuty do hlavní šablony stylů, nebo vyhledat a otevřít šablonu stylů s vestavěnými pravidly šablon.

Příklad v tomto tématu ukazuje ladění v odkazované šabloně stylů.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Ladění v odkazované šabloně stylů

1. Otevřete dokument XML v aplikaci Visual Studio. Tento příklad používá následující dokument:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. Přidejte následující *xslincludefile. xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3. Přidejte následující soubor *xslinclude. xsl* :

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4. Přidejte zarážku na instrukci `<xsl:include href="xslincludefile.xsl" />`.

5. Spustit ladění.

6. Po zastavení ladicího programu na `<xsl:include href="xslincludefile.xsl" />` instrukcí klikněte na tlačítko **Krokovat** s vnořením. Ladění lze pokračovat v odkazované šabloně stylů. Hierarchie je viditelná a Návrhář zobrazuje správnou cestu.

## <a name="see-also"></a>Viz také:

- [Profiler XSLT](../xml-tools/xslt-profiler.md)