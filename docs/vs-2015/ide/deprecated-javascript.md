---
title: '&lt;deprecated &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665806"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje vystaralou funkci nebo metodu.

## <a name="syntax"></a>Syntaxe

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parametry
 `type` volitelné. Určuje, zda bude funkce nebo metoda odebrána v budoucí verzi nebo zda již byla funkce nebo metoda odebrána a že její použití může mít za následek chybu. Nastavte na `deprecate` a určete tak, že funkce nebo metoda bude v budoucí verzi odebrána. Nastavte na `remove` a určete tak, že funkce nebo metoda již byla odebrána.

 `locid` volitelné. Identifikátor pro informace o lokalizaci funkce nebo metody. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném v prvku [\<loc >](../ide/loc-javascript.md) .

 `description` volitelné. Popis funkce nebo metody, která je zastaralá.

## <a name="remarks"></a>Poznámky
 Prvky, které slouží k přidání poznámek k funkcím, které zahrnují `<deprecated>`, musí být umístěny v těle funkce před všemi příkazy. Když označíte funkci jako zastaralou, doporučujeme, abyste nahradili její [\<summary >](../ide/summary-javascript.md) prvek elementem `<deprecated>`.

## <a name="example"></a>Příklad
 Následující kód ukazuje použití prvku `<deprecated>`.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
