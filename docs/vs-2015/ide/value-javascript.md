---
title: '&lt;Hodnota&gt; (JavaScript) | Dokumentace Microsoftu'
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
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f88f3ae2e7442549004d2331b4517eb7fa2b5509
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914330"
---
# <a name="ltvaluegt-javascript"></a>&lt;Hodnota&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje informace o dokumentaci pro `get` a `set` funkce pro vlastnosti ECMAScript 3.  
  
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
 `type`  
 Volitelné. Datový typ vlastnosti. Typ může být jeden z následujících akcí:  
  
- Typ jazyka ECMAScript, které je ve specifikaci ECMAScript 5 jako `Number` a `Object`.  
  
- Modelu DOM, jako objekt `HTMLElement`, `Window`, a `Document`.  
  
- Funkce jazyka JavaScript konstruktoru.  
  
  `integer`  
  Volitelné. Pokud `type` je `Number`, určuje, zda je vlastnost celé číslo. Nastavte na `true` k označení, že vlastnost je celé číslo; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `domElement`  
  Volitelné. Tento atribut je zastaralá; `type` atribut má přednost před tento atribut. Tento atribut určuje, zda je vlastnost zdokumentovaných prvek modelu DOM. Nastavte na `true` k určení, že vlastnost je prvek modelu DOM; v opačném případě nastavte na `false`. Pokud `type` není nastaven atribut a `domElement` je nastavena na `true`, technologie IntelliSense jsou považovány za vlastnost zdokumentované `HTMLElement` při dokončování příkazů.  
  
  `mayBeNull`  
  Volitelné. Určuje, jestli dokument vlastnost lze nastavit na hodnotu null. Nastavte na `true` k označení, že vlastnost může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementType`  
  Volitelné. Pokud `type` je `Array`, tento atribut určuje typ prvků v poli.  
  
  `elementInteger`  
  Volitelné. Pokud `type` je `Array` a `elementType` je `Number`, tento atribut určuje, zda jsou prvky v poli celých čísel. Nastavte na `true` k označení, který prvků v poli jsou celá čísla; v opačném případě nastavte na `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `elementDomElement`  
  Volitelné. Tento atribut je zastaralá; `elementType` atribut má přednost před tento atribut. Pokud `type` je `Array`, tento atribut určuje, zda prvků v poli jsou prvky modelu DOM. Nastavte na `true` k určení, které prvky jsou prvky modelu DOM; v opačném případě nastavte na `false`. Pokud `elementType` není nastaven atribut a `elementDomElement` je nastavena na `true`, technologie IntelliSense zpracovává každý prvek v poli jako `HTMLElement` při dokončování příkazů.  
  
  `elementMayBeNull`  
  Volitelné. Pokud `type` je `Array`, určuje, zda prvků v poli může být nastavena na hodnotu null. Nastavte na `true` k označení, že prvků v poli může být nastaven na hodnotu null; jinak vrátí hodnotu, nastavte na `false`. Výchozí hodnota je `false`. Tento atribut není používá sada Visual Studio k poskytování informací technologie IntelliSense.  
  
  `locid`  
  Volitelné. Identifikátor lokalizace informace o vlastnosti. Identifikátor je buď členem, nebo ID odpovídá `name` hodnotu v sadě zprávy určené OpenAjax metadat atributu. Typ identifikátoru závisí na formátu určeného v [ \<umístění >](../ide/loc-javascript.md) elementu.  
  
  `description`  
  Volitelné. Popis vlastnosti.  
  
## <a name="remarks"></a>Poznámky  
 Použití vlastnosti ECMAScript 5 [ \<summary >](../ide/summary-javascript.md) elementu.  
  
 Použití `<value>` element bezprostředně před `get` nebo `set` funkce.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat `<value>` elementu na `get` funkce.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentační komentáře XML](../ide/xml-documentation-comments-javascript.md)



