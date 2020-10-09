---
title: klíčové slovo default může být v příkazu switch uvedeno jenom jednou | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862782"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>Klíčové slovo 'default' může být v příkazu 'switch' použito pouze jednou
Pokusili jste se použít **výchozí** příkaz více než jednou v rámci příkazu switch. Výchozím případem je vždy poslední příkaz Case v příkazu switch (Jedná se o případ vzdálení).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte všechny další **výchozí** příkazy Case z `switch` příkazu (použijte maximálně jeden výchozí příkaz Case v příkazu switch).  
  
## <a name="see-also"></a>Viz také  
 [Příkaz switch](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Řízení toku programu](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [JavaScript – vyhrazená slova](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)