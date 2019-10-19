---
title: Délka pole musí být konečné kladné celé číslo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69494f1485a97ff4f2c98cf2493e5d0bc5b8aa9f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576082"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Délka pole musí být konečné kladné celé číslo
Zavoláte konstruktor **Array** s argumentem, který není celé číslo (celá čísla se skládají z nuly a sady kladných celých čísel).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte kladná celá čísla pouze při vytváření nového objektu `Array`. Chcete-li vytvořit pole s jediným prvkem, který není celé číslo, udělejte ho v procesu se dvěma kroky. Nejprve vytvořte pole s jedním prvkem a potom umístěte hodnotu do prvního prvku (pole [0]). Následuje příklad, který generuje tuto chybu.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Následující příklad ukazuje správný způsob, jak určit pole s jediným číselným prvkem.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Pro velikost pole není k dispozici horní limit, který je jiný než maximální celočíselná hodnota (přibližně 4 000 000 000).  
  
## <a name="see-also"></a>Viz také:  
 [Používání polí](../../javascript/advanced/using-arrays-javascript.md)