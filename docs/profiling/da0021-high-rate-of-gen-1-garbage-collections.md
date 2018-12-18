---
title: 'DA0021: Vysoká míra 1. generace uvolňování pamětí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fc809e39f444b44e6bb71b87b6c7c30774be146
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894453"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Vysoká míra 1. generace kolekce pamětí

|||  
|-|-|  
|Id pravidla|DA0021|  
|Kategorie|Použití rozhraní .NET framework|  
|Metod profilace|Všechny|  
|Zpráva|Je velmi vysoká míra 1. generace uvolňování pamětí, ke kterým dochází. Pokud, podle návrhu, většina datových struktur vašeho programu jsou přiděleny a trvala po dlouhou dobu, to není obvykle problém. Ale pokud toto chování nežádoucí, vaše aplikace může být Připnutí objekty. Pokud si nejste jisti, můžete shromáždit .NET paměť přidělení dat a objekt životnosti informace pro pochopení způsobu přidělení paměti, které vaše aplikace používá.|  
|Typ pravidla|Informace o|  

 Při profilování pomocí vzorkování, paměti .NET nebo metodám sporu prostředků, musíte shromáždit minimálně 10 vzorky k aktivaci tohoto pravidla.  

## <a name="cause"></a>příčina  
 Údaje o výkonu systému, která byla shromážděna během profilování znamenat, že podstatnou část objekty paměti for.NET Framework byla uvolněny v 1. generace uvolňování ve srovnání s shromažďování dat 0. generace.  

## <a name="rule-description"></a>Popis pravidla  
 Rozhraní Microsoft .NET common language runtime (CLR) poskytuje mechanismus správy automatické paměti, která používá systému uvolňování paměti pro uvolnění paměti z objektů, které aplikace se už používá. Uvolňování paměti je orientované na generování založeno na předpokladu, že jsou krátkodobé a jednorázové mnoho přidělení. Lokální proměnné by měl být například krátkodobou. Spustit nově vytvořené objekty v generaci 0 (0. generace) a potom pokroku na generaci 1, pokud se uvolňování paměti spusťte a nakonec přechod do 2. generace zvládnout situaci, kdy aplikace stále používá.  

 Objekty v generaci 0 se vybírají obvykle velmi efektivně a často. Objekty v 1. generace jsou shromažďovány méně často a méně efektivní. Nakonec dlouhodobými objekty v generaci 2 by měl být shromažďovány i méně často. 2. generace kolekce, která je spuštění úplného uvolňování paměti kolekce, je také nejvíce náročná operace.  

 Toto pravidlo je vyvoláno při proporcionálně příliš mnoho generace došlo k uvolnění paměti 1. Pokud příliš mnoho poměrně krátkodobé objekty byly zachovány při 0. generace kolekce ale počítače pak můžou být shromážděny v kolekci generace 1, může být nadměrné náklady na správu paměti. Další informace najdete v tématu [uprostřed života krize](http://go.microsoft.com/fwlink/?LinkId=177835) Zveřejněte na výkon Tidbits Rico Mariani na webové stránce MSDN.  

## <a name="how-to-investigate-a-warning"></a>Zkoumání upozornění  
 Dvakrát klikněte na zprávu v okně Seznam chyb, přejděte [zobrazení značky](../profiling/marks-view.md) dat profilování. Najít **paměť .NET CLR\\Počet úklidů 0** a **paměť .NET CLR\\Počet úklidů 1** sloupce. Zjistěte, jestli konkrétní fázích provádění programu kde uvolňování paměti dochází častěji. Porovnat tyto hodnoty **% času v uvolňování paměti** sloupec, pokud vzor přidělení spravované paměti je příčinou režie na správu využívala příliš mnoho paměti.  

 Informace o tom aplikace vzor využití spravované paměti, profilujte ji znovu spuštěna přidělení paměti analýze profilu a žádosti o měření doba života objektu.  

 Informace o tom, jak zlepšit výkon kolekce uvolnění paměti, naleznete v tématu [základní informace o uvolňování paměti a typech výkonu](http://go.microsoft.com/fwlink/?LinkId=148226) na webu společnosti Microsoft. Informace o režii související se automatické uvolňování paměti naleznete v tématu [velký objekt haldy Nepokrytý](http://go.microsoft.com/fwlink/?LinkId=177836).