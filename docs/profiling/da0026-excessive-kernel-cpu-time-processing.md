---
title: DA0026 – nadměrné zpracování času procesoru jádra | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 38452ce95b299be11e20150440c815127b66d061
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332408"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Nadměrný čas zpracování procesoru jádra

|||
|-|-|
|ID pravidla|TODO|
|Kategorie|Využití Nástroje pro profilaci|
|Metoda profilace|Vzorkování|
|Zpráva|Bylo měřeno relativně vysoké množství času procesoru režimu jádra. Zvažte šetření zdroje s povoleným vzorkováním SysCall.|
|Typ pravidla|Informace|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>Příčina
 Poměrná doba procesoru spuštěná v režimu jádra překročila dobu trvání v uživatelském režimu. Zvažte znovu profilaci a vzorkování počtu systémových volání (voláním) a určete příčinu vysoké doby spuštění režimu jádra.

## <a name="rule-description"></a>Popis pravidla
 Poměrně vysoký podíl času, který aplikace strávila při provádění režimu jádra, může mít za následek další šetření. Aplikace v uživatelském režimu přejde do režimu jádra, aby prováděla vstupně-výstupní operace, aby bylo možné čekat na primitivní prvky synchronizace vlákna nebo procesu, nebo provést systémové volání. Můžete prozkoumat typy systémových volání, která aplikace zajišťuje, a funkce, které jsou pro ně zodpovědné, když vyberete možnost shromažďování ukázkových zásobníků volání na základě volání systému.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Chcete-li prozkoumat typy systémových volání, které aplikace vytváří, spusťte profil znovu a vyberte možnost shromažďování vzorků na základě volání systému. Další informace najdete v tématu [Postupy: výběr událostí vzorkování](../profiling/how-to-choose-sampling-events.md) , pokud používáte nástroje pro profilaci v integrovaném vývojovém prostředí (IDE). Pokud používáte nástroje pro profilaci z příkazového řádku, přečtěte si část **Možnosti intervalu vzorkování** v článku [VSPerfCmd](../profiling/vsperfcmd.md) v tématu Referenční informace o nástrojích příkazového řádku pro nástroje pro profilaci.
