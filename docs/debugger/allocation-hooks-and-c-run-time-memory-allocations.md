---
title: Háky přidělení a přidělení běhové paměti jazyka C
description: Pochopení přidělujících háky a přidělení paměti za běhu v nástroji Visual Studio pro ladění. Funkce zavěšení přidělení musí explicitně ignorovat _CRT_BLOCK bloky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], hook functions
- memory allocation, troubleshooting allocation hooks
- allocation hooks
- hooks, allocation
ms.assetid: cc34ee96-3d91-41bd-a019-aa3759139e7e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49739a0c07426329dc20f7fd459febcc70866ec9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866057"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Háky přidělení a přidělení běhové paměti jazyka C
Velmi důležité omezení funkcí zavěšení přidělení je, že musí explicitně ignorovat `_CRT_BLOCK` bloky. Tyto bloky jsou přidělení paměti prováděná interně funkcemi běhové knihovny jazyka C, pokud provádějí jakékoli volání funkcí běhové knihovny jazyka C, které přidělují interní paměť. Bloky můžete ignorovat `_CRT_BLOCK` vložením následujícího kódu na začátek funkce Hooku přidělení:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Pokud váš Hook přidělení Neignoruje `_CRT_BLOCK` bloky, pak jakákoli funkce knihovny run-time jazyka C volaná ve vašem zavěšení může zachytit program v nekonečné smyčce. Například `printf` provede interní přidělení. Pokud váš kód zavěšení volá `printf` , výsledné přidělení pak způsobí, že se váš vidlice znovu volá, čímž se znovu zavolá **printf** a tak dále, dokud se zásobník nepřesměruje. Pokud potřebujete nahlásit `_CRT_BLOCK` operace přidělení, jedním ze způsobů obcházení tohoto omezení je použití funkcí rozhraní API systému Windows namísto běhových funkcí pro formátování a výstup. Vzhledem k tomu, že rozhraní API systému Windows nepoužívají haldu běhové knihovny jazyka C, nebudou zasílat do nekonečné smyčky vaše zavěšení připojení.

Pokud prohlížíte zdrojové soubory knihovny run-time, uvidíte, že výchozí funkce Hooku přidělení, **CrtDefaultAllocHook** (která jednoduše vrátí **hodnotu true**), je umístěna v samostatném souboru vlastní DBGHOOK. C. Chcete-li, aby byl zavěšení připojení volán i pro přidělení spouštěcího kódu modulu runtime, který je proveden před funkcí **Main** vaší aplikace, můžete tuto výchozí funkci nahradit jednou z vlastních funkcí namísto použití [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Viz také
- [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)
