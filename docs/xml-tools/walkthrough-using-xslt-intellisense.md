---
title: 'Návod: Používání IntelliSense XSLT'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 606c4ad307de46d19989d14e2c660cc0286cb803
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604379"
---
# <a name="walkthrough-using-xslt-intellisense"></a>Návod: Používání IntelliSense XSLT

Tento návod ukazuje, jak použít IntelliSense XSLT k automatickému dokončení hodnoty některých atributů.

## <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Chcete-li použít IntelliSense v atributu name elementu xsl: with-param a element xsl: call-template

1. Vytvořte nový soubor XSLT a zkopírujte do něj následující kód:

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

2. Vložte kurzor po `<xsl:template name="msg23" match="msg23">` a stiskněte klávesu **ENTER**. Pak začněte psát následující prvek `xsl:call-template`:

    ```xml
    <xsl:call-template name="localized-message">
    </xsl:call-template>
    ```

     Seznam názvů šablon se zobrazí v atributu `name=""` `xsl:call-template` elementu při psaní.

3. Vložte kurzor po `<xsl:call-template name="localized-message">` a stiskněte klávesu **ENTER**. Pak začněte psát následující prvek `xsl:with-param`:

    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>
    ```

     Seznam názvů parametrů se zobrazí v atributu `name=""` `xsl:with-param` elementu.

## <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Chcete-li použít technologii IntelliSense v atributu mode elementu xsl: Apply-Templates

1. Vytvořte nový soubor XSLT a zkopírujte do něj následující kód:

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

2. Vložte kurzor po `<xsl:apply-templates select="phone" />` a stiskněte klávesu **ENTER**. Pak začněte psát následující prvek `xsl: apply-templates`:

    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">
    ```

     Seznam režimů šablon se zobrazí v atributu `mode=""` `xsl:apply-templates` elementu.

## <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Použití IntelliSense v atributech StyleSheet-prefix a Result-prefix elementu xsl: Namespace-alias

1. Vytvořte nový soubor XSLT a zkopírujte do něj následující kód:

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

2. Vložte kurzor po `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` a stiskněte klávesu **ENTER**. Pak začněte psát následující prvek `xsl:namespace-alias`:

    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>
    ```

     Všimněte si, jak se seznam prefixů objevil v atributech `stylesheet-prefix` a `result-prefix` elementu `xsl:namespace-alias`.

## <a name="see-also"></a>Viz také:

- [Funkce IntelliSense v editoru XML](../xml-tools/xml-editor-intellisense-features.md)