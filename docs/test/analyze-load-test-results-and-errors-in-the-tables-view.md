---
title: Analýza výsledků zátěžových testů a chyb
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e337c30a4b6a08f123ef7ee33dee704e9412de
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565172"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů a chyb v tabulkovém zobrazení Analyzéru zátěžového testu

Při zobrazení výsledků spuštění zátěžového testu můžete zobrazit různých podoken, které vám nabízí různé způsoby, jak analyzovat data. Data můžete zobrazit jako graf, chcete-li zobrazit změny v průběhu času, nebo můžete zobrazit data jako podrobné tabulky.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li přepnout do zobrazení tabulky, zvolte **tabulky** na **zátěžový test** nástrojů. Chcete-li přepnout mezi jednotlivými tabulkami, použijte **tabulky** rozevíracího seznamu na panelu nástrojů nad mřížku tabulky. V zobrazení tabulky můžete zobrazit až čtyři tabulky v čase. Další informace najdete v tématu [dlaždice zátěžového testu tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) v tomto tématu.

Většina číselné hodnoty, které se zobrazují v tabulce pro čítače výkonu jsou kumulativní přes celou zátěžového testu. Sloupce s názvem **poslední** představují výjimku a představovat hodnotu od posledního intervalu vzorkování.

> [!NOTE]
> Sloupce s názvem **poslední** jsou k dispozici pouze tehdy, když je spuštěn zátěžový test. Po dokončení zátěžového testu nejsou k dispozici tyto sloupce.

Výběrem názvu sloupce, které chcete řadit můžete seřadit většinu tabulky. Ve výchozím nastavení nezobrazují některé tabulky všech dostupných sloupců. Sloupce můžete přidat do tabulek, pokud jsou k dispozici sloupce. Přidání sloupce, klikněte pravým tlačítkem na tabulku a pak zvolte **Přidat/odebrat sloupce**.

> [!NOTE]
> Zkopírovat data z tabulky do jiných aplikací, jako je například aplikace Excel pro další analýzy.

## <a name="the-load-test-tables"></a>Tabulky zátěžového testu

Následující tabulka obsahuje seznam tabulek, které jsou k dispozici k analýze zátěžových testů.

|Název tabulky|Popis|
|-|-|
|Chyby|Zobrazí seznam chyb, ke kterým došlo během zátěžového testu. Další informace najdete v tématu [tabulka The chyby](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) v tomto tématu a [výsledky zátěžového testu analyzovat](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Stránky|Zobrazí seznam stránek přístup při spuštění zátěžového testu. Některá data v této tabulce je k dispozici, až po dokončení zátěžového testu. Další informace najdete v tématu [postupy: zobrazení webové stránky odpovědi](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Požadavky|Zobrazí podrobnosti pro jednotlivé požadavky vydané během zátěžového testu. To zahrnuje všechny požadavky HTTP a závislé požadavky, jako jsou obrázky. Další informace najdete v tématu [tabulky The Requests](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) v tomto tématu.|
|Trasování SQL|Zobrazí výsledky trasování jazyka SQL. Tato tabulka je k dispozici, až po dokončení zátěžového testu a pouze v případě, že během testu byl použit trasování jazyka SQL. Další informace najdete v tématu [tabulka dat trasovacího SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) v tomto tématu.|
|Testy|Zobrazí podrobnosti pro jednotlivé testy spuštěny během zátěžového testu. Další informace najdete v tématu [testy tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) v tomto tématu.|
|Mezní hodnoty|Zobrazí seznam mezních pravidel, ke kterým došlo během zátěžového testu. Další informace najdete v tématu [analýza mezních pravidel](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakce|Zobrazí seznam transakcí, ke kterým došlo během spuštění zátěžového testu. Další informace najdete v tématu [The transakcí](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) v tomto tématu.|
|Agenti|Zobrazí jenom v případě, že je váš zátěžový test pomocí testovacího kontroléru a testovacích agentů. Zobrazí seznam agentů, které byly použity při spuštění zátěžového testu. Agenti tabulka uvádí, kolik požadavků agenta otestovali a získali těchto požadavků, kolik se nezdařilo. Kromě toho agentů tabulka obsahuje počet testů, které v kombinaci testů testy zatížení, který agent a z nich, kolik se nezdařilo.|
|Podrobnosti o testu|Zobrazí podrobnosti pro testy obsažené v poměru testů zátěžového testu. Podrobnosti zahrnují název testu, scénář, který byl test, čas spuštění testu, délku doba trvání test spuštěn a výsledek testu, která Pokud test úspěšný nebo neúspěšný. Pokud se test nezdařil, je k dispozici v odkazu **podrobnosti** sloupce. Můžete zvolit odkaz, kterým se dostanete do editoru testu výkonnosti webu s neúspěšným požadavkem zvýrazní.|

## <a name="collect-percentile-data"></a>Shromažďovat data pro percentil

Některé tabulky testu zatížení může obsahovat další sloupce, které zahrnují percentil dat a doby odezvy rozdělen do skupin podle emulace sítě. Ve výchozím nastavení tato data nejsou shromažďována. Zobrazení dat je k dispozici pouze při ukládání výsledků do databáze, a ne při uložení místně. Další informace najdete v tématu [výsledků zátěžového testu Správa v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md). Kromě toho pro shromažďování těchto dat v **editoru zátěžových testů**v části **parametrů běhu** uzlu, vyberte konkrétní spuštění uzlu nastavení změnit. V **vlastnosti** okně pro **úložiště podrobností časování** vlastnosti, vyberte **StatisticsOnly** nebo **AllIndividualDetails**. Další informace najdete v tématu [postupy: zobrazení webové stránky odpovědi](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Tabulka požadavků

**Požadavky** tabulka obsahuje podrobnosti pro jednotlivé požadavky vydané během zátěžového testu. To zahrnuje všechny požadavky HTTP a závislé požadavky, jako jsou obrázky. V tabulce jsou uvedeny požadavky testu a scénář, protože jeden požadavek může být součástí mnoho testů a scénáře.

V následující tabulce jsou uvedeny ve sloupcích v **požadavky** tabulky:

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|**Požadavek**|Adresa URL požadavku. Například *home.html*, nebo *orange arrow.gif*.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Test**|Název testu.|Ano|
|**Celkem**|Celkový počet tento požadavek testu výkonnosti webu vydanou v průběhu zátěžového testu spusťte. Celkový počet zahrnuje úspěšné i neúspěšné požadavky, ale nezahrnuje žádosti uložené v mezipaměti, protože nejsou vysílány webovému serveru.|Ano|
|**Předaný**|Počet pokusů požadavku byl vystaven a předán.|Ne|
|**Se nezdařilo**|Počet pokusů požadavku byl vystaven a se nezdařilo. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete použít libovolný hypertextového odkazu pro zobrazení jednotlivých chyb v seznamu **chyby zátěžového testu** dialogové okno. Další informace najdete v tématu [výsledky zátěžového testu analyzovat](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ano|
|**Uložit do mezipaměti**|Celkový počet pokusů, které se již v mezipaměti požadavku.|Ne|
|**Počet požadavků za sekundu**|Sazba za sekundu žádosti při spuštění zátěžového testu.|Ne|
|**Předaný za sekundu**|Sazba za sekundu během zátěžového testu, pro instance této žádosti, který předá tento požadavek.|Ne|
|**Za sekundu**|Sazba za sekundu tohoto požadavku během zátěžového testu, pro instance této žádosti, která selhala.|Ne|
|**Čas prvního bajtu**|Průměrná doba pro přijetí prvního bajtu odpovědi, měřená od okamžiku, kdy byla vyslána žádost webovému serveru. Jednotky jsou sekund.|Ne|
|**Doba odezvy**|Průměrná doba pro přijetí celou odpověď na žádost, měřená od okamžiku, kdy byla vyslána žádost webovému serveru. Jednotky jsou sekund.|Ano|
|**Délka obsahu**|Průměrná délka obsahu odpovědi na požadavek. Jednotky jsou bajtů.|Ano|

## <a name="the-tests-table"></a>V tabulce testy

**Testy** tabulka obsahuje podrobnosti pro jednotlivé testy spuštěny během zátěžového testu. V tabulce jsou uvedeny testy podle testu a scénář, protože jeden test lze zahrnout mnoho scénářů.

V následující tabulce jsou uvedeny ve sloupcích v **testy** tabulky.

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|**Test**|Název testu.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Celkem**|Celkový počet, kolikrát byl spuštěn test ve scénáři. Jedná se o počet, kolikrát test předaný a se nezdařilo.|Ano|
|**Předaný**|Počet pokusů, test byl spuštěny ve scénáři a předán.|Ano|
|**Se nezdařilo**|Počet pokusů, test byl spuštěny ve scénáři a selhal. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete použít libovolný hypertextového odkazu pro zobrazení jednotlivých chyb v seznamu **chyby zátěžového testu** dialogové okno. Další informace najdete v tématu [výsledky zátěžového testu analyzovat](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ano|
|**Testy za sekundu**|Sazba za sekundu testu při spuštění zátěžového testu.|Ano|
|**Předaný za sekundu**|Sazba za sekundu během zátěžového testu, pro instance tohoto testu, který předá tento test.|Ne|
|**Za sekundu**|Sazba za sekundu během zátěžového testu pro instance tohoto testu, který se nepodařilo spustit tento test.|Ne|
|**Čas testu**|Průměrná doba pro spuštění testu při spuštění zátěžového testu. Jednotky jsou sekund.|Ano|
|**90 % testovacího času**|90. percentil hodnoty pro čas testu.|Ne|
|**95 % testovacího času**|95. percentil hodnoty pro čas testu.|Ano|
|**Požadavky a testování**|Průměrný počet požadavků v testu, pokud je výkon webového testu.|Ne|

## <a name="the-transactions-table"></a>Tabulka transakcí

**Transakce** tabulka uvádí seznam transakcí, ke kterým došlo během spuštění zátěžového testu. . Transakce odkazují buď transakce definované v testu výkonnosti webu, nebo na časovače definované v rámci testu jednotek. Transakce neodkazuje na transakce databáze.

V následující tabulce jsou uvedeny ve sloupcích v **transakce** tabulky.

> [!NOTE]
> Chcete-li zobrazit všechny sloupce, je nutné povolit vlastnost úložiště podrobností časování, která je spojena s aktivní parametr spuštění. Další informace najdete v tématu [postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Sloupec|Popis|Zobrazuje bez podrobnosti časování|
|-|-|-|
|**Transakce**|Název transakce.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Test**|Název testu.|Ano|
|**Celkem**|Celkový počet transakcí vystavených během zátěžového testu.|Ano|
|**Čas transakce**|Je čas ke spuštění transakce při spuštění zátěžového testu. Pro testy výkonnosti webu, myslíte, že čas spadá do výpočtu. Jednotky jsou sekund.|Ne|
|**Doba odezvy**|Doba odezvy pro transakce webového testu výkonu v spuštění zátěžového testu. Doba odezvy se liší od doby transakce v tom, že doba odezvy nezahrnuje žádné zvažte čas, ke které došlo během transakce. Jednotky jsou sekund.|Ne|
|**Ave. Transaction – čas**|Průměrná doba transakce. Tento čas zahrnuje čas přemýšlení. Například pokud máte tři požadavky a každý má čas přemýšlení, tentokrát budou zahrnovat tyto časy přemýšlení a vyžaduje skutečný čas ke spuštění.|Ne|
|**Ave. doba odezvy**|Průměrná doba odezvy pro transakce webového testu výkonu ve spuštění zátěžového testu. Doba odezvy se liší od doby transakce v tom, že doba odezvy nezahrnuje žádné zvažte čas, ke které došlo během transakce. Jednotky jsou sekund.|Ne|
|**Minimální doba odezvy**|To nezahrnuje čas přemýšlení.|Ne|
|**Maximální doba odezvy**|To nezahrnuje čas přemýšlení.|Ne|
|**Medián doby odezvy**|To nezahrnuje čas přemýšlení.|Ne|
|**90 % doby odezvy**|90. percentil hodnoty pro čas transakce. To nezahrnuje čas přemýšlení. **Poznámka:** tím se liší od Visual Studio Team System 2008 testu zatížení Agent, který používá **90 % času transakce** hodnotu.|Ne|
|**95 % doby odezvy**|95. percentil hodnoty pro čas transakce. To nezahrnuje čas přemýšlení. **Poznámka:** tím se liší od Visual Studio Team System 2008 testu zatížení Agent, který používá **95 % doby transakce** hodnotu.|Ne|
|**99 % doby odezvy**|Úrovni 99. percentil hodnoty pro čas transakce. To nezahrnuje čas přemýšlení.|Ne|
|**Směrodatná odchylka doby odezvy**|To nezahrnuje čas přemýšlení.|Ne|

## <a name="the-errors-table"></a>V tabulce chyb

Při spuštění zátěžového testu můžete analyzovat chyby, ke kterým dochází. Analýza chyb a nastavení testů jsou důležitou součástí procesu testu zatížení. Pokud došlo k chybám, **chyby** hypertextového odkazu se zobrazí ve stavovém řádku testu zatížení a určuje počet chyb, ke kterým došlo. Zobrazit tabulku chyby, zvolte hypertextový odkaz.

Chyby tabulky skupiny chyb, ke kterým došlo během zátěžového testu s typem a podtypem chyby. K dispozici je také **celkový** řádek v tabulce, který určuje celkový počet všech chyb, ke kterým došlo.

Chyby tabulka obsahuje následující sloupce:

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|Type|Typ chyby. Například HttpError.|Ano|
|SubType|Podtyp chybu. Například LoadTestException.|Ano|
|Počet|Číslo chyby tohoto typu, ke které došlo během zátěžového testu. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete použít libovolný hypertextový odkaz, chcete-li zobrazit seznam jednotlivých chyb.|Ano|
|Poslední zpráva|Zpráva popisující chybu Například 404 - NotFound.|Ano|

Další informace najdete v tématu [práce s tabulkami testu zatížení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Potom přejít na seznam chyb

Chyby tabulky skupiny chyb podle typu a podtyp chyby. Chcete-li zobrazit tabulku jednotlivých chyb, zobrazí **chyby zátěžového testu** dialogové okno. Chcete-li zobrazit dialogové okno, zvolte hypertextový odkaz v **počet** sloupec tabulky chyb. Můžete také zobrazit dialogové okno kliknutím pravým tlačítkem řádek v tabulce chyb, který je vyplněný a zvolíte **chyby**.

> [!NOTE]
> Jsou shromažďovány pouze prvních 1 000 instancí libovolnou kombinaci typem a podtypem chyby. Při zobrazení **chyby zátěžového testu** dialogové okno, zobrazí se maximálně prvních 1 000 instancí tuto chybu.

**Chyby zátěžového testu** tabulka obsahuje následující sloupce:

|Sloupec|Popis|
|-|-|
|**čas**|Doba během zátěžového testu na kterém došlo k chybě.|
|**Agent**|Název počítače agenta, na kterém došlo k chybě. To je důležité, když spustíte zátěžové testování pomocí testovacích kontrolérů a testovacích agentů. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Název webového testu v kterém došlo k chybě.|
|**Scénář**|Název scénáře, ve kterém došlo k chybě.|
|**Požadavek**|Adresa URL požadavku, ve kterém došlo k chybě.|
|**Typ**|Typ chyby. Například HttpError.|
|**Podtyp**|Podtyp chybu. Například LoadTestException.|
|**Text**|Text chybové zprávy. Například 404 - NotFound.|
|**Zásobník**|Položky v tomto sloupci jsou buď prázdná, nebo slovo **zásobníku** je formátován jako hypertextový odkaz. Můžete použít hypertextového odkazu pro zobrazení trasování zásobníku pro chybu.|
|**Podrobnosti**|Položky v tomto sloupci jsou buď prázdná, nebo slovo **TestLog** je formátován jako hypertextový odkaz. Tento odkaz můžete izolovat chyby v zátěžovém testu. Například výběr **TestLog** odkaz na žádost chyby webové výkonnosti testu se otevřou se výsledky testu výkonnosti webu v prohlížeči výsledků testování webového výkonu a zvýraznit Chyba žádosti.|

> [!NOTE]
> Seřadí tabulku kliknutím na záhlaví sloupců.

## <a name="the-sql-trace-data-table"></a>Tabulka dat trasování SQL

Během spuštění k analýze později zátěžového testu lze shromažďovat data trasování SQL. Shromažďování dat trasování vám umožní identifikovat nejpomaleji spouštění dotazů a uložených procedur v databázi serveru SQL Server, který je právě testováno.

Pokud je povoleno trasování SQL, soubor se vytvoří během zátěžového testu, který obsahuje data trasování. Tato data se automaticky uloží v Store výsledky zátěžového testu na konci testovacího běhu a odstraní se tento soubor trasování. Analýza dat trasování v **trasování SQL** tabulky po dokončení zátěžového testu.

### <a name="to-view-sql-trace-data"></a>Chcete-li zobrazit data trasování SQL

1. V Analyzéru zátěžového testu, zvolte **tabulky** na panelu nástrojů, abyste měli jistotu, že se zobrazí mřížku tabulky.

2. V **tabulky** rozevíracího seznamu vyberte **trasování SQL**.

3. Data trasování, která byla shromážděna během spuštění se zobrazí v mřížce. V tabulce jsou uvedeny nejpomaleji probíhajících operací SQL, seřazené podle doby trvání, se načítají nejpomaleji. v horní části. Obvykle **doba trvání** sloupec je první sloupec prozkoumat. Data se zobrazí v milisekundách.

   Zobrazení sloupců jsou následující:

    - **Event – třída**

    - **Doba trvání**

    - **CPU**

    - **Operace čtení**

    - **Zapíše**

    - **Textové podrobnosti**

    - **startTime**

    - **Koncový čas**

   Pokud chcete trasovat události SQL než data podle těchto sloupců, můžete nastavit vlastní vlastní SQL trasování pomocí nástroje SQL Profiler, odděleně od sady Visual Studio.

## <a name="tile-load-test-tables"></a>Dlaždice zátěžového testu tabulky

Při zobrazení výsledků spuštění zátěžového testu můžete zobrazit data jako podrobné tabulky. Chcete-li přepnout do zobrazení tabulky, zvolte **tabulky** na **zátěžový test** nástrojů. Tabulky, které jsou k dispozici jsou **chyby**, **stránky**, **požadavky**, **trasování SQL**, **testy**,  **Prahové hodnoty**, a **transakce**. Další informace najdete v tématu [práce s tabulkami testu zatížení](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

V zobrazení tabulky můžete zobrazit až čtyři tabulky v čase bez tabulek překrývající se.

### <a name="to-tile-tables"></a>Na dlaždici tabulky

1. Na **Analyzéru zátěžového testu** nástrojů, zvolte **tabulky**.

     Otevře se zobrazení tabulky. Výchozí rozložení je dva vodorovné panely.

2. Na **Analyzéru zátěžového testu** nástrojů, zvolte **rozložení** tlačítko a pak vyberte jednu z následujících možností:

    - **Jeden Panel**

    - **Dva vodorovné panely**

    - **Tři horizontální panely**

    - **Čtyři horizontální panely**

3. Pokud chcete přepnout mezi jednotlivými tabulkami, pomocí rozevíracího seznamu výše mřížku tabulky v jednotlivých panelech.

    > [!NOTE]
    > Ve více než jeden panel nelze zobrazit stejné tabulky. Pokud změníte zobrazí jeden panelu do tabulky již zobrazena v jiného panelu tabulku, přepněte tabulky panelů.

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: přístup k analýze výsledků zátěžového testu](../test/how-to-access-load-test-results-for-analysis.md)
- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analýza překročení mezních pravidel](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Správa výsledků zátěžových testů v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Přehled souhrnu výsledků zátěžového testu](../test/load-test-results-summary-overview.md)
