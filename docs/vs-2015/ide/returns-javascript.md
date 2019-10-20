---
title: '&lt;returns &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669958"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns &gt; (JavaScript)
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
 `type` volitelné. Datový typ vrácené hodnoty. Typ může být jeden z následujících:

- Typ jazyka ECMAScript ve specifikaci ECMAScript 5, například `Number` a `Object`.

- Objekt modelu DOM, například `HTMLElement`, `Window` a `Document`.

- Funkce konstruktoru jazyka JavaScript.

  `integer` volitelné. Pokud je `type` `Number`, určuje, zda je vrácená hodnota celé číslo. Nastavte na `true` pro indikaci, že návratová hodnota je celé číslo. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` volitelné. Tento atribut je zastaralý. atribut `type` má přednost před tímto atributem. Tento atribut určuje, zda dokumentované návratová hodnota je element modelu DOM. Nastavte na `true`, chcete-li určit, že návratová hodnota je element modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `type` není nastaven a `domElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje dokumentovaný návratovou hodnotu jako `HTMLElement`.

  `mayBeNull` volitelné. Určuje, zda může být dokumentovaný návratová hodnota nastavena na hodnotu null. Nastavte na `true` pro indikaci, že návratová hodnota může být nastavena na hodnotu null. v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` volitelné. Pokud je `type` `Array`, tento atribut určuje typ prvků v poli.

  `elementInteger` volitelné. Pokud je `type` `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na `true` pro indikaci, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` volitelné. Tento atribut je zastaralý. atribut `elementType` má přednost před tímto atributem. Je-li `type` `Array`, tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na `true`, chcete-li určit, že prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `elementType` není nastaven a `elementDomElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje každý prvek v poli jako `HTMLElement`.

  `elementMayBeNull` volitelné. Pokud je `type` `Array`, určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` pro indikaci, že elementy v poli mohou být nastaveny na hodnotu null; v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `locid` volitelné. Identifikátor lokalizačních informací o vrácené hodnotě. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném ve značce [\<loc >](../ide/loc-javascript.md) .

  `value` volitelné. Určuje kód, který má být vyhodnocen pro použití technologií IntelliSense namísto samotného kódu funkce. Tento atribut můžete například použít k poskytnutí IntelliSense pro asynchronní zpětná volání, jako je například `Promise`. Použití atributu `value` s `<returns>` prvkem může zlepšit výkon technologie IntelliSense tím, že se vynechá zdlouhavé provádění kódu.

  `description` volitelné. Popis návratové hodnoty.

## <a name="remarks"></a>Poznámky
 Element `<returns>` musí být umístěn v těle funkce před všemi příkazy.

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
