---
title: Principy přidělování paměti a hodnot dat životnosti objektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 816f750148cc30de86fc116f80f64b218b4699d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145449"
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Princip přidělování paměti a hodnot životnosti objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metoda profilování *alokace paměti .net* [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci shromažďuje informace o velikosti a počtu objektů, které byly vytvořeny v rámci přidělení nebo zničení v uvolňování paměti a další informace o *zásobníku volání* funkce při výskytu události. *Zásobník volání* je dynamická struktura, která ukládá informace o funkcích, které jsou spuštěny na procesoru.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Profiler paměti přerušuje procesor počítače při každém přidělení objektu .NET Framework v profilované aplikaci. Při shromažďování dat o době životnosti objektu přerušuje profiler procesor po každém uvolnění paměti rozhraní .NET Framework. Data jsou agregována pro každou profilovou funkci a pro každý typ objektu.  
  
## <a name="allocation-data"></a>Alokační data  
 Při výskytu události. Memory se zvýší celkový počet a velikost objektů přidělených nebo zničených paměti.  
  
 Když dojde k události přidělení paměti, Profiler zvýší počty vzorků pro každou funkci v zásobníku volání. Když jsou data shromážděna, pouze jedna funkce v zásobníku volání aktuálně provádí kód v těle své funkce. Ostatní funkce v zásobníku jsou rodiče v hierarchii volání funkcí, které čekají na vrácení funkcí, které volají.  
  
- V případě události alokace Profiler zvýší počet *exkluzivních* vzorků funkce, ve které aktuálně probíhá zpracování instrukcí. Vzhledem k tomu, že exkluzivní vzorek je také součástí celkových (*včetně*) vzorků funkce, je také zvýšen celkový počet vzorků aktuálně aktivní funkce.  
  
- Profiler zvýší celkový počet vzorků všech ostatních funkcí v zásobníku volání.  
  
## <a name="lifetime-data"></a>Data o životnosti  
 Systém uvolňování paměti .NET Framework spravuje přidělování a uvolňování paměti pro vaši aplikaci. Pro optimalizaci výkonu uvolňování paměti je spravovaná halda rozdělená na tři generace: 0, 1 a 2. Systém uvolňování paměti v době běhu ukládá nové objekty v generaci 0. Objekty, které zůstávají kolekce, jsou povýšeny a uloženy v generacích 1 a 2.  
  
 Uvolňování paměti uvolňuje paměť uvolněním celé generace objektů. Pro objekty, které vytvořil profilovaná aplikace, zobrazuje zobrazení životnost objektů počet a velikost objektů a generaci, když jsou uvolněny.
