---
description: Pokusili jste se vyvolat metodu Enumerator. prototype. atEnd –, Enumerator. prototype. Item, Enumerator. prototype. moveFirst nebo Enumerator. prototype. moveNext pro objekt jiného typu než enumerátor.
title: Byl očekáván objekt Enumerator | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fc48ca3e0f17d97af3d538033c2319538afc079
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571048"
---
# <a name="enumerator-object-expected"></a>Byl očekáván objekt Enumerator
Pokusili jste se vyvolat metodu **Enumerator. prototype. atEnd –, Enumerator. prototype. Item, Enumerator. prototype. MoveFirst** nebo **Enumerator. prototype. MoveNext** u objektu jiného typu než `Enumerator` . Objekt tohoto typu vyvolání musí být typu `Enumerator` . Tady je příklad kódu, který toto pravidlo přerušuje:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Vyvolejte metodu **Enumerator. prototype. atEnd –**, **Enumerator. prototype. Item**, **Enumerator. prototype. MoveFirst** nebo **Enumerator. prototype. MoveNext** pro objekty typu `Enumerator` . Chcete-li zjistit, zda je objekt `Enumerator` objekt, použijte:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Enumerator – objekt](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)
