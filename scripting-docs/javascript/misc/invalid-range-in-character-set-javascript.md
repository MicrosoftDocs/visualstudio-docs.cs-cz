---
title: Neplatný rozsah ve znakové nastavit (JavaScript) | Dokumentace Microsoftu
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
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903631"
---
# <a name="invalid-range-in-character-set-javascript"></a>Neplatný rozsah ve znakové sadě (JavaScript)
Pokoušíte se o vytvoření regulárního výrazu s rozsahem sadě neplatný znak. Znakových sad musí být v rozsahu od jednotlivé znaky, jako je například a-z nebo 0-9; třídy znaků, jako je například \w nemůže obsahovat ve znakové sadě. První znak v rozsahu také musí být uvedena před druhým znakem v rozsahu. Příklad:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Používejte pouze jednotlivé znaky pro vytváření sady znak regulárního výrazu a ujistěte se, že jsou ve správném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)