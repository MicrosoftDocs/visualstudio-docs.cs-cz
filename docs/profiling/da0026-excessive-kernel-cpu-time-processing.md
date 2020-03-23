---
title: 'DA0026: Nadměrné zpracování času procesoru jádra | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 2c8b4cb63eb4647ddab4220ed6729894fe8a456f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777486"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Nadměrný čas zpracování procesoru jádra

|||
|-|-|
|Id pravidla|Todo|
|Kategorie|Využití nástrojů profilování|
|Metoda profilování|Vzorkování|
|Zpráva|Bylo měřeno poměrně vysoké množství času procesoru v režimu jádra. Zvažte zkoumání zdroje s povolenou vzorkování SysCall.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Podíl času procesoru, který byl proveden v režimu jádra, překročil dobu strávenou v uživatelském režimu. Zvažte profilování znovu a vzorkování počet volání systému (syscalls) k určení příčiny vysoké doby spuštění režimu jádra.

## <a name="rule-description"></a>Popis pravidla
 Relativně vysoký podíl času, který aplikace strávila v provedení režimu jádra, může vyžadovat další šetření. Aplikace v uživatelském režimu přechází do režimu jádra k provádění vstupně-vaoperací, čekání na základní prvky synchronizace vláken nebo procesů nebo provádění systémových volání. Můžete prozkoumat druhy systémových volání aplikace a které funkce, které jsou odpovědné za ně při výběru možnosti shromažďovat ukázkové zásobníky volání na základě systémových volání.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Chcete-li prozkoumat druhy systémových volání, které vaše aplikace provede, spusťte profil znovu a vyberte možnost shromažďovat vzorky na základě systémových volání. Přečtěte [si postup: Zvolte vzorkování událostí,](../profiling/how-to-choose-sampling-events.md) pokud používáte nástroje profilování uvnitř ide pro další informace. Pokud používáte nástroje profilování z příkazového řádku, podívejte se do části **Volby intervalu ukázky** v článku [VSPerfCmd](../profiling/vsperfcmd.md) v odkazu na nástroje příkazového řádku Nástroje profilování.
