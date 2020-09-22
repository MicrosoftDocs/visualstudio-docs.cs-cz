---
title: Zvolit události vzorkování | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f28859b1c17c735be405c6c56ebabcbe43903170
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851291"
---
# <a name="how-to-choose-sampling-events"></a>Postupy: výběr událostí vzorkování
Ve výchozím nastavení [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Nástroje pro profilaci shromažďuje údaje o výkonu v intervalu, který je zadán jako počet cyklů procesoru používaných profilací procesu. Výchozí počet cyklů v intervalu je 10 000 000, což je přibližně 0,01 sekund na 1 GH počítači. Můžete změnit počet cyklů v intervalu a můžete změnit ukázkovou událost. K dispozici jsou následující ukázkové události:

- Hodinové cykly – pro problémy vázané na procesor.

- Chyby stránky – pro problémy související s pamětí.

- Volání systému – pro problémy související s vstupně-výstupními operacemi.

- Čítač výkonu – čítače procesoru pro problémy s výkonem nízké úrovně.

> [!IMPORTANT]
> Pokud shromažďujete data paměti .NET (přidělení nebo životnost objektů nebo obojí) pomocí metody vzorkování, všechny události vzorkování zadané uživatelem jsou ignorovány a příslušné přidělení paměti nebo události uvolňování paměti nebo obojí jsou použity ke shromažďování dat.

### <a name="to-select-a-sample-event"></a>Výběr události vzorku

1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu a pak klikněte na **vlastnosti**.

2. Na **stránkách vlastností**klikněte na vlastnosti **vzorkování** .

3. V rozevíracím seznamu **událost vzorku** vyberte událost vzorku, kterou chcete použít k profilování aplikace.

    > [!NOTE]
    > **Dostupné čítače výkonu** jsou povoleny pouze v případě, že v rozevíracím seznamu **událost vzorku** vyberete **čítač výkonu** .

4. Pokud vyberete **čítač výkonu**, vyberte konkrétní čítač CPU z ovládacího prvku stromové zobrazení **čítače výkonu k dispozici** .

    - Čítače v uzlu **přenosné události** jsou k dispozici na všech typech procesorů.

    - Čítače v uzlu **události platformy** jsou specifické pro procesor v aktuálním počítači a nemusí být k dispozici na jiných typech procesorů.

5. Když vyberete událost vzorku, v textovém poli **interval vzorkování** se zobrazí výchozí hodnota interval vzorkování. V případě potřeby můžete do textového pole zadat hodnotu, kterou požadujete.

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Postupy: výběr metod shromažďování](../profiling/how-to-choose-collection-methods.md)
- [Čítače procesoru a systému Windows](../profiling/cpu-and-windows-counters.md)
- [Porozumění hodnotám dat vzorkování](../profiling/understanding-sampling-data-values.md)
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
