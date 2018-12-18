---
title: Vytvoření komentářů k dokumentaci XML pro technologie IntelliSense jazyka JavaScript | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d15144a2cee70e5f6bdc496bf2c09eb8fb95c85d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220555"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Vytvoření komentářů k dokumentaci XML pro technologie IntelliSense jazyka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Dokumentační komentáře XML* jsou JavaScript komentáře, že přidáte do skriptu k poskytnutí informací o kódu prvky, jako jsou functions, polí a proměnné. V sadě Visual Studio tyto textové popisy jsou zobrazovány s technologií IntelliSense při odkazu funkce skriptu.  
  
 Toto téma obsahuje základní kurz o používání dokumentační komentáře XML. Další informace o použití další prvky, jako například [ \<var >](../ide/var-javascript.md) a [ \<hodnota >](../ide/value-javascript.md)a další příklady naleznete v tématu [dokumentační komentáře XML ](../ide/xml-documentation-comments-javascript.md). Informace o získání informací technologie IntelliSense pro asynchronní zpětné volání, jako `Promise`, naleznete v tématu [ \<vrátí >](../ide/returns-javascript.md).  
  
> [!NOTE]
>  Dokumentační komentáře XML jsou k dispozici pouze z odkazovaných souborů, sestavení a služeb.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Chcete-li vytvořit dokumentační komentáře XML pro funkce jazyka JavaScript  
  
-   Ve funkci, přidejte [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), a [ \<vrátí >](../ide/returns-javascript.md) elementy a předcházet každý element s třemi lomítky (/ / / / /).  
  
    > [!NOTE]
    >  Každý prvek musí být na jednom řádku.  
  
     Následující příklad ukazuje funkce jazyka JavaScript.  
  
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
  
-   Chcete-li zobrazit dokumentační komentáře XML, zadejte název a levou závorku funkce, která je označena dokumentační komentáře XML, jako v následujícím příkladu:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Při psaní levou závorku funkce, která obsahuje komentáře dokumentace XML Editor kódu používá technologii IntelliSense pro zobrazení informací, která je definována v dokumentační komentáře XML.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Chcete-li vytvořit komentáře dokumentace XML pro pole jazyka JavaScript  
  
-   V definici funkce nebo objekt konstruktoru přidat [ \<pole >](../ide/field-javascript.md) prvek před třemi lomítky (/ / / / /).  
  
     Následující příklad ukazuje použití `<field>` prvek funkce konstruktoru. Další příklady najdete v tématu [ \<pole >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Chcete-li zobrazit dokumentační komentáře XML, vytvoření objektu pomocí funkce konstruktoru, který je označen dokumentační komentáře XML, jako v následujícím příkladu.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Na dalším řádku zadejte název objektu a období zobrazíte informace technologie IntelliSense pro pole.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Chcete-li vytvořit dokumentační komentáře XML pro přetížené funkce  
  
1.  Ve funkci, přidejte [ \<podpis >](../ide/signature-javascript.md) – element pro jednotlivá přetížení. V těchto elementech, přidat ostatní prvky `<summary>`, `<param>`, a `<returns>`, před každý element s tři lomítka (/ / / / /).  
  
     Následující příklad ukazuje přetížené funkce jazyka JavaScript. V tomto příkladu přetížení lišit podle typu parametru.  
  
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
  
2.  Chcete-li zobrazit dokumentační komentáře XML, zadejte název a levou závorku funkce, která je označena dokumentační komentáře XML, jako v následujícím příkladu:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Chcete-li vytvořit lokalizovanou IntelliSense  
  
1.  Vytvořte soubor XML, který se dokumentační komentáře ve formátu OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  MessageBundle je doporučený formát. Tento formát není podporován v Microsoft Ajax nebo soubory .winmd. Další informace o použití alternativní `VSDoc` formátování naleznete v tématu [ \<umístění >](../ide/loc-javascript.md).  
  
     Následující příklad ukazuje obsahu v souboru sajdkára, která obsahuje lokalizované informace technologie IntelliSense. Toto je soubor XML, který je umístěný ve složce specifické pro jazykovou verzi, například JA. Složka musí být ve stejném umístění jako soubor .js, který obsahuje `<loc>` elementu. Název souboru XML souboru musí odpovídat `filename` zadané v parametru `<loc>` elementu.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  V souboru .js přidejte následující kód. `<loc>` Elementu musí být deklarován před veškerým skriptem a řídí stejnými pravidly používání, jako `<reference>` elementu. Další informace najdete v tématu [technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md) a [ \<umístění >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  V souboru .js přidejte dokumentace elementů XML a popisy výchozí. Nastavte `locid` hodnoty tak, aby odpovídaly odpovídajícího atributu `name` hodnoty atributů ze souboru sajdkáry. Výchozí popis se nahradí lokalizované informace technologie IntelliSense, pokud je k dispozici.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Chcete-li zobrazit dokumentační komentáře XML, zadejte název a levou závorku funkce, jako v následujícím příkladu:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Technologie IntelliSense jazyka JavaScript](../ide/javascript-intellisense.md)   
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Návod: technologie IntelliSense jazyka JavaScript v ASP.NET](http://msdn.microsoft.com/en-us/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)



