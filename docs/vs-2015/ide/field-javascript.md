---
title: '&lt;Field &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663855"
---
# <a name="ltfieldgt-javascript"></a>&lt;Field &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci, včetně popisu, pro pole nebo člena, který je definován v objektu.

## <a name="syntax"></a>Syntaxe

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>Parametry
 `name` Název pole nebo členu. Když je `<field>` element použit ve funkci konstruktoru, `name` je požadován a definuje člena, na který se značka vztahuje. Když `<field>` je element přímo opatřen poznámkami k poli, je tento atribut ignorován a název používaný aplikací Visual Studio je název skutečného pole ve zdrojovém kódu.

 `static` Volitelné. Určuje, zda je pole členem funkce konstruktoru nebo členem objektu vráceného funkcí konstruktoru. Nastavte, aby se `true` pole považovalo za člena funkce konstruktoru. Nastavte, aby se `false` pole považovalo za člena objektu vráceného funkcí konstruktoru.

 `type` Volitelné. Datový typ pole. Typ může být jeden z následujících:

- Typ jazyka ECMAScript ve specifikaci ECMAScript 5, například `Number` a `Object` .

- Objekt modelu DOM, například, `HTMLElement` `Window` , a `Document` .

- Funkce konstruktoru jazyka JavaScript.

  `integer` Volitelné. Pokud `type` je `Number` , určuje, zda je pole celé číslo. Nastavte na hodnotu `true` , chcete-li označit, že pole je celé číslo. v opačném případě nastavte na `false` . Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `domElement` Volitelné. Tento atribut je zastaralý. `type` atribut má přednost před tímto atributem. Tento atribut určuje, zda je dokumentované pole prvkem modelu DOM. Nastavte na hodnotu `true` , chcete-li určit, že pole je prvek modelu DOM. v opačném případě nastavte na `false` . Pokud `type` atribut není nastaven a `domElement` je nastaven na hodnotu `true` , technologie IntelliSense bude při dokončování příkazů zacházet s dokumentovaným polem jako `HTMLElement` při provádění příkazu.

  `mayBeNull` Volitelné. Určuje, zda může být zdokumentované pole nastaveno na hodnotu null. Nastavte na `true` k označení, že pole může být nastaveno na hodnotu null. v opačném případě nastavte na `false` . Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementType` Volitelné. Pokud `type` je `Array` , tento atribut určuje typ prvků v poli.

  `elementInteger` Volitelné. Pokud `type` je `Array` a `elementType` je `Number` , tento atribut určuje, zda jsou prvky v poli celá čísla. Nastavte na hodnotu `true` , chcete-li označit, že prvky v poli jsou celá čísla. v opačném případě nastavte na `false` . Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `elementDomElement` Volitelné. Tento atribut je zastaralý. `elementType` atribut má přednost před tímto atributem. Pokud `type` je `Array` , tento atribut určuje, zda prvky v poli jsou prvky modelu DOM. Nastavte na hodnotu `true` , chcete-li určit, že prvky jsou prvky modelu DOM. v opačném případě nastavte na `false` . Pokud `elementType` atribut není nastaven a `elementDomElement` je nastaven na hodnotu `true` , technologie IntelliSense zpracuje každý prvek v poli jako `HTMLElement` při provádění příkazu.

  `elementMayBeNull` Volitelné. Pokud `type` je `Array` , určuje, zda elementy v poli mohou být nastaveny na hodnotu null. Nastavte na `true` k označení toho, že elementy v poli mohou být nastaveny na hodnotu null. v opačném případě nastavte na `false` . Výchozí hodnota je `false`. Tento atribut se v aplikaci Visual Studio nepoužívá k poskytnutí informací IntelliSense.

  `helpKeyword` Volitelné. Klíčové slovo pro nápovědu F1

  `locid` Volitelné. Identifikátor pro informace o lokalizaci pole. Identifikátor je buď ID člena, nebo odpovídá `name` hodnotě atributu v sadě zpráv definované pomocí metadat OpenAjax. Typ identifikátoru závisí na formátu zadaném ve [\<loc>](../ide/loc-javascript.md) značce.

  `value` Volitelné. Určuje kód, který má být vyhodnocen pro použití technologií IntelliSense namísto samotného kódu funkce. Pro `<field>` je tento atribut podporován pro funkce konstruktoru, ale není podporován pro literály objektů. Tento atribut lze použít k poskytnutí informací o typu, pokud není definován typ pole. Například můžete použít `value=’1’` k považovat typ pole za číslo.

  `description` Volitelné. Popis pole

## <a name="remarks"></a>Poznámky
 `name`Atribut je vyžadován při dokumentování pole ve funkci konstruktoru. Pro všechny ostatní scénáře jsou všechny atributy `<field>` elementu volitelné.

 Při dokumentaci funkce konstruktoru `<field>` musí být element uveden bezprostředně před deklarací pole. `name`Atribut se musí shodovat s názvem pole použitým ve zdrojovém kódu. U členů objektu `name` lze atribut vynechat, pokud `<field>` se prvek zobrazí bezprostředně před deklarací člena objektu.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje, jak použít `<field>` element.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít `<field>` element s `static` atributem nastaveným na `true` .

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít `<field>` element s `static` atributem nastaveným na `false` .

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít `<field>` element s `value` atributem.

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>Viz také
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)
