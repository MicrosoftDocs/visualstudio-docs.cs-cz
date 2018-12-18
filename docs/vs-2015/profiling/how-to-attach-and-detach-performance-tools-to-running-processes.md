---
title: 'Postupy: připojení a odpojení nástroje Sledování výkonu ke spuštěným procesům | Dokumentace Microsoftu'
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
manager: ghogen
ms.openlocfilehash: 931608decb44f0e49cb4ae2984b9cbf724a63d56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778238"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Postupy: připojení a odpojení nástroje Sledování výkonu ke spuštěným procesům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profiler slouží k připojení nebo odpojení od spuštěného procesu pro usnadnění odběru vzorků a shromažďuje data výkonu. Tímto způsobem může Profilovat proces, pokud chcete se vyhnout, shromažďování dat o čas načtení aplikace, nebo k monitorování výkonu procesu po jeho dosažení určitý stav.  
  
> [!NOTE]
>  Následující postup se vztahuje k připojení a odpojení procesy v rámci [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] integrované environmnent vývojové (prostředí IDE). Informace o tom, jak pomocí nástrojů příkazového řádku najdete v tématu [profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md). Informace o tom, jak služby profilů najdete v tématu [profilování služby](../profiling/command-line-profiling-of-services.md).  
  
 Procesy, které jsou k dispozici pro profil záviset na oprávnění uživatelského přístupu, které jsou nastaveny správcem počítače. Uživatelský účet může třeba mít oprávnění pro kterýkoli z následujících:  
  
- Pokročilé funkce, profilace, pokud správce nastavil ovladač a spouštění služby.  
  
- Ukázka profilace pouze (uživatelé domény).  
  
- Odepřete přístup k profilaci pro každého.  
  
  Další informace najdete v tématu [profilace a zabezpečení Windows Vista](../profiling/profiling-and-windows-vista-security.md) a možností správy v [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Připojit ke spuštěnému procesu  
  
1.  Na **analyzovat** nabídky, přejděte k **Profiler** a potom klikněte na tlačítko **Attach/Detach**.  
  
     \- nebo –  
  
     V **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **Attach/Detach**.  
  
     **Připojit Profiler k procesu** zobrazí se dialogové okno.  
  
2.  Klikněte na název, který chcete připojit k procesu.  
  
3.  Klikněte na tlačítko **připojit**.  
  
### <a name="to-detach-from-a-running-process"></a>Chcete-li odpojit od spuštěného procesu  
  
1.  Na **analyzovat** nabídky, přejděte k **Profiler** a potom klikněte na tlačítko **Attach/Detach**.  
  
     \- nebo –  
  
     V **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **Attach/Detach**.  
  
     **Připojit Profiler k procesu** zobrazí se dialogové okno.  
  
2.  Klikněte na název image, ze kterého se má odpojit.  
  
3.  Klikněte na tlačítko **odpojit**.  
  
## <a name="see-also"></a>Viz také  
 [Řízení sběru dat](../profiling/controlling-data-collection.md)   
 [Přehled výkonnostní relace](../profiling/performance-session-overview.md)   
 [Postupy: zahájení a ukončení shromažďování dat výkonu](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilace a zabezpečení Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)



