---
title: 'DA0023: vysoký čas procesoru GC | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f0dd45486f526954d7dfce45cd607ff6196eae00
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777644"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Vysoký čas procesoru uvolňování paměti

|||
|-|-|
|Id pravidla|DA0023|
|Kategorie|Využití .NET Framework|
|Metoda profilace|Vše|
|Zpráva|% Času v uvolňování paměti je poměrně vysoké. Tato indikace nadměrného množství režijních nákladů na uvolňování paměti může mít vliv na odezvu vaší aplikace. Můžete shromáždit data o přidělování paměti .NET a informace o životnosti objektů, abyste porozuměli způsobu přidělení paměti, které vaše aplikace používá lépe.|
|Typ pravidla|Informativní|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>příčina
 Data o výkonu systému shromažďovaná během profilace označují, že množství času stráveného uvolňováním paměti je v porovnání s celkovou dobou zpracování aplikace významné.

## <a name="rule-description"></a>Popis pravidla
 Modul CLR (Common Language Runtime) platformy Microsoft .NET poskytuje automatický mechanismus správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je zaměřený na generaci, a to na základě předpokladu, že mnoho přidělení je krátkodobé. Místní proměnné, například by měly být krátkodobé. Nově vytvořené objekty začínají v generaci 0 (gen 0) a poté budou dokončeny na generaci 1, když přestanou běžet v uvolňování paměti, a nakonec přechod na generaci 2, pokud je aplikace stále používá.

 Objekty v generaci 0 jsou často a efektivně shromažďovány. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivní. A konečně dlouhodobé objekty v generaci 2 by měly být shromažďovány ještě méně často. Největší náročná operace je shromažďování 2, což je úplné spuštění uvolňování paměti.

 Toto pravidlo je vyvoláno, když je čas strávený uvolňováním paměti významný v porovnání s celkovou dobou zpracování aplikace.

> [!NOTE]
> Když je poměr doby strávená uvolňováním paměti nadměrně v porovnání s celkovou dobou zpracování aplikace, [DA0024: Nadměrný čas procesoru uvolňování paměti](../profiling/da0024-excessive-gc-cpu-time.md) , místo aby bylo toto pravidlo aktivováno.

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvakrát klikněte na zprávu v okně Seznam chyb, abyste přešli na [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledá **paměť .NET CLR\\% času ve SLOUPCI GC** . Určete, zda existují konkrétní fáze provádění programu, kde režie pro uvolňování paměti spravované paměti je těžší než jiné fáze. Porovná hodnoty% času v GC na míru uvolňování paměti hlášené v počtu **kolekcí 0. generace**, **počet kolekcí 1**. generace, počet kolekcí **s hodnotou 2** . generace.

 Hodnota% času v GC se pokusí hlásit množství času, který aplikace stráví prováděním uvolňování paměti úměrnou celkovému množství zpracování. Pamatujte na to, že pokud hodnota% času v GC může vykazovat vysokou hodnotu, ale není to kvůli nadměrnému uvolňování paměti. Další informace o tom, jak se počítá hodnota% času v GC, najdete v tématu [rozdíl mezi daty výkonu hlášených různými nástroji – 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) vstupem do **blogového blogu Maoni** na webu MSDN. Pokud dojde k chybám stránky nebo dojde k přerušení aplikace jinou funkcí s vyšší prioritou v počítači při uvolňování paměti, bude% času v čítači GC tyto další prodlevy odrážet.
