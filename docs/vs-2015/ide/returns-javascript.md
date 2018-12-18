---
title: '&lt;Vrátí&gt; (JavaScript) | Dokumentace Microsoftu'
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
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5896c35c53feedb2f253bd86691f2fbf6793099e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875707"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Vrátí&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci pro výsledek volání funkce nebo metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Volitelné. Datový typ vrácené hodnoty. Typ může být jeden z následujících akcí:  
  
- Zadejte jazyka ECMAScript specifikací ECMAScript 5, třeba `Number` a `Object`.  
  
- Modelu DOM, jako objekt `HTMLElement`, `Window`, a `Document`.  
  
- Funkce jazyka JavaScript konstruktoru.  
  
  `integer`  
  Volitelné. Pokud `type` je `Number`, určuje, zda se vrácená hodnota je celé číslo. Nastavte na `true` k označení, že vrácená hodnota je celé číslo; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `domElement`  
  Volitelné. Tento atribut je zastaralá; `type` atribut má přednost před tento atribut. Tento atribut určuje, zda zdokumentovaných vrácená hodnota je prvek modelu DOM. Nastavte na `true` k určení, že návratová hodnota je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud `type` není nastaven atribut a `domElement` je nastavena na `true`, technologie IntelliSense jsou považovány za zdokumentovaných návratovou hodnotu `HTMLElement` při dokončování příkazů.  
  
  `mayBeNull`  
  Volitelné. Určuje, jestli má dokument vrátit hodnotu je možné nastavit na hodnotu null. Nastavte na `true` k označení, že návratová hodnota může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementType`  
  Volitelné. Pokud `type` je `Array`, tento atribut určuje typ prvků v poli.  
  
  `elementInteger`  
  Volitelné. Pokud `type` je `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celých čísel. Nastavte na `true` k označení, který prvků v poli jsou celá čísla; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementDomElement`  
  Volitelné. Tento atribut je zastaralá; `elementType` atribut má přednost před tento atribut. Pokud `type` je `Array`, tento atribut určuje, zda prvků v poli jsou prvky modelu DOM. Nastavte na `true` k určení, které prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud `elementType` není nastaven atribut a `elementDomElement` je nastavena na `true`, technologie IntelliSense zpracovává každý prvek v poli jako `HTMLElement` při dokončování příkazů.  
  
  `elementMayBeNull`  
  Volitelné. Pokud `type` je `Array`, určuje, zda prvků v poli může být nastavena na hodnotu null. Nastavte na `true` k označení, že prvků v poli může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `locid`  
  Volitelné. Identifikátor lokalizace informace o vrácené hodnotě. Identifikátor je buď členem, nebo ID odpovídá `name` hodnotu v sadě zprávy určené OpenAjax metadat atributu. Typ identifikátoru závisí na formátu určeného v [ \<umístění >](../ide/loc-javascript.md) značky.  
  
  `value`  
  Volitelné. Určuje kód, který by se mělo vyhodnotit pro použití technologií IntelliSense místo samotný kód funkce. Například můžete použít tento atribut na poskytovat technologii IntelliSense pro asynchronními zpětnými voláními, například `Promise`. Použití `value` atributem `<returns>` element může zlepšit výkon technologie IntelliSense obejitím spuštění zdlouhavé kódu.  
  
  `description`  
  Volitelné. Popis návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `<returns>` Elementu musí být umístěn v těle funkce před vykonáním jakýchkoli příkazů.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `<returns>` elementu.  
  
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
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)



