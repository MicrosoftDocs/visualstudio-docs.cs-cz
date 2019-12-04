---
title: 'Postupy: Konfigurace snížení šumu v zobrazeních sestav | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776329"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Postupy: Konfigurace snížení šumu v zobrazeních sestav
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

4. Klikněte na tlačítko **OK**.

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

4. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:
- [Přizpůsobení zobrazení sestav nástrojů pro výkon](../profiling/customizing-performance-tools-report-views.md)
- [Postupy: Vyloučení krátkých funkcí z instrumentace nebo jejich zahrnutí do instrumentace](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)
- [Zobrazení stromu volání](../profiling/call-tree-view.md)
- [Zobrazení přidělení](../profiling/dotnet-memory-allocations-view.md)
