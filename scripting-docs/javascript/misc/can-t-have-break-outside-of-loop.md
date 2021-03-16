---
description: Pokusili jste se použít klíčové slovo break mimo smyčku.
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
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570645"
---
# <a name="cant-have-break-outside-of-loop"></a>Příkaz 'break' nemůže být uveden mimo smyčku
Pokusili jste se použít klíčové slovo **Break** mimo smyčku. Klíčové slovo **Break** slouží k ukončení smyčky nebo `switch` příkazu. Musí být vložen do těla smyčky nebo `switch` příkazu. **Popisek** však může následovat za klíčovým slovem Break.  
  
```js
break labelname;  
```  
  
 Pokud používáte vnořené smyčky nebo  `switch` příkazy a potřebujete rozdělit smyčku, která není nejvnitřnější, stačí pouze označený tvar tohoto klíčového slova break.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že se klíčové slovo **Break** zobrazuje uvnitř ohraničující smyčky nebo příkazu switch.  
  
## <a name="see-also"></a>Viz také  
 [break – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Řízení toku programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Řešení potíží se skripty](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
