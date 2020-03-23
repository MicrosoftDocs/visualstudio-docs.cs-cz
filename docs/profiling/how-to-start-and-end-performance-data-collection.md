---
title: 'Postup: Shromažďování dat o výkonu zahájení a ukončení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: da75306018cf19855c7cb7f74ac3ffc4e84bcd9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774508"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Postup: Shromažďování dat o výkonu zahájení a ukončení
Před zahájením profilování je nutné přidat cílový binární soubor, který chcete profilovat do relace výkonu. Chcete-li přidat cíl, klepněte v **Průzkumníku výkonu**pravým **tlačítkem** myši na cíle a potom klepněte na příkaz **Přidat cílový binární soubor**. V dialogovém okně **Přidat cílový binární** vyberte název souboru a klepněte na tlačítko **Otevřít**. Je přidán nový binární soubor.

### <a name="to-start-profiling"></a>Chcete-li začít profilování

1. Klikněte pravým tlačítkem myši na název relace výkonu v okně **Průzkumník výkonu** a zvolte jednu z následujících možností:

    - **Spustit s profilováním** - spustí aplikaci a okamžitě začne profilování.

    - **Spustit s profilování pozastaveno** - spustí aplikaci, ale nespustí profilování. Profilování můžete začít výběrem **kolekce životopisů** v okně **Řízení kolekce dat.** Další informace naleznete v [tématu Postup: Pozastavení a obnovení shromažďování dat o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Ukončení profilování

- Upřednostňovanou metodou ukončení relace profilování je ukončení aplikace. Chcete-li profilování okamžitě ukončit, klepněte na panelu nástrojů **Průzkumníka výkonu** na **tlačítko Zastavit**.

## <a name="see-also"></a>Viz také
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Postupy: Pozastavení a opětovné spuštění shromažďování dat o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md)
