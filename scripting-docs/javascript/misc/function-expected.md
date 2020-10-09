---
title: Očekává se funkce | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2028d8923c2f81d1d99fec752d7ac0ce2fb32f65
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862169"
---
# <a name="function-expected"></a>Byla očekávána funkce
Buď jste se pokusili vyvolat jednu z metod **prototypu funkce** u objektu, který nebyl `Function` objekt, nebo jste použili objekt v kontextu volání funkce. Například následující kód vytvoří tuto chybu, protože **příklad** není funkce.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pouze metody **prototypu volání funkcí** pro `Function` objekty.  
  
- Ujistěte se, že používáte operátor volání funkce `()` pouze k volání funkcí.  
  
## <a name="see-also"></a>Viz také  
 [Function – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype – vlastnost (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)