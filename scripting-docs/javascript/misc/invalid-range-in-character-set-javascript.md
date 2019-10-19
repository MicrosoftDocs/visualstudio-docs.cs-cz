---
title: Neplatný rozsah ve znakové sadě (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29f28f0ceeb6bd1bf0a8f28438afd803d3a9a9ac
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576624"
---
# <a name="invalid-range-in-character-set-javascript"></a>Neplatný rozsah ve znakové sadě (JavaScript)
Pokusili jste se vytvořit regulární výraz s neplatným rozsahem znakové sady. Znakové sady musí být v rozsahu od pouze jednoho znaku, například a-z nebo 0-9; třídy znaků, jako je například \w, nemůžete zahrnout do znakové sady. První znak v rozsahu musí být také před druhým znakem v rozsahu. Příklad:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte pouze jeden znak pro vytvoření sady znaků regulárního výrazu a ujistěte se, že jsou ve správném pořadí.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [objektu regulárního výrazu](../../javascript/reference/regular-expression-object-javascript.md)  
 [Syntaxe regulárního výrazu (JavaScript)](https://msdn.microsoft.com/library/1400241x)