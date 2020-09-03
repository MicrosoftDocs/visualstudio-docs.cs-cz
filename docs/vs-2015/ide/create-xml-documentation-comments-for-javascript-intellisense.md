---
title: Vytvoření dokumentačních komentářů XML pro JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619550"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Vytvoření dokumentačních komentářů XML pro JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Dokumentační komentáře XML* jsou komentáře JavaScriptu, které přidáte do skriptu k poskytnutí informací o prvcích kódu, jako jsou například funkce, pole a proměnné. V aplikaci Visual Studio jsou tyto textové popisy při odkazování na funkci skriptu zobrazeny v technologii IntelliSense.

 V tomto tématu najdete základní kurz k používání dokumentačních komentářů XML. Informace o používání dalších prvků, jako jsou [\<var>](../ide/var-javascript.md) a a [\<value>](../ide/value-javascript.md) Další příklady kódu, naleznete v [dokumentaci k dokumentaci XML](../ide/xml-documentation-comments-javascript.md). Informace o poskytování informací technologie IntelliSense pro asynchronní zpětné volání, jako je `Promise` například, naleznete v tématu [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> Dokumentační komentáře XML jsou k dispozici pouze z odkazovaných souborů, sestavení a služeb.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Vytvoření dokumentačních komentářů XML pro funkci JavaScriptu

- Ve funkci, přidejte [\<summary>](../ide/summary-javascript.md) prvky, [\<param>](../ide/param-javascript.md) a a [\<returns>](../ide/returns-javascript.md) před každý prvek se třemi lomítky (///).

    > [!NOTE]
    > Každý prvek musí být na jednom řádku.

     Následující příklad ukazuje funkci JavaScriptu.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Chcete-li zobrazit dokumentační komentáře XML, zadejte název a levou závorku funkce, která je označena dokumentačními komentáři XML, jak je uvedeno v následujícím příkladu:

    ```javascript
    var areaVal = getArea(
    ```

     Když zadáte levou závorku funkce, která obsahuje dokumentační komentáře XML, Editor kódu použije technologii IntelliSense k zobrazení informací, které jsou definovány v dokumentačních komentářích XML.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Vytvoření dokumentačních komentářů XML pro pole JavaScriptu

- V definici funkce nebo objektu konstruktoru přidejte [\<field>](../ide/field-javascript.md) element, kterému předchází tři lomítka (///).

     Následující příklad ukazuje použití `<field>` prvku ve funkci konstruktoru. Další příklady naleznete v tématu [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Chcete-li zobrazit dokumentační komentáře XML, vytvořte objekt pomocí konstruktoru funkce, který je označen pomocí dokumentačních komentářů XML, jak je uvedeno v následujícím příkladu.

    ```javascript
    var eng = new Engine();
    ```

- Na dalším řádku zadejte název objektu a tečku pro zobrazení informací o IntelliSense pro pole.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Vytvoření dokumentačních komentářů XML pro přetíženou funkci

1. Ve funkci přidejte [\<signature>](../ide/signature-javascript.md) prvek pro každé přetížení. V těchto prvcích přidejte další prvky, jako například `<summary>` , `<param>` a `<returns>` , před každý prvek se třemi lomítky (///).

     Následující příklad ukazuje přetíženou funkci JavaScriptu. V tomto příkladu se přetížení liší podle typu parametru.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Chcete-li zobrazit dokumentační komentáře XML, zadejte název a levou závorku funkce, která je označena dokumentačními komentáři XML, jak je uvedeno v následujícím příkladu:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Vytvoření lokalizované technologie IntelliSense

1. Vytvořte soubor XML, který obsahuje dokumentační komentáře ve formátu OpenAjax MessageBundle.

    > [!IMPORTANT]
    > MessageBundle je doporučený formát. Tento formát není podporován v Microsoft Ajax nebo v souborech. winmd. Informace o použití alternativního `VSDoc` formátu naleznete v tématu [\<loc>](../ide/loc-javascript.md) .

     Následující příklad ukazuje obsah v souboru. postranníer, který obsahuje lokalizované informace technologie IntelliSense. Jedná se o soubor XML, který je umístěn ve složce specifické pro jazykovou verzi, jako je například JA. Složka musí být ve stejném umístění jako soubor. js, který obsahuje `<loc>` element. Název souboru XML se musí shodovat s `filename` parametrem zadaným v `<loc>` elementu.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. V souboru. js přidejte následující kód. `<loc>`Element musí být deklarován před libovolným skriptem a musí splňovat stejná pravidla použití jako `<reference>` element. Další informace naleznete v tématu [JavaScript IntelliSense](../ide/javascript-intellisense.md) a [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. V souboru. js přidejte prvky dokumentace XML a výchozí popisy. Nastavte `locid` hodnoty atributu tak, aby odpovídaly odpovídajícím `name` hodnotám atributu ze souboru. vozík. Výchozí popisy budou nahrazeny lokalizovanou informací technologie IntelliSense, pokud jsou k dispozici.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Chcete-li zobrazit dokumentační komentáře XML, zadejte název a levou závorku funkce, jako v následujícím příkladu:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Viz také
 [JavaScript](../ide/javascript-intellisense.md) – [Komentáře k dokumentaci XML](../ide/xml-documentation-comments-javascript.md) IntelliSense [NIB: návod: JavaScript IntelliSense v ASP.NET](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
