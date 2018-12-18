---
title: '&lt;var&gt; (JavaScript) | Dokumentace Microsoftu'
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
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 04f592bab7679ed3e8fe8791872ce2280d05359a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881973"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
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
 `type`  
 Volitelné. Datový typ proměnné. Typ může být jeden z následujících akcí:  
  
- Typ jazyka ECMAScript, které je ve specifikaci ECMAScript 5 jako `Number` a `Object`.  
  
- Modelu DOM, jako objekt `HTMLElement`, `Window`, a `Document`.  
  
- Funkce jazyka JavaScript konstruktoru.  
  
  `integer`  
  Volitelné. Pokud `type` je `Number`, určuje, zda je proměnná typu integer. Nastavte na `true` k označení, že je proměnná typu integer; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `domElement`  
  Volitelné. Tento atribut je zastaralá; `type` atribut má přednost před tento atribut. Tento atribut určuje, zda je proměnná zdokumentovaných prvek modelu DOM. Nastavte na `true` k určení, že proměnná je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud `type` není nastaven atribut a `domElement` je nastavena na `true`, technologie IntelliSense jsou považovány za zdokumentovaných proměnné `HTMLElement` při dokončování příkazů.  
  
  `mayBeNull`  
  Volitelné. Určuje, jestli dokument proměnnou lze nastavit na hodnotu null. Nastavte na `true` označíte, že proměnnou lze nastavit na hodnotu null; v opačném případě nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementType`  
  Volitelné. Pokud `type` je `Array`, tento atribut určuje typ prvků v poli.  
  
  `elementInteger`  
  Volitelné. Pokud `type` je `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celých čísel. Nastavte na `true` k označení, který prvků v poli jsou celá čísla; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementDomElement`  
  Volitelné. Tento atribut je zastaralá; `elementType` atribut má přednost před tento atribut. Pokud `type` je `Array`, tento atribut určuje, zda prvků v poli jsou prvky modelu DOM. Nastavte na `true` k určení, které prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud `elementType` není nastaven atribut a `elementDomElement` je nastavena na `true`, technologie IntelliSense zpracovává každý prvek v poli jako `HTMLElement` při dokončování příkazů.  
  
  `elementMayBeNull`  
  Volitelné. Pokud `type` je `Array`, určuje, zda prvků v poli může být nastavena na hodnotu null. Nastavte na `true` k označení, že prvků v poli může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `helpKeyword`  
  Volitelné. Klíčové slovo nápovědy F1.  
  
  `locid`  
  Volitelné. Identifikátor lokalizace informace o proměnnou. Identifikátor je buď členem, nebo ID odpovídá `name` hodnotu v sadě zprávy určené OpenAjax metadat atributu. Typ identifikátoru závisí na formátu určeného v [ \<umístění >](../ide/loc-javascript.md) značky.  
  
  `description`  
  Volitelné. Popis proměnné.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `<var>` elementu.  
  
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



