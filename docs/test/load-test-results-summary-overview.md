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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7df3324c2182c376cb9547a4192fca3e601b3dd5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584488"
---
# <a name="load-test-results-summary-overview"></a>Souhrn výsledků zátěžových testů

Po spuštění zátěžového testu můžete zobrazit souhrn zátěžového testu, abyste rychle pochopili výsledky. Souhrn zátěžového testu poskytuje klíčové výsledky v kompaktním a snadno čitelném formátu. Můžete také vytisknout souhrn zátěžového testu. To umožňuje pohodlné použití při sdělování výsledků zúčastněným stranám. Souhrn zátěžového testu je také výchozí zobrazení při otevření výsledku zátěžového testu z dříve spuštěného zátěžového testu. Další informace naleznete v [tématu How to: Access load test results for analysis](../test/how-to-access-load-test-results-for-analysis.md).

![Souhrnné zobrazení](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Souhrn zátěžového testu

Souhrn zátěžového testu je rozdělen do oddílů. Počáteční oddíly se zobrazí v horní části souhrnu a jsou vždy viditelné. Při zobrazení souhrnu zátěžového testu jsou nejprve následující položky:

- Informace o testovacím běhu

- Celkové výsledky

- Klíčová statistika: 5 nejpomalejších stránek

- Klíčová statistika: Top 5 Nejpomalejší testy

- Klíčová statistika: Top 5 Nejpomalejší sql operace

    > [!NOTE]
    > Část Operace SQL se zobrazí pouze v případě, že je v zátěžovém testu povoleno trasování SQL.

Uzavírací oddíly se zobrazí na konci souhrnu a mohou být sbaleny, aby se ušetřilo místo. Na konci souhrnu zátěžového testu jsou zobrazeny následující položky:

- Výsledky testů

- Výsledky stránky

- Výsledky transakcí

- Systém pod testováním zdrojů

- Prostředky řadiče a agenta

- chyby

## <a name="test-run-information"></a>Informace o zkušebním běhu

Část s informacemi o spuštění testu obsahuje obecné informace o spuštění, včetně názvu testu, počátečního a koncového času a řadiče, který test spustil. Tato část také obsahuje volitelný popis spuštění, které přidáte při spuštění zátěžového testu.

## <a name="overall-results"></a>Celkové výsledky

Část s celkovými výsledky obsahuje souhrnné výsledky testu včetně počtu požadavků za sekundu, celkového počtu neúspěšných požadavků, průměrné doby odezvy a průměrného času stránky.

## <a name="key-statistic-top-5-slowest-pages"></a>Klíčová statistika: 5 nejpomalejších stránek

Nejpomalejší sekce stránek obsahuje prvních 5 nejpomalejších stránek v zátěžovém testu. Pro každou stránku se zobrazí adresa URL a průměrná doba načítání stránky. Stránky jsou uvedeny v sestupném pořadí. Můžete zvolit adresu URL stránky, chcete-li otevřít tabulku **Stránky** a zkontrolovat další podrobnosti o této stránce. Další informace naleznete v [tématu How to: View web page response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Hodnota percentilu pro **95 % času stránky (s)** hlásí, že 95 % stránek bylo dokončeno za méně než tentokrát v sekundách.

## <a name="key-statistic-top-5-slowest-tests"></a>Klíčová statistika: Top 5 nejpomalejších testů

Nejpomalejší testovací sekce obsahuje prvních 5 nejpomalejších testů v zátěžovém testu. Název testu a průměrná doba testu jsou zobrazeny pro každý test. Testy jsou uvedeny v sestupném pořadí. Můžete zvolit název testu otevřít tabulku **Testy** a zkontrolovat další podrobnosti pro tento test. Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Hodnota percentilu pro **95 % doba testování (s)** hlásí, že 95 % testů bylo dokončeno za méně než tentokrát v sekundách.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Klíčová statistika: Top 5 nejpomalejších operací SQL

Pokud je v zátěžovém testu povoleno trasování SQL, nejpomalejší dotazobsahuje nejpomalejší dotazy v zátěžovém testu. Název operace a doba trvání jsou zobrazeny pro každý test. Doba trvání je zobrazena v mikrosekundách (SQL Server 2005) nebo v milisekundách (SQL Server 2000 a starší). Testy jsou uvedeny v sestupném pořadí podle doby trvání. Můžete zvolit název operace otevřít tabulku **trasování SQL** a zkontrolovat další podrobnosti pro tuto operaci. Další informace naleznete [v tabulce dat trasování SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Výsledky testu

Část s výsledky testů obsahuje seznam všech testů a scénářů v zátěžovém testu. Název testu, scénář, počet jeho spuštění, počet neúspěšných a průměrná doba testu. Můžete zvolit název testu otevřít tabulku **Testy** a zkontrolovat další podrobnosti pro tento test. Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tento oddíl můžete sbalit a rozbalit výběrem šipky vlevo od názvu oddílu.

## <a name="page-results"></a>Výsledky stránky

Část s výsledky stránky obsahuje seznam všech webových stránek v zátěžovém testu. Zobrazí se adresa URL, scénář, název testu, průměrný čas stránky a počet. Můžete zvolit adresu URL stránky, chcete-li otevřít tabulku **Stránky** a zkontrolovat další podrobnosti o této stránce. Další informace naleznete v [tématu How to: View web page response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Tento oddíl můžete sbalit a rozbalit výběrem šipky vlevo od názvu oddílu.

## <a name="transaction-results"></a>Výsledky transakce

Část s výsledky transakce obsahuje seznam všech transakcí v zátěžovém testu. Název transakce, scénář, test, doba odezvy, uplynulý čas a počet jsou zobrazeny. Můžete zvolit název transakce otevřít tabulku **Transakce** a zkontrolovat další podrobnosti pro tuto transakci. Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tento oddíl můžete sbalit a rozbalit výběrem šipky vlevo od názvu oddílu.

Hodnoty percentilu vykazují následující informace o transakci:

- 90 % z celkového počtu transakcí \<bylo dokončeno za méně než čas> sekund.

- 95 % z celkového počtu transakcí \<bylo dokončeno za méně než čas> sekund.

## <a name="system-under-test-resources"></a>Systém pod zkouškou zdrojů

Část Testovaná část prostředků obsahuje seznam počítačů, které jsou sadou cílových počítačů, pro které je generováno zatížení. To zahrnuje všechny počítače, ze kterých shromažďujete sady čítačů jiné než agent nebo řadič. Zobrazí se název počítače, % času procesoru a dostupné paměti. Můžete zvolit název počítače pro otevření **systému** v části Test grafu a zobrazit využití prostředků v průběhu času. Další informace naleznete [v tématu Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Tento oddíl můžete sbalit a rozbalit výběrem šipky vlevo od názvu oddílu.

## <a name="controller-and-agent-resources"></a>Prostředky řadiče a agenta

Část prostředků řadiče a agenta obsahuje seznam počítačů, které se používají ke spuštění testu. Zobrazí se název počítače, % času procesoru a dostupné paměti. Můžete zvolit název počítače pro otevření **grafu Řadič a agenti** a zobrazit využití prostředků v průběhu času. Další informace naleznete [v tématu Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Tento oddíl můžete sbalit a rozbalit výběrem šipky vlevo od názvu oddílu.

## <a name="errors"></a>chyby

Část chybobsahuje seznam všech chyb, ke kterým došlo během zátěžového testu. Zobrazí se typ a podtyp chyby, počet a poslední zpráva. Můžete zvolit chybu pro otevření tabulky **Chyby** a zkontrolujte další podrobnosti o této chybě. Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tento oddíl můžete sbalit a rozbalit výběrem šipky vlevo od názvu oddílu.

## <a name="print-a-summary"></a>Tisk souhrnu

Souhrn zátěžového testu můžete vytisknout tak, že v souhrnu zvolíte **Tisk** v místní nabídce. Náhled tisku můžete nejprve zobrazit tak, že v místní nabídce v souhrnu zvolíte **Náhled.** Můžete také tisknout přímo z obrazovky náhledu.

## <a name="see-also"></a>Viz také

- [Analyzovat porušení pravidel prahových hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
