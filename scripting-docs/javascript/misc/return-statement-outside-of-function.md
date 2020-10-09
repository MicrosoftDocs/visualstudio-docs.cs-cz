---
title: příkaz ' Return ' mimo funkci | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ec17d9e421d06736a236e26dd5a1200a5564e7d
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862043"
---
# <a name="return-statement-outside-of-function"></a>příkaz 'return' mimo funkci
Použili jste `return` příkaz v globálním rozsahu kódu. `return`Příkaz by měl být použit pouze v těle funkce.  
  
 Volání funkce s `()` operátorem je výraz. Všechny výrazy mají hodnoty; `return` příkaz se používá k určení hodnoty vrácené funkcí. Formulář Obecné je:  
  
```js
  
return [ expression ];  
```  
  
 Při `return` spuštění příkazu se vyhodnotí *výraz* a vrátí se jako hodnota funkce. Pokud není žádný výraz, vrátí se **undefined** .  
  
 Spuštění funkce se zastaví při `return` spuštění příkazu, i když v těle funkce stále zbývá jiné příkazy. Výjimkou z tohoto pravidla je, pokud příkaz **return** nastane uvnitř bloku **Try** a existuje odpovídající blok **finally** , kód v bloku **finally** se spustí před vrácením funkce.  
  
 Pokud funkce vrátí, protože dosáhne konce těla funkce bez provedení `return` příkazu, vrácená hodnota je **nedefinovaná** hodnota (to znamená, že výsledek funkce nelze použít jako součást rozsáhlejšího výrazu).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte `return` příkaz z hlavního těla vašeho kódu (globální rozsah).  
  
## <a name="see-also"></a>Viz také  
 [Return – příkaz](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/return)   
 [Function – objekt](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [caller – vlastnost (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/caller)