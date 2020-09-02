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
ms.openlocfilehash: 28eec125914f0207fbdf79a39ea2140dd74d6d0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816225"
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
 [Object – objekt](../../javascript/reference/object-object-javascript.md)   
 [Objekty a pole](../../javascript/objects-and-arrays-javascript.md)