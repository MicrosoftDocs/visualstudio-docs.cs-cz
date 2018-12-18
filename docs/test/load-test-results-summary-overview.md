---
title: Přehled souhrnu výsledků zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3f5187aabeb0c8e2ef81b0c6b6883b96590d7005
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062606"
---
# <a name="load-test-results-summary-overview"></a>Přehled souhrnu výsledků zátěžového testu

Po spuštění zátěžového testu můžete zobrazit souhrn zátěžového testu rychle porozumět výsledky. Souhrn zátěžového testu poskytuje klíče výsledky kompaktní a snadno přečíst formátu. Můžete také vytisknout souhrnem zátěžového testu. Je to vhodné pro použití při komunikaci výsledky účastníkům. Souhrn zátěžového testu je také výchozí zobrazení při otevření výsledku zátěžového testu z dříve spuštěném zátěžovém testu. Další informace najdete v tématu [postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md).

![Souhrnné zobrazení](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Souhrn zátěžového testu

Souhrn zátěžového testu je rozdělený do částí. Počáteční části se zobrazí v horní části přehledu a jsou vždycky viditelná. Při zobrazení shrnutí testu zatížení jsou první následující položky:

- Informace o testovacím běhu

- Celkové výsledky

- Klíčová Statistika: Top 5 Nejpomalejších stránek

- Klíčová Statistika: Top 5 Nejpomalejších Tesů

- Klíčová Statistika: Top 5 Nejpomalejších SQL operací

    > [!NOTE]
    > V části SQL operací se zobrazí jenom v případě, že je povoleno trasování SQL v zátěžovém testu.

Pravé části na konci souhrn se zobrazí a mohou být sbalena pro úsporu místa. Na konci souhrnem zátěžového testu se zobrazí následující položky:

- Výsledky testů

- Výsledky stránky

- Výsledky transakce

- Systém pod správou zdrojů testu

- Řadič a Agent prostředky

- Chyby

## <a name="test-run-information"></a>Testovací běh informace

Testovací běh část s informacemi o obsahuje obecné informace o daném spuštění, včetně názvu testu, počáteční a koncové časy a kontroler, který spustil test. Tato část také obsahuje volitelný popis spuštění, které můžete přidat při spuštění zátěžového testu.

## <a name="overall-results"></a>Celkové výsledky

Celkové výsledky část obsahuje souhrnné výsledky testů, včetně počtu požadavků za sekundu, celkový počet neúspěšných žádostí, Průměrná doba odezvy a doby Průměrná doba načtení stránky.

## <a name="key-statistic-top-5-slowest-pages"></a>Klíčová Statistika: 5 nejpomalejších stránek

Nejpomalejší stránky obsahuje top 5 nejpomalejších stránek v zátěžovém testu. Adresa URL a dobou načítání Průměrná doba načtení stránky se zobrazí pro každou stránku. Na stránkách jsou uvedeny v sestupném pořadí. Můžete také adresa URL stránky otevřete **stránky** tabulky a kontrolovat další podrobnosti pro danou stránku. Další informace najdete v tématu [postupy: zobrazení webové stránky odpovědi](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Hodnota percentilu **95 % doba stránky (sek)** hlásit, že 95 % stránek dokončit za méně než tento časový interval v sekundách.

## <a name="key-statistic-top-5-slowest-tests"></a>Klíčová Statistika: 5 nejpomalejších Tesů

Nejpomalejší testy oddíl obsahuje nejčastější 5 nejpomalejších tesů v zátěžovém testu. Název testu a průměrný čas testu se zobrazí pro každý test. Testy jsou uvedeny v sestupném pořadí. Můžete použít název testu, otevřete **testy** tabulky a prozkoumejte další podrobnosti pro tento test. Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Hodnota percentilu **95 % doby testu (sek)** hlásit, že 95 % testů dokončeno za méně než tento časový interval v sekundách.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Klíčová Statistika: 5 nejpomalejších SQL operací Top

Pokud je povoleno trasování SQL v zátěžovém testu, nejpomalejší dotazy oddíl obsahuje nejčastější dotazy 5 nejpomalejších v zátěžovém testu. Pro každý test se zobrazí název operace a dobu trvání. Zobrazí se doba trvání v mikrosekundách (SQL Server 2005) nebo v milisekundách (SQL Server 2000 a starší). Testy jsou uvedeny v sestupném pořadí podle doby trvání. Můžete použít název operace otevřít **trasování SQL** tabulky a prozkoumejte další podrobnosti pro danou operaci. Další informace najdete v tématu [tabulka dat trasovacího SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Výsledky testů

Část výsledky testu obsahuje seznam všech testů a scénáře v zátěžovém testu. Název testu, scénář, počet pokusů, které došlo ke spuštění, počet pokusů, které došlo k selhání a průměrný čas testu se zobrazí. Můžete použít název testu, otevřete **testy** tabulky a prozkoumejte další podrobnosti pro tento test. Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Můžete sbalit a kliknutím na šipku nalevo od názvu oddílu rozbalením tohoto oddílu.

## <a name="page-results"></a>Výsledky stránky

Výsledky stránky obsahuje seznam všech webové stránky v zátěžovém testu. Adresa URL, scénář, název testu, Průměrná doba načtení stránky čas a počty jsou zobrazeny. Můžete také adresa URL stránky otevřete **stránky** tabulky a kontrolovat další podrobnosti pro danou stránku. Další informace najdete v tématu [postupy: zobrazení webové stránky odpovědi](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Můžete sbalit a kliknutím na šipku nalevo od názvu oddílu rozbalením tohoto oddílu.

## <a name="transaction-results"></a>Výsledky transakce

Výsledky transakce obsahuje seznam všech transakcí v zátěžovém testu. Název transakce, scénář, test, doby odezvy, uplynulý čas a počty jsou zobrazeny. Můžete použít název transakce, otevřete **transakce** tabulky a zkontrolujte podrobnosti u dané transakce. Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Můžete sbalit a kliknutím na šipku nalevo od názvu oddílu rozbalením tohoto oddílu.

Hodnoty percentilu sestava následující informace o transakci:

-   Dokončili jste 90 % z celkového počtu transakcí v méně než \<čas > sekund.

-   95 % z celkového počtu transakcí byly dokončeny v méně než \<čas > sekund.

## <a name="system-under-test-resources"></a>Systém pod správou zdrojů testu

Systém části zdroje testu obsahuje seznam počítačů, které podporují sadu cílových počítačů, pro které se generuje zatížení. To zahrnuje všechny počítače, ze kterého budete shromažďovat sady čítačů, než Agent nebo kontroler. Název počítače, % času procesoru a paměti k dispozici jsou zobrazeny. Můžete použít název počítače, otevřete **zkoušený systém** grafů a zobrazení využití prostředků v průběhu času. Další informace najdete v tématu [výsledků zátěžového testu analyzovat v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Můžete sbalit a kliknutím na šipku nalevo od názvu oddílu rozbalením tohoto oddílu.

## <a name="controller-and-agent-resources"></a>Řadič a agent prostředků

Řadič a agent oddíl prostředků obsahuje seznam počítačů, které se používají ke spuštění testu. Název počítače, % času procesoru a paměti k dispozici jsou zobrazeny. Můžete použít název počítače, otevřete **řadiče a agentů** grafů a zobrazení využití prostředků v průběhu času. Další informace najdete v tématu [výsledků zátěžového testu analyzovat v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Můžete sbalit a kliknutím na šipku nalevo od názvu oddílu rozbalením tohoto oddílu.

## <a name="errors"></a>Chyby

V oddílu chyby obsahuje seznam všech chyb, ke kterým došlo během zátěžového testu. Zobrazí se typ a podtyp chyby, počty a poslední zprávy. Můžete také otevřít chybu **chyby** tabulky a prozkoumejte další podrobnosti pro danou chybu. Další informace najdete v tématu [Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Můžete sbalit a kliknutím na šipku nalevo od názvu oddílu rozbalením tohoto oddílu.

## <a name="print-a-summary"></a>Tisk souhrn

Souhrn zátěžového testu můžete vytisknout výběrem **tisk** v místní nabídce na souhrn. Můžete zobrazit náhled tisku první volbou **Náhled** v místní nabídce na souhrn. Můžete také vytisknout přímo z obrazovky ve verzi preview.

## <a name="see-also"></a>Viz také:

- [Analýza překročení mezních pravidel](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)