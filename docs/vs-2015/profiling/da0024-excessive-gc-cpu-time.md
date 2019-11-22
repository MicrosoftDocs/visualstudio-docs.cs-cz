---
title: 'DA0024: Nadměrný čas procesoru GC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0414e8bc4b5789f08751749b52f870c7c5e5167
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300099"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadměrný čas procesoru uvolňování paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID pravidla | DA0024 |  
| Kategorie |. Použití rozhraní .NET Framework |  
| Metoda profilování | Vše |  
| Zpráva |% času v uvolňování paměti je velmi vysoká. Existuje nadměrné množství režijních nákladů na shromažďování paměti. |  
| Typ pravidla | Upozornění |  
  
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
  
 Hodnota% času v GC se pokusí hlásit množství času, který aplikace stráví prováděním uvolňování paměti úměrnou celkovému množství zpracování. Počítejte s tím, že pokud hodnota% času v GC může nahlásit velmi vysokou hodnotu, ale není to kvůli nadměrnému uvolňování paměti. Další informace o tom, jak se počítá hodnota% času v GC, najdete v tématu [rozdíl mezi daty výkonu hlášených různými nástroji – 4](https://go.microsoft.com/fwlink/?LinkId=177863) záznamem **Maoni blogu** na webu MSDN. Pokud dojde k chybám stránky nebo dojde k přerušení aplikace jinou funkcí s vyšší prioritou v počítači při uvolňování paměti, bude% času v čítači GC tyto další prodlevy odrážet.
