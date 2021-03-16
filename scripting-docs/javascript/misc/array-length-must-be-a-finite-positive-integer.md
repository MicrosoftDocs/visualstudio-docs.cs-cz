---
description: Zavoláte konstruktor Array s argumentem, který není celé číslo (celá čísla se skládají z nuly a sady kladných celých čísel).
title: Délka pole musí být konečné kladné celé číslo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 49d3d2985706ad6cfca9b6ac441baa039ccf04af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572114"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>Délka pole musí být konečné kladné celé číslo
Zavoláte konstruktor **Array** s argumentem, který není celé číslo (celá čísla se skládají z nuly a sady kladných celých čísel).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte kladná celá čísla pouze při vytváření nového `Array` objektu. Chcete-li vytvořit pole s jediným prvkem, který není celé číslo, udělejte ho v procesu se dvěma kroky. Nejprve vytvořte pole s jedním prvkem a potom umístěte hodnotu do prvního prvku (pole [0]). Následuje příklad, který generuje tuto chybu.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     Následující příklad ukazuje správný způsob, jak určit pole s jediným číselným prvkem.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Pro velikost pole není k dispozici horní limit, který je jiný než maximální celočíselná hodnota (přibližně 4 000 000 000).  
  
## <a name="see-also"></a>Viz také  
 [Používání polí](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
