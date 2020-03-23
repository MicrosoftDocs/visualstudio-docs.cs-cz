---
title: Zobrazení podrobností o funkci | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6e5bd33d9924784220addafca85a63f550df02c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779256"
---
# <a name="function-details-view"></a>Zobrazení podrobností funkce
V okně **Zobrazení podrobností funkce** se zobrazí následující informace:

- Pruhový graf **Distribuce nákladů** představuje vztahy mezi vybranou funkcí a volacími funkcemi, které provedly vybranou funkci, a mezi vybranou funkcí a funkcemi, které byly volány.

- Tabulka **Podrobnosti výkonu funkce,** která zobrazuje data souhrnného profilování pro zadanou funkci.

- Okno **Zobrazení kódu funkce,** které zobrazuje kód funkce, když je kód k dispozici.

  Okno **Zobrazení kódu funkce** je samostatné podokno. Ve výchozím nastavení jsou obě podokna rozdělena vodorovně a okno **Zobrazení kódu funkce** je umístěno v dolní části rámečku.

- Chcete-li obě podokna rozdělit svisle, klepněte na panelu nástrojů na **Rozdělená obrazovka svisle.**

- Chcete-li změnit relativní velikost podoken, klepněte na stínované ohraničení mezi rámečky a přetáhněte ohraničení do jiného umístění.

## <a name="cost-distribution-bar-chart"></a>Pruhový graf distribuce nákladů

### <a name="performance-metrics"></a>Metriky výkonu
 V rozevíracím seznamu **Metrika výkonu** můžete určit, které hodnoty se zobrazí v zobrazení. Hodnoty, které jsou k dispozici, závisí na metodě profilování, která byla použita v datovém souboru profilování. Názvy v závorcích jsou názvy řádků v tabulce **Podrobnosti výkonu funkce.**

### <a name="bar-chart"></a>Pruhový graf
 **Volající funkce**

 Panel **Volající funkce** zobrazuje funkce, které volaly vybranou funkci. Velikost bloku, který obsahuje volající funkci, je úměrná příspěvku volající funkce k celkové hodnotě metriky výkonu pro vybranou funkci.

 Klepnutím na název volající funkce z ní můžete vytvořit vybranou funkci v zobrazení.

- Pokud existuje příliš mnoho volajících funkcí do seznamu, funkce s nejmenšípříspěvky jsou shromažďovány v **Other** bloku. Kliknutím na **Jiné** zobrazíte všechny volavé a volané funkce vybrané funkce v okně **Zobrazení volajícího/volaného.** Další informace naleznete v [tématu Caller/Callee View](../profiling/caller-callee-view.md).

- Pokud neexistují žádné volající funkce nebo pokud je funkce vstupní funkcí vlákna nebo procesu, zobrazí se blok **Horní zásobník.**

  **Vybraná funkce**

  Vybraný panel funkcí zobrazuje příspěvky volaných funkcí a kódu ve vybrané funkci k celkové metrice výkonu vybrané funkce. Velikost bloku, který obsahuje volanou funkci nebo tělo funkce, je úměrná jeho příspěvku k celkové hodnotě metriky výkonu pro vybranou funkci.

  Klepnutím na název volané funkce z ní můžete vytvořit vybranou funkci v zobrazení.

- Hodnota **Celkem** je metrika výkonu pro vybranou funkci.

- Funkce **Body** blok představuje částku celkové hodnoty metriky výkonu, ke kterým došlo v přímém spuštění kódu v těle funkce.

- Funkce, které jsou volány vybranou funkcí, jsou uvedeny v blocích. Velikost bloku vybraných funkcí představuje velikost metriky celkového výkonu pro vybranou funkci, ke které došlo ve volané funkci.

- Pokud existuje příliš mnoho volajících funkcí do seznamu, funkce s nejmenšípříspěvky jsou shromažďovány v **Other** bloku. Kliknutím na **Jiné** zobrazíte všechny volavé a volané funkce vybrané funkce v okně **Zobrazení volajícího/volaného.** Další informace naleznete v [tématu Caller/Callee View](../profiling/caller-callee-view.md).

- Pokud neexistují žádné takzvané funkce, zobrazí se dolní **část zásobníku** bloku.

## <a name="function-performance-details"></a>Podrobnosti o výkonu funkce
 Tabulka Podrobnosti výkonu funkce obsahuje souhrnná data pro metriky výkonu vybrané funkce. Zobrazí se hodnota i procento. Určíte data profilování, která se zobrazí v grafu, a tabulku podrobností v seznamu **metrik výkonu.**

|Sloupec|Popis|
|------------|-----------------|
|**Exkluzivní**|- Množství metriky výkonu, ke které došlo při provádění těla funkce.|
|**Ve volání**|- Množství metriky výkonu, ke které došlo ve funkcích, které vybraná funkce volala.|
|**Včetně součtu**|- Součet **hodnot Exclusive** a **In Calls.**|

## <a name="function-code-view"></a>Zobrazení kódu funkce
 Okno **Zobrazení kódu funkce** zobrazí seznam zdrojového kódu, pokud je k dispozici. Vedle řádků zdrojového kódu, které volají další funkce, obsahuje stínovaný sloupec hodnoty metrik výkonu pro volanou funkci. Chcete-li zdrojový kód upravit, klikněte na odkaz na soubor zdrojového kódu.

## <a name="cost-distribution-bar-chart-values"></a>Hodnoty pruhového grafu distribuce nákladů

### <a name="sampling"></a>Vzorkování
 Následující tabulka vysvětluje hodnoty v seznamu Metrika výkonu pro profilování dat, která byla shromážděna pomocí metody vzorkování.

|||
|-|-|
|**Včetně vzorků (odebraných vzorků)**|- Pro volající funkce počet vzorků, které byly shromážděny při volání vybrané funkce touto volající funkcí.<br />- Pro tělo funkce počet vzorků, které byly shromážděny při vybrané funkce bylo provádění vlastního kódu.<br />- Pro volanou funkci počet vzorků, které byly shromážděny při spuštění volané funkce z důvodu volání z vybrané funkce.|

### <a name="instrumentation"></a>Instrumentace
 Následující tabulka vysvětluje hodnoty v seznamu Metrika výkonu pro profilování dat, která byla shromážděna pomocí metody instrumentace.

|||
|-|-|
|**Uplynulý včetně času (uplynulý čas)**|Uplynulý čas zahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br /><br /> - Pro **volající funkce**, množství uplynulý čas, který byl vynaložen provádění instance vybrané funkce, které byly volány funkce. Čas strávený ve funkcích volaný vybranou funkcí je zahrnut.<br />- Pro **tělo funkce**, celkové množství uplynulého času stráveného prováděním kódu vybrané funkce. Čas strávený v volaná funkce není zahrnuta.<br />- Pro volanou funkci množství času stráveného prováděním instancí funkce, které byly volány vybranou funkcí. Součet zahrnuje čas strávený ve funkcích, které funkce volala. Čas strávený ve funkcích volaný vybranou funkcí je zahrnut.|
|**Čas aplikace včetně (čas aplikace)**|Čas aplikace nezahrnuje čas strávený při volání operačního systému, jako jsou například přepnutí kontextu a operace vstupu a výstupu.<br /><br /> - Pro **volající funkce**, množství času aplikace, který byl vynaložen provádění instance vybrané funkce, které byly volány funkce. Čas strávený ve funkcích volaný vybranou funkcí je zahrnut.<br />- Pro **tělo funkce**, celkové množství času aplikace stráveného prováděním kódu vybrané funkce. Čas strávený v volaná funkce není zahrnuta.<br />- Pro volanou funkci množství času aplikace stráveného prováděním instancí funkce, které byly volány vybranou funkcí. Součet zahrnuje čas strávený ve funkcích, které funkce volala.|

### <a name="net-memory"></a>Paměť .NET
 Následující tabulka vysvětluje hodnoty v seznamu Metrika výkonu pro profilování dat, která byla shromážděna pomocí metody profilování paměti .NET.

|||
|-|-|
|**Inkluzivní přidělení (přidělení)**|- Pro **volající funkce**, počet objektů, které byly přiděleny instance vybrané funkce, které funkce volá. Číslo zahrnuje objekty, které byly přiděleny funkcemi, které volala vybraná funkce.<br />- Pro **tělo funkce**, počet objektů, které byly přiděleny vybranou funkcí při provádění vlastního kódu. Objekty přidělené ve funkcích volaných vybranou funkcí nejsou zahrnuty.<br />- Pro volanou funkci počet objektů, které byly přiděleny instancemi funkce, které byly volány vybranou funkcí. Číslo zahrnuje objekty, které byly přiděleny funkce, které funkce volá.|
|**Včetně bajtů (bajtů)**|- Pro **volající funkce**, počet bajtů, které byly přiděleny instance vybrané funkce, které funkce volá. Číslo zahrnuje bajty, které byly přiděleny funkcemi, které volala vybraná funkce.<br />- Pro **tělo funkce**, celkový počet bajtů, které byly přiděleny vybrané funkce při provádění vlastního kódu. Bajty přidělené ve funkcích volaných vybranou funkcí nejsou zahrnuty.<br />- Pro volanou funkci počet bajtů, které byly přiděleny instancemi funkce, které byly volány vybranou funkcí. Číslo zahrnuje bajty, které byly přiděleny funkce, které funkce volá.|

### <a name="concurrency"></a>Souběžnost
 Následující tabulka vysvětluje hodnoty v seznamu Metrika výkonu pro profilování dat, která byla shromážděna pomocí metody souběžnosti.

|||
|-|-|
|**Inkluzivní tvrzení (tvrzení)**|- Pro **volající funkce**, počet událostí konflikty prostředků, ke kterým došlo v instancích vybrané funkce, které funkce volá. Číslo zahrnuje konfliktní události ve funkcích, které vybraná funkce volala.<br />- Pro **tělo funkce**, celkový počet konfliktních událostí, ke kterým došlo, když funkce prováděla vlastní kód. Konflikty vyskytující se ve funkcích, které byly volány vybranou funkcí, nejsou zahrnuty.<br />- Pro volanou funkci počet konfliktních událostí, ke kterým došlo v instancích funkce, které byly volány vybranou funkcí. Číslo zahrnuje konfliktní události, ke kterým došlo ve funkcích, které jsou volány.|
|**Včetně blokovaného času (blokovaný čas)**|- Pro volající funkce čas, který byl strávený v událostech tvrzení o prostředku pro instance vybrané funkce, kterou funkce volala. Čas zahrnuje blokovaný čas ve funkcích, které vybraná funkce volána.<br />- Pro **tělo funkce**, celkový čas, který byl stráven v konfliktní události, ke kterým došlo, když funkce byla provádění vlastního kódu. Konflikty vyskytující se ve funkcích, které vybraná funkce volána nejsou zahrnuty.<br />- Pro volanou funkci čas, který byl stráven v událostech konfliktů prostředků pro instance funkce, kterou vybraná funkce volala. Čas zahrnuje blokovaný čas, ke kterému došlo ve funkcích, které funkce volala.|
