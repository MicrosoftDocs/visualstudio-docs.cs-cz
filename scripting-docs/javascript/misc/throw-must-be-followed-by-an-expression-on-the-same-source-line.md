---
title: Za Throw musí následovat výraz na stejném řádku zdroje | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572760"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Vyvolání musí být následováno výrazem na stejném řádku zdroje
Použili jste klíčové slovo `throw`, ale nenásledovala s výrazem na stejném řádku zdroje. Příkaz `throw` se skládá ze dvou částí: klíčové slovo `throw` následovaný výrazem, který má být vyvolán. Příklad:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Tyto dvě součásti nemůžete rozdělit.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že klíčové slovo `throw` a výraz, který má být vyvolán, se zobrazí na stejném řádku.  
  
## <a name="see-also"></a>Viz také:  
 [Objekt Error](../../javascript/reference/error-object-javascript.md)    
   [příkazu throw](../../javascript/reference/throw-statement-javascript.md)  
 [try...catch...finally – příkaz](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)