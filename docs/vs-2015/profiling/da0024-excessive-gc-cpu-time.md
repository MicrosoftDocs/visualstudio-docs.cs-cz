---
title: 'DA0024: Nadměrný čas uvolňování paměti procesor | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910f66a31f959fe15cc7165eda4e531e7965e670
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754260"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadměrný čas procesoru uvolňování paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA0024 |  
| Kategorie |. Použití rozhraní .NET Framework |  
| Metoda profilace | Všechny |  
| Zpráva | % času v uvolňování paměti je velmi vysoké. Existuje nadměrné množství režie uvolňování paměti. |  
| Typ pravidla | Upozornění |  
  
 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  
  
## <a name="cause"></a>příčina  
 Údaje o výkonu systému, která byla shromážděna během profilování označuje, že množství času stráveného při uvolňování paměti je příliš vysoká ve srovnání s časem zpracování celkový počet aplikací.  
  
## <a name="rule-description"></a>Popis pravidla  
 Rozhraní Microsoft .NET common language runtime (CLR) poskytuje mechanismus správy automatické paměti, která používá systému uvolňování paměti pro uvolnění paměti z objektů, které aplikace se už používá. Uvolňování paměti je orientované na generování založeno na předpokladu, že jsou krátkodobé a jednorázové mnoho přidělení. Lokální proměnné by měl být například krátkodobou. Spustit nově vytvořené objekty v generaci 0 (0. generace) a potom pokroku na generaci 1, pokud se uvolňování paměti spusťte a nakonec přechod do 2. generace zvládnout situaci, kdy aplikace stále používá.  
  
 Objekty v generaci 0 se vybírají obvykle velmi efektivně a často. Objekty v 1. generace jsou shromažďovány méně často a méně efektivní. Nakonec dlouhodobými objekty v generaci 2 by měl být shromažďovány i méně často. 2. generace kolekce, která je spuštění úplného uvolňování paměti kolekce, je také nejvíce náročná operace.  
  
 Toto pravidlo je vyvoláno, když množství času stráveného při uvolňování paměti je příliš vysoká. ve srovnání s časem zpracování celkový počet aplikací.  
  
> [!NOTE]
>  Při poměr doby trvání uvolňování paměti je důležité, ale ne příliš velké ve srovnání s časem zpracování celkový počet aplikací [DA0023: vysoký GC čas procesoru](../profiling/da0023-high-gc-cpu-time.md) namísto toto pravidlo aktivuje se upozornění.  
  
## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [zobrazení značky](../profiling/marks-view.md) dat profilování. Najít **paměť .NET CLR\\% času v uvolňování paměti** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde je těžší než ostatní fáze režie uvolňování paměti spravované paměti. Ohlášení porovnat hodnoty % času v uvolňování paměti hodnota, která se frekvence uvolňování paměti **Počet úklidů 0**, **Počet úklidů 1**, **Počet úklidů 2** hodnoty .  
  
 % Času v uvolňování paměti hodnotu pokusí ohlásit množství času, kterou aplikace stráví provádí uvolňování paměti úměrná celkový objem zpracování. Mějte na paměti, že existují okolnosti, kdy % času v uvolňování paměti hodnotu můžete ohlásit na velmi vysokou hodnotu, ale není kvůli nadměrné uvolňování paměti. Další informace o způsobu, jakým se počítá % času v uvolňování paměti hodnotu, najdete v článku [rozdíl mezi výkonu Data hlášených různých nástrojů – 4](http://go.microsoft.com/fwlink/?LinkId=177863) vstupu **Maoni na Weblogu** na webové stránce MSDN. Pokud se vyskytnou chyby stránky nebo aplikace jiných vyšší prioritu práce na počítači není přerušeno během uvolňování paměti, projeví se % času v uvolňování paměti čítače tyto další zpoždění.



