---
title: Byl očekáván objekt regulárního výrazu | Dokumentace Microsoftu
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8e3c48b116680fe73d4cc318038cb2c13c4164
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280309"
---
# <a name="regular-expression-object-expected"></a>Byl očekáván objekt regulárního výrazu
Pokusili jste se vyvolat **RegExp.prototype.toString** nebo **RegExp.prototype.valueOf** metodu na objekt typu než `RegExp`. Objekt tohoto typu volání musí být typu `RegExp`.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Vyvolat pouze **RegExp.prototype.toString** nebo **RegExp.prototype.valueOf** metod u objektů typu `RegExp`.  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)