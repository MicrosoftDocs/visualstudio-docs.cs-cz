---
title: 'Postup: Zvolte vzorkovací události | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 82462ae5052150da7761dfcd855e5339e1b7d821
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779048"
---
# <a name="how-to-choose-sampling-events"></a>Postup: Volba vzorkovacích událostí
Ve výchozím [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nastavení nástroje profilování shromažďují údaje o výkonu v intervalu, který je určen jako počet cyklů procesoru, které jsou používány profilovaný proces. Výchozí počet cyklů v intervalu je 10 000 000, což je přibližně 0,01 sekundy v počítači s 1 GH. Můžete změnit počet cyklů v intervalu a můžete změnit ukázkovou událost. K dispozici jsou následující ukázkové události:

- Hodiny cykly - pro problémy vázané na procesor.

- Chyby stránky - pro problémy související s pamětí.

- Systémová volání - pro i/o-související problémy.

- Čítač výkonu – čítače procesoru pro problémy s výkonem nižší úrovně.

> [!IMPORTANT]
> Pokud shromažďujete data paměti .NET (přidělení nebo životnost objektu nebo obojí) pomocí metody vzorkování, všechny uživatelem zadané vzorkovací události jsou ignorovány a příslušná přidělení paměti nebo události uvolňování paměti nebo obojí, se používají ke shromažďování dat.

### <a name="to-select-a-sample-event"></a>Výběr ukázkové události

1. V **Průzkumníku výkonu**klepněte pravým tlačítkem myši na relaci výkonu a potom klepněte na příkaz **Vlastnosti**.

2. Na **stránkách vlastností**klepněte na vlastnosti **Vzorkování.**

3. V rozevíracím seznamu **Ukázkové události** vyberte ukázkovou událost, kterou chcete použít k profilování aplikace.

    > [!NOTE]
    > **Čítače výkonu K dispozici** jsou povoleny pouze v případě, že v rozevíracím seznamu ukázkových událostí vyberete **čítač** **výkonu.**

4. Pokud vyberete **čítač výkon**, vyberte konkrétní čítač procesoru z ovládacího prvku zobrazení **stromu čítače výkon ů k dispozici.**

    - Čítače v uzlu **Přenosné události** jsou k dispozici na všech typech procesorů.

    - Čítače v uzlu **Události platformy** jsou specifické pro procesor v aktuálním počítači a nemusí být k dispozici na jiných typech procesorů.

5. Když vyberete ukázkovou událost, zobrazí se v textovém poli Interval vzorkování výchozí hodnota intervalu **vzorkování.** V případě potřeby můžete do textového pole zadat požadovanou hodnotu.

## <a name="see-also"></a>Viz také
- [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
- [Postup: Zvolte metody kolekce](../profiling/how-to-choose-collection-methods.md)
- [Čítače procesoru a Windows](../profiling/cpu-and-windows-counters.md)
- [Principy hodnot vzorkovacích dat](../profiling/understanding-sampling-data-values.md)
- [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
