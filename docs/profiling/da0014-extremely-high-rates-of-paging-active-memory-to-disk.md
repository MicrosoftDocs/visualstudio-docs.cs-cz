---
title: 'DA0014: Extrémně vysoká míra stránkování aktivní paměti na disk | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e068771ba0fcc9b044ba7ff5243a75ceb3161e03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779406"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Velmi vysoké míry stránkování aktivní paměti na disk

|||
|-|-|
|Id pravidla|DA0014 řekl:|
|Kategorie|Paměť a stránkování|
|Metoda profilování|Všechny|
|Zpráva|Dochází k extrémně vysoké rychlosti stránkování aktivní paměti na disk. Aplikace může být vázána na paměť.|
|Typ pravidla|Upozornění|

 Při profilování pomocí vzorkování, .NET paměti nebo metody tvrzení prostředků, je nutné shromáždit alespoň 25 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která byla shromážděna při spuštění profilování, označují, že během profilování došlo k extrémně vysoké rychlosti stránkování aktivní paměti na disk a z disku. Rychlost stránkování na této úrovni obvykle ovlivňuje výkon aplikace a odezvu. Zvažte snížení přidělení paměti revistou algoritmů. Může být také třeba zvážit požadavky na paměť vaší aplikace. znovu spuštěné profilování v počítači s více pamětí.

## <a name="rule-description"></a>Popis pravidla
 Nadměrné stránkování na disk může být způsobeno nedostatkem fyzické paměti. Pokud stránkovací operace dominují použití fyzického disku, kde je umístěn stránkovací soubor, mohou zpomalit další operace disku orientované na aplikace na stejný disk.

 Stránky jsou často čteny z disku nebo zapisovány na disk v operacích hromadného stránkování. Počet stránek výstup/s je často mnohem větší než počet page zápisy/s, například. Protože výstup stránek/s obsahuje také změněné datové stránky ze systémové mezipaměti souborů. Není však vždy snadné určit, který proces je přímo zodpovědný za stránkování nebo proč.

> [!NOTE]
> Toto pravidlo je aktivováno, když úrovně stránkování aktivní paměti dosáhnou velmi vysoké rychlosti. Pokud je úroveň stránkování významná, ale ne extrémní, informační pravidlo [DA0017: Vysoká rychlost stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) je místo toho aktivována.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Poklepáním na zprávu v okně Seznam chyb přejděte do zobrazení [Značky.](../profiling/marks-view.md) Najděte sloupec **Paměť\Stránky/s.** Zjistěte, zda existují určité fáze provádění programu, kde stránkování vi aktivity je těžší než ostatní.

 Pokud shromažďujete data profilu pro ASP.NET aplikace ve scénáři zátěžového testování, zkuste znovu spustit zátěžový test v počítači nakonfigurovaném s další fyzickou pamětí (nebo pamětí RAM).

 Zvažte snížení přidělení paměti revicí algoritmů a zabránění mATY náročné na paměť, jako jsou String.Concat a String.Substring.
