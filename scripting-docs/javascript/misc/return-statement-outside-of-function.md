---
title: příkaz ' Return ' mimo funkci | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573688"
---
# <a name="return-statement-outside-of-function"></a>příkaz 'return' mimo funkci
Použili jste příkaz `return` v globálním rozsahu kódu. Příkaz `return` by měl být uveden pouze v těle funkce.  
  
 Volání funkce s operátorem `()` je výraz. Všechny výrazy mají hodnoty; příkaz `return` slouží k určení hodnoty vrácené funkcí. Formulář Obecné je:  
  
```js
  
return [ expression ];  
```  
  
 Při spuštění příkazu `return` se vyhodnotí *výraz* a vrátí se jako hodnota funkce. Pokud není žádný výraz, vrátí se **undefined** .  
  
 Spuštění funkce se zastaví při spuštění příkazu `return`, a to i v případě, že v těle funkce stále zbývá jiné příkazy. Výjimkou z tohoto pravidla je, pokud příkaz **return** nastane uvnitř bloku **Try** a existuje odpovídající blok **finally** , kód v bloku **finally** se spustí před vrácením funkce.  
  
 Pokud funkce vrátí, protože dosáhne konce těla funkce bez provedení příkazu `return`, vrácená hodnota je **nedefinovaná** hodnota (to znamená, že výsledek funkce nelze použít jako součást většího výrazu).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte příkaz `return` z hlavního těla vašeho kódu (globální rozsah).  
  
## <a name="see-also"></a>Viz také:  
   [příkazu return](../../javascript/reference/return-statement-javascript.md)  
 [Objekt funkce](../../javascript/reference/function-object-javascript.md)   
 [caller – vlastnost (Function)](../../javascript/reference/caller-property-function-javascript.md)