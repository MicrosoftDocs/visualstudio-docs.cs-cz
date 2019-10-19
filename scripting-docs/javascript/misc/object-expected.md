---
title: Očekáván objekt | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 1611596d844d43ef72663154dc48791830dfe29f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573726"
---
# <a name="object-expected"></a>Očekáván objekt
Pokusili jste se vyvolat metodu nebo vlastnost objektu jiného typu než `Object` nebo jste předali argument jiného typu než `Object`, pokud byl vyžadován `Object`.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu `Object` vyvolat pouze metodu nebo vlastnost.  
  
- Pokud dojde k chybě pro argument bez objektu, předejte objekt typu `Object`.  
  
- Ověřte, zda je místo objektu typu `Object` vyvolána reference nedefinovaného nebo null.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Objekt objektu  ](../../javascript/reference/object-object-javascript.md)  
 [Objekty a pole](../../javascript/objects-and-arrays-javascript.md)