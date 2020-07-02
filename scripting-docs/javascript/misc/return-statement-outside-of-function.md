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
ms.openlocfilehash: 32eadcf5ae88dbe64c8ccdb3effbb85bc79f9b32
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816732"
---
# <a name="return-statement-outside-of-function"></a>příkaz 'return' mimo funkci
Použili jste `return` příkaz v globálním rozsahu kódu. `return`Příkaz by měl být použit pouze v těle funkce.  
  
 Volání funkce s `()` operátorem je výraz. Všechny výrazy mají hodnoty; `return`příkaz se používá k určení hodnoty vrácené funkcí. Formulář Obecné je:  
  
```js
  
return [ expression ];  
```  
  
 Při `return` spuštění příkazu se vyhodnotí *výraz* a vrátí se jako hodnota funkce. Pokud není žádný výraz, vrátí se **undefined** .  
  
 Spuštění funkce se zastaví při `return` spuštění příkazu, i když v těle funkce stále zbývá jiné příkazy. Výjimkou z tohoto pravidla je, pokud příkaz **return** nastane uvnitř bloku **Try** a existuje odpovídající blok **finally** , kód v bloku **finally** se spustí před vrácením funkce.  
  
 Pokud funkce vrátí, protože dosáhne konce těla funkce bez provedení `return` příkazu, vrácená hodnota je **nedefinovaná** hodnota (to znamená, že výsledek funkce nelze použít jako součást rozsáhlejšího výrazu).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte `return` příkaz z hlavního těla vašeho kódu (globální rozsah).  
  
## <a name="see-also"></a>Viz také:  
 [Return – příkaz](../../javascript/reference/return-statement-javascript.md)   
 [Function – objekt](../../javascript/reference/function-object-javascript.md)   
 [caller – vlastnost (Function)](../../javascript/reference/caller-property-function-javascript.md)