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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75584488"
---
# <a name="load-test-results-summary-overview"></a>Přehled souhrnu výsledků zátěžového testu

Po spuštění zátěžového testu můžete zobrazit souhrn zátěžového testu, abyste pochopili výsledky rychle. Souhrn zátěžového testu poskytuje klíč jako výsledek kompaktního a snadno čitelného formátu. Můžete také vytisknout souhrn zátěžového testu. To usnadňuje použití při komunikaci výsledků se zúčastněnými stranami. Souhrn zátěžového testu je také výchozím zobrazením při otevření výsledků zátěžového testu z dříve spuštěného zátěžového testu. Další informace najdete v tématu [Postup: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md).

![Souhrnné zobrazení](../test/media/ltest_summaryview.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="the-load-test-summary"></a>Souhrn zátěžového testu

Souhrn zátěžového testu je rozdělen na oddíly. Úvodní oddíly se zobrazí v horní části souhrnu a jsou vždy viditelné. Při zobrazení souhrnu zátěžového testu jsou nejprve následující položky:

- Informace o testovacím běhu

- Celkové výsledky

- Klíčová Statistika: nejčastější 5 nejpomalejších stránek

- Klíčová Statistika: Top 5 nejpomalejších testů

- Klíčová Statistika: nejčastějších 5 nejpomalejších operací SQL

    > [!NOTE]
    > Oddíl operace SQL se zobrazí pouze v případě, že je v rámci zátěžového testu povoleno trasování SQL.

Uzavírací oddíly se zobrazí na konci souhrnu a můžete je sbalit, aby se ušetřilo místo. Na konci souhrnu zátěžového testu se zobrazí následující položky:

- Výsledky testů

- Výsledky stránky

- Výsledky transakce

- Systém v rámci testovacích zdrojů

- Prostředky kontroleru a agentů

- Chyby

## <a name="test-run-information"></a>Informace o testovacím běhu

Část informace o testovacím běhu obsahuje obecné informace o běhu, včetně názvu testu, času zahájení a ukončení a kontroler, který test spustil. Tato část obsahuje také volitelný popis běhu, který přidáte při spuštění zátěžového testu.

## <a name="overall-results"></a>Celkové výsledky

Oddíl celkových výsledků obsahuje souhrnné výsledky testu, včetně počtu požadavků za sekundu, celkového počtu neúspěšných žádostí, průměrné doby odezvy a průměrného času stránky.

## <a name="key-statistic-top-5-slowest-pages"></a>Klíčová Statistika: nejčastější 5 nejpomalejších stránek

Oddíl nejpomalejších stránek obsahuje nejvyšších 5 nejpomalejších stránek v zátěžovém testu. Pro každou stránku se zobrazí adresa URL a Průměrná doba načítání stránky. Stránky jsou uvedeny v sestupném pořadí. Můžete vybrat adresu URL stránky a otevřít tabulku **stránky** a zkontrolovat další podrobnosti této stránky. Další informace najdete v tématu [Postup: zobrazení odpovědi na webovou stránku](../test/how-to-view-web-page-response-time-in-a-load-test.md).

Hodnota percentilu pro **95% stránku doba stránky (sekundy)** , která byla dokončena za méně než tuto dobu v sekundách, je 95% ze stránek.

## <a name="key-statistic-top-5-slowest-tests"></a>Klíčová Statistika: Top 5 nejpomalejších testů

Oddíl nejpomalejších testů obsahuje horních 5 nejpomalejších testů v zátěžovém testu. Pro každý test se zobrazí název testu a Průměrná doba testování. Testy jsou uvedeny v sestupném pořadí. Můžete zvolit název testu a otevřít tabulku **testů** a zkontrolovat další podrobnosti pro tento test. Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

Hodnota percentilu pro sestavu **95% doby testování (sekundy)** , že 95% testů bylo dokončeno za méně než tuto dobu v sekundách.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Klíčová Statistika: nejčastějších 5 nejpomalejších operací SQL

Pokud je v zátěžovém testu povoleno trasování SQL, obsahuje oddíl nejpomalejších dotazů prvních 5 nejpomalejších dotazů v zátěžovém testu. Pro každý test se zobrazí název operace a doba trvání. Doba trvání se zobrazuje v mikrosekundách (SQL Server 2005) nebo v milisekundách (SQL Server 2000 a starší). Testy jsou uvedeny v sestupném pořadí podle doby trvání. Můžete zvolit název operace pro otevření tabulky **trasování SQL** a zkontrolovat další podrobnosti pro tuto operaci. Další informace najdete v [tabulce dat trasování SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Výsledky testů

Část výsledky testu obsahuje seznam všech testů a scénářů v zátěžovém testu. Název testu, scénáře, počet pokusů o spuštění, počet neúspěšných pokusů a zobrazený průměrný čas testu. Můžete zvolit název testu a otevřít tabulku **testů** a zkontrolovat další podrobnosti pro tento test. Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tuto část můžete sbalit a rozbalit výběrem šipky nalevo od názvu oddílu.

## <a name="page-results"></a>Výsledky stránky

Část výsledky stránky obsahuje seznam všech webových stránek v rámci zátěžového testu. Adresa URL, scénář, název testu, průměrný čas stránky a počet se zobrazí. Můžete vybrat adresu URL stránky a otevřít tabulku **stránky** a zkontrolovat další podrobnosti této stránky. Další informace najdete v tématu [Postup: zobrazení odpovědi na webovou stránku](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Tuto část můžete sbalit a rozbalit výběrem šipky nalevo od názvu oddílu.

## <a name="transaction-results"></a>Výsledky transakce

Část výsledky transakce obsahuje seznam všech transakcí v rámci zátěžového testu. Zobrazí se název transakce, scénář, test, doba odezvy, uplynulý čas a počet. Můžete zvolit název transakce a otevřít tabulku **transakcí** a zkontrolovat další podrobnosti pro tuto transakci. Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tuto část můžete sbalit a rozbalit výběrem šipky nalevo od názvu oddílu.

Hodnoty percentilu vykazují následující informace o transakci:

- 90% celkových transakcí bylo dokončeno za méně než \<time> sekund.

- 95% celkových transakcí bylo dokončeno za méně než \<time> sekund.

## <a name="system-under-test-resources"></a>Systém v rámci testovacích zdrojů

Část systém v části zdroje testu obsahuje seznam počítačů, které jsou sadou cílových počítačů, pro které se generuje zátěž. To zahrnuje všechny počítače, ze kterých shromažďujete sady čítačů kromě agenta nebo řadiče. Zobrazí se název počítače, čas procesoru a dostupná paměť. Můžete zvolit název počítače pro otevření **systému v rámci testovacího** grafu a využití prostředků v průběhu času. Další informace naleznete v tématu [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Tuto část můžete sbalit a rozbalit výběrem šipky nalevo od názvu oddílu.

## <a name="controller-and-agent-resources"></a>Prostředky kontroleru a agentů

Část řadiče a prostředky agenta obsahuje seznam počítačů, které se používají ke spuštění testu. Zobrazí se název počítače, čas procesoru a dostupná paměť. Můžete zvolit název počítače a otevřít tak graf **kontroleru a agentů** a podívat se na využití prostředků v průběhu času. Další informace naleznete v tématu [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Tuto část můžete sbalit a rozbalit výběrem šipky nalevo od názvu oddílu.

## <a name="errors"></a>Chyby

Oddíl Errors obsahuje seznam všech chyb, ke kterým došlo během zátěžového testu. Zobrazí se typ a podtyp chyby, počet a poslední zpráva. Můžete zvolit chybu a otevřít tabulku **chyby** a zkontrolovat další podrobnosti o této chybě. Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Tuto část můžete sbalit a rozbalit výběrem šipky nalevo od názvu oddílu.

## <a name="print-a-summary"></a>Tisk souhrnu

Souhrn zátěžového testu lze vytisknout výběrem možnosti **Tisk** v místní nabídce souhrnu. Náhled tisku můžete nejdřív zobrazit tak, že v místní nabídce na souhrnu zvolíte **Tisk náhledu** . Můžete také tisknout přímo z obrazovky náhledu.

## <a name="see-also"></a>Viz také

- [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
