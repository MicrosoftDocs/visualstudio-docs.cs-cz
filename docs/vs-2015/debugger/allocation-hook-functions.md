---
title: Funkce háku přidělení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d201f22d461a04890899ac1cebc177cb1521555
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743353"
---
# <a name="allocation-hook-functions"></a>Funkce háku přidělení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce háku přidělení, nainstalovat pomocí [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), je volána pokaždé, když přidělená, znovu přidělený nebo uvolnění paměti. Tento typ připojení je použít k mnoha různým účelům. Použije k testování způsob, jakým aplikace zpracovává situace nedostatku paměti, například nebo prozkoumat vzory přidělování nebo do protokolu informace o přidělení paměti pro pozdější analýzu.  
  
> [!NOTE]
>  Mějte na paměti omezení týkající se použití funkce knihovny run-time jazyka C ve funkci háku přidělení, je popsáno v [zavěšení přidělení a přidělení paměti jazyka C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkce háku přidělení by měl mít prototyp vypadat asi takto:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Ukazatel, který můžete předat [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) je typu **_crt_alloc_hook –**, jak jsou definovány v CRTDBG. V:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Při volání knihovny run-time hook, *nAllocType* argument určuje, jaké přidělení operace se má provést (**_HOOK_ALLOC**, **_HOOK_REALLOC**, nebo **_HOOK_FREE**). V případě bezplatné nebo realokace `pvData` obsahuje ukazatel na téma uživatele bloku se být uvolněna. V případě přidělení, tento ukazatel je však má hodnotu null, protože ještě nedošlo k přidělení paměti. Zbývající argumenty obsahují velikost přidělení Nejistá, jeho typ bloku číslo sekvenční žádosti přidružené a ukazatel soubor název a číslo řádku ve kterém bylo provedeno přidělení paměti, pokud je k dispozici. Poté, co funkce háku provádí libovolné analýzu a jiné úlohy jeho autor potřebuje, musí vracet buď **TRUE**, což indikuje, že operace přidělení může pokračovat, nebo **FALSE**, která udává, který operace by selhat. Jednoduché hook tohoto typu může zkontrolovat množství paměti přidělené zatím a vrátit **FALSE** malé limit překročení velikosti. Aplikace pak neprovádějí druh chyby přidělení, která by obvykle dochází pouze v případě, že dostupná paměť byla velmi nízký. Složitější háky může udržovat přehled o přidělení vzory, analýza využití paměti nebo zprávy při výskytu určitých situacích.  
  
## <a name="see-also"></a>Viz také  
 [Háky přidělení a přidělení běhové paměti jazyka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Zápis funkce háku ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



