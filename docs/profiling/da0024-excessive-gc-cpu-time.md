---
title: 'DA0024: Nadměrný čas procesoru GC | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b8352095bcf31c137d391c2ed2e832d34e0ec7b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779347"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadměrný čas procesoru uvolňování paměti

|||
|-|-|
|Id pravidla|DA0024|
|Kategorie|Využití .NET Framework|
|Metoda profilace|Vše|
|Zpráva|% Času v uvolňování paměti je velmi vysoké. Existuje nadměrné množství režijních nákladů na uvolňování paměti.|
|Typ pravidla|Upozornění|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>příčina
 Údaje o výkonu systému, které byly shromážděny během profilace, ukazují, že množství času stráveného uvolňováním paměti je příliš vysoké v porovnání s celkovou dobou zpracování aplikace.

## <a name="rule-description"></a>Popis pravidla
 Modul CLR (Common Language Runtime) platformy Microsoft .NET poskytuje automatický mechanismus správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je zaměřený na generaci, a to na základě předpokladu, že mnoho přidělení je krátkodobé. Místní proměnné, například by měly být krátkodobé. Nově vytvořené objekty začínají v generaci 0 (gen 0) a poté budou dokončeny na generaci 1, když přestanou běžet v uvolňování paměti, a nakonec přechod na generaci 2, pokud je aplikace stále používá.

 Objekty v generaci 0 jsou často shromažďovány a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivní. A konečně dlouhodobé objekty v generaci 2 by měly být shromažďovány ještě méně často. Největší náročná operace je shromažďování 2, což je úplné spuštění uvolňování paměti.

 Toto pravidlo je vyvoláno, když je množství času stráveného uvolňováním paměti příliš vysoké v porovnání s celkovou dobou zpracování aplikace.

> [!NOTE]
> Pokud je poměr času stráveného uvolňováním paměti značný, ale není nadměrně v porovnání s celkovou dobou zpracování aplikace, [DA0023: vysoký čas procesoru GC](../profiling/da0023-high-gc-cpu-time.md) se místo tohoto pravidla aktivuje.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvakrát klikněte na zprávu v okně Seznam chyb, abyste přešli na [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledá **paměť .NET CLR\\% času ve SLOUPCI GC** . Určete, zda existují konkrétní fáze provádění programu, kde režie pro uvolňování paměti spravované paměti je těžší než jiné fáze. Porovná hodnoty% času v GC na míru uvolňování paměti hlášené v počtu **kolekcí 0. generace**, **počet kolekcí 1**. generace, počet kolekcí **s hodnotou 2** . generace.

 Hodnota% času v GC se pokusí hlásit množství času, který aplikace stráví prováděním uvolňování paměti úměrnou celkovému množství zpracování. Počítejte s tím, že pokud hodnota% času v GC může vykazovat vysokou hodnotu, ale není to kvůli nadměrnému uvolňování paměti. Další informace o tom, jak se počítá hodnota% času v GC, najdete v tématu [rozdíl mezi daty výkonu hlášených různými nástroji – 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) vstupem do **blogového blogu Maoni** na webu MSDN. Pokud dojde k chybám stránky nebo je aplikace před uvolňováním paměti přerušené jinou úlohou s vyšší prioritou, bude% času v čítači GC tyto další prodlevy odrážet.
