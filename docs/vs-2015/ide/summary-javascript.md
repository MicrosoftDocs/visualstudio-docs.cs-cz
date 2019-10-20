---
title: '&lt;summary &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646852"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje popis funkce nebo metody.

## <a name="syntax"></a>Syntaxe

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parametry
 `locid` volitelné. Identifikátor pro informace o lokalizaci funkce nebo metody. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném v prvku [\<loc >](../ide/loc-javascript.md) .

 `description` volitelné. Popis funkce nebo metody.

## <a name="remarks"></a>Poznámky
 Prvky, které slouží k přidání poznámek k funkcím, které zahrnují [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)a [\<returns >](../ide/returns-javascript.md), musí být umístěny v těle funkce před všemi příkazy.

## <a name="example"></a>Příklad
 Následující kód ukazuje použití prvku `<summary>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
