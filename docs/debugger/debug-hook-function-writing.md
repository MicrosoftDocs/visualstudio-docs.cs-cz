---
title: Zápis funkce vidlice ladění | Microsoft Docs
description: Přečtěte si o řadě vlastních funkcí ladicího programu, které můžete napsat, abyste mohli vložit svůj kód do předdefinovaných bodů uvnitř normálního zpracování ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76727da1ed057902d8f757594f5ed2e07bcf3cea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857542"
---
# <a name="debug-hook-function-writing"></a>Zápis funkce háku ladění
Tato část popisuje počet vlastních funkcí ladicího programu, které můžete psát, a to tak, že vložíte kód do některých předdefinovaných bodů uvnitř normálního zpracování ladicího programu.

## <a name="in-this-section"></a>V tomto oddílu
 [Funkce zavěšení bloků klienta](../debugger/client-block-hook-functions.md) Obsahuje doprovodné materiály a prototyp pro psaní funkcí, které ověřují nebo oznamují obsah dat uložených v _CLIENT_BLOCK blocích.

 [Funkce zavěšení přidělení](../debugger/allocation-hook-functions.md) Definuje funkci zavěšení přidělení, zkoumá jejich různá použití, omezuje omezení a poskytuje prototyp.

 [Zavěšení přidělení a přidělení paměti CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Popisuje omezení funkcí zavěšení přidělení explicitních ignorování `_CRT_BLOCK` bloků, pokud provádějí jakékoli volání funkcí běhové knihovny jazyka C, které přidělují interní paměť. Toto téma také obsahuje důsledky v případě, že zavěšení přidělení Neignoruje `_CRT_BLOCK` bloky (s příklady) a jak změnit výchozí funkci zavěšení přidělení, **CrtDefaultAllocHook**.

 [Funkce zavěšení sestav](../debugger/report-hook-functions.md) V tomto tématu jsou popsány informace `_CrtSetReportHook` , které můžete použít k filtrování sestav pro zaměření na konkrétní typy přidělení. Toto téma také poskytuje prototyp.

## <a name="related-sections"></a>Související oddíly

- [Techniky ladění CRT](../debugger/crt-debugging-techniques.md) – odkazy na techniky ladění pro knihovnu C Run-Time Library, včetně použití knihovny ladění CRT, maker pro vytváření sestav, rozdílů mezi `malloc` a `_malloc_dbg` , zápisem funkcí ladicího programu a haldy ladění CRT.