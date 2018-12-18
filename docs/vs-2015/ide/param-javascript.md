---
title: '&lt;Param&gt; (JavaScript) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b1178fc6ff2cb5b4664930eaa70fd3de5ebed0f5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949068"
---
# <a name="ltparamgt-javascript"></a>&lt;Param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Informace o dokumentaci pro parametr určuje ve funkci nebo metodu.  
  
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
 `name`  
 Požadováno. Název parametru  
  
 `type`  
 Volitelné. Datový typ parametru. Typ může být jeden z následujících akcí:  
  
- Zadejte jazyka ECMAScript specifikací ECMAScript 5, třeba `Number` a `Object`.  
  
- Modelu DOM, jako objekt `HTMLElement`, `Window`, a `Document`.  
  
- Funkce jazyka JavaScript konstruktoru.  
  
  `integer`  
  Volitelné. Pokud `type` je `Number`, určuje, zda je parametr celé číslo. Nastavte na `true` k označení, že je parametr celé číslo; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `domElement`  
  Volitelné. Tento atribut je zastaralá; `type` atribut má přednost před tento atribut. Tento atribut určuje, zda je parametr zdokumentovaných prvek modelu DOM. Nastavte na `true` k určení, že parametr je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud `type` není nastaven atribut a `domElement` je nastavena na `true`, IntelliSense považuje za parametr zdokumentované `HTMLElement` při dokončování příkazů.  
  
  `mayBeNull`  
  Volitelné. Určuje, jestli dokument parametr lze nastavit na hodnotu null. Nastavte na `true` k označení, že parametr může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementType`  
  Volitelné. Pokud `type` je `Array`, tento atribut určuje typ prvků v poli.  
  
  `elementInteger`  
  Volitelné. Pokud `type` je `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celých čísel. Nastavte na `true` k označení, který prvků v poli jsou celá čísla; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementDomElement`  
  Volitelné. Tento atribut je zastaralá; `elementType` atribut má přednost před tento atribut. Pokud `type` je `Array`, tento atribut určuje, zda prvků v poli jsou prvky modelu DOM. Nastavte na `true` k určení, které prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud `elementType` není nastaven atribut a `elementDomElement` je nastavena na `true`, technologie IntelliSense zpracovává každý prvek v poli jako `HTMLElement` při dokončování příkazů.  
  
  `elementMayBeNull`  
  Volitelné. Pokud `type` je `Array`, určuje, zda prvků v poli může být nastavena na hodnotu null. Nastavte na `true` k označení, že prvků v poli může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `locid`  
  Volitelné. Identifikátor lokalizace informace o parametru. Identifikátor je buď členem, nebo ID odpovídá `name` hodnotu v sadě zprávy určené OpenAjax metadat atributu. Typ identifikátoru závisí na formátu určeného v [ \<umístění >](../ide/loc-javascript.md) elementu.  
  
  `parameterArray`  
  Volitelné. Určuje, jestli dokument parametr lze opakuje ve volání funkce, podobně jako parametry, které jsou podporovány v opakující se `String.format` funkce. Nastavte na `true` označíte, že parametr může být opakovaný; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `optional`  
  Volitelné. Určuje, zda je parametr zdokumentovaných volitelné ve volání funkce. Nastavte na `true` k označení, že parametr je nepovinný; jinak vrátí hodnotu, nastavte na `false`.  
  
  `value`  
  Volitelné. Určuje kód, který by se mělo vyhodnotit pro použití technologií IntelliSense místo samotný kód funkce. Pomocí tohoto atributu je poskytují informace o typu, pokud typ parametru není definován. Například můžete použít `value=’1’` považovat typ parametru jako číslo.  
  
  `description`  
  Volitelné. Popis parametru.  
  
## <a name="remarks"></a>Poznámky  
 Jediný požadovaný atribut je `name`. Všechny ostatní atributy jsou volitelné.  
  
 Prvky používaná k anotaci funkce, jako například [ \<summary >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), a [ \<vrátí >](../ide/returns-javascript.md), musí být umístěn v těle funkce před vykonáním jakýchkoli příkazů.  
  
 Pokud existuje více `<param>` prvky, které mají stejný název, jednu z `<param>` prvky se používá a redundantní prvky jsou ignorovány. Chování, které určuje, který element se používá není definován. Pokud `name` odkazuje na neexistující parametr je ignorován elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `<param>` elementu.  
  
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



