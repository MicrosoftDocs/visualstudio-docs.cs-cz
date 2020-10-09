---
title: Očekáván objekt | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862107"
---
# <a name="object-expected"></a>Očekáván objekt
Pokusili jste se vyvolat metodu nebo vlastnost objektu typu, který je jiný než `Object` , nebo jste předali argument jiného typu, než `Object` Když `Object` byl vyžadován.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu volejte pouze metodu nebo vlastnost `Object` .  
  
- Pokud dojde k chybě pro argument bez objektu, předejte objekt typu `Object` .  
  
- Zkontroluje, zda je místo objektu typu vyvolán odkaz na nedefinovaný nebo null `Object` .  
  
     Například pokud se zobrazí tato chyba v myVar v následujícím kódu:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     místo toho můžete použít tento kód:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Object – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Objekty a pole](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)