---
title: Byl očekáván typ catch | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47411a6376cd843b3a12cf74ed1800775b98cd83
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861954"
---
# <a name="expected-catch"></a>Byl očekáván příkaz 'catch'
Použili jste blok **Try** zpracování výjimek, ale nezapsali jste přidružený příkaz **catch** . Mechanismus zpracování výjimek vyžaduje, aby kód, který může selhat, a kód, který by neměl být proveden, pokud dojde k výjimce, je zabalen do bloku **Try** . Výjimky jsou vyvolány v rámci bloku **Try** pomocí příkazu **throw** a zachyceny mimo blok **Try** s jedním nebo více příkazy **catch** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte přidružený blok **catch** .  
  
- Zkuste místo bloku **catch** použít blok **finally** .  
  
## <a name="see-also"></a>Viz také  
 [zkusit... zachytit... Finally – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Error – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)