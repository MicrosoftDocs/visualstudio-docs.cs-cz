---
title: Analýza výsledků zátěžového testu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591226"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů pomocí analyzátoru zátěžového testu

Při použití **analyzátoru zátěžového testu**najděte problémová místa, identifikujte chyby a měřte zlepšení ve vaší aplikaci.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analyzovat výsledky zátěžového testu těmito způsoby:

- Sledujte zátěžový test, když je spuštěn.

- Analyzujte zátěžový test po jeho dokončení.

- Zobrazení výsledků předchozího zátěžového testu.

Můžete také vytvořit sestavy, které porovnávají dvě nebo více sestav pro analýzu trendů a sdílejí je se zúčastněnými stranami. Viz [Vykazování výsledků zátěžových testů pro porovnání testů nebo analýzu trendů](../test/compare-load-test-results.md).

Tyto úlohy můžete dokončit bez ohledu na to, zda spustíte zátěžový test z aplikace Visual Studio Enterprise nebo z příkazového řádku a zda spustíte zátěžový test v jednom počítači nebo ve vzdáleném počítači.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Rozdíly mezi analýzou spuštěného a dokončeného zátěžového testu

Při spuštění zátěžového testu se **analyzátor zátěžového testu** zobrazí na samostatné kartě spolu s názvem zátěžového testu a časem, kdy byl test spuštěn (například **LoadTest1 [12:40 PM]**). Při spuštění zátěžového testu je v paměti udržována menší sada dat čítače výkonu. Tuto sadu dat můžete sledovat při spuštění zátěžového testu. Po dokončení zátěžového testu můžete analyzovat úplnou sadu dat z databáze. Existují rozdíly v tom, jaká data se zobrazí při spuštění zátěžového testu a jaká data můžete zobrazit po dokončení zátěžového testu. Například 90 procent a 95 procent data doby odezvy se nevypočítávají, dokud není dokončen zátěžový test. Některé rozdíly se vyskytují také ve funkčnosti nástrojů, které jsou k dispozici pro analýzu dat.

Při spuštění zátěžového testu jsou k dispozici dvě zobrazení: zobrazení **Grafy** a Zobrazení **tabulek.** Zobrazení **Grafy** umožňuje grafčích čítačů výkonu, které jsou shromažďovány. Zobrazení **Tabulky** poskytuje informace o jednotlivých testech, stránkách, transakcích a požadavcích, které jsou shromažďovány. Získáte také tabulku se seznamem chyb.

Ve výchozím nastavení se po dokončení spuštění zátěžového testu zobrazí **souhrnné** zobrazení. Pomocí panelu nástrojů můžete přepínat mezi zobrazeními **Souhrn**, **Grafy**, **Tabulky**a **Podrobnosti.** **Analyzátor zátěžového testu** lze ukotvit nebo nastavit plovoucí pomocí obvyklých technik manipulace okna sady Visual Studio. Při analýze dokončených spuštění zátěžového testu můžete mít současně otevřené více **analyzátorů zátěžového testu** a porovnat různé spuštění zátěžového testu.

## <a name="tasks"></a>Úlohy

|Úlohy|Přidružená témata|
|-|-|
|**Přístup k výsledkům zátěžového testu:** Při spuštění zátěžového testu z Editoru zátěžového testu se automaticky otevřou výsledky zátěžového testu a průběžný zátěžový test se zobrazí v **analyzátoru zátěžového testu**.|-   [Postup: Přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)|
|**Přidejte poznámky analýzy k zátěžovému testu:** Při provádění analýzy můžete do zátěžového testu přidat komentáře. Komentáře jsou uloženy trvale, spolu s výsledkem zátěžového testu. Popis, který zadáte, se také zobrazí ve sloupci **Popis,** který je přidružen k zátěžovému testu v dialogovém okně **Otevřít a spravovat výsledky testů** v Editoru zátěžového testu.<br /><br /> Další informace naleznete v [tématu How to: Access load test results for analysis](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Komentáře se navíc zobrazí při vytváření sestavy aplikace Excel pro výsledky zátěžového testu.<br /><br /> Další informace naleznete [v tématu Reporting load tests výsledky pro porovnání testů nebo analýzu trendů](../test/compare-load-test-results.md).||
|**Analýza výsledků zátěžového testu:** Po přístupu k datům spuštění zátěžového testu můžete analyzovat výsledná data. Můžete zobrazit souhrn zátěžového testu, abyste rychle porozuměli výsledkům. Souhrn zátěžového testu zobrazuje klíčové výsledky v kompaktním a snadno čitelném formátu.<br /><br /> Souhrn zátěžového testu můžete vytisknout. To umožňuje pohodlné použití při sdělování výsledků zúčastněným stranám.<br /><br /> Můžete analyzovat podrobnosti o výsledcích zátěžového testu pomocí grafů a tabulek ve výsledcích. Patří mezi ně **chyby**, **stránky**, **požadavky**, **trasování SQL**, **testy**, **prahové hodnoty**a **transakce**.|-   [Souhrn výsledků zátěžových testů](../test/load-test-results-summary-overview.md)<br />-   [Postup: Zobrazení odpovědi na webovou stránku](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analýza porušení pravidel prahové hodnoty](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analýza aktivity virtuálního uživatele ve výsledcích zátěžového testu za účelem izoluje problémy s výkonem:** Graf aktivity virtuálního uživatele můžete použít k vizualizaci toho, co virtuální uživatelé dělají během zátěžového testu. To vám může pomoci izolovat špičky v procesoru nebo klesne v požadavcích/s a určit, které testy nebo stránky jsou spuštěny během těchto špičky a kapky.|-   [Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|
