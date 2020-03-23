---
title: 'Postup: Shromažďování dat čítače procesoru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98291051a135a95ab72b4c3bfa09743d9620b94e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776368"
---
# <a name="how-to-collect-cpu-counter-data"></a>Postupy: Shromažďování dat čítačů procesoru

Čítač událostí procesoru se používá ke shromažďování dat o výkonu specifického pro hardware. Tento článek ukazuje, jak shromažďovat data čítače událostí při použití metody profilování instrumentace.

Dojde ke dvěma typům událostí čítače procesoru:

- Přenosné události – události procesoru, které lze shromažďovat, bez ohledu na konkrétní procesor.

- Události platformy – události procesoru, které jsou spojeny s konkrétním procesorem.

  Přenosné události zahrnují obecné události, jako jsou například instrukce vyřazené a nezastavené cykly, události vyrovnávací paměti procesoru, události větvení a události mezipaměti L2. Čítače událostí platformy jsou určeny výrobcem procesoru.

  Kategorie událostí lze sdílet mezi přenosnými a platformovými čítači. Například následující kategorie dat jsou často společné pro oba typy:

- Události paměti.

- Události front-endu.

- Pobočkové události.

  V profileru můžete shromažďovat data čítačů výkonu dvěma způsoby:

- Shromažďujte data z jednoho nebo více čítačů při profilování podle instrumentace.

- Určete událost čítače jako interval vzorkování při profilování vzorkováním. Další informace naleznete v [tématu How to: Choose sampling events](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Shromažďování dat čítače výkonu procesoru při profilování podle instrumentace

1. Na stránkách **vlastností**relace výkonu klepněte na **položku Čítače procesoru.**

2. Zaškrtněte políčko **Shromáždit čítače procesoru.**

3. Rozbalte strom **Čítače výkonu k dispozici,** dokud nenajdete ukázkové události, které chcete shromažďovat.

4. Pro každou událost, kterou chcete shromáždit, vyberte událost a kliknutím na šipku vpravo přidejte událost do seznamu **Vybrané čítače.**

    > [!NOTE]
    > **Dostupné čítače výkonu** jsou povoleny pouze v případě, že zaškrtnete políčko **Shromáždit čítače procesoru.**

## <a name="see-also"></a>Viz také

[Konfigurace výkonových relací](../profiling/configuring-performance-sessions.md)
[Vlastnosti relace výkonu](../profiling/performance-session-properties.md)
[Čítače procesoru](../profiling/cpu-and-windows-counters.md)
a Windows[Postup: Volba událostí vzorkování](../profiling/how-to-choose-sampling-events.md)
