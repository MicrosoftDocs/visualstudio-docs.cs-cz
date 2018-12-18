---
title: Analýza výsledků zátěžových testů v zobrazení grafů analyzéru zátěžového testu
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9c635d3a2c21d1ab84feca285c8cea8eb2aac68f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895077"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů v zobrazení grafů Analyzéru zátěžového testu

Výsledky zátěžového testu se zobrazí jako data v několika různých podoken.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li zobrazit výsledky testů jako grafy, zvolte **grafy** na **zátěžový test** nástrojů. Každé jednotlivé grafu se zobrazí v panelu s názvem grafu zobrazí v horní části stránky v rozevíracím seznamu. K zobrazení různých graf na panelu, vyberte název jiného grafu ze seznamu.

Až čtyři grafu lze zobrazit panely najednou. Můžete přepínat mezi jiný panel rozložení pomocí **panelové rozložení** tlačítka panelu nástrojů.

Jsou k dispozici několik předdefinovaných grafy. Můžete použít předdefinované grafů, jako je nebo je můžete přizpůsobit. Kromě toho můžete vytvořit vlastní grafy. Další informace najdete v tématu [postupy: Přidání a odstranění čítačů pro grafy](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) a [postupy: vytváření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Integrované grafy

V následující tabulce jsou uvedeny předdefinované grafy, které jsou k dispozici k analýze výsledků zátěžového testu.

|Název grafu|Popis|
|-|-|
|Klíčoví ukazatelé|Čítače, které popisují základní aspekty testování výkonu, jako je například uživatelské zatížení, propustnost a dobu odezvy.|
|Doba odezvy testu|Data o množství času testy provést, aby spustil.|
|Doba odezvy stránky|Průměrná doba odezvy pro webové stránky, které jsou přístupné během zátěžového testu.|
|Testovaný systém|Informace o počítačích, na kterých aplikace právě testováno spuštění. To zahrnuje data o využití paměti, procesoru, fyzického disku, procesy.<br /><br /> Ve výchozím nastavení se shromažďují pouze čítače Počet MB k dispozici a času procesoru.|
|Kontrolér a agenti|Informace o počítačích, na kterých zátěžové testy spustit. To zahrnuje data o využití paměti, procesoru, fyzického disku, procesy.<br /><br /> Ve výchozím nastavení jenom počet MB k dispozici a se shromažďují čítače času procesoru.|
|Doba odezvy transakce|Průměrná doba odezvy pro transakce prováděné během zátěžového testu.|

 Různé čítače lze zobrazit v grafu v době běhu a po spuštění testu.

> [!NOTE]
> Pouze čítače výkonu doby odpovědi lze přidat do grafu automaticky generované odpovědi čas.

 Informace o čítači zobrazí v grafu i v legendě pod grafy. Můžete také přiblížíte části grafu. Další informace najdete v tématu [postupy: přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Zobrazí v grafech čítače

 Zobrazení grafů *čítače*. Čítače odkazovat na data shromážděná během zátěžového testu, jako jsou například testy za sekundu nebo průměrnou testovacího času. Další informace o čítačích najdete v tématu [určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

 Legenda pro čítače, které jsou zobrazeny v grafu zobrazí několik sloupců užitečné údaje o spuštění zátěžového testu. Chcete-li vypnout zobrazení všech dat v grafu, zrušte zaškrtnutí políčka v řádku v legendě.

 Legenda obsahuje následující sloupce:

|Čítač|Název čítače|
|-|-|
|instance|Název instance čítače.|
|Kategorie|Název kategorie čítače.|
|Počítače|Název počítače, do které se shromažďují čítače.|
|Barva|Barva čáry v grafu.|
|Rozsah|Označuje číslo, která je reprezentována 100 v grafu pro tento čítač. Pro rozsah, jejíž horní hodnota je 10 000 operací, například 100 popisek v horní části grafu představuje 10 000.|
|min|Určuje minimální hodnotu pro čítač v milisekundách.|
|maximální počet|Určuje maximální hodnotu pro čítač v milisekundách.|
|Průměr|Označuje průměrná hodnota čítače v milisekundách.|
|poslední|Uvádí hodnotu čítače během posledního intervalu vzorkování v milisekundách.|

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-|
|**Přizpůsobit grafy pomocí legendy:** zobrazení The grafů legendy zobrazuje informace pro každý čítač výkonu, který je spojen s grafem. Legendu můžete odebrat čítače výkonu, čítače výkonu v grafu zvýraznit a přizpůsobení možností zobrazování.|-   [Použití legendy zobrazení grafů k analýze zátěžových testů](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Zobrazit čítače v grafech:** přidáte různé druhy dat k zátěžovému testu výsledků graf tak, že čítače v grafu.|-   [Postupy: Přidání a odstranění čítačů pro grafy](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Přiblížit na grafy:** po dokončení zátěžového testu můžete použít přiblížení pruhy pro přiblížení či posune do oblasti grafu. Podle přiblížit, můžete zkoumat data, která byla vygenerována během spuštění jemnější podrobně zátěžového testu.|-   [Postupy: přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Rozložení grafů vedle sebe:** můžete uspořádat grafy výsledků zátěžového testu v některém z několika způsoby. Až čtyři grafy můžete dlaždici.||
|**Vytváření vlastních grafů:** můžete navrhovat grafy, které zobrazí konkrétní informace o výsledcích zátěžového testu. Navrhněte vlastní graf tak, že zadáte počítadla testu zatížení, které se zobrazí grafu.|-   [Postupy: vytváření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Exportovat data čítače výkonu v grafu:** můžete exportovat data grafu do aplikace Microsoft Excel s použitím **exportovat Data grafu do aplikace Excel** tlačítko **Analyzéru zátěžového testu** nástrojů při nacházíte **grafy** zobrazení.||

## <a name="related-tasks"></a>Související úlohy

 [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

 [Postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md)

 [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Viz také:

- [Postupy: Přidání a odstranění čítačů pro grafy](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Postupy: vytváření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Postupy: přiblížení oblasti grafu](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)