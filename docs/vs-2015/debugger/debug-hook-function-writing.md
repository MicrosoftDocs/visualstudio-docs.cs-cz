---
title: Zápis funkce vidlice ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0554c1494bec757d1baecd78cdc302608e5b6b3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573037"
---
# <a name="debug-hook-function-writing"></a>Zápis funkce háku ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato část popisuje počet vlastních funkcí ladicího programu, které můžete psát, a to tak, že vložíte kód do některých předdefinovaných bodů uvnitř normálního zpracování ladicího programu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce háku bloku klienta](../debugger/client-block-hook-functions.md)  
 Obsahuje doprovodné materiály a prototyp pro psaní funkcí, které ověřují nebo oznamují obsah dat uložených v _CLIENT_BLOCK blocích.  
  
 [Funkce háku přidělení](../debugger/allocation-hook-functions.md)  
 Definuje funkci zavěšení přidělení, zkoumá jejich různá použití, omezuje omezení a poskytuje prototyp.  
  
 [Zavěšení přidělení a přidělení paměti CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Popisuje omezení funkcí zavěšení přidělení explicitních ignorování `_CRT_BLOCK` bloků, pokud provádějí jakékoli volání funkcí běhové knihovny jazyka C, které přidělují interní paměť. Toto téma také obsahuje důsledky v případě, že zavěšení přidělení Neignoruje `_CRT_BLOCK` bloky (s příklady) a jak změnit výchozí funkci zavěšení přidělení, **CrtDefaultAllocHook**.  
  
 [Sestava funkcí háku](../debugger/report-hook-functions.md)  
 V tomto tématu jsou popsány informace `_CrtSetReportHook` , které můžete použít k filtrování sestav pro zaměření na konkrétní typy přidělení. Toto téma také poskytuje prototyp.  
  
## <a name="related-sections"></a>Související oddíly  
 [Techniky ladění CRT](../debugger/crt-debugging-techniques.md)  
 Obsahuje odkazy na techniky ladění pro běhovou knihovnu jazyka C, včetně použití knihovny ladění CRT, maker pro vytváření sestav, rozdílů mezi `malloc` a `_malloc_dbg` , psaní funkcí zavěšení ladění a haldy ladění CRT.
