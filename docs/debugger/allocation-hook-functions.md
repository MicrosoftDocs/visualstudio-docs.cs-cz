---
title: Funkce zavěšení přidělení | Microsoft Docs
description: Přečtěte si, jak používat funkce zavěšení přidělení, které jsou nainstalovány pomocí _CrtSetAllocHook, pokud potřebujete provést ladění v jazyce C run-time (CRT) v aplikaci Visual Studio.
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0bea73a044dabce5270c06f68658f85c612574c
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729181"
---
# <a name="allocation-hook-functions"></a>Funkce háku přidělení
Funkce zavěšení přidělení, která je nainstalována pomocí [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), je volána při každém přidělení, přidělení nebo uvolnění paměti. Tento typ zavěšení můžete použít pro mnoho různých účelů. Použijte ji k otestování, jak aplikace zpracovává nedostatečné paměťové situace, například pro kontrolu způsobů přidělení, nebo informace o přidělení protokolu pro pozdější analýzu.

> [!NOTE]
> Pamatujte na omezení použití funkcí běhové knihovny jazyka C ve funkci zavěšení přidělení popsané v části [háky přidělení a přidělení paměti C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).

 Funkce Hooku přidělení by měla mít prototyp podobný následujícímu příkladu:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Ukazatel, který předáte [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) , je typu **_CRT_ALLOC_HOOK**, jak je definováno v souboru Crtdbg. Y

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Když knihovna run-time volá váš Hook, argument *nAllocType* určuje, jakou operaci přidělení má být proveden (**_HOOK_ALLOC**, **_HOOK_REALLOC** nebo **_HOOK_FREE**). V bezplatném nebo ve přerozdělování `pvData` má ukazatel na článek o uživateli bloku, který má být uvolněn. U přidělení je však tento ukazatel null, protože přidělení neproběhlo. Zbývající argumenty obsahují velikost příslušného přidělení, jeho typ bloku, pořadové číslo požadavku, který je k němu přidružen, a ukazatel na název souboru. Pokud je k dispozici, argumenty také obsahují číslo řádku, ve kterém bylo přidělení provedeno. Jakmile funkce Hooku provede jakoukoli analýzu a další úkoly, které chce autor, musí vrátit **hodnotu true**, která značí, že operace přidělení může pokračovat nebo **hodnota false**, což značí, že operace by neměla selhat. Jednoduchý vidlice tohoto typu může ověřit množství přidělené paměti a vrátit **hodnotu false** , pokud by tato hodnota přesáhla malý limit. Aplikace by pak vyvolala druh chyb přidělení, ke kterým by normálně docházelo pouze v případě, že je dostupná paměť velmi nízká. Složitější zavěšení můžou sledovat vzory přidělování, analyzovat využití paměti nebo nahlásit, kdy nastane určitá situace.

## <a name="see-also"></a>Viz také

- [Zavěšení přidělení a přidělení paměti C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)