---
title: Nelze přiřadit k výsledku funkce | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: aca09fe3b516fbb8f27def982bf34a22d33d4ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572360"
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
  
## <a name="see-also"></a>Viz také:  
 [Objekt funkce](../../javascript/reference/function-object-javascript.md)   
 [Psaní  kódu JavaScriptu](../../javascript/writing-javascript-code.md)  
 [Funkce](../../javascript/functions-javascript.md)