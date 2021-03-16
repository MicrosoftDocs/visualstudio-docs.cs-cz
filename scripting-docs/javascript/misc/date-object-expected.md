---
description: Pokusili jste se vyvolat metodu Date. prototype. toString nebo Date. prototype. valueOf – u objektu jiného typu než Date.
title: Byl očekáván objekt Date | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 171514ae180c2e9b24e8aee56a23c47a909bd152
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571087"
---
# <a name="date-object-expected"></a>Byl očekáván objekt Date
Pokusili jste se vyvolat metodu **Date. prototype. ToString** nebo **Date. prototype. valueOf –** u objektu jiného typu než `Date` . Objekt tohoto typu vyvolání musí být typu `Date` . Například:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu volejte pouze metody **Date. prototyp. ToString** nebo **Date. prototype. valueOf –** `Date` .  
  
## <a name="see-also"></a>Viz také  
 [Date – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [GETDATE – metoda (Date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Vnitřní objekty](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)
