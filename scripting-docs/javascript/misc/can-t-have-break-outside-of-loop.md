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
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817655"
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
 [break – příkaz](../../javascript/reference/break-statement-javascript.md)   
 [Řízení toku programu](../../javascript/controlling-program-flow-javascript.md)   
 [Řešení potíží se skripty](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)