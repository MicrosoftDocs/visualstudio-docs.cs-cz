---
title: Háky přidělení a přidělení běhové paměti jazyka C | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79e55ec521de098a7ae0339c4460502dde3d482d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745787"
---
# <a name="allocation-hooks-and-c-run-time-memory-allocations"></a>Háky přidělení a přidělení běhové paměti jazyka C
Velmi důležité omezení funkcí zavěšení přidělení je, že musí explicitně ignorovat `_CRT_BLOCK` bloky. Tyto bloky jsou přidělení paměti prováděná interně funkcemi běhové knihovny jazyka C, pokud provádějí jakékoli volání funkcí běhové knihovny jazyka C, které přidělují interní paměť. Bloky `_CRT_BLOCK` můžete ignorovat vložením následujícího kódu na začátek funkce Hooku přidělení:

```cpp
if ( nBlockUse == _CRT_BLOCK )
    return( TRUE );
```

Pokud váš zavěšení přidělení Neignoruje `_CRT_BLOCK` bloky, pak jakákoli funkce knihovny run-time jazyka C, která je volána ve vašem zavěšení, může zachytit program v nekonečné smyčce. Například `printf` provede interní přidělení. Pokud váš kód zavěšení volá `printf`, pak výsledné přidělení způsobí, že se váš vidlice znovu volá, čímž se znovu zavolá **printf** a tak dále, až do přetečení zásobníku. Pokud potřebujete nahlásit `_CRT_BLOCK` operací přidělení, jedním ze způsobů obcházení tohoto omezení je použití funkcí rozhraní API systému Windows namísto běhových funkcí pro formátování a výstup. Vzhledem k tomu, že rozhraní API systému Windows nepoužívají haldu běhové knihovny jazyka C, nebudou zasílat do nekonečné smyčky vaše zavěšení připojení.

Pokud prohlížíte zdrojové soubory běhové knihovny, uvidíte, že výchozí funkce Hooku přidělení **CrtDefaultAllocHook** (která jednoduše vrátí **hodnotu true**) se nachází v samostatném souboru vlastního DBGHOOK. R. Chcete-li, aby byl zavěšení připojení volán i pro přidělení spouštěné spouštěcím kódem za běhu, který je proveden před funkcí **Main** vaší aplikace, můžete tuto výchozí funkci nahradit jednou z vlastních místo pomocí [_ CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook).

## <a name="see-also"></a>Viz také:
- [Zápis funkce volání pro ladění](../debugger/debug-hook-function-writing.md)
