---
title: '&lt;param &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670363"
---
# <a name="ltparamgt-javascript"></a>&lt;param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci pro parametr v rámci funkce nebo metody.

## <a name="syntax"></a>Syntaxe

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Parametry
 `name` nutné. Název parametru

 `type` volitelné. Datový typ parametru Typ může být jeden z následujících:

- Typ jazyka ECMAScript ve specifikaci ECMAScript 5, například `Number` a `Object`.

- Objekt modelu DOM, například `HTMLElement`, `Window` a `Document`.

- Funkce konstruktoru jazyka JavaScript.

  `integer` volitelné. Pokud je `type` `Number`, určuje, zda je parametr celé číslo. Nastavte na `true` pro indikaci, že parametr je celé číslo. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` volitelné. Tento atribut je zastaralý. atribut `type` má přednost před tímto atributem. Tento atribut určuje, zda je dokumentovaný parametr prvkem modelu DOM. Nastavte na `true`, chcete-li určit, že parametr je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `type` není nastaven a `domElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje dokumentovaný parametr jako `HTMLElement`.

  `mayBeNull` volitelné. Určuje, zda může být dokumentovaný parametr nastaven na hodnotu null. Nastavte na `true` pro indikaci, že parametr lze nastavit na hodnotu null. v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` volitelné. Pokud je `type` `Array`, tento atribut určuje typ prvků v poli.

  `elementInteger` volitelné. Pokud je `type` `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na `true` pro indikaci, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` volitelné. Tento atribut je zastaralý. atribut `elementType` má přednost před tímto atributem. Je-li `type` `Array`, tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na `true`, chcete-li určit, že prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `elementType` není nastaven a `elementDomElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje každý prvek v poli jako `HTMLElement`.

  `elementMayBeNull` volitelné. Pokud je `type` `Array`, určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` pro indikaci, že elementy v poli mohou být nastaveny na hodnotu null; v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `locid` volitelné. Identifikátor pro informace o lokalizaci parametru. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném v prvku [\<loc >](../ide/loc-javascript.md) .

  `parameterArray` volitelné. Určuje, zda může být dokumentovaný parametr ve volání funkce opakován, podobně jako parametry opakování podporované funkcí `String.format`. Nastavte na `true` pro indikaci, že se dá parametr opakovat. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `optional` volitelné. Určuje, zda je dokumentovaný parametr v volání funkce volitelný. Nastavte na `true` pro indikaci, že parametr je nepovinný. v opačném případě nastavte na `false`.

  `value` volitelné. Určuje kód, který má být vyhodnocen pro použití technologií IntelliSense namísto samotného kódu funkce. Tento atribut lze použít k poskytnutí informací o typu, pokud není definován typ parametru. Můžete například použít `value=’1’` pro zachází s typem parametru jako číslo.

  `description` volitelné. Popis parametru

## <a name="remarks"></a>Poznámky
 Jediný požadovaný atribut je `name`. Všechny ostatní atributy jsou volitelné.

 Prvky, které slouží k přidávání poznámek k funkcím, jako jsou [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)a [\<returns >](../ide/returns-javascript.md), musí být umístěny v těle funkce před všemi příkazy.

 Pokud existuje více `<param>` prvků, které mají stejný název, je použit jeden z `<param>` prvků a redundantní prvky budou ignorovány. Chování, které určuje, který prvek je použit, není definováno. Pokud `name` odkazuje na neexistující parametr, je prvek ignorován.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít `<param>` element.

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

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
