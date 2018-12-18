---
title: Neočekávaný kvantifikátor (JavaScript) | Dokumentace Microsoftu
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef0955bac35009d9b6c82f1856bb9005a08043ad
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282260"
---
# <a name="unexpected-quantifier-javascript"></a>Neočekávaný kvantifikátor (JavaScript)
Při vytváření vaší vyhledávací vzor regulárního výrazu, vytvoříte prvek modelu s faktorem neplatné opakování. Například vzor  
  
```  
/^+/  
```  
  
 je neplatné. protože elementu ^ (začátku vstupu) nemůže mít faktor opakování. Následující tabulka uvádí prvky, které nelze mít faktory opakování.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|^|Začátku vstupu|  
|$|Konec vstupu|  
|\b|Hranice slova|  
|\B|Mimoslovní hranic|  
|*|Nula nebo více opakování|  
|+|Jeden nebo více opakování|  
|?|Žádný nebo jeden opakování|  
|{n}|n opakování|  
|{n}|n nebo další opakování|  
|{n, m}|Z n až m, včetně opakování|  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby že vaše vyhledávací vzor prvek obsahuje pouze faktory právní opakování.  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)