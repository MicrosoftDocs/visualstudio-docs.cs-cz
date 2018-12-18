---
title: 'DA0023: Vysoký GC čas procesoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d13f1c0bc2a024d35611d81f4aba3694f3bc39e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836265"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Vysoký čas procesoru uvolňování paměti

|||  
|-|-|  
|Id pravidla|DA0023|  
|Kategorie|Použití rozhraní .NET framework|  
|Metoda profilace|Všechny|  
|Zpráva|% Času v GC je poměrně vysoká. Tento náznak nadměrného množství režie uvolňování paměti by mohl být ovlivňující rychlost reakce aplikace. Můžete získat .NET paměti přidělení dat objektu životnost informace a porozumět způsobu přidělení paměti, které aplikace používá lépe.|  
|Typ pravidla|Informační|  

 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  

## <a name="cause"></a>příčina  
 Údaje o výkonu systému, který je shromážděných během profilace označuje, že množství času, který byl stráven uvolňování paměti je důležité ve srovnání s časem zpracování celkový počet aplikací.  

## <a name="rule-description"></a>Popis pravidla  
 Rozhraní Microsoft .NET common language runtime (CLR) poskytuje mechanismus správy automatické paměti, která používá systému uvolňování paměti pro uvolnění paměti z objektů, které aplikace se už používá. Uvolňování paměti je orientované na generování založeno na předpokladu, že jsou krátkodobé a jednorázové mnoho přidělení. Lokální proměnné by měl být například krátkodobou. Spustit nově vytvořené objekty v generaci 0 (0. generace) a potom pokroku na generaci 1, pokud se uvolňování paměti spusťte a nakonec přechod do 2. generace zvládnout situaci, kdy aplikace stále používá.  

 Objekty v generaci 0 jsou shromažďovány často a efektivně. Objekty v 1. generace jsou shromažďovány méně často a méně efektivní. Nakonec dlouhodobými objekty v generaci 2 by měl být shromažďovány i méně často. 2. generace kolekce, která je spuštění úplného uvolňování paměti kolekce, je také nejvíce náročná operace.  

 Toto pravidlo je vyvoláno, když množství času, který byl stráven uvolňování paměti je důležité ve srovnání s časem zpracování celkový počet aplikací.  

> [!NOTE]
>  Když podíl času, který byl stráven uvolňování paměti je příliš ve srovnání s časem zpracování celkový počet aplikací, [DA0024: nadměrný čas procesoru uvolňování paměti](../profiling/da0024-excessive-gc-cpu-time.md) namísto toto pravidlo aktivuje se upozornění.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [zobrazení značky](../profiling/marks-view.md) dat profilování. Najít **paměť .NET CLR\\% času v uvolňování paměti** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde je těžší než ostatní fáze režie uvolňování paměti spravované paměti. Ohlášení porovnat hodnoty % času v uvolňování paměti hodnota, která se frekvence uvolňování paměti **Počet úklidů 0**, **Počet úklidů 1**, **Počet úklidů 2** hodnoty .  

 % Času v uvolňování paměti hodnotu pokusí ohlásit množství času, kterou aplikace stráví provádí uvolňování paměti úměrná celkový objem zpracování. Uvědomte si, existují okolnosti, kdy ohlásit vysoké hodnoty % času v hodnotě GC, ale není z důvodu nadměrného uvolňování. Další informace o způsobu, jakým je % času v GC hodnota vypočtena, viz [rozdíl mezi Perf údaje uvedeny pomocí různých nástrojů - 4](http://go.microsoft.com/fwlink/?LinkId=177863) vstup **Maoni's Weblog** na webu MSDN. Pokud se vyskytnou chyby stránky nebo aplikace jiných vyšší prioritu práce na počítači není přerušeno během uvolňování paměti, projeví se % času v uvolňování paměti čítače tyto další zpoždění.