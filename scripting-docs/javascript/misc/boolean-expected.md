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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817668"
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

## <a name="see-also"></a>Viz také:

- [Boolean – objekt](../../javascript/reference/boolean-object-javascript.md)
- [Typy dat](../../javascript/data-types-javascript.md)
- [Řízení toku programu](../../javascript/controlling-program-flow-javascript.md)
- [Kopírování, předávání a porovnávání dat](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)