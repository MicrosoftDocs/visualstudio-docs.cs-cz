---
title: Neplatný argument Replacer | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573813"
---
# <a name="invalid-replacer-argument"></a>Neplatný argument nahrazení
Byl proveden pokus o vyvolání `JSON.stringify` s argumentem, který není platný. Argument `replacer` musí být funkce nebo pole.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Změňte argument `replacer` na funkci nebo pole.  
  
## <a name="example"></a>Příklad  
 Kód v tomto příkladu způsobí chybu za běhu, protože `memberfilter` je objekt namísto funkce nebo pole.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 [funkce JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [JavaScript – chyby za běhu](../../javascript/reference/javascript-run-time-errors.md)