---
title: Byl očekáván objekt Date | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572896"
---
# <a name="date-object-expected"></a>Byl očekáván objekt Date
Pokusili jste se vyvolat metodu **Date. prototype. ToString** nebo **Date. prototype. valueOf –** u objektu jiného typu než `Date`. Objekt tohoto typu volání musí být typu `Date`. Příklad:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu `Date`vyvolat pouze metody **Date. prototyp. ToString** nebo **Date. prototype. valueOf –** .  
  
## <a name="see-also"></a>Viz také:  
 [Objekt data](../../javascript/reference/date-object-javascript.md)   
 [GETDATE – metoda (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Vnitřní objekty](../../javascript/intrinsic-objects-javascript.md)