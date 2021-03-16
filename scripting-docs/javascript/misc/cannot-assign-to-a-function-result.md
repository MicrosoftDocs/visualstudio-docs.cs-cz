---
description: Pokusili jste se přiřadit hodnotu výsledku funkce.
title: Nelze přiřadit k výsledku funkce | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 125d2dc7d41b1b65027952e4e6cb94ff97083e6e
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571919"
---
# <a name="cannot-assign-to-a-function-result"></a>Nelze přiřazovat hodnoty do výsledku funkce
Pokusili jste se přiřadit hodnotu výsledku funkce. Výsledek funkce lze přiřadit proměnné, ale nelze ji použít jako proměnnou. Chcete-li k samotné funkci přiřadit novou hodnotu, vynechejte závorky (operátor volání funkce). Následující příklad ukazuje situaci, kdy se tato chyba generuje.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Nepoužívejte hodnotu výsledku volání funkce jako objekt, ke kterému můžete *přiřadit*. Výsledek volání funkce můžete přiřadit *proměnné* i v případě, že.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Alternativně můžete k proměnné přiřadit samotnou funkci (a nikoli její návratovou hodnotu).  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Function – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Psaní kódu jazyka JavaScript](https://developer.mozilla.org/docs/Learn/Getting_started_with_the_web/JavaScript_basics)   
 [Functions](https://developer.mozilla.org/docs/Learn/JavaScript/Building_blocks/Functions)
