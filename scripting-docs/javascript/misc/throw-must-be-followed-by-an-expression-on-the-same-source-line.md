---
description: Použili jste klíčové slovo throw, ale nenásledovala s výrazem na stejném řádku zdroje.
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
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570710"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Vyvolání musí být následováno výrazem na stejném řádku zdroje
Použili jste `throw` klíčové slovo, ale nesledovali jste výraz na stejném řádku zdroje. `throw`Příkaz se skládá ze dvou částí: `throw` klíčové slovo následovaný výrazem, který má být vyvolán. Například:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Tyto dvě součásti nemůžete rozdělit.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že `throw` klíčové slovo a výraz, který má být vyvolán, se zobrazí na stejném řádku.  
  
## <a name="see-also"></a>Viz také  
 [Error – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [zkusit... zachytit... Finally – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
