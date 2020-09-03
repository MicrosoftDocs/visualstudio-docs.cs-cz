---
title: 'Návod: použití hierarchie XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 46e6acc8f65a9c9589348508f57cc75b04c61ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669548"
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Návod: Používání hierarchie XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj hierarchie XSLT zjednodušuje mnoho úloh vývoje XML. Šablony stylů XSLT často používají `includes` a `imports` pokyny. Kompilace začíná z hlavní šablony stylů, ale pokud se zobrazí chyba v důsledku kompilování šablony stylů XSLT, může být chyba z jiného zdroje než z hlavní šablony stylů. Oprava chyby nebo úprav šablony stylů může vyžadovat přístup k zahrnutým nebo importovaným šablonám stylů. Rozkrokování přes šablonu stylů v ladicím programu může otevřít zahrnuté a importované šablony stylů a v některých případech můžete chtít přidat zarážku v jedné nebo více zahrnutých šablonách stylů.

 Další situací, kdy může být užitečný nástroj hierarchie XSLT, je vložení zarážek na předdefinovaná pravidla šablony. Pravidla šablony jsou speciální šablony generované pro každý režim šablony stylů a volány v `xsl:apply-templates` případě, že uzel nevyhovuje žádné jiné šabloně. Chcete-li implementovat ladění v předdefinovaných pravidlech šablon, ladicí program XSLT vytvoří soubor s pravidly v dočasné složce a zkompiluje je spolu s hlavní šablonou stylů. Bez krokování kódu z některých `xsl:apply-template` může být obtížné najít šablony stylů, které byly zahrnuty do hlavní šablony stylů, nebo vyhledat a otevřít šablonu stylů s předdefinovanými pravidly šablon.

 Příklad v tomto tématu ukazuje ladění v odkazované šabloně stylů.

### <a name="procedure-title"></a>Název procedury

1. Otevřete dokument XML v aplikaci Visual Studio. Tento příklad používá následující `collection.xml` dokument.

    ```
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

2. Přidejte následující `xslincludefile.xsl` :

    ```
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

3. Přidejte následující `xslinclude.xsl` soubor:

    ```
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

4. Přidejte zarážku do instrukce: `<xsl:include href="xslincludefile.xsl" />`

5. Spuštění ladění

6. Po zastavení ladicího programu na pokyn `<xsl:include href="xslincludefile.xsl" />` stiskněte tlačítko krok do. Všimněte si, že ladění může pokračovat v odkazované šabloně stylů. Hierarchie je viditelná a Návrhář zobrazuje správnou cestu.

## <a name="see-also"></a>Viz také
 [Návod: Profiler XSLT](../xml-tools/walkthrough-xslt-profiler.md)
