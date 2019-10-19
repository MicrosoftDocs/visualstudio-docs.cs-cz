---
title: Byl očekáván objekt regulárního výrazu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: bf9e2e99c6a539f450afcfe9eef1f5588d5b84f6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573707"
---
# <a name="regular-expression-object-expected"></a>Byl očekáván objekt regulárního výrazu
Pokusili jste se vyvolat metodu **RegExp. prototyp. ToString** nebo **RegExp. prototype. valueOf –** u objektu jiného typu než `RegExp`. Objekt tohoto typu volání musí být typu `RegExp`.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu `RegExp` volejte pouze metody **RegExp. prototyp. ToString** nebo **RegExp. prototype. valueOf –** .  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)  
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)