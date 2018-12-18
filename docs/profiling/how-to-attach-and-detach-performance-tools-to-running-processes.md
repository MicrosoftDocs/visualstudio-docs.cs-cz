---
title: Připojení nástroje pro měření výkonu ke spuštěným procesům
ms.custom: seodec18
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb245b6930d1a633d5d5befa3266c3c7540c0915
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048525"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Postupy: připojení a odpojení nástroje Sledování výkonu ke spuštěným procesům
Profiler slouží k připojení nebo odpojení od spuštěného procesu pro usnadnění odběru vzorků a shromažďuje data výkonu. Tímto způsobem může Profilovat proces, pokud chcete se vyhnout, shromažďování dat o čas načtení aplikace, nebo k monitorování výkonu procesu po jeho dosažení určitý stav.  
  
> [!NOTE]
>  Následující postup se vztahuje k připojení a odpojení procesy v rámci [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] integrované environmnent vývojové (prostředí IDE). Informace o tom, jak pomocí nástrojů příkazového řádku najdete v tématu [profilu z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md). Informace o tom, jak služby profilů najdete v tématu [profilu služby](../profiling/command-line-profiling-of-services.md).  
  
 Procesy, které jsou k dispozici pro profil záviset na oprávnění uživatelského přístupu, které jsou nastaveny správcem počítače. Uživatelský účet může třeba mít oprávnění pro kterýkoli z následujících:  
  
- Pokročilé funkce, profilace, pokud správce nastavil ovladač a spouštění služby.  
  
- Ukázka profilace pouze (uživatelé domény).  
  
- Odepřete přístup k profilaci pro každého.  
  
  Další informace najdete v tématu [profilace a Windows Vista zabezpečení](../profiling/profiling-and-windows-vista-security.md) a možností správy v [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Připojit ke spuštěnému procesu  
  
1.  Na **ladění** nabídky, přejděte k **Profiler**, pak **prohlížeč výkonu**a potom klikněte na tlačítko **připojit**.    
  
     **Připojit Profiler k procesu** zobrazí se dialogové okno.  
  
2.  Klikněte na název, který chcete připojit k procesu.  
  
3.  Klikněte na tlačítko **připojit**.  
  
### <a name="to-detach-from-a-running-process"></a>Chcete-li odpojit od spuštěného procesu  
  
1.  n **ladění** nabídky, přejděte k **Profiler**, pak **prohlížeč výkonu**a potom klikněte na tlačítko **odpojit**. 
  
     **Připojit Profiler k procesu** zobrazí se dialogové okno.  
  
2.  Klikněte na název image, ze kterého se má odpojit.  
  
3.  Klikněte na tlačítko **odpojit**.  
  
## <a name="see-also"></a>Viz také:  
 [Řízení shromažďování dat](../profiling/controlling-data-collection.md)   
 [Přehled relace výkonu](../profiling/performance-session-overview.md)   
 [Postupy: spuštění a ukončení shromažďování dat o výkonu](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilace a zabezpečení Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)