---
title: 'Postupy: Konfigurace snížení šumu v zobrazeních sestav | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5871473eaba749833714d6382beb487702ebe02d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64830997"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Postupy: Konfigurace snížení šumu v zobrazeních sestav
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sestavy výkonu lze nakonfigurovat pro redukci hluku tím, že omezíte množství dat, která se zobrazí ve stromovém zobrazení volání a v zobrazení přidělení. Díky omezení šumu jsou problémy s výkonem výraznější. To je užitečné při analýze sestav výkonu.  
  
 Mezi možnosti konfigurace snížení šumu patří následující nastavení:  
  
- **Ořezávání** Při analýze sestavy bude zobrazení vynechat funkce, které spadají do nastavení hodnoty a prahové hodnoty, které jste nakonfigurovali, jak je popsáno v následujícím postupu oříznutí. Ve výchozím nastavení je ořezávání povoleno.  
  
- **Skládání** Pokud povolíte skládání, budou po sobě jdoucí funkce na cestě, která splňuje nastavení, které jste nakonfigurovali, sloučeny, jak je popsáno v následující proceduře skládání. Ve výchozím nastavení je skládání povoleno ve výchozím nastavení.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Konfigurace oříznutí pro sestavu výkonu  
  
1. Když se ve vygenerované sestavě zobrazí zobrazení stromu volání nebo zobrazení přidělení, v nabídce **vývojář** klikněte na **Profiler** a pak klikněte na **možnosti omezení šumu**.  
  
     Zobrazí se dialogové okno **redukce šumu** .  
  
2. K povolení ořezávání použijte následující postup:  
  
    1. Vyberte **Povolit ořezávání**. Toto je výchozí nastavení.  
  
        > [!NOTE]
        > Pokud je povolené snižování šumu, v sestavě se zobrazí informační panel. Další informace naleznete v tématu zobrazení [stromu volání](../profiling/call-tree-view.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Nakonfigurujte nastavení hodnoty pomocí rozevíracího seznamu **hodnota** a zvolte příslušné nastavení.  
  
    3. Nakonfigurujte požadované nastavení prahové hodnoty zadáním procentuální hodnoty do textového pole **prahová** hodnota.  
  
    4. Pokud chcete povolit upozornění na snížení šumu ve vygenerované sestavě, vyberte **Zobrazit upozornění, když je povolené snížení šumu**. Toto je výchozí nastavení.  
  
3. Chcete-li zakázat ořezávání, zrušte zaškrtnutí políčka **Povolit oříznutí**.  
  
4. Klikněte na **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Konfigurace skládání pro sestavu výkonu  
  
1. V nabídce **vývojář** klikněte na **Profiler** a pak klikněte na **možnosti omezení šumu**.  
  
     Zobrazí se dialogové okno **redukce šumu** .  
  
2. K povolení skládání použijte následující postup:  
  
    1. Vyberte **Povolit skládání**. Toto je výchozí nastavení.  
  
        > [!NOTE]
        > Pokud je povolené snižování šumu, v sestavě se zobrazí informační panel. Další informace naleznete v tématu zobrazení [stromu volání](../profiling/call-tree-view.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Nakonfigurujte nastavení hodnoty pomocí rozevíracího seznamu **hodnota** a vyberte příslušné nastavení.  
  
    3. Nakonfigurujte požadované nastavení prahové hodnoty zadáním procentuální hodnoty do textového pole **prahová** hodnota.  
  
    4. Pokud chcete povolit upozornění na snížení šumu ve vygenerované sestavě, vyberte **Zobrazit upozornění, když je povolené snížení šumu**. Toto je výchozí nastavení.  
  
3. Chcete-li zakázat skládání, zrušte zaškrtnutí políčka **Povolit skládání**.  
  
4. Klikněte na **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení zobrazení sestav nástrojů pro výkon](../profiling/customizing-performance-tools-report-views.md)   
 [Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view.md)   
 [Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md)
