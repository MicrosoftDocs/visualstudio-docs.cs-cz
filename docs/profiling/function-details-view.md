---
title: Zobrazení podrobností funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7bfc700f0757d99686e28942ff796cf117b1456f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951220"
---
# <a name="function-details-view"></a>Zobrazení podrobností funkce
**Zobrazení podrobností funkce** okně zobrazí následující informace:  
  
- **Distribuce nákladů** vztahy mezi funkce, která jste vybrali a volání funkcí, které provedeny vybrané funkce a mezi vybranou funkci a funkce, které byly volány představuje pruhový graf ho.  
  
- **Podrobnosti o výkonu funkci** tabulky, který zobrazuje souhrnná data profilování pro funkci, která zadáte.  
  
- **Zobrazení kódu funkce** okna, která zobrazuje kód funkce, pokud kód je k dispozici.  
  
  **Zobrazení kódu funkce** okno je na samostatném stavového řádku. Ve výchozím nastavení, jsou dvě podokna Rozdělit horizontálně a **zobrazení kódu funkce** okna je umístěn v dolní části rámce.  
  
- Dvě podokna Rozdělit svisle, klikněte na tlačítko **rozdělit svisle obrazovky** na panelu nástrojů.  
  
- Chcete-li změnit relativní velikosti podoken, klikněte na tlačítko šedé ohraničení mezi snímky a přetažením ohraničení do jiného umístění.  
  
## <a name="cost-distribution-bar-chart"></a>Náklady na distribuci pruhový graf  
  
### <a name="performance-metrics"></a>Metriky výkonu  
 V **metrika výkonu** rozevíracího seznamu, můžete zadat hodnoty, které se zobrazí v zobrazení. Hodnoty, které jsou k dispozici, závisí na metodě profilování, která byla použita v souboru dat profilování. Názvy v závorkách jsou názvy řádků v **podrobnosti o výkonu funkci** tabulky.  
  
### <a name="bar-chart"></a>Pruhový graf  
 **Volání funkcí**  
  
 **Volání funkce** panel ukazuje funkce, které volá vybrané funkce. Velikost bloku, který obsahuje volání funkce je výkonový zisk příspěvek volání funkce k celkové hodnotě metrika výkonu pro vybrané funkce.  
  
 Můžete kliknout na název volající funkce pro zvolení vybrané funkce v zobrazení.  
  
- Pokud existuje příliš mnoho volání funkce do seznamu, funkce s nejmenší příspěvky jsou shromážděny v **jiných** bloku. Klikněte na tlačítko **jiných** zobrazíte všechny volající a volané funkce z vybrané funkce v **zobrazení volající/volaný** okna. Další informace najdete v tématu [zobrazení volající/volaný](../profiling/caller-callee-view.md).  
  
- Pokud neexistují žádné volání funkce, nebo pokud je funkce funkci vstupního vlákna nebo procesu, **horní části zásobníku** bloku se zobrazí.  
  
  **Vybrané funkce**  
  
  Na panelu vybranou funkci zobrazí příspěvky volané funkce a kódu ve funkci vybrané metriky celkového výkonu z vybrané funkce. Velikost bloku, který obsahuje volané funkce nebo tělo funkce je poměr svého příspěvku k celkové hodnotě metrika výkonu pro vybrané funkce.  
  
  Můžete kliknout na název volané funkce pro zvolení vybrané funkce v zobrazení.  
  
- **Celkový** hodnota je metrika výkonu pro vybrané funkce.  
  
- **Tělo funkce** bloku představuje velikost celkové hodnoty metriky výkonu, ke které došlo v přímé provádění kódu v těle funkce.  
  
- Funkce, které jsou volány vybranou funkcí jsou uvedeny v blocích. Velikost bloku vybrané funkce představují množství celkový výkon metriky pro vybrané funkce, ke které došlo ve volané funkci.  
  
- Pokud existuje příliš mnoho volání funkce do seznamu, funkce s nejmenší příspěvky jsou shromážděny v **jiných** bloku. Klikněte na tlačítko **jiných** zobrazíte všechny volající a volané funkce z vybrané funkce v **zobrazení volající/volaný** okna. Další informace najdete v tématu [zobrazení volající/volaný](../profiling/caller-callee-view.md).  
  
- Pokud neexistují žádné volané funkce **dolní části zásobníku** bloku se zobrazí.  
  
## <a name="function-performance-details"></a>Podrobnosti výkonu – funkce  
 Detaily výkonu funkce tabulce souhrnná data pro metriku výkonu vybrané funkce. Zobrazí se hodnota a procenta. Zadejte zadejte v tabulku dat profilování, které se zobrazí v grafu a podrobnosti **metrika výkonu** seznamu.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Exkluzivní**|– Velikost metriku výkonu, ke které došlo při provádění těla funkce.|  
|**Ve volání**|– Velikost metriku výkonu, ke které došlo v funkce, které volaly vybrané funkce.|  
|**Celkový součet**|-Celkový součet **exkluzivní** a **ve volání** hodnoty.|  
  
## <a name="function-code-view"></a>Zobrazení kódu funkce  
 **Zobrazení kódu funkce** okně se zobrazí seznam zdrojového kódu, až bude k dispozici. Vedle řádky zdrojového kódu, které volají dalších funkcí označeno šedou barvou sloupec obsahuje hodnoty metriky výkonu pro volanou funkci. Chcete-li upravit zdrojový kód, klikněte na odkaz k souboru se zdrojovým kódem.  
  
## <a name="cost-distribution-bar-chart-values"></a>Hodnoty v grafu panelu rozdělení nákladů  
  
### <a name="sampling"></a>Vzorkování  
 Následující tabulka vysvětluje hodnoty v seznamu metrika výkonu pro profilování dat, která byla shromážděna pomocí metody vzorkování.  
  
|||  
|-|-|  
|**Celkových vzorků (shromážděných vzorků)**|-Pro volání funkce, počet vzorků, které byly shromážděny při vybrané funkce jmenovala tato volání funkce.<br />-Pro tělo funkce počet vzorků, které byly shromážděny při provádění vlastní kód vybrané funkce.<br />-Pro volaná funkce počet vzorků, které byly shromážděny při volané funkce byla spuštěna z důvodu volání z vybrané funkce.|  
  
### <a name="instrumentation"></a>Instrumentace  
 Následující tabulka vysvětluje hodnoty v seznamu metrika výkonu pro profilování dat, která byla shromážděna pomocí metody instrumentace.  
  
|||  
|-|-|  
|**Uplynulý celkový čas (uplynulý čas)**|Uplynulý čas obsahuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu.<br /><br /> – **Volání funkce**, jaká část uplynulého času, který byl stráven spouštěním instance vybrané funkce, které byly volány funkce. Přikládáme času stráveného ve funkcích volaných vybrané funkce.<br />– **Tělo funkce**, celkové množství uplynulý čas strávený prováděním kódu vybrané funkce. Čas strávený ve volané funkce není součástí.<br />-Pro volaná funkce doba potřebná k provedení instance funkce, které byly volány vybranou funkcí. Celkový počet zahrnuje čas, který byl stráven ve funkcích, které funkce volána. Přikládáme času stráveného ve funkcích volaných vybrané funkce.|  
|**Celkový čas aplikace (aplikace čas)**|Čas aplikace nezahrnuje čas, který byl stráven ve volání do operačního systému, například vstupně výstupní operace a přepnutí kontextu.<br /><br /> -U **volání funkce**, dobu aplikace, který byl stráven spouštěním instance vybrané funkce, které byly volány funkce. Přikládáme času stráveného ve funkcích volaných vybrané funkce.<br />– **Tělo funkce**, celkovou velikost aplikace čas strávený prováděním kódu vybrané funkce. Čas strávený ve volané funkce není součástí.<br />-Pro volaná funkce aplikace doba potřebná k provedení instance funkce, které byly volány vybranou funkcí. Celkový počet zahrnuje čas, který byl stráven ve funkcích, které funkce volána.|  
  
### <a name="net-memory"></a>Paměť .NET  
 Následující tabulka vysvětluje hodnoty v seznamu metrika výkonu pro profilování dat, která byla shromážděna pomocí metody profilace paměti .NET.  
  
|||  
|-|-|  
|**Celkově přidělení (přidělení)**|-U **volání funkce**, počet objektů, které byly přiděleny instance vybrané funkce, která volá funkci. Číslo obsahuje objekty, které byly přiděleny pomocí funkcí, které vybrané funkce volána.<br />– **Tělo funkce**, počet objektů, které byly přiděleny podle vybrané funkce, když probíhal vlastní kód. Přidělené ve funkcích volaných funkcí vybrané objekty nejsou zahrnuty.<br />-Pro volaná funkce počet objektů, které byly přiděleny instancí funkce, které byly volány vybranou funkcí. Číslo obsahuje objekty, které byly přiděleny pomocí funkcí, které funkce volána.|  
|**Celkově bajtů (v bajtech)**|-U **volání funkce**, počet bajtů, které byly přiděleny instance vybrané funkce, která volá funkci. Číslo obsahuje počet bajtů, které byly přiděleny pomocí funkcí, které vybrané funkce volána.<br />– **Tělo funkce**, celkový počet bajtů, které byly přiděleny podle vybrané funkce, když probíhal vlastní kód. Bajtů přidělených funkce volány vybranou funkcí nejsou zahrnuty.<br />-Pro volaná funkce, počet bajtů, které byly přiděleny instancí funkce, které byly volány vybranou funkcí. Číslo obsahuje počet bajtů, které byly přiděleny pomocí funkcí, které funkce volána.|  
  
### <a name="concurrency"></a>Souběžnost  
 Následující tabulka vysvětluje hodnoty v seznamu metrika výkonu pro profilování dat, která byla shromážděna pomocí metody souběžnosti.  
  
|||  
|-|-|  
|**Celkově sporů (sporů)**|-U **volání funkce**, počet prostředků kolizní události, ke kterým došlo v instancích vybrané funkce, která volá funkci. Číslo obsahuje kolizní události ve funkcích, které vybrané funkce volána.<br />– **Tělo funkce**, celkový počet kolizní události, ke kterým došlo při provádění vlastní kód funkce. Kolizí, ke kterým dochází ve funkcích, které byly volány vybranou funkcí nejsou zahrnuty.<br />-Pro volaná funkce číslo kolizní události, ke kterým došlo v instanci funkce, které byly volány vybranou funkcí. Číslo obsahuje kolizní události, ke kterým došlo ve funkcích, které funkce volána.|  
|**Celkový čas (čas zablokování) zablokování**|-Pro volání funkce čas, který byl stráven v prostředku kolize, že události pro instance vybrané funkce, které funkce volána. Čas obsahuje čas zablokování ve funkcích, které vybraná funkce volána.<br />– **Tělo funkce**, celkový čas, který byl stráven v kolizní události, ke kterým došlo při provádění vlastní kód funkce. Kolizí, ke kterým dochází v funkce, které volaly vybrané funkce nejsou zahrnuty.<br />-Pro volaná funkce čas, který se využilo na události kolize prostředků pro instance funkce, která vybrané funkce volána. Čas obsahuje čas zablokování, ke které došlo ve funkcích, které funkce volána.|