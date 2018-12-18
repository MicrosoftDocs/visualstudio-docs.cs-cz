---
title: 'Návod: Používání IntelliSense XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86a71a70296a3b4e49f2cf7c596a7f71063c8297
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693520"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Návod: Používání IntelliSense XSLT

Tento návod ukazuje, jak pomocí XSLT IntelliSense automatické dokončování hodnoty některých atributů.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Použití technologie IntelliSense v atribut názvu xsl: s param a prvek xsl: Call – elementy šablony

1.  Vytvořte nový soubor XSLT a zkopírujte následující kód:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <!-- These 2 elements effectively assign
         $messages = resources/en.xml/<messages>,
         then $messages is used in the "localized-message" template.  -->
    <xsl:param name="lang">en</xsl:param>
    <xsl:variable name="messages"
          select="document(concat('resources/', $lang, '.xml'))/messages"/>

    <xsl:template name="msg23" match="msg23">
    </xsl:template>

    <xsl:template name="localized-message">
      <xsl:param name="msgcode"/>
      <!-- Show message string. -->
      <xsl:message terminate="yes">
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>
      </xsl:message>
    </xsl:template>
    </xsl:stylesheet>
    ```

2.  Vložit kurzor po `<xsl:template name="msg23" match="msg23">` a stiskněte klávesu **Enter**. Začněte psát následující `xsl:call-template` element:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Se zobrazí v seznamu názvy šablon `name=""` atribut `xsl:call-template` element při psaní.

3.  Vložit kurzor po `<xsl:call-template name="localized-message">` a stiskněte klávesu **Enter**. Začněte psát následující `xsl:with-param` element:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Seznam názvů parametrů se zobrazí v `name=""` atribut `xsl:with-param` elementu.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Použití technologie IntelliSense v režimu atribut xsl: element použít šablony

1.  Vytvořte nový soubor XSLT a zkopírujte následující kód:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
      <xsl:template match="/">
        <HTML>
          <BODY>
            <TABLE>
              <xsl:apply-templates select="customers/customer">
                <xsl:sort select="state"/>
                <xsl:sort select="name"/>
              </xsl:apply-templates>
            </TABLE>
          </BODY>
        </HTML>
      </xsl:template>
      <xsl:template match="customer">
        <TR>
          <xsl:apply-templates select="name" />
          <xsl:apply-templates select="address" />
          <xsl:apply-templates select="phone" />
        </TR>
      </xsl:template>
      <xsl:template match="name">
        <TD STYLE="font-size:14pt font-family:serif">
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="address">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone">
        <TD>
          <xsl:apply-templates />
        </TD>
      </xsl:template>
      <xsl:template match="phone" mode="accountNumber">
        <xsl:param name="Area_Code"/>
        <TD STYLE="font-style:italic">
          1-<xsl:value-of select="."/>-001
        </TD>
      </xsl:template>
    </xsl:stylesheet>
    ```

2.  Vložit kurzor po `<xsl:apply-templates select="phone" />` a stiskněte klávesu **Enter**. Začněte psát následující `xsl: apply-templates` element:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Seznam režimů šablonu se zobrazí v `mode=""` atribut `xsl:apply-templates` elementu.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Použití technologie IntelliSense v předponu šablony stylů a výsledek předponu atributy xsl:namespace-alias – element

1.  Vytvořte nový soubor XSLT a zkopírujte následující kód:

    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"
    version="1.0">
      <xsl:param name="browser" select="'InternetExplorer'"/>
      <xsl:template match="/">
        <alt:stylesheet>
          <xsl:choose>
            <xsl:when test="$browser='InternetExplorer'">
              <alt:import href="IERoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:when>
            <xsl:otherwise>
              <alt:import href="OtherBrowserRoutines.xsl"/>
              <alt:template match="/">
                <div>
                  <alt:call-template name="showTable"/>
                </div>
              </alt:template>
            </xsl:otherwise>
          </xsl:choose>
        </alt:stylesheet>
      </xsl:template>
    </xsl:stylesheet>
    ```

2.  Vložit kurzor po `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` a stiskněte klávesu **Enter**. Začněte psát následující `xsl:namespace-alias` element:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Všimněte si, jak seznam předpon zobrazovaly v `stylesheet-prefix` a `result-prefix` atributy `xsl:namespace-alias` elementu.

## <a name="see-also"></a>Viz také:

- [Funkce editoru XML IntelliSense](../xml-tools/xml-editor-intellisense-features.md)