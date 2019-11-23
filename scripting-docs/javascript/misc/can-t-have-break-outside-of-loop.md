---
title: Příkaz ' break ' nemůže být mimo smyčku | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576018"
---
# <a name="cant-have-break-outside-of-loop"></a>Příkaz 'break' nemůže být uveden mimo smyčku
Pokusili jste se použít klíčové slovo **Break** mimo smyčku. Klíčové slovo **Break** slouží k ukončení smyčky nebo příkazu `switch`. Musí být vložen do těla smyčky nebo příkazu `switch`. **Popisek** však může následovat za klíčovým slovem Break.  
  
```js
break labelname;  
```  
  
 Pokud používáte vnořené smyčky nebo příkazy `switch` a potřebujete rozdělit smyčku, která není nejvnitřnější, stačí pouze označený tvar tohoto klíčového slova **Break** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že se klíčové slovo **Break** zobrazuje uvnitř ohraničující smyčky nebo příkazu switch.  
  
## <a name="see-also"></a>Viz také:  
   [příkazu break](../../javascript/reference/break-statement-javascript.md)  
 [Řízení  toku programu](../../javascript/controlling-program-flow-javascript.md)  
 [Řešení potíží se skripty](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)