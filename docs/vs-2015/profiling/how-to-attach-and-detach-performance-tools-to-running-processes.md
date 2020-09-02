---
title: 'Postupy: připojení a odpojení nástrojů výkonu ke spuštěným procesům | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b8fc664ee47cd34ab984d1ac448b45c2f17c5b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804962"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Postupy: připojení a odpojení nástrojů výkonu ke spouštění procesů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler se dá použít k připojení k běžícímu procesu nebo k jeho odpojení a k usnadnění vzorkování a shromažďování dat o výkonu. Tuto metodu můžete použít k profilování procesu, pokud se chcete vyhnout shromažďování dat o době načítání aplikace, nebo ke sledování výkonu procesu po dosažení určitého stavu.  
  
> [!NOTE]
> Následující postup se týká připojení a odpojení procesů v rámci [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] integrovaného vývojového environmnent (IDE). Informace o tom, jak používat nástroje příkazového řádku, naleznete v tématu [profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md). Informace o tom, jak profilovat služby, najdete v tématu profilace [služby](../profiling/command-line-profiling-of-services.md).  
  
 Procesy, které jsou k dispozici pro profil, závisí na uživatelských oprávněních, která jsou nastavena správcem počítače. Uživatelský účet může mít například oprávnění k některým z následujících způsobů:  
  
- Pokročilé funkce profilování, pokud správce nastavil ovladač a službu tak, aby se spouštěly.  
  
- Pouze profilace vzorků (Domain Users).  
  
- Odepřete přístup k profilování pro každého.  
  
  Další informace najdete v tématech [profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možnosti správy v [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Připojení ke spuštěnému procesu  
  
1. V nabídce **analyzovat** přejděte na **Profiler** a pak klikněte na **připojit nebo odpojit**.  
  
     \- ani  
  
     V **prohlížeč výkonu**klikněte pravým tlačítkem myši na relaci výkonu a pak klikněte na tlačítko **připojit nebo odpojit**.  
  
     Zobrazí se dialogové okno **Připojit profiler k procesu** .  
  
2. Klikněte na název procesu, ke kterému se chcete připojit.  
  
3. Klikněte na **připojit**.  
  
### <a name="to-detach-from-a-running-process"></a>Odpojení od běžícího procesu  
  
1. V nabídce **analyzovat** přejděte na **Profiler** a pak klikněte na **připojit nebo odpojit**.  
  
     \- ani  
  
     V **prohlížeč výkonu**klikněte pravým tlačítkem myši na relaci výkonu a pak klikněte na tlačítko **připojit nebo odpojit**.  
  
     Zobrazí se dialogové okno **Připojit profiler k procesu** .  
  
2. Klikněte na název bitové kopie, ze které chcete odpojit.  
  
3. Klikněte na **Odpojit**.  
  
## <a name="see-also"></a>Viz také  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Přehled výkonnostní relace](../profiling/performance-session-overview.md)   
 [Postupy: spuštění a ukončení shromažďování dat výkonu](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilace a zabezpečení systému Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
