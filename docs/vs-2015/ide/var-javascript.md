---
title: '&lt;var &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663065"
---
# <a name="ltvargt-javascript"></a>&lt;var &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci pro proměnnou.

## <a name="syntax"></a>Syntaxe

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>Parametry
 `type` volitelné. Datový typ proměnné. Typ může být jeden z následujících:

- Typ jazyka ECMAScript, který je ve specifikaci ECMAScript 5, například `Number` a `Object`.

- Objekt modelu DOM, například `HTMLElement`, `Window` a `Document`.

- Funkce konstruktoru jazyka JavaScript.

  `integer` volitelné. Pokud je `type` `Number`, určuje, zda je proměnná celé číslo. Nastavte na `true` pro indikaci, že proměnná je celé číslo. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` volitelné. Tento atribut je zastaralý. atribut `type` má přednost před tímto atributem. Tento atribut určuje, zda je dokumentované proměnná prvkem modelu DOM. Nastavte na `true`, chcete-li určit, že proměnná je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `type` není nastaven a `domElement` je nastaven na `true`, technologie IntelliSense považuje dopsanou proměnnou jako `HTMLElement` při provádění příkazu.

  `mayBeNull` volitelné. Určuje, zda lze dokumentovaný proměnnou nastavit na hodnotu null. Nastavte na `true` pro indikaci, že proměnnou lze nastavit na hodnotu null. v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` volitelné. Pokud je `type` `Array`, tento atribut určuje typ prvků v poli.

  `elementInteger` volitelné. Pokud je `type` `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na `true` pro indikaci, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` volitelné. Tento atribut je zastaralý. atribut `elementType` má přednost před tímto atributem. Je-li `type` `Array`, tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na `true`, chcete-li určit, že prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `elementType` není nastaven a `elementDomElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje každý prvek v poli jako `HTMLElement`.

  `elementMayBeNull` volitelné. Pokud je `type` `Array`, určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` pro indikaci, že elementy v poli mohou být nastaveny na hodnotu null; v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `helpKeyword` volitelné. Klíčové slovo pro nápovědu F1

  `locid` volitelné. Identifikátor pro informace o lokalizaci proměnné. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném ve značce [\<loc >](../ide/loc-javascript.md) .

  `description` volitelné. Popis proměnné.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít `<var>` element.

```javascript
/// <var>A rectangle that has a width of 5.</var>
var Rectangle = {
    /// <field type = 'Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type = 'Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}
```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
