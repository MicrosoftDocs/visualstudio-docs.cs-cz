---
title: 'DA0022: vysoká míra pro uvolňování paměti 2. generace | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba70e303c3164417890be51e834d86d8983526cf
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72910526"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Vysoká míra 2. generace uvolňování pamětí

|||
|-|-|
|ID pravidla|DA0022|
|Kategorie|Využití .NET Framework|
|Metoda profilace|Všechny|
|Zpráva|Dochází k poměrně vysoké míře pro uvolňování paměti 2. generace. Pokud je podle návrhu většina datových struktur programu přidělená a trvalá po dlouhou dobu, není to obvykle problém. Nicméně, pokud je toto chování nezamýšlené, vaše aplikace může Připnutí objektů. Pokud si nejste jistí, můžete shromáždit údaje o přidělení paměti .NET a informace o životnosti objektů, abyste pochopili, jaký model přidělení paměti vaše aplikace používá.|
|Typ pravidla|Upozornění|

 Když použijete profilování pomocí vzorkování, paměti .NET nebo způsobů kolizí prostředků, musíte pro aktivaci tohoto pravidla shromáždit aspoň 10 vzorků.

## <a name="cause"></a>příčina
 Údaje o výkonu systému, které byly shromážděny během profilace, naznačují, že významný podíl objektů paměťového for.NET Framework byl v generaci paměti 2 kolekce v porovnání s generace paměti 0 a 1. generace uvolňován.

## <a name="rule-description"></a>Popis pravidla
 Modul CLR (Common Language Runtime) platformy Microsoft .NET poskytuje automatický mechanismus správy paměti, který používá systém uvolňování paměti k uvolnění paměti z objektů, které aplikace již nepoužívá. Systém uvolňování paměti je zaměřený na generaci, a to na základě předpokladu, že mnoho přidělení je krátkodobé. Místní proměnné, například by měly být krátkodobé. Nově vytvořené objekty začínají v generaci 0 (gen 0) a poté budou dokončeny na generaci 1, když přestanou běžet v uvolňování paměti, a nakonec přechod na generaci 2, pokud je aplikace stále používá.

 Objekty v generaci 0 jsou často shromažďovány a obvykle velmi efektivně. Objekty v generaci 1 jsou shromažďovány méně často a méně efektivní. A konečně dlouhodobé objekty v generaci 2 by měly být shromažďovány ještě méně často. Největší náročná operace je shromažďování 2, což je úplné spuštění uvolňování paměti.

 Toto pravidlo je vyvoláno, když dojde k proporcování příliš velkého počtu uvolnění paměti generace 2. Dobře se chovají .NET Framework aplikace budou mít více než 5 časů jako mnoho uvolňování paměti 1. generace jako kolekce 2. generace. (Faktor 10x je pravděpodobně ideální.)

## <a name="how-to-investigate-a-warning"></a>Jak prozkoumat upozornění
 Dvakrát klikněte na zprávu v okně Seznam chyb, abyste přešli na [zobrazení značek](../profiling/marks-view.md) dat profilování. Vyhledá **paměť .NET clr\\# z kolekcí gen 0** a **paměti .NET CLR\\počet sloupců kolekcí 1. generace** . Určete, zda jsou k dispozici určité fáze provádění programu, kde dochází k uvolňování paměti často. Porovnejte tyto hodnoty se sloupcem **% času ve uvolňování** paměti, abyste viděli, jestli se při přidělení spravované paměti nejedná o nadměrné nároky na správu paměti.

 Vysoká část uvolňování paměti generace 2 není vždy problém. Může to být záměrné. Aplikace, která přiděluje velké datové struktury, které musí zůstat aktivní po dlouhou dobu během provádění, může toto pravidlo aktivovat. Když je taková aplikace v paměti, může být vynucená provádět časté uvolňování paměti. Pokud se méně nákladným uvolňováním paměti generace 0 a 1. generace může uvolnit jenom malý objem spravovaných paměti, naplánují se častěji paměťové kolekce s častou generací 2.

 Existují další sloupce paměti .NET CLR v zobrazení značek, které vám pomohou identifikovat problémy uvolňování paměti. Sloupec **% času v GC** vám pomůže pochopit, kolik režijních nákladů na správu paměti dochází. Pokud vaše aplikace obvykle používá poměrně malý počet velkých, ale trvalých objektů, pak by časté kolekce 2. generace neměly spotřebovat nadměrné množství času procesoru. Je-li aplikace v paměti tlak, protože je požadována větší fyzická paměť (RAM), může dojít také k vyvolání odpovídajících pravidel, která vyhodnocují hodnoty sloupce **paměť \ stránky/s** .

 Chcete-li pochopit vzor využití spravované paměti aplikací, profil znovu spusťte profil přidělení paměti a.NET a vyberte možnost profilace životnosti objektu.

 Informace o tom, jak zlepšit výkon uvolňování paměti, najdete v tématu [základy systému uvolňování paměti a Nápověda ke zvýšení výkonu](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) na webu společnosti Microsoft. Informace o režii automatického uvolňování paměti najdete v tématu [large object halda se nepokryla](https://msdn.microsoft.com/magazine/cc534993.aspx).