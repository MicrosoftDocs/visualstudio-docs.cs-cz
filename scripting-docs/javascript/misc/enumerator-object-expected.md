---
title: Byl očekáván objekt Enumerator | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572877"
---
# <a name="enumerator-object-expected"></a>Byl očekáván objekt Enumerator
Pokusili jste se vyvolat metodu **Enumerator. prototype. atEnd –, Enumerator. prototype. Item, Enumerator. prototype. MoveFirst** nebo **Enumerator. prototype. MoveNext** u objektu jiného typu než `Enumerator`. Objekt tohoto typu volání musí být typu `Enumerator`. Tady je příklad kódu, který toto pravidlo přerušuje:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Vyvolejte metodu **Enumerator. prototype. atEnd –** , **Enumerator. prototype. Item**, **Enumerator. prototype. MoveFirst**nebo **Enumerator. prototype. MoveNext** pro objekty typu `Enumerator`. Chcete-li zjistit, zda se jedná o objekt `Enumerator`, použijte:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [Enumerator – objekt](../../javascript/reference/enumerator-object-javascript.md)