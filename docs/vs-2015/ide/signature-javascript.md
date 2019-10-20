---
title: '&lt;signature &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671133"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Seskupí sadu souvisejících prvků pro funkci nebo metodu k poskytnutí dokumentace pro přetížené funkce.

## <a name="syntax"></a>Syntaxe

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Parametry
 `externalid` volitelné. Pokud je atribut `format` pro prvek [\<loc >](../ide/loc-javascript.md) `vsdoc`, tento atribut určuje ID člena používané k vyhledání kódu XML, který je spojen s podpisem. Na rozdíl od atributu `locid` tento atribut určuje, zda mají být načteny všechny prvky v členu, které mají toto ID. Všechny přidružené informace o popisech přítomné v kódu XML budou také sloučeny s prvky zadanými v signatuře. To umožňuje určit další prvky, například `<capability>`, v souboru. vozík bez jejich zadání ve zdrojovém souboru. `externalid` je nepovinný atribut.

 `externalFile` volitelné. Určuje název souboru, ve kterém se má najít `externalid`. Tento atribut se ignoruje, pokud není k dispozici žádná `externalid`. Toto je nepovinný atribut. Výchozí hodnota je název aktuálního souboru, ale Přípona souboru. XML namísto. js. Ve výchozím nastavení se k vyhledání souboru používají pravidla vyhledávání spravovaných prostředků pro lokalizaci.

 `helpKeyword` volitelné. Klíčové slovo pro nápovědu F1

 `locid` volitelné. Identifikátor pro informace o lokalizaci pole. Identifikátor je buď ID člena, nebo odpovídá hodnotě atributu `name` v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném ve značce [\<loc >](../ide/loc-javascript.md) .

## <a name="remarks"></a>Poznámky
 Použijte jeden `<signature>` element pro každý popis přetížené funkce v souboru. js nebo použijte jeden `<signature>` element pro každé zadané ID externího člena.

 Element `<signature>` musí být umístěn v těle funkce před všemi příkazy. Při použití [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)nebo [\<returns >](../ide/returns-javascript.md) prvků s `<signature>` prvkem, umístěte ostatní prvky do bloku `<signature>`.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít `<signature>` element.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
