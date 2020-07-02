---
title: Za Throw musí následovat výraz na stejném řádku zdroje | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815523"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Vyvolání musí být následováno výrazem na stejném řádku zdroje
Použili jste `throw` klíčové slovo, ale nesledovali jste výraz na stejném řádku zdroje. `throw`Příkaz se skládá ze dvou částí: `throw` klíčové slovo následovaný výrazem, který má být vyvolán. Příklad:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Tyto dvě součásti nemůžete rozdělit.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že `throw` klíčové slovo a výraz, který má být vyvolán, se zobrazí na stejném řádku.  
  
## <a name="see-also"></a>Viz také:  
 [Error – objekt](../../javascript/reference/error-object-javascript.md)   
 [throw – příkaz](../../javascript/reference/throw-statement-javascript.md)   
 [zkusit... zachytit... Finally – příkaz](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)