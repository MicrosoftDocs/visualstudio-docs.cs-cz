---
title: Příkaz ' break ' nemůže být mimo smyčku | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee177c8070fc5af8123d7fd78e69b1f767a5b700
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862802"
---
# <a name="cant-have-break-outside-of-loop"></a>Příkaz 'break' nemůže být uveden mimo smyčku
Pokusili jste se použít klíčové slovo **Break** mimo smyčku. Klíčové slovo **Break** slouží k ukončení smyčky nebo `switch` příkazu. Musí být vložen do těla smyčky nebo `switch` příkazu. **Popisek** však může následovat za klíčovým slovem Break.  
  
```js
break labelname;  
```  
  
 Pokud používáte vnořené smyčky nebo **break** `switch` příkazy a potřebujete rozdělit smyčku, která není nejvnitřnější, stačí pouze označený tvar tohoto klíčového slova break.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že se klíčové slovo **Break** zobrazuje uvnitř ohraničující smyčky nebo příkazu switch.  
  
## <a name="see-also"></a>Viz také  
 [break – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Řízení toku programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Řešení potíží se skripty](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)