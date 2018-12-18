---
title: 'Postupy: shromažďování dat čítačů procesoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d5bb2d554ee67a4a2c83decba017e9a1f0fe1e9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813906"
---
# <a name="how-to-collect-cpu-counter-data"></a>Postupy: shromažďování dat čítačů procesoru

Čítače procesoru událostí se používá ke shromažďování dat výkonu hardwaru. Tento článek ukazuje, jak shromažďovat data událostí, použijete-li metoda profilace instrumentace.

Dva typy událostí čítače CPU dojít:

- Události přenositelnosti - procesoru událostí, které se můžou shromažďovat, bez ohledu na konkrétním procesoru.

- Události platformy – procesoru událostí, které jsou spojeny s konkrétním procesoru.

  Události přenositelnosti zahrnují obecné události, jako je vyřazeno pokyny a bez zastavení cykly, události vyrovnávací paměť procesoru, větvení události a události mezipaměti L2. Čítače událostí dostupné platformy jsou určeny výrobce procesoru.

  Kategorie událostí, které mohou být sdíleny platformu a přenosné čítače. Například následující kategorie dat jsou často společné pro oba typy:

- Události paměti.

- Přední události.

- Události větvě.

  Můžete shromažďovat data čítačů výkonu v profileru dvěma způsoby:

- Shromažďování dat z jednoho nebo více čítačů při profilování instrumentace.

- Při profilování pomocí vzorkování, zadáte jako interval vzorkování čítače událostí. Další informace najdete v tématu [postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Ke shromažďování dat čítače výkonu procesoru při profilování instrumentace

1. V relaci výkonu **stránky vlastností**, klikněte na tlačítko **čítače CPU.**

2. Vyberte **shromáždit čítače CPU** zaškrtávací políčko.

3. Rozbalte **dostupných čítačů výkonu** stromové struktury, dokud nenajdete ukázkové události, které chcete shromažďovat.

4. Pro každou událost, která chcete shromažďovat, vyberte události a pak klikněte na tlačítko se šipkou doprava přidejte událost, abyste **vybrané čítače** seznamu.

    > [!NOTE]
    > **Dostupné čítače výkonu** je povolená jenom v případě, že jste vybrali **čítače CPU shromažďovat** zaškrtávací políčko.

## <a name="see-also"></a>Viz také:

[Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)  
[Vlastnosti výkonnostní relace](../profiling/performance-session-properties.md)  
[Čítače procesoru a systému Windows](../profiling/cpu-and-windows-counters.md)  
[Postupy: Výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md)