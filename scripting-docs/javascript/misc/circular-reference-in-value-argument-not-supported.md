---
description: Byl proveden pokus o vyvolání formátu JSON. stringify s neplatnou hodnotou.
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
ms.openlocfilehash: 88e4ead99f8c59a1300d018bff9d3e81b0874b51
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571139"
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
 [Objekt JSON](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [Funkce JSON. Parse](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [JavaScript – chyby za běhu](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
