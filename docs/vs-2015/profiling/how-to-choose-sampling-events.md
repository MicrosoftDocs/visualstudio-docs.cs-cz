---
title: 'Postupy: výběr událostí vzorkování | Dokumentace Microsoftu'
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
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96bf47c6bfc28e0939f6feb9fd7999e898c042a1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734504"
---
# <a name="how-to-choose-sampling-events"></a>Postupy: Výběr událostí vzorkování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástrojů pro profilaci sady shromažďuje údaje o výkonu v intervalu, který je zadán jako počet cyklů procesoru, které jsou používány profilovaný proces. Výchozí počet cyklů v intervalu je 10 000 000, což je na 1 počítači gv přibližně na 0,01 sekund. Počet cyklů v intervalu můžete změnit, a můžete změnit událost vzorku. Následující ukázkové události jsou k dispozici:  
  
-   Hodinových cyklů - problémů vázané na procesor.  
  
-   Chyby stránek – pro problémy související s pamětí.  
  
-   Systémová volání - I O souvisejícím s/problémů.  
  
-   Čítač výkonu – čítače CPU pro problémy výkonu na nízké úrovni.  
  
> [!IMPORTANT]
>  Pokud pomocí metody vzorkování se shromažďování dat paměti .NET (přidělení správu životnosti objektů nebo obojí), jsou ignorovány všechny zadané uživatelem vzorkování událostí a přidělení paměti odpovídající události kolekce paměti nebo obojí, se používá ke shromažďování dat.  
  
### <a name="to-select-a-sample-event"></a>Vybrat událost vzorku  
  
1.  V **prohlížeč výkonu**, klikněte pravým tlačítkem na relaci výkonu a pak klikněte na tlačítko **vlastnosti**.  
  
2.  V **stránky vlastností**, klikněte na tlačítko **vzorkování** vlastnosti.  
  
3.  Z **událost vzorku** rozevíracího seznamu vyberte událost vzorku, kterou chcete použít pro profilování aplikace.  
  
    > [!NOTE]
    >  **Dostupných čítačů výkonu** jsou povolené jenom v případě, že vyberete **čítač výkonu** z **událost vzorku** rozevíracího seznamu.  
  
4.  Pokud vyberete **čítač výkonu**, vyberte konkrétní čítač procesoru z **dostupných čítačů výkonu** ovládací prvek zobrazení stromové struktury.  
  
    -   Hodnoty čítačů **události přenositelnosti** uzlu jsou k dispozici na všech typech procesory.  
  
    -   Hodnoty čítačů **události platformy** uzlu jsou specifické pro procesor na aktuálním počítači a nemusí být k dispozici na jiných typů procesory.  
  
5.  Když vyberete událost vzorku, výchozí hodnota intervalu vzorkování se zobrazí v **interval vzorkování** textového pole. V případě potřeby můžete zadat hodnotu, která má v textovém poli.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Postupy: výběr metod kolekcí](../profiling/how-to-choose-collection-methods.md)   
 [Využití procesoru a čítače Windows](../profiling/cpu-and-windows-counters.md)   
 [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)   
 [Profilace prostřednictvím příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)



