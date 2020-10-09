---
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
ms.openlocfilehash: 5e63ee2970c90ffcfff5c02a384d3346b3ea6229
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862633"
---
# <a name="enumerator-object-expected"></a>Byl očekáván objekt Enumerator
Pokusili jste se vyvolat metodu **Enumerator. prototype. atEnd –, Enumerator. prototype. Item, Enumerator. prototype. MoveFirst** nebo **Enumerator. prototype. MoveNext** u objektu jiného typu než `Enumerator` . Objekt tohoto typu vyvolání musí být typu `Enumerator` . Tady je příklad kódu, který toto pravidlo přerušuje:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Vyvolejte metodu **Enumerator. prototype. atEnd –**, **Enumerator. prototype. Item**, **Enumerator. prototype. MoveFirst**nebo **Enumerator. prototype. MoveNext** pro objekty typu `Enumerator` . Chcete-li zjistit, zda je objekt `Enumerator` objekt, použijte:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Enumerator – objekt](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/Enumerator)