---
title: Byla očekávána logická hodnota | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868089"
---
# <a name="boolean-expected"></a>Byla očekávána logická hodnota
Pokusili jste se vyvolat **Boolean.prototype.toString** nebo **Boolean.prototype.valueOf** metodu na objekt typu než `Boolean`. Objekt tohoto typu volání musí být typu `Boolean`. Příklad:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Oprava této chyby

- Vyvolat pouze **Boolean.prototype.toString** nebo **Boolean.prototype.valueOf** metod u objektů typu **Boolean.**

## <a name="see-also"></a>Viz také

- [Boolean – objekt](../../javascript/reference/boolean-object-javascript.md)
- [Datové typy](../../javascript/data-types-javascript.md)
- [Řízení toku programu](../../javascript/controlling-program-flow-javascript.md)
- [Kopírování, předávání a porovnávání dat](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)