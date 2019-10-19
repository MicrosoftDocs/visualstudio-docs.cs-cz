---
title: Cyklický odkaz v argumentu hodnoty není podporován | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572334"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Cyklický odkaz v argumentu hodnoty není podporován
Byl proveden pokus o vyvolání `JSON.stringify` s neplatnou hodnotou. Argument `value`, pole nebo objekt obsahuje cyklický odkaz.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odebere cyklický odkaz z argumentu.  
  
## <a name="example"></a>Příklad  
 Kód v tomto příkladu způsobí chybu za běhu, protože `john` má odkaz na `mary` a `mary` má odkaz na `john`. Chcete-li odebrat cyklický odkaz, buď odeberte nebo zrušte nastavení vlastnosti `brother` z objektu `mary` nebo vlastnosti `sister` z objektu `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu JSON](../../javascript/reference/json-object-javascript.md)  
 @No__t_1 [funkce JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)  
 [JavaScript – chyby za běhu](../../javascript/reference/javascript-run-time-errors.md)