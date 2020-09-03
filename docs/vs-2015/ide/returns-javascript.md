---
title: '&lt;Vrátí &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669958"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Vrátí &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci pro výsledek volání funkce nebo metody.

## <a name="syntax"></a>Syntaxe

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parametry
 `type` Volitelné. Datový typ vrácené hodnoty. Typ může být jeden z následujících:

- Typ jazyka ECMAScript ve specifikaci ECMAScript 5, například `Number` a `Object` .

- Objekt modelu DOM, například, `HTMLElement` `Window` , a `Document` .

- Funkce konstruktoru jazyka JavaScript.

  `integer` Volitelné. Pokud `type` je `Number` , určuje, zda je vrácená hodnota celé číslo. Nastavte na `true` hodnotu, chcete-li označit, že návratová hodnota je celé číslo. v opačném případě nastavte na `false` . Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` Volitelné. Tento atribut je zastaralý. `type` atribut má přednost před tímto atributem. Tento atribut určuje, zda dokumentované návratová hodnota je element modelu DOM. Nastavte na `true` hodnotu, chcete-li určit, že návratová hodnota je prvek modelu DOM. v opačném případě nastavte na `false` . Pokud `type` atribut není nastaven a `domElement` je nastaven na hodnotu `true` , technologie IntelliSense považuje popsanou návratovou hodnotu jako `HTMLElement` při provádění příkazu.

  `mayBeNull` Volitelné. Určuje, zda může být dokumentovaný návratová hodnota nastavena na hodnotu null. Nastavte na hodnotu `true` , chcete-li určit, že návratová hodnota může být nastavena na hodnotu null. v opačném případě nastavte na `false` . Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` Volitelné. Pokud `type` je `Array` , tento atribut určuje typ prvků v poli.

  `elementInteger` Volitelné. Pokud `type` je `Array` a `elementType` je `Number` , tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na hodnotu `true` , chcete-li označit, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false` . Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` Volitelné. Tento atribut je zastaralý. `elementType` atribut má přednost před tímto atributem. Pokud `type` je `Array` , tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na hodnotu `true` , chcete-li určit, že prvky jsou prvky modelu DOM. v opačném případě nastavte na `false` . Pokud `elementType` atribut není nastaven a `elementDomElement` je nastaven na hodnotu `true` , technologie IntelliSense zpracuje každý prvek v poli jako `HTMLElement` při provádění příkazu.

  `elementMayBeNull` Volitelné. Pokud `type` je `Array` , určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` k označení toho, že elementy v poli mohou být nastaveny na hodnotu null. v opačném případě nastavte na `false` . Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `locid` Volitelné. Identifikátor lokalizačních informací o vrácené hodnotě. Identifikátor je buď ID člena, nebo odpovídá `name` hodnotě atributu v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném ve [\<loc>](../ide/loc-javascript.md) značce.

  `value` Volitelné. Určuje kód, který má být vyhodnocen pro použití technologií IntelliSense namísto samotného kódu funkce. Můžete například použít tento atribut k poskytnutí IntelliSense pro asynchronní zpětná volání, jako je například `Promise` . Použití `value` atributu s `<returns>` prvkem může zlepšit výkon technologie IntelliSense tím, že se vynechá zdlouhavé provádění kódu.

  `description` Volitelné. Popis návratové hodnoty.

## <a name="remarks"></a>Poznámky
 `<returns>`Element musí být umístěn v těle funkce před všemi příkazy.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít `<returns>` element.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
