---
title: Očekávána logická hodnota | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576061"
---
# <a name="boolean-expected"></a>Byla očekávána logická hodnota
Došlo k pokusu o vyvolání metody **Boolean. prototyp. ToString** nebo **Boolean. prototype. valueOf –** u objektu jiného typu než `Boolean`. Objekt tohoto typu volání musí být typu `Boolean`. Příklad:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Oprava této chyby

- Pro objekty typu Boolean volejte pouze metody **Boolean. prototyp. ToString** nebo **Boolean. prototype. valueOf –** **.**

## <a name="see-also"></a>Viz také:

- [Boolean – objekt](../../javascript/reference/boolean-object-javascript.md)
- [Datové typy](../../javascript/data-types-javascript.md)
- [Řízení toku programu](../../javascript/controlling-program-flow-javascript.md)
- [Kopírování, předávání a porovnávání dat](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)