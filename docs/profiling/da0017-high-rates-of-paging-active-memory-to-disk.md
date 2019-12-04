---
title: 'DA0017: vysoké míry stránkování aktivní paměti na disk | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779386"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Vysoké míry stránkování aktivní paměti na disk

|||
|-|-|
|Id pravidla|DA0017|
|Kategorie|Paměť a stránkování|
|Metoda profilace|Vše|
|Zpráva|Dochází k vysoké míře stránkování aktivní paměti na disk. Vaše aplikace může být vázána na paměť.|
|Typ pravidla|Informace o nástroji|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>příčina
 Data o výkonu systému shromážděná v rámci procesu profilace označují, že při průběhu procesu profilace došlo k velkému stránkování aktivní paměti a z disku na disk. Rychlost stránkování na této úrovni obvykle ovlivní výkon a rychlost odezvy aplikace. Zvažte snížení přidělení paměti díky revizi algoritmů. Možná budete muset zvážit také požadavky na paměť aplikace.

## <a name="rule-description"></a>Popis pravidla

> [!NOTE]
> Toto informační pravidlo se aktivuje, když úrovně stránkování aktivní paměti dosáhnou významného množství. Když dojde k extrémně vysoké úrovni stránkování, pravidlo upozornění [DA0014: extrémně vysoké míry stránkování aktivní paměti na disk](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) je místo toho.

 Nadměrné stránkování na disk může být způsobeno nedostatkem fyzické paměti. Pokud operace stránkování rozliší použití fyzického disku, na kterém se nachází stránkovací soubor, může zpomalit jiné operace disku orientované na jednotlivé aplikace na stejný disk.

 Stránky se často čtou z disku nebo zapisují na disk v rámci hromadných operací stránkování. Počet výstupních stránek/s je často mnohem větší než počet zápisů stránek za sekundu, například. Vzhledem k tomu, že výstup stránek/s zahrnuje i změněné datové stránky ze systémové mezipaměti souborů. Není však vždy jednoduché určit, který proces je přímo zodpovědný za stránkování nebo proč.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
 Dvojitým kliknutím na zprávu v okně Seznam chyb přejdete do zobrazení [značky](../profiling/marks-view.md) . Vyhledejte sloupec **paměť \ stránky/s** . Určete, zda existují konkrétní fáze spuštění programu, kde aktivita v/v stránkování je těžší než jiné.

 Pokud shromažďujete data profilu pro aplikaci ASP.NET ve scénáři testování zatížení, zkuste znovu spustit zátěžový test na počítači nakonfigurovaném s další fyzickou pamětí (nebo pamětí RAM).

 Zvažte snížení přidělení paměti tím, že revidujete algoritmy a vyhnete se rozhraním API náročným na paměť, jako je například String. Concat a String. substring.
