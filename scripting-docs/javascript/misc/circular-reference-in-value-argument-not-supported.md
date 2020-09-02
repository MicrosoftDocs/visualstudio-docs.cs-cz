---
title: Cyklický odkaz v argumentu hodnoty není podporován | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817616"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Cyklický odkaz v argumentu hodnoty není podporován
Byl proveden pokus o vyvolání `JSON.stringify` s neplatnou hodnotou. `value`Argument, pole nebo objekt obsahuje cyklický odkaz.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odebere cyklický odkaz z argumentu.  
  
## <a name="example"></a>Příklad  
 Kód v tomto příkladu způsobuje chybu za běhu, protože `john` obsahuje odkaz na `mary` a `mary` má odkaz na `john` . Chcete-li odebrat cyklický odkaz, buď odeberte, nebo zrušte jeho vlastnost `brother` z `mary` objektu nebo `sister` vlastnosti `john` objektu.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Viz také  
 [Objekt JSON](../../javascript/reference/json-object-javascript.md)   
 [Funkce JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [JavaScript – chyby za běhu](../../javascript/reference/javascript-run-time-errors.md)