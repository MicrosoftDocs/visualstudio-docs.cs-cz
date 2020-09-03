---
title: Analýza Výsledky testů zatížení
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9300dd1ebeaee9d87d2527dbc49fa66e319970c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591226"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analýza výsledků zátěžového testu pomocí analyzátoru zátěžového testu

Při použití **analyzátoru zátěžového testu**můžete najít kritická místa, identifikovat chyby a měřit vylepšení aplikace.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analyzovat výsledky zátěžového testu následujícími způsoby:

- Monitorujte zátěžový test, když je spuštěn.

- Analyzovat zátěžový test po jeho dokončení.

- Zobrazit výsledky z předchozího zátěžového testu.

Můžete také vytvořit sestavy, které porovnávají dvě nebo více sestav pro analýzu trendů a sdílejte je se zúčastněnými stranami. Viz [výsledky testů zatížení vytváření sestav pro porovnání testů nebo analýzy trendů](../test/compare-load-test-results.md).

Tyto úlohy lze dokončit bez ohledu na to, zda spustíte zátěžový test z Visual Studio Enterprise nebo z příkazového řádku a zda spustíte zátěžový test na jednom nebo na vzdáleném počítači.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Rozdíly mezi analýzou běžícího a dokončeného zátěžového testu

Při spuštění zátěžového testu se **analyzátor zátěžového testu** zobrazí na samostatné kartě společně s názvem zátěžového testu a časem spuštění testu (například **LOADTEST1 [12:40 PM]**). Při spuštění zátěžového testu je menší sada dat čítače výkonu udržována v paměti. Tuto sadu dat můžete monitorovat při spuštění zátěžového testu. Po dokončení zátěžového testu můžete analyzovat kompletní sadu dat z databáze. Existují rozdíly v tom, jaká data se zobrazí při spuštění zátěžového testu a jaká data lze vidět po dokončení zátěžového testu. Například údaje o době odezvy 90% a 95% nejsou vypočítány, dokud se zátěžový test nedokončí. K určitým rozdílům dochází také ve funkcích nástrojů, které jsou k dispozici pro analýzu dat.

Při spuštění zátěžového testu jsou k dispozici dvě zobrazení: zobrazení **grafů** a zobrazení **tabulek** . Zobrazení **grafů** umožňuje shromažďovat shromažďované čítače výkonu. V zobrazení **tabulky** získáte informace o jednotlivých testech, stránkách, transakcích a požadavcích, které jsou shromažďovány. Zobrazí se také tabulka, která obsahuje seznam chyb.

Ve výchozím nastavení se po dokončení zátěžového testu zobrazí **souhrnné** zobrazení. Můžete přepínat mezi zobrazeními **Souhrn**, **grafy**, **tabulky**a **Podrobnosti** pomocí panelu nástrojů. **Analyzátor zátěžového testu** lze ukotvit nebo nastavit na hodnotu float pomocí obvyklých technik manipulace s oknem sady Visual Studio. Při analýze dokončených běhů zátěžového testu lze současně otevřít více **analyzátorů zátěžových testů** pro porovnání různých běhů zátěžového testu.

## <a name="tasks"></a>Úlohy

|Úlohy|Přidružená témata|
|-|-|
|**Přístup k výsledkům zátěžového testu:** Při spuštění zátěžového testu z Editor zátěžového testu se výsledky zátěžového testu otevřou automaticky a spuštěný test zatížení se zobrazí v **analyzátoru zátěžového testu**.|-   [Postupy: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)|
|**Přidejte poznámky k analýze pro zátěžový test:** Můžete přidat komentáře k zátěžovým testům při provádění analýz. Komentáře jsou trvale uloženy spolu s výsledkem zátěžového testu. Popis, který zadáte, se také zobrazí ve sloupci **Popis** , který je přidružený k zátěžového testu, v dialogovém okně **otevřít a spravovat výsledky testů** v Editor zátěžového testu.<br /><br /> Další informace najdete v tématu [Postup: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Kromě toho se komentáře zobrazí při vytváření sestavy aplikace Excel pro výsledky zátěžového testu.<br /><br /> Další informace naleznete v tématu [výsledky testů zátěžových testů pro porovnání testů nebo analýzy trendů](../test/compare-load-test-results.md).||
|**Analýza výsledků zátěžového testu:** Po přístupu k datům spuštění zátěžového testu můžete analyzovat výsledná data. Můžete zobrazit souhrn zátěžového testu a rychle porozumět výsledkům. Souhrn zátěžového testu zobrazuje výsledky klíče v kompaktním a snadno čitelném formátu.<br /><br /> Můžete vytisknout souhrn zátěžového testu. To usnadňuje použití při komunikaci výsledků se zúčastněnými stranami.<br /><br /> Podrobnosti o výsledcích zátěžového testu můžete analyzovat pomocí grafů a tabulek ve výsledcích. Mezi ně patří **chyby**, **stránky**, **požadavky**, **trasování SQL**, **testy**, **prahové hodnoty**a **transakce**.|-   [Přehled souhrnu výsledků zátěžového testu](../test/load-test-results-summary-overview.md)<br />-   [Postupy: zobrazení odpovědi na webovou stránku](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analýza aktivity virtuálních uživatelů ve výsledcích zátěžového testu pro izolaci potíží s výkonem:** Graf aktivity virtuálního uživatele můžete použít k vizualizaci toho, co virtuální uživatelé provádějí během zátěžového testu. To vám může přispět k izolaci špičky v procesoru nebo poklesu požadavků/s a určení, které testy nebo stránky běží během těchto Špičk a poklesu.|-   [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
