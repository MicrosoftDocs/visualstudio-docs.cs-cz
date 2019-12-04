---
title: 'Postupy: spuštění a ukončení shromažďování dat výkonu | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774508"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Postupy: spuštění a ukončení shromažďování dat výkonu
Předtím, než spustíte profilování, je nutné do relace výkonu přidat cílový binární soubor, který chcete profilovat. Chcete-li přidat cíl, klikněte pravým tlačítkem myši na **cíle** v **prohlížeč výkonu**a pak klikněte na **Přidat cílový binární soubor**. V dialogovém okně **Přidat cílový binární** soubor vyberte název souboru a potom klikněte na tlačítko **otevřít**. Byl přidán nový binární soubor.

### <a name="to-start-profiling"></a>Spuštění profilace

1. V okně **prohlížeč výkonu** klikněte pravým tlačítkem na název relace výkonu a vyberte jednu z následujících možností:

    - **Spustit s profilací** – spustí aplikaci a ihned zahájí profilaci.

    - **Spustit s pozastaveným profilací** – spustí aplikaci, ale nespustí profilování. Profilaci můžete spustit výběrem možnosti **pokračovat v kolekci** v okně **ovládací prvek shromažďování dat** . Další informace najdete v tématu [Postup: pozastavení a obnovení shromažďování dat o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md).

### <a name="to-end-profiling"></a>Ukončení profilace

- Upřednostňovanou metodou ukončení relace profilování je ukončení aplikace. Pokud chcete profilaci okamžitě zastavit, na panelu nástrojů **prohlížeč výkonu** klikněte na **zastavit**.

## <a name="see-also"></a>Viz také:
- [Řízení shromažďování dat](../profiling/controlling-data-collection.md)
- [Postupy: Pozastavení a opětovné spuštění shromažďování dat o výkonu](../profiling/how-to-pause-and-resume-performance-data-collection.md)
