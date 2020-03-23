---
title: Analýza výsledků zátěžových testů v zobrazení grafů analyzátoru zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dac639b8513e8ef675c6246476791b9351241130
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591265"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů v zobrazení grafů analyzátoru zátěžového testu

Výsledky zátěžového testu jsou zobrazeny jako data v několika různých podoknech.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li zobrazit výsledky testů jako grafy, zvolte **Grafy** na panelu nástrojů **zátěžového testu.** Každý jednotlivý graf je zobrazen v panelu s názvem grafu zobrazeným v horní části rozevíracího seznamu. Chcete-li v panelu zobrazit jiný graf, zvolte jiný název grafu ze seznamu.

Najednou lze zobrazit až čtyři panely grafu. Mezi různými rozvrženími panelů můžete přepínat pomocí tlačítka panelu **pro panel.**

K dispozici je několik vestavěných grafů. Můžete použít vestavěné grafy tak, jak jsou, nebo je můžete přizpůsobit. Kromě toho můžete vytvořit vlastní grafy. Další informace naleznete v [tématu Postup: Přidání a odstranění čítačů v grafech](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) a [Postup: Vytvoření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Vestavěné grafy

V následující tabulce jsou uvedeny předdefinované grafy, které jsou k dispozici pro analýzu výsledků zátěžových testů.

|Název grafu|Popis|
|-|-|
|Klíčové ukazatele|Čítače, které popisují základní aspekty výkonu testu, jako je zatížení uživatele, propustnost a doba odezvy.|
|Doba odezvy testu|Data o množství času testy trvat spustit.|
|Doba odezvy stránky|Průměrná doba odezvy pro webové stránky, které jsou přístupné během zátěžového testu.|
|Testovky|Informace o počítačích, ve kterých je testovaná aplikace spuštěna. To zahrnuje údaje o využití paměti, procesor, fyzický disk, procesy.<br /><br /> Ve výchozím nastavení jsou shromažďovány pouze čítače Dostupné mbajty a Čas procesoru.|
|Správce a agenti|Informace o počítačích, na kterých jsou spuštěny zátěžové testy. To zahrnuje údaje o využití paměti, procesor, fyzický disk, procesy.<br /><br /> Ve výchozím nastavení jsou shromažďovány pouze čítače Dostupné mbajty a Čas procesoru.|
|Doba odezvy transakce|Průměrná doba odezvy pro transakce, ke kterým dochází během zátěžového testu.|

Můžete zobrazit různé čítače v grafu za běhu i po spuštění testu.

> [!NOTE]
> Do automaticky generovaného grafu doby odezvy lze přidat pouze čítače výkonu doby odezvy.

Informace o čítači se zobrazí v grafu i v legendě pod grafy. Můžete také přiblížit část grafu. Další informace naleznete [v tématu Postup: Přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Čítače zobrazené v grafech

Grafy zobrazují *čítače*. Čítače odkazují na data shromážděná během zátěžového testu, jako jsou testy za sekundu nebo průměrná doba testu. Další informace o čítačích naleznete [v tématu Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

Legenda pro čítače, které jsou zobrazeny v grafech, zobrazuje několik sloupců užitečných dat o spuštění zátěžového testu. Chcete-li vypnout zobrazení všech dat v grafu, zrušte zaškrtnutí políčka v řádku v legendě.

Legenda obsahuje následující sloupce:

|Čítač|Název čítače|
|-|-|
|Instance|Název instance čítače.|
|Kategorie|Název kategorie čítače.|
|Počítač|Název počítače, do kterého je shromažďovánčí čítač.|
|Barvy|Barva čáry v grafu.|
|Rozsah|Označuje číslo, které je v grafu pro tento čítač reprezentováno číslem 100. Například pro oblast, jejíž horní hodnota je 10 000, popisek 100 v horní části grafu představuje 10 000.|
|Minimum|Označuje minimální hodnotu čítače v milisekundách.|
|Maximum|Označuje maximální hodnotu čítače v milisekundách.|
|Avg|Označuje průměrnou hodnotu čítače v milisekundách.|
|Poslední|Zobrazuje hodnotu čítače během posledního intervalu vzorkování v milisekundách.|

## <a name="tasks"></a>Úlohy

|Úlohy|Přidružená témata|
|-|-|
|**Přizpůsobení grafů pomocí legendy:** Legenda zobrazení Grafy zobrazuje informace pro každý čítač výkonu, který je přidružen k grafu. Legendu můžete použít k odebrání čítačů výkonu, zvýraznění čítačů výkonu v grafu a přizpůsobení možností vykreslování.|-   [Použití legendy zobrazení grafů k analýze zátěžových testů](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Čítače zobrazení v grafech:** Do grafu výsledků zátěžového testu můžete přidat různé druhy dat umístěním čítačů do grafu.|-   [Postup: Přidání a odstranění čítačů v grafech](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Přiblížení grafů:** Po dokončení zátěžového testu můžete pomocí pruhů přiblížení přiblížit a posunout se do oblasti grafu. Přiblížením můžete zkontrolovat data, která byla generována během spuštění zátěžového testu v jemnějších detailech.|-   [Postup: Přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Dlaždice grafy:** Grafy výsledků zátěžových testů můžete uspořádat v libovolném z několika vzorů. Můžete dlaždicově uspořádat až čtyři grafy.||
|**Vytvořit vlastní grafy:** Můžete navrhnout grafy, které zobrazují konkrétní informace o výsledcích zátěžových testů. Vlastní graf navrhnete zadáním čítačů zátěžového testu, které se zobrazí v grafu.|-   [Postup: Vytvoření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Exportujte data čítačů výkonu v grafu:** Data grafu můžete exportovat do aplikace Microsoft Excel pomocí tlačítka **Exportovat data grafu do aplikace Excel** na panelu nástrojů Load Test **Analyzer,** když jste v zobrazení **Grafy.**||

## <a name="related-tasks"></a>Související úlohy

[Analýza výsledků zátěžových testů a chyb v zobrazení tabulek](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

[Postup: Přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)

[Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Viz také

- [Postup: Přidání a odstranění čítačů v grafech](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Postup: Vytvoření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Postup: Přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
