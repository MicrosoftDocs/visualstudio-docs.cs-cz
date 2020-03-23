---
title: 'DA0503: Průměrná pracovní sada v bajtů pro proces profilovaný | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8c9d309d7bf10cee07cc30c4568d2dfa59d1be56
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777447"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Průměrná pracovní sada v bajtů pro proces profilovaný

|||
|-|-|
|Id pravidla|DA0503 řekl:|
|Kategorie|Monitorování zdrojů|
|Metoda profilování|Všechny|
|Zpráva|Tyto informace byly shromážděny pouze pro informaci. Čítač Pracovní sada procesu měří využití fyzické paměti procesem, který profilujete. Vykázaná hodnota je průměr vypočítaný ve všech intervalech měření.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva hlásí průměrné množství fyzické paměti, které proces aktuálně používá v bajtů (pracovní sada). Pracovní sada procesu představuje stránky z adresního prostoru procesu, které jsou aktuálně umístěny ve fyzické paměti.

 Vykázaná hodnota zahrnuje rezidentní stránky ze segmentů sdílené paměti, na které proces odkazuje. Sdílené knihovny DLL, na které jsou zahrnuty odkazy na proces, jsou zahrnuty do segmentů sdílené paměti, které se počítají. Hodnota pracovní sady procesu může být vyšší než velikost virtuální paměti, kterou proces přidělil z důvodu segmentů sdílené paměti.

 Vykázaná hodnota je průměr za všechny intervaly měření, ve kterých byl profilovaný proces aktivní.

 Velikost pracovní sady procesu odráží, kolik virtuální paměti proces aktivně používá. To je také ovlivněno množství fyzické paměti (nebo paměti RAM) k dispozici ke spuštění aplikace a tvrzení pro tuto fyzickou paměť z jiných spuštěných procesů. Pokud je fyzická paměť omezena, hodnota pracovní sady procesu se může výrazně lišit, protože operační systémy se snaží vyvážit využití paměti mezi aktivními procesy pravidelným ořezáváním poměrně neaktivních stránek z pracovních sad procesů.

 Další informace o pracovních sadách procesů naleznete v [tématu Pracovní sada](/windows/win32/memory/working-set) v dokumentaci ke správě paměti systému Windows v aplikaci MSDN.

## <a name="how-to-use-rule-data"></a>Použití dat pravidla
 Pomocí hodnoty pravidla můžete porovnat výkon různých verzí nebo sestavení programu nebo porozumět výkonu aplikace v různých scénářích profilování.

 Poklepáním na zprávu v okně Seznam chyb přejděte do zobrazení [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledejte sloupce **Process\Working Set** a **Memory\Pages/sec.** Porovnejte dva sloupce a zjistěte, zda existují určité fáze provádění programu, které se zdají být spojeny se zvýšenou aktivitou stránkování vi.
