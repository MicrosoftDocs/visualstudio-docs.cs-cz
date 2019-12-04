---
title: Zobrazení podrobností funkce | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779256"
---
# <a name="function-details-view"></a>Zobrazení podrobností funkce
V okně **zobrazení podrobností funkce** se zobrazí následující informace:

- Pruhový graf **rozdělení nákladů** představuje vztahy mezi funkcí, kterou jste vybrali, a volání funkcí, které provedly vybranou funkci, a mezi vybranou funkcí a funkcemi, které byly volány.

- Tabulka **Podrobnosti o výkonu funkce** , která zobrazuje souhrnná data profilace pro funkci, kterou určíte.

- Okno **zobrazení kódu funkce** , které zobrazuje kód funkce, když je kód k dispozici.

  Okno **zobrazení kódu funkce** je samostatné podokno. Ve výchozím nastavení jsou dvě podokna rozděleny vodorovně a okno **zobrazení kódu funkce** je umístěno na konci rámečku.

- Chcete-li rozdělit dvě podokna svisle, klikněte na možnost **rozdělit obrazovku svisle** na panelu nástrojů.

- Chcete-li změnit relativní velikost podoken, klikněte na stínované ohraničení mezi snímky a přetáhněte ohraničení do jiného umístění.

## <a name="cost-distribution-bar-chart"></a>Pruhový graf rozdělení nákladů

### <a name="performance-metrics"></a>Metrika výkonu
 V rozevíracím seznamu **metrika výkonu** můžete určit, které hodnoty se zobrazí v zobrazení. Hodnoty, které jsou k dispozici, závisí na metodě profilování, která byla použita v souboru dat profilování. Názvy v závorkách jsou názvy řádků v tabulce **podrobnosti výkonu funkce** .

### <a name="bar-chart"></a>Pruhový graf
 **Volání funkcí**

 Panel **volající funkce** zobrazuje funkce, které volaly vybranou funkci. Velikost bloku, který obsahuje volání funkce, je úměrná příspěvku volání funkce k celkové hodnotě metriky výkonu pro vybranou funkci.

 Můžete kliknout na název volající funkce a nastavit ji jako vybranou funkci v zobrazení.

- Pokud je v seznamu příliš mnoho volání funkcí, funkce s nejmenšími příspěvky jsou shromažďovány v **jiném** bloku. Kliknutím na tlačítko **Další** zobrazíte všechny volání a volané funkce vybrané funkce v okně **zobrazení volající/volaný** . Další informace naleznete v tématu [zobrazení volající/volaný](../profiling/caller-callee-view.md).

- Pokud nejsou k dispozici žádné volání funkcí nebo pokud je funkce vstupní funkcí vlákna nebo procesu, zobrazí se **horní část bloku zásobníku** .

  **Vybraná funkce**

  Vybraný panel funkcí zobrazuje příspěvky volaných funkcí a kódu ve vybrané funkci na celkovou metriku výkonu vybrané funkce. Velikost bloku obsahujícího volanou funkci nebo tělo funkce jsou v poměru k jeho příspěvku na celkovou hodnotu metriky výkonu pro vybranou funkci.

  Kliknutím na název volané funkce můžete nastavit, aby byla vybraná funkce v zobrazení.

- **Celková** hodnota je metrika výkonu pro vybranou funkci.

- Blok **těla funkce** představuje velikost celkové hodnoty metriky výkonu, ke které došlo v přímém provádění kódu v těle funkce.

- Funkce, které jsou volány vybranou funkcí, jsou uvedeny v části bloky. Velikost vybraného bloku Functions reprezentuje množství metriky celkového výkonu pro vybranou funkci, ke které došlo ve volané funkci.

- Pokud je v seznamu příliš mnoho volání funkcí, funkce s nejmenšími příspěvky jsou shromažďovány v **jiném** bloku. Kliknutím na tlačítko **Další** zobrazíte všechny volání a volané funkce vybrané funkce v okně **zobrazení volající/volaný** . Další informace naleznete v tématu [zobrazení volající/volaný](../profiling/caller-callee-view.md).

- Pokud nejsou žádné volané funkce, zobrazí se **dolní část bloku zásobníku** .

## <a name="function-performance-details"></a>Podrobnosti o výkonu funkce
 Tabulka Podrobnosti o výkonu funkce poskytuje souhrnná data pro metriku výkonu vybrané funkce. Zobrazí se hodnota i procento. Zadejte data profilace, která se zobrazí v grafu, a v tabulce podrobností v seznamu **metrika výkonu** .

|Sloupec|Popis|
|------------|-----------------|
|**Vyhrazen**|– Množství metriky výkonu, ke kterému došlo při provádění těla funkce.|
|**V voláních**|– Množství metriky výkonu, k nimž došlo ve funkcích, které vyvolala vybraná funkce.|
|**Celkový součet**|– Celková hodnota **exkluzivních** hodnot a **v případě volání** .|

## <a name="function-code-view"></a>Zobrazení kódu funkce
 Okno **zobrazení kódu funkce** zobrazuje seznam zdrojového kódu, pokud je k dispozici. Vedle řádků zdrojového kódu, které volají jiné funkce, obsahuje šedivý sloupec hodnoty metriky výkonu volané funkce. Chcete-li upravit zdrojový kód, klikněte na odkaz na soubor zdrojového kódu.

## <a name="cost-distribution-bar-chart-values"></a>Hodnoty pruhového grafu distribuce nákladů

### <a name="sampling"></a>Kontrol
 Následující tabulka vysvětluje hodnoty v seznamu metrik výkonu pro data profilování, která byla shromážděna pomocí metody vzorkování.

|||
|-|-|
|**Zahrnuté vzorky (shromážděné vzorky)**|– Pro volání funkce počet vzorků, které byly shromážděny při volání vybrané funkce touto voláním funkce.<br />– Pro tělo funkce počet vzorků, které byly shromážděny v případě, že vybraná funkce prováděla vlastní kód.<br />– Pro volanou funkci počet vzorků, které byly shromážděny při spuštění volané funkce z důvodu volání z vybrané funkce.|

### <a name="instrumentation"></a>Instrumentace
 Následující tabulka vysvětluje hodnoty v seznamu metrik výkonu pro data profilace, která byla shromážděna pomocí metody instrumentace.

|||
|-|-|
|**Uplynulý celkový čas (uplynulý čas)**|Uplynulý čas zahrnuje čas strávený v voláních k operačnímu systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br /><br /> – Pro **volání funkce**je to množství uplynulého času, který strávil provádění instancí vybrané funkce, které byly volány funkcí. Součástí je čas strávený ve funkcích, které vyvolala vybraná funkce.<br />– Pro **tělo funkce**celková hodnota uplynulého času stráveného prováděním kódu vybrané funkce. Čas strávený volanými funkcemi není zahrnutý.<br />– Pro volanou funkci, čas strávený prováděním instancí funkce, které byly volány vybranou funkcí. Celkový součet zahrnuje čas strávený ve funkcích, které funkce volala. Součástí je čas strávený ve funkcích, které vyvolala vybraná funkce.|
|**Celková doba aplikace (doba použití)**|Čas aplikace neobsahuje čas strávený voláním operačního systému, jako jsou například přepínače kontextu a vstupně-výstupní operace.<br /><br /> – Pro **volání funkce**, množství času aplikace strávené prováděním instancí vybrané funkce, které byly volány funkcí. Součástí je čas strávený ve funkcích, které vyvolala vybraná funkce.<br />– Pro **tělo funkce**celková doba trvání aplikace strávená spouštěním kódu vybrané funkce. Čas strávený volanými funkcemi není zahrnutý.<br />– Pro volanou funkci se jednalo o množství času aplikace stráveného prováděním instancí funkce, které byly volány vybranou funkcí. Celkový součet zahrnuje čas strávený ve funkcích, které funkce volala.|

### <a name="net-memory"></a>Paměť .NET
 Následující tabulka vysvětluje hodnoty v seznamu metrik výkonu pro data profilování, která byla shromážděna pomocí metody profilace paměti .NET.

|||
|-|-|
|**Celkové přidělení (přidělení)**|– Pro **volání funkce**počet objektů, které byly přiděleny instancemi vybrané funkce, kterou funkce volala. Toto číslo zahrnuje objekty, které byly přiděleny funkcemi, které vyvolala vybraná funkce.<br />– Pro **tělo funkce**počet objektů, které byly přiděleny pomocí vybrané funkce při provádění vlastního kódu. Objekty přidělené ve funkcích volaných vybranou funkcí nejsou zahrnuté.<br />– Pro volanou funkci počet objektů, které byly přiděleny instancemi funkce, které byly volány vybranou funkcí. Číslo zahrnuje objekty, které byly přiděleny funkcemi, které volala funkce.|
|**Včetně bajtů (v bajtech)**|– Pro **volání funkce**počet bajtů, které byly přiděleny instancemi vybrané funkce, kterou funkce volala. Toto číslo zahrnuje bajty, které byly přiděleny funkcemi, které vyvolala vybraná funkce.<br />– Pro **tělo funkce**celkový počet bajtů, které byly přiděleny vybranou funkcí při provádění vlastního kódu. Bajty přidělené ve funkcích volaných vybranou funkcí nejsou zahrnuté.<br />– Pro volanou funkci počet bajtů, které byly přiděleny instancemi funkce, které byly volány vybranou funkcí. Toto číslo zahrnuje bajty, které byly přiděleny funkcemi, které volala funkce.|

### <a name="concurrency"></a>Souběžnost
 Následující tabulka vysvětluje hodnoty v seznamu metrik výkonu pro data profilace, která byla shromážděna pomocí metody souběžnosti.

|||
|-|-|
|**Celkové spory (spory)**|– Pro **volání funkce**počet událostí kolizí prostředků, ke kterým došlo v instancích vybrané funkce, kterou funkce volala. Toto číslo zahrnuje události kolizí ve funkcích, které vyvolala vybraná funkce.<br />– Pro **tělo funkce**celkový počet událostí kolizí, k nimž došlo, když funkce prováděla vlastní kód. Spory vyskytující se ve funkcích, které byly volány pomocí vybrané funkce, nejsou zahrnuty.<br />– Pro volanou funkci počet událostí kolizí, ke kterým došlo v instancích funkce, které byly volány vybranou funkcí. Toto číslo zahrnuje události kolizí, k nimž došlo ve funkcích, které volá Function.|
|**Celkový čas zablokování (čas zablokování)**|– Pro volání funkce, čas strávený v událostech kolizí prostředků pro instance vybrané funkce, která je volána funkcí. Čas zahrnuje čas zablokování ve funkcích, které vybrala funkce s názvem.<br />– Pro **tělo funkce**celkový čas strávený v událostech kolizí, k nimž došlo, když funkce prováděla vlastní kód. Spory vyskytující se ve funkcích, které vybraná funkce volá, nejsou zahrnuté.<br />– Pro volanou funkci čas strávený v událostech kolizí prostředků pro instance funkce, kterou vyvolala vybraná funkce. Čas zahrnuje čas zablokování, ke kterému došlo ve funkcích, které funkce volala.|
