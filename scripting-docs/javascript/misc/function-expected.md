---
title: Očekává se funkce | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576584"
---
# <a name="function-expected"></a>Byla očekávána funkce
Buď jste se pokusili vyvolat jednu z metod **prototypu funkce** u objektu, který nebyl `Function` objekt, nebo jste použili objekt v kontextu volání funkce. Například následující kód vytvoří tuto chybu, protože **příklad** není funkce.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro `Function` objekty volejte pouze metody **prototypu funkce** .  
  
- Ujistěte se, že používáte operátor volání funkce `()` pouze k volání funkcí.  
  
## <a name="see-also"></a>Viz také:  
 [Objekt funkce](../../javascript/reference/function-object-javascript.md)   
 [prototype – vlastnost (Object)](../../javascript/reference/prototype-property-object-javascript.md)