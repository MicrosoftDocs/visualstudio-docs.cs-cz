---
title: Vyloučení krátkých funkcí z instrumentace nebo jejich zahrnutí do instrumentace
description: Ve výchozím nastavení jsou krátké funkce, které nevolají jiné funkce, vyloučené z instrumentace pro snížení režie. Přečtěte si, jak je zahrnout nebo vyloučit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ad449ba25e2b97397ae87cfe64eb7253ac5728b7
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800405"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Postupy: vyloučení nebo zahrnutí krátkých funkcí z instrumentace
Ve výchozím nastavení nástroje pro profilování vyloučí *malé funkce* z instrumentace. Malé funkce jsou krátké funkce, které nedělají žádná volání funkcí. Vyloučení těchto malých funkcí přináší méně režijních nákladů na instrumentaci, a proto zlepšuje rychlost instrumentace. Vyloučení malých funkcí také snižuje datový soubor profilování výkonu (.*velikost VSP*) a čas potřebný k analýze. Pokud jsou vyloučeny malé funkce, čas strávený v malých funkcích se počítá s výhradním a úplným časem jejich nadřazených funkcí. Malé funkce se dají vyloučit nebo zahrnout do instrumentace, jak je popsáno v následujícím postupu.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Vyloučení nebo zahrnutí krátkých funkcí z instrumentace

1. V **prohlížeč výkonu** vyberte možnost **relace výkonu** , klikněte pravým tlačítkem myši a vyberte možnost **vlastnosti**.

     Zobrazí se dialogové okno **Stránky vlastností**.

2. Na **stránkách vlastností** klikněte na vlastnosti **instrumentace** .

3. Pokud chcete vyloučit krátké funkce z instrumentace, vyberte **vyloučit krátké funkce z instrumentace**. Toto je výchozí nastavení.

     -nebo-

     Pokud chcete do instrumentace zahrnout krátké funkce, zrušte zaškrtnutí políčka **vyloučit krátké funkce z instrumentace**.

4. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)
