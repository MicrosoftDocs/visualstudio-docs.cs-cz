---
title: '&lt;value &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656389"
---
# <a name="ltvaluegt-javascript"></a>&lt;value &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci pro funkce `get` a `set` pro vlastnosti ECMAScript 3.

## <a name="syntax"></a>Syntaxe

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Parametry
 `type` volitelné. Datový typ vlastnosti. Typ může být jeden z následujících:

- Typ jazyka ECMAScript, který je ve specifikaci ECMAScript 5, například `Number` a `Object`.

- Objekt modelu DOM, například `HTMLElement`, `Window` a `Document`.

- Funkce konstruktoru jazyka JavaScript.

  `integer` volitelné. Pokud je `type` `Number`, určuje, zda je vlastnost celé číslo. Nastavte na `true` pro indikaci, že vlastnost je celé číslo. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` volitelné. Tento atribut je zastaralý. atribut `type` má přednost před tímto atributem. Tento atribut určuje, zda je podokumentovaný vlastnost prvkem modelu DOM. Nastavte na `true`, chcete-li určit, že vlastnost je element modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `type` není nastaven a `domElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje popsanou vlastnost jako `HTMLElement`.

  `mayBeNull` volitelné. Určuje, zda může být podokumentovaný vlastnost nastavena na hodnotu null. Nastavte na `true` pro indikaci, že vlastnost může být nastavena na hodnotu null. v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` volitelné. Pokud je `type` `Array`, tento atribut určuje typ prvků v poli.

  `elementInteger` volitelné. Pokud je `type` `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na `true` pro indikaci, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` volitelné. Tento atribut je zastaralý. atribut `elementType` má přednost před tímto atributem. Je-li `type` `Array`, tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na `true`, chcete-li určit, že prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud atribut `elementType` není nastaven a `elementDomElement` je nastaven na `true`, IntelliSense při provádění příkazu zpracuje každý prvek v poli jako `HTMLElement`.

  `elementMayBeNull` volitelné. Pokud je `type` `Array`, určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` pro indikaci, že elementy v poli mohou být nastaveny na hodnotu null; v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `locid` volitelné. Identifikátor pro informace o lokalizaci vlastnosti. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném v prvku [\<loc >](../ide/loc-javascript.md) .

  `description` volitelné. Popis vlastnosti

## <a name="remarks"></a>Poznámky
 Vlastnosti ECMAScriptu 5 používají prvek [\<summary >](../ide/summary-javascript.md) .

 Použijte prvek `<value>` bezprostředně před funkcí `get` nebo `set`.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje použití prvku `<value>` ve funkci `get`.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
