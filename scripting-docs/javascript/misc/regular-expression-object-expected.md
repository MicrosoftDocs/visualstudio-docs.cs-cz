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
ms.openlocfilehash: d9f5816c0bf3ad7c8dbf7d394952c631923d89cf
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814626"
---
# <a name="regular-expression-object-expected"></a>Byl očekáván objekt regulárního výrazu
Pokusili jste se vyvolat metodu **RegExp. prototyp. ToString** nebo **RegExp. prototype. valueOf –** u objektu jiného typu než `RegExp` . Objekt tohoto typu vyvolání musí být typu `RegExp` .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro objekty typu volejte pouze metody **RegExp. prototyp. ToString** nebo **RegExp. prototype. valueOf –** `RegExp` .  
  
## <a name="see-also"></a>Viz také:  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)