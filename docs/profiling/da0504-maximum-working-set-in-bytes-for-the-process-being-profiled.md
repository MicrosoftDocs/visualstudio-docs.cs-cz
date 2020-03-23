---
title: 'DA0504: Maximální pracovní sada v bajtů pro proces profilovaný | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a181ecb66c3735eb34ab3c866c3c68b2397781f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779321"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maximum Pracovní sady v bajtech pro profilovaný Proces

|||
|-|-|
|Id pravidla|DA0504|
|Kategorie|Správa prostředků|
|Metoda profilování|Všechny|
|Zpráva|Tyto informace byly shromážděny pouze pro informaci. Čítač Pracovní sada procesu měří využití fyzické paměti procesem, který profilujete. Uvedená hodnota je maximální pozorovaná ve všech intervalech měření.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="rule-description"></a>Popis pravidla
 Tato zpráva hlásí maximální množství fyzické paměti v bajtů, které proces aktuálně používá. Pracovní sada procesu představuje stránky z adresního prostoru procesu, které jsou aktuálně umístěny ve fyzické paměti. Toto pravidlo hlásí maximální hodnotu pro pracovní sadu procesu, zatímco profilování bylo aktivní.

 Uvedená hodnota zahrnuje rezidentní stránky ze segmentů sdílené paměti, na které proces odkazuje. Sdílené knihovny DLL, na které jsou zahrnuty odkazy na proces, jsou zahrnuty do segmentů sdílené paměti, které se počítají. Hodnota pracovní sady procesu může být vyšší než velikost virtuální paměti, kterou proces přidělil z důvodu segmentů sdílené paměti.

 Velikost pracovní sady procesu odráží, kolik virtuální paměti proces aktivně používá. To je také ovlivněno množství fyzické paměti (nebo paměti RAM) k dispozici ke spuštění aplikace a tvrzení pro tuto fyzickou paměť z jiných spuštěných procesů. Další informace o pracovních sadách procesů naleznete v [tématu Pracovní sada](/windows/win32/memory/working-set) v dokumentaci ke správě paměti systému Windows v aplikaci MSDN.

## <a name="how-to-use-rule-data"></a>Použití dat pravidla
 Pravidlo shromažďuje tato naměřená data ze zařízení pro sledování výkonu systému Windows a hlásí je pouze pro informaci. Slouží k porovnání výkonu různých verzí nebo sestavení programu nebo k pochopení výkonu aplikace v různých testovacích scénářích.

 Poklepáním na zprávu v okně Seznam chyb přejděte do [zobrazení značek](../profiling/marks-view.md) dat profilování. Najděte sloupce čítače **Proces\Pracovní sada** a **Paměť\Stránky/s.** Poté najděte maximální hodnotu **process\working set** a porovnejte ji s hodnotou **Memory\Pages/sec.** Maximální pracovní sada je často spojena s intervalem, ve kterém je snížena aktivita stránkování vi, zejména v případě, že je počítač omezen na paměť.
