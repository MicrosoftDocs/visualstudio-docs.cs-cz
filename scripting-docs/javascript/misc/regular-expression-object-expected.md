---
title: Byl očekáván objekt regulárního výrazu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370e5a8028bae0e60c265ba65dca12668e4b8d8c
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862055"
---
# <a name="regular-expression-object-expected"></a>Byl očekáván objekt regulárního výrazu
Pokusili jste se vyvolat metodu **RegExp. prototyp. ToString** nebo **RegExp. prototype. valueOf –** u objektu jiného typu než `RegExp` . Objekt tohoto typu vyvolání musí být typu `RegExp` .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu volejte pouze metody **RegExp. prototyp. ToString** nebo **RegExp. prototype. valueOf –** `RegExp` .  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntaxe regulárního výrazu (JavaScript)](/previous-versions/1400241x(v=vs.100))