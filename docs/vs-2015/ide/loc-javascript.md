---
title: '&lt;loc &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651469"
---
# <a name="ltlocgt-javascript"></a>&lt;loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje umístění a typ souboru. postranního vozíku, který poskytuje lokalizované informace technologie IntelliSense.

## <a name="syntax"></a>Syntaxe

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Parametry
 `filename` volitelné. Kořenový název souboru vozíku, který obsahuje informace o lokalizaci pro neutrální jazykovou verzi. Když aplikace Visual Studio hledá informace o lokalizaci, pokusí se najít verzi tohoto souboru specifickou pro jazykovou verzi. Například pokud je `filename` jQuery. XML, Visual Studio vyhledá správnou složku specifickou pro jazykovou verzi (například JA) ve stejném umístění jako soubor. js, který obsahuje prvek `<loc>`. Pokud nalezne složku specifickou pro jazykovou verzi, zkontroluje, zda v ní existuje soubor jQuery. XML. Pokud nemůže najít správný soubor, místo toho použije spravovaná pravidla umístění prostředků. Výchozí hodnota pro `filename` je název aktuálního souboru, ale s příponou. XML namísto. js.

 `format` volitelné. Typ souboru postranního vozíku, který se používá k lokalizaci. Pomocí `messagebundle` můžete určit použití sad zpráv definovaných v otevřených metadatech AJAX. `messagebundle` je doporučený formát. Tento formát však není podporován v Microsoft Ajax nebo v souborech. winmd. Použijte `vsdoc` k určení formátu lokalizace Standard .NET Framework, který je používán Microsoft Ajax a prostředí Windows Runtime. Tento atribut je nepovinný. `vsdoc` je výchozí formát.

## <a name="remarks"></a>Poznámky
 Element `<loc>` musí být uveden v horní části souboru ve stejném oddílu jako `<reference>` element. Pravidla použití prvku `<loc>` jsou stejná jako `<reference>` element. Další informace naleznete v části direktivy odkazů v tématu [JavaScript IntelliSense](../ide/javascript-intellisense.md).

 Visual Studio zpracuje jeden `<loc>` element pro každý soubor. js. Pokud je k dispozici více prvků `<loc>`, je použit pouze jeden prvek `<loc>`. Chování pro určení, který `<loc>` element, který se má použít, není definováno.

 Při použití formátu sady zpráv použijte atribut `locid` v dokumentačních komentářích XML k určení hodnoty atributu `name`.

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití prvku `<loc>` s formátem MessageBundle. Přidejte následující kód XML do souboru s názvem messageFilename. XML a umístěte jej do správné složky specifické pro jazykovou verzi, jak je uvedeno v popisu parametru `filename`.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Pro příklad messagebundle přidejte následující kód do souboru JavaScriptu v projektu. Element `<loc>` musí být uveden jako první řádek v souboru JavaScriptu. Popisy v tomto kódu budou nahrazeny lokalizovanými popisy, pokud jsou k dispozici.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 Následující příklad používá formát VSDoc. Přidejte následující kód XML do souboru s názvem scriptFilename. XML a umístěte jej do správné složky specifické pro jazykovou verzi.

```
<?xml version="1.0" encoding="utf-8" ?>
<doc>
  <assembly>
    <name>Lights</name>
  </assembly>
  <members>
    <member name="M:illuminate">
      <summary>Activates a light. </summary>
      <param name='a'>The light to activate. </param>
    </member>
  </members>
</doc>

```

 Pro příklad VSDoc přidejte následující kód do souboru JavaScriptu v projektu. Popisy v tomto kódu budou nahrazeny lokalizovanými popisy, pokud jsou k dispozici.

```javascript
/// <loc filename="scriptFilename.xml" format="vsdoc" />

function illuminate(a)
{
    /// <summary locid='M:illuminate'>description</summary>
    /// <param name='a' type='Number'>parameter a description</param>
}

```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
