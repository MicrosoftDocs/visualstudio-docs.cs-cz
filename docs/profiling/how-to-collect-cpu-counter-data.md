---
title: 'Postupy: shromažďování dat čítačů procesoru | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776368"
---
# <a name="how-to-collect-cpu-counter-data"></a>Postupy: shromažďování dat čítačů procesoru

Čítač událostí procesoru se používá ke shromažďování dat o výkonu specifických pro hardware. V tomto článku se dozvíte, jak shromažďovat data čítačů událostí při použití metody profilace instrumentace.

Vyskytují se dva typy událostí čítače CPU:

- Přenosné události – události procesoru, které je možné shromáždit bez ohledu na konkrétní procesor.

- Události platformy – události procesoru, které jsou spojeny s konkrétním PROCESORem.

  Přenosné události zahrnují obecné události, jako jsou vyřazení pokynů a nezastavené cykly, události vyrovnávací paměti procesoru, větvení události a události mezipaměti L2. Dostupné čítače událostí platformy určují výrobce procesoru.

  Kategorie událostí lze sdílet mezi přenosnými a čítači platforem. Například následující kategorie dat jsou často běžné pro oba typy:

- Události paměti.

- Události front-endu.

- Události větve.

  Data čítače výkonu můžete shromažďovat dvěma způsoby v profileru:

- Shromažďování dat z jednoho nebo více čítačů při profilaci instrumentace.

- Zadejte událost počítadla jako interval vzorkování, když budete profilovat vzorkováním. Další informace najdete v tématu [Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Shromažďování dat čítače výkonu procesoru při profilaci pomocí instrumentace

1. Na **stránce vlastností**výkonnostní relace klikněte na **čítače procesoru.**

2. Zaškrtněte políčko **shromáždit čítače procesoru** .

3. Rozbalte strom **dostupných čítačů výkonu** , dokud nenajdete ukázkové události, které chcete shromáždit.

4. Pro každou událost, kterou chcete shromáždit, vyberte událost a kliknutím na šipku vpravo přidejte událost do seznamu **vybrané čítače** .

    > [!NOTE]
    > **Dostupné čítače výkonu** jsou povoleny pouze v případě, že zaškrtnete políčko **shromáždit čítače procesoru** .

## <a name="see-also"></a>Viz také:

[Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)
[vlastností výkonnostní relace](../profiling/performance-session-properties.md)
[čítače CPU a systému Windows](../profiling/cpu-and-windows-counters.md)
[Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md)
