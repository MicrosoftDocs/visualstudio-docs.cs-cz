---
description: V globálním rozsahu kódu jste použili návratový příkaz.
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
ms.openlocfilehash: c275db9b2b13f6730ef62a757502b1d51a59ee43
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571659"
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
