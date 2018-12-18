---
title: Nelze přiřadit do výsledku funkce | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788721"
---
# <a name="cannot-assign-to-a-function-result"></a>Nelze přiřazovat hodnoty do výsledku funkce
Jste se pokusili o přiřazení hodnoty do výsledku funkce. Výsledek funkce lze přiřadit k proměnné, ale nelze zadat jako proměnnou. Pokud chcete přiřadit novou hodnotu na samotnou funkci, vynechejte závorky (operátor volání funkce). Následující příklad ukazuje situace, ve kterém se tato chyba je generována.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Nepoužívejte hodnotu výsledku volání funkce jako něco můžete *přiřadit*. Můžete přiřadit výsledek volání funkce *proměnné* když.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Funkce můžete alternativně přiřadit samostatně (a ne její návratovou hodnotu) a proměnné.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Function – objekt](../../javascript/reference/function-object-javascript.md)   
 [Psaní kódu jazyka JavaScript](../../javascript/writing-javascript-code.md)   
 [Funkce](../../javascript/functions-javascript.md)