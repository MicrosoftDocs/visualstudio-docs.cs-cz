---
title: '&lt;hodnota &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656389"
---
# <a name="ltvaluegt-javascript"></a>&lt;hodnota &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci `get` pro `set` funkce a pro vlastnosti ECMAScript 3.

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
 `type` Volitelné. Datový typ vlastnosti. Typ může být jeden z následujících:

- Typ jazyka ECMAScript, který je ve specifikaci ECMAScript 5, například `Number` a `Object` .

- Objekt modelu DOM, například, `HTMLElement` `Window` , a `Document` .

- Funkce konstruktoru jazyka JavaScript.

  `integer` Volitelné. Pokud `type` je `Number` , určuje, zda je vlastnost celé číslo. Nastavte na hodnotu `true` , chcete-li označit, že vlastnost je celé číslo. v opačném případě nastavte na `false` . Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` Volitelné. Tento atribut je zastaralý. `type` atribut má přednost před tímto atributem. Tento atribut určuje, zda je podokumentovaný vlastnost prvkem modelu DOM. Nastavte na hodnotu `true` , chcete-li určit, zda je vlastnost prvkem modelu DOM. v opačném případě nastavte na `false` . Pokud `type` atribut není nastaven a `domElement` je nastaven na hodnotu `true` , technologie IntelliSense zpracuje dokumentovaný vlastnost jako `HTMLElement` při dokončování příkazu.

  `mayBeNull` Volitelné. Určuje, zda může být podokumentovaný vlastnost nastavena na hodnotu null. Nastavte na `true` hodnotu, chcete-li určit, že vlastnost může být nastavena na hodnotu null. v opačném případě nastavte na `false` . Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` Volitelné. Pokud `type` je `Array` , tento atribut určuje typ prvků v poli.

  `elementInteger` Volitelné. Pokud `type` je `Array` a `elementType` je `Number` , tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na hodnotu `true` , chcete-li označit, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false` . Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` Volitelné. Tento atribut je zastaralý. `elementType` atribut má přednost před tímto atributem. Pokud `type` je `Array` , tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na hodnotu `true` , chcete-li určit, že prvky jsou prvky modelu DOM. v opačném případě nastavte na `false` . Pokud `elementType` atribut není nastaven a `elementDomElement` je nastaven na hodnotu `true` , technologie IntelliSense zpracuje každý prvek v poli jako `HTMLElement` při provádění příkazu.

  `elementMayBeNull` Volitelné. Pokud `type` je `Array` , určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` k označení toho, že elementy v poli mohou být nastaveny na hodnotu null. v opačném případě nastavte na `false` . Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `locid` Volitelné. Identifikátor pro informace o lokalizaci vlastnosti. Identifikátor je buď ID člena, nebo odpovídá `name` hodnotě atributu v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném v [\<loc>](../ide/loc-javascript.md) elementu.

  `description` Volitelné. Popis vlastnosti

## <a name="remarks"></a>Poznámky
 Vlastnosti ECMAScript 5 používají [\<summary>](../ide/summary-javascript.md) element.

 Použijte `<value>` prvek těsně před `get` `set` funkcí or.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít `<value>` element na `get` funkci.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
