---
title: Byl očekáván objekt | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add25325653627d23eb699ab53c0f2799c8322f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788658"
---
# <a name="object-expected"></a>Očekáván objekt
Pokoušíte se o vyvolání metody nebo vlastnosti objektu typu jiné než `Object`, nebo jiné než předaný argument typu `Object` při `Object` nebyla nutná.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pouze vyvolání metody nebo vlastnosti u objektů typu `Object`.  
  
-   Pokud dojde k chybě pro argument jiný objekt, předat objekt typu `Object`.  
  
-   Zkontrolujte, zda získávání vyvolání odkaz na nedefinovaný nebo hodnotu null. namísto objekt typu `Object`.  
  
     Například, pokud se tato chyba na MojeProm v následujícím kódu:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Místo toho můžete použít tento kód:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Object – objekt](../../javascript/reference/object-object-javascript.md)   
 [Objekty a pole](../../javascript/objects-and-arrays-javascript.md)