---
title: 'DA0017: Vysoká míra stránkování aktivní paměti na disk | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 87e7c6b2d94602eca9e81098bb50bd0330b2bcd9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779386"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Vysoké míry stránkování aktivní paměti na disk

|||
|-|-|
|Id pravidla|DA0017 řekl:|
|Kategorie|Paměť a stránkování|
|Metoda profilování|Všechny|
|Zpráva|Dochází k vysoké rychlosti stránkování aktivní paměti na disk. Aplikace může být vázána na paměť.|
|Typ pravidla|Informace|

 Při profilování pomocí vzorkování, .NET paměti nebo prostředků konfliktmetody, je nutné shromáždit alespoň 10 vzorků k aktivaci tohoto pravidla.

## <a name="cause"></a>Příčina
 Data o výkonu systému, která byla shromážděna při spuštění profilování, označují, že během profilování došlo k vysoké rychlosti stránkování aktivní paměti na disk a z disku. Rychlost stránkování na této úrovni obvykle ovlivní výkon aplikace a odezvu. Zvažte snížení přidělení paměti revistou algoritmů. Může být také třeba zvážit požadavky na paměť vaší aplikace.

## <a name="rule-description"></a>Popis pravidla

> [!NOTE]
> Toto informační pravidlo se aktivuje, když úrovně stránkování aktivní paměti dosáhnou značného množství. Když dojde k extrémně vysoké úrovni stránkování, pravidlo upozornění [DA0014: Extrémně vysoké rychlosti stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) požáry místo.

 Nadměrné stránkování na disk může být způsobeno nedostatkem fyzické paměti. Pokud stránkovací operace dominují použití fyzického disku, kde je umístěn stránkovací soubor, mohou zpomalit další operace disku orientované na aplikace na stejný disk.

 Stránky jsou často čteny z disku nebo zapsány na disk v operacích hromadného stránkování. Počet stránek výstup/s je často mnohem větší než počet page zápisy/s, například. Protože výstup stránek/s obsahuje také změněné datové stránky ze systémové mezipaměti souborů. Není však vždy snadné určit, který proces je přímo zodpovědný za stránkování nebo proč.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Poklepáním na zprávu v okně Seznam chyb přejděte do zobrazení [Značky.](../profiling/marks-view.md) Najděte sloupec **Paměť\Stránky/s.** Zjistěte, zda existují určité fáze provádění programu, kde stránkování vi aktivity je těžší než ostatní.

 Pokud shromažďujete data profilu pro ASP.NET aplikace ve scénáři zátěžového testování, zkuste znovu spustit zátěžový test v počítači nakonfigurovaném s další fyzickou pamětí (nebo pamětí RAM).

 Zvažte snížení přidělení paměti revicí algoritmů a zabránění mATY náročné na paměť, jako jsou String.Concat a String.Substring.
