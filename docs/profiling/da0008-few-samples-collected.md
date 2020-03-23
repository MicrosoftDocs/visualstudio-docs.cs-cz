---
title: 'DA0008: Několik odebraných vzorků | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15f8eeb370a3f1e61981e0e936704d33f6b44bbd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779438"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Shromážděno málo ukázek

|||
|-|-|
|Id pravidla|DA0008 řekl:|
|Kategorie|Využití nástrojů profilování|
|Metoda profilování|Vzorkování|
|Zpráva|Bylo shromážděno jen několik vzorků. Zvažte delší nebo rychlejší vzorkovací frekvenci pro významnější výsledky.|
|Typ pravidla|Informace|

## <a name="cause"></a>Příčina
 Jen pár vzorků bylo shromážděno v profilování.

## <a name="rule-description"></a>Popis pravidla
 Při použití metody vzorkování byste měli shromáždit statisticky významný počet vzorků, abyste se ujistili, že data představují skutečné chování programu. Chcete-li minimalizovat vzorkování chyby, měli byste se pokusit shromáždit alespoň 1000 vzorků chování spuštění instrukce programu. Pokud neshromažďujete dostatek vzorků, můžete být při analýze dat profilování uvedeni v omyl.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Zvažte profilování delší spuštění aplikace nebo pomocí rychlejší vzorkovací frekvence k získání statisticky významných výsledků. Informace o tom, jak změnit vzorkovací frekvenci v ide sady Visual Studio, naleznete v [tématu Postup: Volba vzorkovacích událostí](../profiling/how-to-choose-sampling-events.md). Další informace o tom, jak změnit vzorkovací frekvenci při použití příkazového řádku Nástroje profilování, naleznete v [tématu Časovač](../profiling/timer.md) v odkazu [VSPerfCmd.](../profiling/vsperfcmd.md)
