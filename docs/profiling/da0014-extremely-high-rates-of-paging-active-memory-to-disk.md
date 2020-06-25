---
title: DA0014 – extrémně vysoké míry stránkování aktivní paměti na disk | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 40a3b6e584c774f4824fa89afa2c76d59c240657
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328064"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Velmi vysoké míry stránkování aktivní paměti na disk

|||
|-|-|
|ID pravidla|DA0014|
|Kategorie|Paměť a stránkování|
|Metoda profilace|Vše|
|Zpráva|Dochází k extrémně vysoké míře stránkování aktivní paměti na disk. Vaše aplikace může být vázána na paměť.|
|Typ pravidla|Upozornění|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit alespoň 25 vzorků.

## <a name="cause"></a>Příčina
 Data o výkonu systému shromážděná v rámci procesu profilace signalizují, že při průběhu procesu profilace se objevila extrémně vysoká míra stránkování aktivní paměti na disk a z disku. Rychlost stránkování na této úrovni obvykle ovlivňuje výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace. opětovné spuštění profilování na počítači s větší pamětí

## <a name="rule-description"></a>Popis pravidla
 Nadměrné stránkování na disk může být způsobeno nedostatkem fyzické paměti. Pokud operace stránkování rozliší použití fyzického disku, na kterém se nachází stránkovací soubor, může zpomalit jiné operace disku orientované na jednotlivé aplikace na stejný disk.

 Stránky se často čtou z disku nebo zapisují na disk v rámci hromadných operací stránkování. Počet výstupních stránek/s je často mnohem větší než počet zápisů stránek za sekundu, například. Vzhledem k tomu, že výstup stránek/s zahrnuje i změněné datové stránky ze systémové mezipaměti souborů. Není však vždy jednoduché určit, který proces je přímo zodpovědný za stránkování nebo proč.

> [!NOTE]
> Toto pravidlo se aktivuje, když úrovně stránkování aktivní paměti dosáhnou velmi vysoké míry. Pokud je úroveň stránkování významná, ale ne extrémní, informační pravidlo [DA0017: vysoká míra stránkování aktivní paměti na disk](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) je místo toho aktivována.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Dvojitým kliknutím na zprávu v okně Seznam chyb přejdete do zobrazení [značky](../profiling/marks-view.md) . Vyhledejte sloupec **paměť \ stránky/s** . Určete, zda existují konkrétní fáze spuštění programu, kde aktivita v/v stránkování je těžší než jiné.

 Pokud shromažďujete data profilu pro aplikaci ASP.NET ve scénáři testování zatížení, zkuste znovu spustit zátěžový test na počítači nakonfigurovaném s další fyzickou pamětí (nebo pamětí RAM).

 Zvažte snížení přidělení paměti tím, že revidujete algoritmy a vyhnete se rozhraním API náročným na paměť, jako je například String. Concat a String. substring.
