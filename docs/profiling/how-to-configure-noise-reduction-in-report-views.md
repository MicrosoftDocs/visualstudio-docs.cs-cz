---
title: 'Postup: Konfigurace snížení šumu v zobrazení sestavy | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ccfb9dab504bc3fa9405bb56c9fce82ed18820ac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776329"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Postup: Konfigurace snížení šumu v zobrazeních sestavy
Sestavy výkonu lze nakonfigurovat pro snížení šumu omezením množství dat, která je uvedena v zobrazení stromu volání a zobrazení přidělení. Při použití snížení šumu jsou problémy s výkonem výraznější. To je užitečné při analýze zpráv o výkonu.

 Možnosti konfigurace redukce šumu zahrnují následující nastavení:

- **Ořezávání** Při analýze sestavy zobrazení vynechá funkce, které spadají do nastavení hodnot a prahových hodnot, které jste nakonfigurovali, jak je popsáno v následujícím postupu oříznutí. Ve výchozím nastavení je oříznutí povoleno.

- **Skládání** Pokud povolíte skládání, po sobě jdoucí funkce na cestě, které splňují nastavení, které jste nakonfigurovali, budou sloučeny, jak je popsáno v následujícím postupu skládání. Ve výchozím nastavení je skládání ve výchozím nastavení povoleno.

### <a name="to-configure-trimming-for-a-performance-report"></a>Konfigurace oříznutí pro sestavu výkonu

1. Když se v generované sestavě zobrazí zobrazení stromu volání nebo zobrazení přidělení, klikněte v nabídce **Vývojář** na **Položku Profiler** a potom na **položku Možnosti snížení šumu**.

     Zobrazí se dialogové okno **Redukce šumu.**

2. Chcete-li povolit oříznutí, postupujte takto:

    1. Vyberte **Povolit oříznutí**. Toto je výchozí nastavení.

        > [!NOTE]
        > Pokud je povolena redukce šumu, zobrazí se v sestavě informační panel. Další informace naleznete v [tématu Zobrazení stromu volání](../profiling/call-tree-view.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).

    2. Nakonfigurujte nastavení hodnoty pomocí rozevíracího seznamu **Hodnota** a výběrem příslušného nastavení.

    3. Nakonfigurujte požadované nastavení prahové hodnoty zadáním procentuální hodnoty do textového pole **Prahová hodnota.**

    4. Chcete-li povolit upozornění na snížení šumu ve vygenerované sestavě, vyberte **možnost Zobrazit upozornění, když je povolena redukce šumu**. Toto je výchozí nastavení.

3. Chcete-li ořezávání zakázat, zrušte zaškrtnutí **políčka Povolit oříznutí**.

4. Klikněte na tlačítko **OK**.

### <a name="to-configure-folding-for-a-performance-report"></a>Konfigurace skládání pro sestavu výkonu

1. V nabídce **Vývojář** klikněte na **Profiler** a potom klikněte na **Možnosti snížení šumu**.

     Zobrazí se dialogové okno **Redukce šumu.**

2. Chcete-li povolit skládání, postupujte takto:

    1. Vyberte **Povolit skládání**. Toto je výchozí nastavení.

        > [!NOTE]
        > Pokud je povolena redukce šumu, zobrazí se v sestavě informační panel. Další informace naleznete v [tématu Zobrazení stromu volání](../profiling/call-tree-view.md) a [zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md).

    2. Nakonfigurujte nastavení hodnoty pomocí rozevíracího seznamu **Hodnota** a výběrem příslušného nastavení.

    3. Nakonfigurujte požadované nastavení prahové hodnoty zadáním procentuální hodnoty do textového pole **Prahová hodnota.**

    4. Chcete-li povolit upozornění na snížení šumu ve vygenerované sestavě, vyberte **možnost Zobrazit upozornění, když je povolena redukce šumu**. Toto je výchozí nastavení.

3. Chcete-li překazit skládání, zrušte zaškrtnutí **políčka Povolit skládání**.

4. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
- [Přizpůsobení zobrazení sestavy nástrojů výkonu](../profiling/customizing-performance-tools-report-views.md)
- [Postup: Vyloučení nebo zahrnutí krátkých funkcí z instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Zobrazení stromu volání](../profiling/call-tree-view.md)
- [Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md)
