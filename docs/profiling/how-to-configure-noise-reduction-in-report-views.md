---
title: 'Postupy: Konfigurace snížení šumu v zobrazeních sestav | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 460251aaa89c22d7bb1320d19882af4f68736cc0
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815181"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Postupy: Konfigurace snížení šumu v zobrazeních sestav
Sestavy pro zvýšení výkonu mohou být konfigurovány pro snížení šumu omezením množství dat, který se zobrazí v zobrazení stromu volání a zobrazení přidělení. Pomocí snížení šumu jsou výraznější problémy s výkonem. To je užitečné, když analyzujete sestavy pro zvýšení výkonu.  
  
 Možnosti konfigurace snížení šumu patří následující nastavení:  
  
-   **Ořezávání** při sestavy se analyzují, bude zobrazení vynechejte funkce, které se nacházejí v nastavení hodnoty a prahové hodnoty, které jste nakonfigurovali, jak je popsáno v následujícím postupu oříznutí. Ve výchozím nastavení je povoleno oříznutí.  
  
-   **Skládání** Pokud povolíte skládání, budou sloučeny po sobě jdoucích funkce v cestě, které splňují nastavení, které jste nakonfigurovali, jak je popsáno v následujícím postupu skládání. Ve výchozím nastavení je ve výchozím nastavení povolené skládání.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Ke konfiguraci oříznutí pro Sestava výkonu  
  
1.  Při zobrazení stromu volání nebo přidělení – zobrazení se zobrazí v vygenerovanou sestavu na **vývojáře** nabídky, klikněte na tlačítko **profileru** a pak klikněte na **možnosti snížení šumu**.  
  
     **Snížení šumu** zobrazí se dialogové okno.  
  
2.  Pokud chcete povolit oříznutí, postupujte takto:  
  
    1.  Vyberte **povolit oříznutí**. Toto je výchozí nastavení.  
  
        > [!NOTE]
        >  Pokud je povoleno snížení šumu, se zobrazí informační panel zobrazí v sestavě. Další informace najdete v tématu [zobrazení stromu volání](../profiling/call-tree-view.md) a [přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Konfigurace nastavení hodnoty pomocí **hodnotu** rozevíracího seznamu a zvolením příslušné nastavení.  
  
    3.  Konfigurovat nastavení požadovanou prahovou hodnotu zadáním procentuální hodnotu v **prahová hodnota** textové pole.  
  
    4.  Chcete-li upozornění snížení šumu v vygenerovanou sestavu, vyberte **zobrazí varování, pokud je povoleno snížení šumu**. Toto je výchozí nastavení.  
  
3.  Chcete-li zakázat ořezávání, zrušte **povolit oříznutí**.  
  
4.  Click **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Ke konfiguraci skládání pro Sestava výkonu  
  
1.  Na **vývojáře** nabídky, klikněte na tlačítko **profileru** a pak klikněte na **možnosti snížení šumu**.  
  
     **Snížení šumu** zobrazí se dialogové okno.  
  
2.  Pokud chcete povolit skládání, postupujte takto:  
  
    1.  Vyberte **Povolit skládání**. Toto je výchozí nastavení.  
  
        > [!NOTE]
        >  Pokud je povoleno snížení šumu, se zobrazí informační panel zobrazí v sestavě. Další informace najdete v tématu [zobrazení stromu volání](../profiling/call-tree-view.md) a [přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Konfigurace nastavení hodnoty pomocí **hodnotu** rozevíracího seznamu a výběrem příslušné nastavení.  
  
    3.  Konfigurovat nastavení požadovanou prahovou hodnotu zadáním procentuální hodnotu v **prahová hodnota** textové pole.  
  
    4.  Chcete-li upozornění snížení šumu v vygenerovanou sestavu, vyberte **zobrazí varování, pokud je povoleno snížení šumu**. Toto je výchozí nastavení.  
  
3.  Chcete-li zakázat skládání, zrušte **Povolit skládání**.  
  
4.  Click **OK**.  
  
## <a name="see-also"></a>Viz také:  
 [Přizpůsobení zobrazení sestav nástrojů výkonu](../profiling/customizing-performance-tools-report-views.md)   
 [Postupy: vyloučení nebo zahrnutí funkce CShort z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Zobrazení stromu volání](../profiling/call-tree-view.md)   
 [Přidělení – zobrazení](../profiling/dotnet-memory-allocations-view.md)