---
title: Neočekávaný kvantifikátor (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f67f9a2fc81b0bd950e171e4274eb09eacd88bbc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861855"
---
# <a name="unexpected-quantifier-javascript"></a>Neočekávaný kvantifikátor (JavaScript)
Při vytváření vzoru hledání regulárního výrazu jste vytvořili prvek vzoru s neplatným faktorem opakování. Například vzor  
  
```js
/^+/  
```  
  
 je neplatné, protože element ^ (začátek vstupu) nemůže mít faktor opakování. V následující tabulce jsou uvedeny prvky, které nemůžou mít faktory opakování.  
  
|Element|Popis|  
|-------------|-----------------|  
|^|Začátek vstupu|  
|$|Konec vstupu|  
|\b|Hranice slova|  
|\B|Hranice jiné než slova|  
|*|Nula nebo více opakování|  
|+|Jeden nebo více opakování|  
|?|Nula nebo jedna opakování|  
|n|n opakování|  
|{n,}|n nebo více opakování|  
|{n, m}|Od n do m opakování, včetně|  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zajistěte, aby element vzoru hledání obsahoval pouze platné faktory opakování.  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntaxe regulárního výrazu (JavaScript)](/previous-versions/1400241x(v=vs.100))