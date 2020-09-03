---
title: Funkce zavěšení přidělení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 81135546ffa208a4efb96569cd7968dfe560cdf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702523"
---
# <a name="allocation-hook-functions"></a>Funkce háku přidělení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkce zavěšení přidělení, která je nainstalována pomocí [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), je volána při každém přidělení paměti, opětovném přidělení nebo uvolnění. Tento typ zavěšení lze použít pro mnoho různých účelů. Použijte ji k otestování, jak aplikace zpracovává nedostatečné paměťové situace, například nebo pro kontrolu vzorů přidělení nebo k protokolování informací o přidělení pro pozdější analýzu.  
  
> [!NOTE]
> Pamatujte na omezení použití funkcí běhové knihovny jazyka C ve funkci zavěšení přidělení popsané v části [zavěšení přidělení a přidělení paměti za běhu jazyka c](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Funkce Hooku přidělení by měla mít prototyp podobný následujícímu:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Ukazatel, který předáte [_CrtSetAllocHook](https://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) , je typu **_CRT_ALLOC_HOOK**, jak je definováno v souboru Crtdbg. Y  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Když knihovna run-time volá váš Hook, argument *nAllocType* určuje, jakou operaci přidělení se má provést (**_HOOK_ALLOC**, **_HOOK_REALLOC**nebo **_HOOK_FREE**). V případě bezplatného nebo přerozdělení `pvData` obsahuje ukazatel na téma uživatele bloku, který má být uvolněn. V případě přidělení je však tento ukazatel null, protože přidělení ještě neproběhlo. Zbývající argumenty obsahují velikost příslušného přidělení, jeho typ bloku, pořadové číslo požadavku, který je k němu přidružen, a ukazatel na název souboru a číslo řádku, ve kterém bylo přidělení provedeno, je-li k dispozici. Jakmile funkce Hooku provede jakoukoli analýzu a další úkoly, které chce autor, musí vrátit **hodnotu true**, která značí, že operace přidělení může pokračovat nebo **hodnota false**, což značí, že operace by neměla selhat. Jednoduchý vidlice tohoto typu může ověřit množství přidělené paměti a vrátit **hodnotu false** , pokud by tato hodnota přesáhla malý limit. Aplikace by pak vyvolala druh chyb přidělení, ke kterým by normálně docházelo pouze v případě, že je dostupná paměť velmi nízká. Složitější zavěšení můžou sledovat vzory přidělování, analyzovat využití paměti nebo nahlásit, kdy nastane určitá situace.  
  
## <a name="see-also"></a>Viz také  
 [Háky přidělení a přidělení běhové paměti jazyka C](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
