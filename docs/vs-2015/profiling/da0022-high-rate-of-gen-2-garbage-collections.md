---
title: 'DA0022: Vysoká míra 2. generace uvolňování pamětí | Dokumentace Microsoftu'
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
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8da44ab48ae468c5b71bcd08d106548f40d04aa8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757058"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Vysoká míra 2. generace kolekce pamětí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id pravidla | DA0022 |  
| Kategorie |. Použití rozhraní .NET Framework |  
| Metoda profilace | Všechny |  
| Zpráva | Je velmi vysoká míra 2. generace uvolňování pamětí, ke kterým dochází. Pokud, podle návrhu, většina datových struktur vašeho programu jsou přiděleny a trvala po dlouhou dobu, to není obvykle problém. Ale pokud toto chování nežádoucí, vaše aplikace může být Připnutí objekty. Pokud si nejste jisti, můžete shromáždit .NET paměť přidělení dat a objekt životnosti informace pro pochopení způsobu přidělení paměti, které vaše aplikace používá. |  
| Typ pravidla | Upozornění |  
  
 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  
  
## <a name="cause"></a>příčina  
 Údaje o výkonu systému, která byla shromážděna během profilování znamenat, že podstatnou část objekty paměti for.NET Framework byla uvolněny v procesu 2. generace uvolňování paměti ve srovnání s 0. generace a uvolnění paměti generace 1.  
  
## <a name="rule-description"></a>Popis pravidla  
 Rozhraní Microsoft .NET common language runtime (CLR) poskytuje mechanismus správy automatické paměti, která používá systému uvolňování paměti pro uvolnění paměti z objektů, které aplikace se už používá. Uvolňování paměti je orientované na generování založeno na předpokladu, že jsou krátkodobé a jednorázové mnoho přidělení. Lokální proměnné by měl být například krátkodobou. Spustit nově vytvořené objekty v generaci 0 (0. generace) a potom pokroku na generaci 1, pokud se uvolňování paměti spusťte a nakonec přechod do 2. generace zvládnout situaci, kdy aplikace stále používá.  
  
 Objekty v generaci 0 se vybírají obvykle velmi efektivně a často. Objekty v 1. generace jsou shromažďovány méně často a méně efektivní. Nakonec dlouhodobými objekty v generaci 2 by měl být shromažďovány i méně často. 2. generace kolekce, která je spuštění úplného uvolňování paměti kolekce, je také nejvíce náročná operace.  
  
 Toto pravidlo je vyvoláno při proporcionálně příliš mnoho generace 2 kolekce uvolnění paměti dochází. Které jsou v pořádku aplikací využívajících rozhraní .NET Framework bude mít víc než 5 třikrát tolik generace 1 uvolnění paměti jako kolekce generace 2. (Faktor 10 x je pravděpodobně ideální.)  
  
## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [zobrazení značky](../profiling/marks-view.md) dat profilování. Najít **paměť .NET CLR\\Počet úklidů 0** a **paměť .NET CLR\\Počet úklidů 1** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde uvolňování paměti dochází častěji. Porovnat tyto hodnoty **% času v uvolňování paměti** sloupec, pokud vzor přidělení spravované paměti je příčinou režie na správu využívala příliš mnoho paměti.  
  
 Vysoký podíl 2. generace uvolňování pamětí není vždy problém. Může být záměrné. Aplikace, která přiděluje velkých datových struktur, které musí zůstat aktivní po dlouhou dobu, během provádění mohou aktivovat toto pravidlo. Pokud takové aplikace je přetížena paměť, může vynutit k provedení uvolnění paměti časté. Pokud levnější generace 0 a 1. generace uvolňování paměti mohl uvolnit pouze malou část spravované paměti, bude naplánováno častější 2. generace uvolňování pamětí.  
  
 Existují další paměť .NET CLR sloupce v zobrazení značky, který vám pomůže identifikovat problémy kolekce uvolnění paměti. **% Času v uvolňování paměti** sloupec vám pomůže pochopit, jak velká režie na správu paměti dochází. Pokud vaše aplikace používá obvykle poměrně malý počet velkých ale trvalé objekty, neměl spotřebovávat časté kolekce generace 2 nadměrné množství času procesoru. Pokud aplikace je přetížena paměť, protože další fyzické paměti (RAM) je vyžadován, související pravidla, která se vyhodnotí **Paměť\Stránky/s** hodnot sloupců může také vyvolat.  
  
 Informace o tom aplikace vzor využití spravované paměti, profilujte ji znovu spuštěna analýze profilu přidělení paměti a vyberte dobu života objektu profilace možnost.  
  
 Informace o tom, jak zlepšit výkon kolekce uvolnění paměti, naleznete v tématu [základní informace o uvolňování paměti a typech výkonu](http://go.microsoft.com/fwlink/?LinkId=148226) na webu společnosti Microsoft. Informace o režii související se automatické uvolňování paměti naleznete v tématu [velký objekt haldy Nepokrytý](http://go.microsoft.com/fwlink/?LinkId=177836).



