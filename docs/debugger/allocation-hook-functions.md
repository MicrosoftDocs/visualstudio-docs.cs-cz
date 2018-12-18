---
title: Funkce háku přidělení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d49bbff482683c4ac3e0f5f6a4060b176db0d94
ms.sourcegitcommit: 97204b85caadbcf14baeb6738710e287a196673e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "37433353"
---
# <a name="allocation-hook-functions"></a>Funkce háku přidělení
Funkce háku přidělení, nainstalovat pomocí [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), je volána pokaždé, když přidělená, nevyčerpané nebo uvolnění paměti. Tento typ připojení můžete použít k mnoha různým účelům. Pomocí něho můžete testovat, jak aplikace zpracovává situace nedostatku paměti, například k prozkoumání vzory přidělování nebo protokolovat informace o přidělení paměti pro pozdější analýzu.  
  
> [!NOTE]
>  Mějte na paměti omezení týkající se použití funkce knihovny run-time jazyka C ve funkci háku přidělení, je popsáno v [zavěšení přidělení a přidělení paměti jazyka C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkce háku přidělení by měl mít prototyp jako v následujícím příkladu:  
  
```cpp
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Ukazatel, který můžete předat [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) je typu **_crt_alloc_hook –**, jak jsou definovány v CRTDBG. V:  
  
```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Při volání knihovny run-time hook, *nAllocType* argument určuje, jaké přidělení operace se provést (**_HOOK_ALLOC**, **_HOOK_REALLOC**, nebo **_HOOK_FREE**). V bezplatné nebo realokace `pvData` má ukazatel na článek uživatele bloku se být uvolněna. Ale pro přidělení, ukazatele this má hodnotu null, protože nedošlo k přidělení paměti. Zbývající argumenty obsahují velikost přidělení Nejistá, jeho typ bloku číslo sekvenční žádosti přidružené a ukazatel na název souboru. Pokud je k dispozici argumenty také zahrnovat číslo řádku, ve kterém bylo provedeno přidělení. Poté, co funkce háku provádí libovolné analýzu a jiné úlohy jeho autor potřebuje, musí vracet buď **TRUE**, což indikuje, že operace přidělení může pokračovat, nebo **FALSE**, která udává, který operace by selhat. Jednoduché hook tohoto typu může zkontrolovat množství paměti přidělené zatím a vrátit **FALSE** malé limit překročení velikosti. Aplikace pak neprovádějí druh chyby přidělení, která by obvykle dochází pouze v případě, že dostupná paměť byla velmi nízký. Složitější háky může udržovat přehled o přidělení vzory, analýza využití paměti nebo zprávy při výskytu určitých situacích.  
  
## <a name="see-also"></a>Viz také  
 [Háky přidělení a přidělení běhové paměti jazyka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Zápis funkce volání pro ladění](../debugger/debug-hook-function-writing.md)   
