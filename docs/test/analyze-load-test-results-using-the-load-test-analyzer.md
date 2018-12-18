---
title: Analýza výsledků zátěžových testů
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 719163e53b1f8c68850b3f4f211838631a25274a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055605"
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů pomocí Analyzéru zátěžového testu

Nalezení problémových míst, identifikovat chyby a měřit zlepšení ve vaší aplikaci, když použijete **Analyzéru zátěžového testu**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Analýza výsledků zátěžových testů v těchto způsobů:

-   Sledujte zátěžový test, když je spuštěn.

-   Analyzujte test zatížení po jeho dokončení.

-   Zobrazení výsledků z předchozího testu zatížení.

Můžete také vytvořit sestavy, které porovnávají dva nebo více sestav pro analýzu trendů sdílet se zúčastněnými stranami. Zobrazit [sestav zátěžové testy s výsledky pro porovnávání testů a analýzu trendů](../test/compare-load-test-results.md).

Tyto kroky můžete udělat, jestli spuštění zátěžového testu ze sady Visual Studio Enterprise nebo z příkazového řádku a určuje, zda spustit zátěžový test v jednom počítači nebo ve vzdáleném počítači.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Rozdíly mezi analýzy spuštěné a dokončeného zátěžového testu

 Při spuštění zátěžového testu **Analyzéru zátěžového testu** zobrazí na samostatné kartě, společně s názvem vašeho testu zatížení a čas, který byl spuštěn test (třeba **LoadTest1 [12:40 hodin]**). Při běhu zátěžového testu, menší sady dat čítače výkonu se zachová v paměti. Tato sada dat můžete sledovat, při spuštění zátěžového testu. Po dokončení zátěžového testu můžete analyzovat kompletní data z databáze. Existují rozdíly v jaká data se zobrazí, když běží zátěžové testy a co data, která se zobrazí po zátěžového testu byla dokončena. Například 90 až 95 procent data o době odezvy se nevypočítá až do dokončení zátěžového testu. Několik rozdílů dojít také funkčnosti nástroje, které jsou k dispozici, pokud chcete analyzovat data.

 Při spuštění zátěžového testu, jsou k dispozici dvě zobrazení: **grafy** zobrazení a **tabulky** zobrazení. **Grafy** zobrazení vám umožní graf čítače výkonu, které se shromažďují. **Tabulky** zobrazení poskytuje informace o jednotlivých testů, stránek, transakce a požadavky, které byly shromážděny. Získáte také tabulku, která se zobrazí seznam chyb.

 Ve výchozím nastavení po dokončení zátěžového testu **Souhrn** zobrazení. Můžete přepínat mezi **Souhrn**, **grafy**, **tabulky**, a **podrobnosti** zobrazeními pomocí panelu nástrojů. **Analyzéru zátěžového testu** můžete ukotvit nebo nastavit jako plovoucí prvek pomocí obvyklých technik zpracování okno Visual Studio. Při analýze spuštění dokončeného zátěžového testu můžete mít více **zatížení testování analyzátory** otevřít ve stejnou dobu pro porovnání různých zátěžový test běží.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-|
|**Přístup k výsledky zátěžového testu:** při spuštění zátěžového testu z editoru zátěžových testů, výsledky zátěžového testu se automaticky otevře a spuštění zátěžového testu se zobrazí v **Analyzéru zátěžového testu**.|-   [Postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md)|
|**Přidat poznámky analýzy do zátěžového testu:** přidáte komentáře do zátěžového testu při provádění analýzu. Komentáře jsou uloženy trvale, společně s výsledkem zátěžového testu. Popis, který můžete zadat také zobrazí v **popis** sloupec, který je spojen se zátěžovým testem v **otevřít a spravovat výsledky testu** dialogové okno v editoru zátěžového testu.<br /><br /> Další informace najdete v tématu [postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Kromě toho komentáře se zobrazí, když vytváříte sestavu aplikace Excel pro zatížení výsledky testů.<br /><br /> Další informace najdete v tématu [sestav zátěžové testy s výsledky pro porovnávání testů a analýzu trendů](../test/compare-load-test-results.md).||
|**Analýza výsledků zátěžových testů:** po přistupujete ke spuštění data zátěžového testu, můžete analyzovat Výsledná data. Můžete zobrazit souhrn zátěžového testu rychle porozumět výsledky. Souhrn zátěžového testu zobrazí klíčové výsledky ve formátu kompaktní a snadno čtení.<br /><br /> Souhrn zátěžového testu můžete vytisknout. Je to vhodné pro použití při komunikaci výsledky účastníkům.<br /><br /> Podrobnosti o výsledky zátěžového testu můžete analyzovat pomocí grafů a tabulek ve výsledcích. Patří mezi ně **chyby**, **stránky**, **požadavky**, **trasování SQL**, **testy**,  **Prahové hodnoty**, a **transakce**.|-   [Přehled souhrnu výsledků zátěžového testu](../test/load-test-results-summary-overview.md)<br />-   [Postupy: zobrazení webové stránky odpovědi](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analýza mezních pravidel](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analýza aktivity virtuálních uživatelů ve vašich výsledcích zátěžového testu k izolování problémů s výkonem:** graf aktivity virtuálního uživatele můžete použít k vizualizaci, co dělají virtuálních uživatelů během zátěžového testu. To může pomoci izolovat poraďte se špičkami Procesorem nebo výpadky požadavků za sekundu a určit, které testy nebo stránky jsou spuštěny během těchto provozní špičky a drops.|-   [Analýza aktivity virtuálních uživatelů v podrobném zobrazení](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|