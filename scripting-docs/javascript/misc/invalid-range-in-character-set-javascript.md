---
description: Pokusili jste se vytvořit regulární výraz s neplatným rozsahem znakové sady.
title: Neplatný rozsah ve znakové sadě (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 9441f9cfd3adf94ddd38841d522c83922c9154f1
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571672"
---
# <a name="invalid-range-in-character-set-javascript"></a>Neplatný rozsah ve znakové sadě (JavaScript)
Pokusili jste se vytvořit regulární výraz s neplatným rozsahem znakové sady. Znakové sady musí být v rozsahu od pouze jednoho znaku, například a-z nebo 0-9; třídy znaků, jako je například \w, nemůžete zahrnout do znakové sady. První znak v rozsahu musí být také před druhým znakem v rozsahu. Například:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte pouze jeden znak pro vytvoření sady znaků regulárního výrazu a ujistěte se, že jsou ve správném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Objekt regulárního výrazu](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntaxe regulárního výrazu (JavaScript)](/previous-versions/1400241x(v=vs.100))
