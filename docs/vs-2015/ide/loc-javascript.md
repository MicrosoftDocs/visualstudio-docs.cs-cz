---
title: '&lt;Loc &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651469"
---
# <a name="ltlocgt-javascript"></a>&lt;Loc &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje umístění a typ souboru. postranního vozíku, který poskytuje lokalizované informace technologie IntelliSense.

## <a name="syntax"></a>Syntaxe

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Parametry
 `filename` Volitelné. Kořenový název souboru vozíku, který obsahuje informace o lokalizaci pro neutrální jazykovou verzi. Když aplikace Visual Studio hledá informace o lokalizaci, pokusí se najít verzi tohoto souboru specifickou pro jazykovou verzi. Například pokud `filename` je jquery.xml, Visual Studio vyhledá správnou složku specifickou pro jazykovou verzi (například ja) ve stejném umístění jako soubor. js, který obsahuje `<loc>` element. Pokud nalezne složku specifickou pro jazykovou verzi, zkontroluje, zda soubor jquery.xml v něm existuje. Pokud nemůže najít správný soubor, místo toho použije spravovaná pravidla umístění prostředků. Výchozí hodnota pro `filename` je název aktuálního souboru, ale s příponou. XML namísto. js.

 `format` Volitelné. Typ souboru postranního vozíku, který se používá k lokalizaci. Slouží `messagebundle` k určení použití sad zpráv definovaných v otevřených metadatech AJAX. `messagebundle` je doporučeným formátem. Tento formát však není podporován v Microsoft Ajax nebo v souborech. winmd. Slouží `vsdoc` k určení formátu lokalizace standard .NET Framework, který se používá v Microsoft Ajax a prostředí Windows Runtime. Tento atribut je nepovinný. `vsdoc` je výchozí formát.

## <a name="remarks"></a>Poznámky
 `<loc>`Element musí být uveden v horní části souboru ve stejném oddílu jako `<reference>` element. Pravidla použití pro `<loc>` element jsou stejná jako `<reference>` element. Další informace naleznete v části direktivy odkazů v tématu [JavaScript IntelliSense](../ide/javascript-intellisense.md).

 Visual Studio zpracuje jeden `<loc>` element pro každý soubor. js. Pokud je `<loc>` k dispozici více prvků, `<loc>` je použit pouze jeden prvek. Chování při určování prvku, který `<loc>` se má použít, není definováno.

 Při použití formátu sady zpráv použijte `locid` atribut v dokumentačních komentářích XML k určení `name` hodnoty atributu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít `<loc>` element s formátem MessageBundle. Přidejte následující XML do souboru s názvem messageFilename.xml a uložte soubor do správné složky specifické pro jazykovou verzi, jak je uvedeno v popisu `filename` parametru.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Pro příklad messagebundle přidejte následující kód do souboru JavaScriptu v projektu. `<loc>`Element musí být uveden jako první řádek v souboru JavaScriptu. Popisy v tomto kódu budou nahrazeny lokalizovanými popisy, pokud jsou k dispozici.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 Následující příklad používá formát VSDoc. Přidejte následující XML do souboru s názvem scriptFilename.xml a uložte soubor do správné složky specifické pro jazykovou verzi.

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
