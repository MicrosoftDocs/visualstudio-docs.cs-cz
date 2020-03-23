---
title: Vyloučení krátkých funkcí z instrumentace nebo jejich zahrnutí do instrumentace
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de6d6325b1e518146768798c773754c091861aa8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775911"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Postup: Vyloučení nebo zahrnutí krátkých funkcí z instrumentace
Ve výchozím nastavení nástroje profilování vylučují *malé funkce* z instrumentace. Malé funkce jsou krátké funkce, které neprovádějí žádné volání funkce. Vyloučení těchto malých funkcí zajišťuje menší nároky na instrumentaci, a tím i vyšší rychlost instrumentace. Vyloučení malých funkcí také snižuje profilování výkonu datového souboru (.* vsp*) a čas potřebný pro analýzu. Pokud jsou vyloučeny malé funkce, čas strávený v malých funkcích se započítává do výhradního a inkluzivního času jejich nadřazených funkcí. Malé funkce mohou být vyloučeny nebo zahrnuty do instrumentace, jak je popsáno v následujícím postupu.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Vyloučení nebo zahrnutí krátkých funkcí z instrumentace

1. V **Průzkumníku výkonu**vyberte **Relaci výkonu** a potom klepněte pravým tlačítkem myši a vyberte **vlastnosti**.

     Zobrazí se dialogové okno **Stránky vlastností**.

2. Na **stránkách vlastností**klepněte na **vlastnosti instrumentace.**

3. Chcete-li vyloučit krátké funkce z instrumentace, vyberte **vyloučit krátké funkce z instrumentace**. Toto je výchozí nastavení.

     -nebo-

     Chcete-li do instrumentace zahrnout krátké funkce, **zrušte zaškrtnutí zrušte možnost Vyloučit krátké funkce z instrumentace**.

4. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)
