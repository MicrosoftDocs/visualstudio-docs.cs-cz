---
description: Buď jste se pokusili vyvolat jednu z metod prototypu funkce u objektu, který nebyl objektem funkce, nebo jste použili objekt v kontextu volání funkce.
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
ms.openlocfilehash: 99e354118844d7e57f708cf3f2d5653ee1c0fc65
ms.sourcegitcommit: 3a855d3513407ea78336386dc3be0b75142614b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2021
ms.locfileid: "103622605"
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
