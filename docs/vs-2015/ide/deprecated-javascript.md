---
title: '&lt;zastaralé &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665806"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;zastaralé &gt; (JavaScript)
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
 `type` Volitelné. Určuje, zda bude funkce nebo metoda odebrána v budoucí verzi nebo zda již byla funkce nebo metoda odebrána a že její použití může mít za následek chybu. Nastavte na hodnotu `deprecate` pro určení, že funkce nebo metoda bude v budoucí verzi odebrána. Nastavte na hodnotu `remove` , chcete-li určit, že funkce nebo metoda již byla odebrána.

 `locid` Volitelné. Identifikátor pro informace o lokalizaci funkce nebo metody. Identifikátor je buď ID člena, nebo odpovídá `name` hodnotě atributu v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném v [\<loc>](../ide/loc-javascript.md) elementu.

 `description` Volitelné. Popis funkce nebo metody, která je zastaralá.

## <a name="remarks"></a>Poznámky
 Prvky, které slouží k přidání poznámek k funkcím, které zahrnují `<deprecated>` , musí být umístěny v těle funkce před všemi příkazy. Když označíte funkci jako zastaralou, doporučujeme nahradit její [\<summary>](../ide/summary-javascript.md) prvek `<deprecated>` elementem.

## <a name="example"></a>Příklad
 Následující kód ukazuje, jak použít `<deprecated>` element.

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
