---
description: Došlo k pokusu o vyvolání metody Boolean. prototyp. toString nebo Boolean. prototype. valueOf – u objektu jiného než logického typu.
title: Očekávána logická hodnota | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571438"
---
# <a name="boolean-expected"></a>Byla očekávána logická hodnota
Došlo k pokusu o vyvolání metody **Boolean. prototyp. ToString** nebo **Boolean. prototype. valueOf –** u objektu jiného typu než `Boolean` . Objekt tohoto typu vyvolání musí být typu `Boolean` . Například:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Oprava této chyby

- Pro objekty typu Boolean volejte pouze metody **Boolean. prototyp. ToString** nebo **Boolean. prototype. valueOf –** **.**

## <a name="see-also"></a>Viz také

- [Boolean – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Datové typy](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Řízení toku programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Kopírování, předávání a porovnávání dat](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
