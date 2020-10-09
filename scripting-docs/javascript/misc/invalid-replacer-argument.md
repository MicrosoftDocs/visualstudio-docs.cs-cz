---
title: Neplatný argument Replacer | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6a77675a1cb618210d9c44104cf6397dda03c11
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862569"
---
# <a name="invalid-replacer-argument"></a>Neplatný argument nahrazení
Byl proveden pokus o vyvolání `JSON.stringify` s argumentem, který není platný. `replacer`Argument musí být funkce nebo pole.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Změňte `replacer` argument na funkci nebo pole.  
  
## <a name="example"></a>Příklad  
 Kód v tomto příkladu způsobuje chybu za běhu, protože `memberfilter` se jedná o objekt namísto funkce nebo pole.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Viz také  
 [Objekt JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [Funkce JSON. Parse](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript – chyby za běhu](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)