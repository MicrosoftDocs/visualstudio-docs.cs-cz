---
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
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862658"
---
# <a name="boolean-expected"></a>Byla očekávána logická hodnota
Došlo k pokusu o vyvolání metody **Boolean. prototyp. ToString** nebo **Boolean. prototype. valueOf –** u objektu jiného typu než `Boolean` . Objekt tohoto typu vyvolání musí být typu `Boolean` . Příklad:

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