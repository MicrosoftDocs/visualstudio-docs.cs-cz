---
title: Analýza výsledků a chyb zátěžového testu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565172"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů a chyb v zobrazení Tabulek analyzátoru zátěžového testu

Při zobrazení výsledků spuštění zátěžového testu můžete zobrazit různá podokna, která poskytují různé způsoby analýzy dat. Data můžete zobrazit jako graf, abyste viděli, jak se v průběhu času mění, nebo můžete data zobrazit jako podrobné tabulky.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li přepnout do zobrazení tabulky, zvolte **Tabulky** na panelu nástrojů **zátěžového testu.** Chcete-li přepínat mezi různými tabulkami, použijte rozevírací seznam **Tabulka** na panelu nástrojů nad mřížkou tabulky. V zobrazení tabulky můžete zobrazit až čtyři tabulky najednou. Další informace naleznete v [tématu Dlaždice zatížení testovací tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) v tomto tématu.

Většina číselných hodnot zobrazených v tabulce pro čítače výkonu se sčítají po celou dobu spuštění zátěžového testu. Sloupce s názvem **Poslední** jsou výjimkou a představují hodnotu z posledního intervalu vzorkování.

> [!NOTE]
> Sloupce s názvem **Poslední** jsou k dispozici pouze při provádění zátěžového testu. Po dokončení zátěžového testu tyto sloupce nejsou k dispozici.

Většinu tabulek můžete seřadit výběrem názvu sloupce, podle kterého chcete řadit. Ve výchozím nastavení se v některých tabulkách nezobrazují všechny dostupné sloupce. Pokud jsou sloupce k dispozici, můžete do tabulek přidat sloupce. Chcete-li přidat sloupce, klepněte pravým tlačítkem myši na tabulku a pak zvolte **Přidat nebo odebrat sloupce**.

> [!NOTE]
> Data z tabulky můžete zkopírovat do jiných aplikací, například do aplikace Excel, pro další analýzu.

## <a name="the-load-test-tables"></a>Tabulky zátěžových testů

V následující tabulce jsou uvedeny tabulky, které jsou k dispozici pro analýzu spuštění zátěžových testů.

|Název tabulky|Popis|
|-|-|
|chyby|Zobrazí seznam chyb, ke kterým došlo během spuštění zátěžového testu. Další informace naleznete v [tabulce Chyby](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) v tomto tématu a [Analýza výsledků zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Stránky|Zobrazí seznam stránek, ke které se přistupuje během spuštění zátěžového testu. Některá data v této tabulce jsou k dispozici pouze po dokončení zátěžového testu. Další informace naleznete v [tématu How to: View web page response](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Žádosti|Zobrazí podrobnosti pro jednotlivé požadavky vydané během zátěžového testu. To zahrnuje všechny požadavky HTTP a závislé požadavky, jako jsou obrázky. Další informace naleznete v [tabulce Požadavky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) v tomto tématu.|
|Trasování SQL|Zobrazí výsledky trasování SQL. Tato tabulka je k dispozici pouze po dokončení zátěžového testu a pouze v případě, že trasování SQL byla použita během testu. Další informace naleznete v [tabulce dat trasování SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) v tomto tématu.|
|Testy|Zobrazí podrobnosti pro jednotlivé testy spuštěné během zátěžového testu. Další informace naleznete v [tabulce Testy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) v tomto tématu.|
|Prahové hodnoty|Zobrazí seznam porušení pravidel prahové hodnoty, ke kterým došlo během spuštění zátěžového testu. Další informace naleznete v [tématu Analýza porušení pravidel prahové hodnoty](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakce|Zobrazí seznam transakcí, ke kterým došlo během spuštění zátěžového testu. Další informace naleznete v [tabulce Transakce](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) v tomto tématu.|
|Agenti|Zobrazí se pouze v případě, že zátěžový test používá testovací řadič a testovací agenty. Zobrazí seznam agentů, které byly použity během spuštění zátěžového testu. Tabulka Agenti obsahuje počet požadavků testovaného agenta a těchto požadavků, kolik se nezdařilo. Kromě toho agenti tabulka obsahuje počet testů v kombinaci testů zatížení, které testovaný agent a ty, kolik se nezdařilo.|
|Podrobnosti testu|Zobrazí podrobnosti o testech obsažených v testovací směsi pro zátěžový test. Podrobnosti zahrnují název testu, scénář, ve který byl test, čas, kdy byl test spuštěn, dobu, po kterou byl test spuštěn, a výsledek testu označující, zda test prošel nebo selhal. Pokud se test nezdařil, ve sloupci **Podrobnosti** je k dispozici odkaz. Můžete zvolit odkaz, který vás přenese do editoru testů výkonnosti webu se zvýrazněným neúspěšným požadavkem.|

## <a name="collect-percentile-data"></a>Shromažďování dat percentilu

Některé tabulky zátěžového testu mohou obsahovat další sloupce, které obsahují data percentilu a doby odezvy rozdělené do skupin na základě emulace sítě. Ve výchozím nastavení nejsou tato data shromažďována. Data percentilu jsou k dispozici pouze při ukládání výsledků do databáze, nikoli při místním uložení. Další informace naleznete [v tématu Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md). Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** konkrétní uzel nastavení spuštění, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku StatisticsOnly** nebo **AllIndividualDetails**. Další informace naleznete v [tématu How to: View web page response](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Tabulka Požadavky

Tabulka **Požadavky** zobrazuje podrobnosti pro jednotlivé požadavky vydané během zátěžového testu. To zahrnuje všechny požadavky HTTP a závislé požadavky, jako jsou obrázky. Tabulka uvádí požadavky podle testu a scénáře, protože jeden požadavek může být zahrnut do mnoha testů a scénářů.

V následující tabulce jsou **uvedeny** sloupce v tabulce Požadavky:

|Sloupec|Popis|Viditelné ve výchozím nastavení|
|-|-|-|
|**Požadavek**|Adresa URL požadavku. Například *home.html*nebo *orange-arrow.gif*.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Test**|Název testu.|Ano|
|**Celkem**|Celkový počet tohoto požadavku na test výkonu webu vydaný během spuštění zátěžového testu. Celkový počet zahrnuje předané a neúspěšné požadavky, ale neobsahuje požadavky uložené v mezipaměti, protože nejsou vydány na webový server.|Ano|
|**Předán**|Počet, kolikrát byl požadavek vydán a předán.|Ne|
|**Failed**|Počet, kolikrát byl požadavek vydán a selhal. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete zvolit libovolný hypertextový odkaz a zobrazit seznam jednotlivých chyb v dialogovém okně **Chyby zátěžového testu.** Další informace naleznete v [tématu Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ano|
|**Mezipaměti**|Celkový počet, kolikrát byl požadavek již uložen do mezipaměti.|Ne|
|**Požadavky/s**|Rychlost za sekundu požadavku během spuštění zátěžového testu.|Ne|
|**Předáno/s**|Rychlost za sekundu tohoto požadavku během spuštění zátěžového testu pro instance tohoto požadavku, který prošel.|Ne|
|**Nezdařilo se/s**|Rychlost za sekundu tohoto požadavku během spuštění zátěžového testu pro instance tohoto požadavku, které se nezdařily.|Ne|
|**Čas prvního bajtu**|Průměrná doba pro příjem prvního bajtu odpovědi měřená od okamžiku odeslání požadavku na webový server. Jednotky jsou vteřiny.|Ne|
|**Doba odezvy**|Průměrná doba pro příjem celé odpovědi na požadavek měřená od okamžiku odeslání požadavku na webový server. Jednotky jsou vteřiny.|Ano|
|**Délka obsahu**|Průměrná délka obsahu odpovědi na požadavek. Jednotky jsou bajty.|Ano|

## <a name="the-tests-table"></a>Tabulka Testy

Tabulka **Testy** zobrazuje podrobnosti pro jednotlivé testy spuštěné během zátěžového testu. Tabulka uvádí testy podle testu a scénáře, protože jeden test může být zahrnut a v mnoha scénářích.

V následující tabulce jsou uvedeny sloupce v tabulce **Testy.**

|Sloupec|Popis|Viditelné ve výchozím nastavení|
|-|-|-|
|**Test**|Název testu.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Celkem**|Celkový počet spuštění testu ve scénáři. To zahrnuje počet, kolikrát test prošel a selhal.|Ano|
|**Předán**|Počet spuštění testu ve scénáři a předání.|Ano|
|**Failed**|Počet spuštění testu ve scénáři a selhání. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete zvolit libovolný hypertextový odkaz a zobrazit seznam jednotlivých chyb v dialogovém okně **Chyby zátěžového testu.** Další informace naleznete v [tématu Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ano|
|**Testy/s**|Rychlost za sekundu testu během spuštění zátěžového testu.|Ano|
|**Předáno/s**|Rychlost za sekundu tohoto testu během spuštění zátěžového testu pro instance tohoto testu, který prošel.|Ne|
|**Nezdařilo se/s**|Rychlost za sekundu tohoto testu během spuštění zátěžového testu pro instance tohoto testu, které se nezdařily.|Ne|
|**Zkušební čas**|Průměrná doba pro spuštění testu během spuštění zátěžového testu. Jednotky jsou vteřiny.|Ano|
|**90% zkušební doba**|90. hodnota percentilu pro zkušební čas.|Ne|
|**95% zkušební doba**|95. hodnota percentilu pro zkušební čas.|Ano|
|**Požadavky/test**|Průměrný počet požadavků v testu, pokud se jedná o test výkonu webu.|Ne|

## <a name="the-transactions-table"></a>Tabulka Transakce

Tabulka **Transakce** zobrazuje seznam transakcí, ke kterým došlo během spuštění zátěžového testu. Transakce odkazují buď na transakce definované v testu výkonu webu, nebo časovače definované v testu částí. Transakce neodkazuje na databázové transakce.

V následující tabulce jsou uvedeny sloupce v tabulce **Transakce.**

> [!NOTE]
> Chcete-li zobrazit všechny sloupce, musíte povolit vlastnost Úložiště podrobností časování, která je přidružena k aktivnímu nastavení spuštění. Další informace naleznete v [tématu Postup: Zadejte vlastnost Úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Sloupec|Popis|Viditelné bez podrobností časování|
|-|-|-|
|**Transakce**|Název transakce.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Test**|Název testu.|Ano|
|**Celkem**|Celkový počet transakcí vydaných během spuštění zátěžového testu.|Ano|
|**Čas transakce**|Čas pro provedení transakce během spuštění zátěžového testu. Pro testy výkonu webu je do výpočtu zahrnut čas přemýšlení. Jednotky jsou vteřiny.|Ne|
|**Doba odezvy**|Doba odezvy pro transakci testu výkonu webu v spuštění zátěžového testu. Doba odezvy se liší od doby transakce v době odezvy nezahrnuje žádné myšlenky, ke kterým došlo během transakce. Jednotky jsou vteřiny.|Ne|
|**Ave. Čas transakce**|Průměrná doba transakce. Tato doba zahrnuje myšlenkové časy. Například pokud máte tři požadavky a každý má čas přemýšlení, tato doba bude zahrnovat tyto časy přemýšlení a skutečný čas pro provádění požadavků.|Ne|
|**Ave. Doba odezvy**|Průměrná doba odezvy pro transakci testu výkonu webu v spuštění zátěžového testu. Doba odezvy se liší od doby transakce v době odezvy nezahrnuje žádné myšlenky, ke kterým došlo během transakce. Jednotky jsou vteřiny.|Ne|
|**Min doba odezvy**|To nezahrnuje doby vymyšlení.|Ne|
|**Maximální doba odezvy**|To nezahrnuje doby vymyšlení.|Ne|
|**Medián doby odezvy**|To nezahrnuje doby vymyšlení.|Ne|
|**90% doba odezvy**|90. hodnota percentilu pro transakční čas. To nezahrnuje doby vymyšlení. **Poznámka:**  To se liší od Visual Studio Team System 2008 Test Load Agent, který používal **90 % hodnota transakční čas.**|Ne|
|**95% doba odezvy**|95. hodnota percentilu pro transakční čas. To nezahrnuje doby vymyšlení. **Poznámka:**  To se liší od Visual Studio Team System 2008 Test Load Agent, který používal **95 % hodnota transakční čas.**|Ne|
|**99% doba odezvy**|99. hodnota percentilu pro transakční čas. To nezahrnuje doby vymyšlení.|Ne|
|**Doba odezvy std dev**|To nezahrnuje doby vymyšlení.|Ne|

## <a name="the-errors-table"></a>Tabulka Chyby

Při spuštění zátěžového testu můžete analyzovat chyby, ke kterým dochází. Analýza chyb a úprava testů jsou důležitou součástí procesu zátěžového testu. Pokud došlo k chybám, zobrazí se na stavovém řádku zátěžového testu hypertextový odkaz **na chyby** a určuje počet chyb, ke kterým došlo. Chcete-li zobrazit tabulku chyb, zvolte hypertextový odkaz.

Tabulka chyb seskupuje chyby, ke kterým došlo během zátěžového testu podle typu a podtypu chyby. V tabulce je také **celkový** řádek, který určuje celkový počet všech chyb, ke kterým došlo.

Tabulka chyb obsahuje následující sloupce:

|Sloupec|Popis|Při výchozím nastavení viditelné|
|-|-|-|
|Typ|Typ chyby. Například HttpError.|Ano|
|Podtypu|Podtyp chyby. Například LoadTestException.|Ano|
|Počet|Počet chyb tohoto typu, ke kterým došlo během zátěžového testu. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete zvolit libovolný hypertextový odkaz a zobrazit seznam jednotlivých chyb.|Ano|
|Poslední zpráva|Zpráva popisující chybu Například 404 - NotFound.|Ano|

Další informace naleznete v [tématu Práce s tabulkami zátěžových testů](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Přechod k podrobnostem seznamu chyb

Tabulka chyb seskupuje chyby podle typu a podtypu chyby. Chcete-li zobrazit tabulku jednotlivých chyb, zobrazí se dialogové okno **Chyby zátěžového testu.** Chcete-li dialogové okno zobrazit, zvolte hypertextový odkaz ve sloupci **Počet** tabulky chyb. Dialogové okno můžete také zobrazit tak, že klepnete pravým tlačítkem myši na řádek v tabulce chyb, která je naplněna, a výběrem **možnosti Chyby**.

> [!NOTE]
> Jsou shromažďovány pouze prvních 1 000 instancí libovolného typu chyby a kombinace podtypů. Když zobrazíte dialogové okno **Chyby zátěžového testu,** uvidíte maximálně prvních 1 000 instancí, které se chyby.

Tabulka **Chyby zátěžového testu** obsahuje následující sloupce:

|Sloupec|Popis|
|-|-|
|**Čas**|Čas během zátěžového testu, kdy došlo k chybě.|
|**Agent**|Název počítače agenta, ve kterém došlo k chybě. To je důležité při spuštění zátěžových testů pomocí testovacích řadičů a testovacích agentů. Další informace naleznete v [tématu Instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Název testu výkonu webu, ve kterém došlo k chybě.|
|**Scénář**|Název scénáře, ve kterém došlo k chybě.|
|**Požadavek**|Adresa URL požadavku, ve kterém došlo k chybě.|
|**Typ**|Typ chyby. Například HttpError.|
|**Podtypu**|Podtyp chyby. Například LoadTestException.|
|**Text**|Text chybové zprávy. Například 404 - NotFound.|
|**Zásobník**|Položky v tomto sloupci jsou prázdné nebo je slovo **Zásobník** formátováno jako hypertextový odkaz. Můžete zvolit hypertextový odkaz pro zobrazení trasování zásobníku chyby.|
|**Podrobnosti**|Položky v tomto sloupci jsou prázdné nebo je slovo **TestLog** formátováno jako hypertextový odkaz. Tento odkaz vám může pomoci izolovat chyby v zátěžovém testu. Například výběrodkazu **TestLog** na webové maty testu výkonu otevře výsledky testu výkonu webu v prohlížeči výsledků testu výkonnosti webu a zvýrazní chybu požadavku.|

> [!NOTE]
> Tabulku můžete seřadit výběrem záhlaví sloupců.

## <a name="the-sql-trace-data-table"></a>Tabulka dat trasování SQL

Můžete shromažďovat data trasování SQL během spuštění zátěžového testu k pozdější analýze. Shromažďování dat trasování umožňuje identifikovat nejpomalejší spuštěné dotazy a uložené procedury v databázi SQL Server, která je testována.

Pokud je povoleno trasování SQL, vytvoří se během spuštění zátěžového testu soubor, který obsahuje data trasování. Tato data jsou automaticky uložena v úložišti výsledků zátěžového testu na konci testovacího běhu a trasovací soubor se odstraní. Po dokončení zátěžového testu analyzujete data trasování v tabulce **trasování SQL.**

### <a name="to-view-sql-trace-data"></a>Zobrazení dat trasování SQL

1. V analyzátoru zátěžového testu zvolte **tabulky** na panelu nástrojů, abyste se ujistili, že je zobrazena mřížka tabulky.

2. V rozevíracím seznamu **Tabulka** vyberte **možnost Trasování SQL**.

3. Data trasování, která byla shromážděna během spuštění, se zobrazí v mřížce. Tabulka uvádí nejpomalejší spuštěné operace SQL seřazené podle doby trvání, přičemž nejpomalejší je nahoře. Obvykle **duration** sloupec je první sloupec zkoumat. Data se zobrazí v milisekundách.

   Zobrazené sloupce jsou následující:

    - **Třída události**

    - **Doba trvání**

    - **Cpu**

    - **Čte**

    - **Píše**

    - **TextData**

    - **Starttime**

    - **Endtime**

   Pokud chcete trasovat jiné události SQL než data identifikovaná v těchto sloupcích, můžete nastavit vlastní trasování SQL pomocí nástroje SQL Profiler, odděleného od sady Visual Studio.

## <a name="tile-load-test-tables"></a>Tabulky zátěžových testů dlaždic

Při zobrazení výsledků spuštění zátěžového testu můžete zobrazit data jako podrobné tabulky. Chcete-li přepnout do zobrazení tabulky, zvolte **Tabulky** na panelu nástrojů **zátěžového testu.** K dispozici jsou tabulky **Chyby**, **Stránky**, **Požadavky**, **Trasování SQL**, **Testy**, **Prahové hodnoty**a **Transakce**. Další informace naleznete v [tématu Práce s tabulkami zátěžových testů](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

V zobrazení tabulky můžete zobrazit až čtyři tabulky najednou, aniž by se tabulky překrývaly.

### <a name="to-tile-tables"></a>Dlaždice tabulek

1. Na panelu nástrojů **Analyzátor zatížení testu** zvolte **Tabulky**.

     Otevře se zobrazení tabulky. Výchozí rozložení jsou dva vodorovné panely.

2. Na panelu nástrojů **Load Test Analyzer** zvolte tlačítko **rozložení** a pak zvolte jednu z následujících možností:

    - **Jeden panel**

    - **Dva vodorovné panely**

    - **Tři vodorovné panely**

    - **Čtyři vodorovné panely**

3. Chcete-li přepínat mezi různými tabulkami, použijte rozevírací seznam nad mřížkou tabulky v jednotlivých panelech.

    > [!NOTE]
    > Stejnou tabulku nelze zobrazit ve více než jednom panelu. Pokud změníte tabulku zobrazenou na jednom panelu na tabulku, která je již zobrazena na jiném panelu, tabulky přepínají panely.

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postup: Přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)
- [Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analyzovat porušení pravidel prahových hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Souhrn výsledků zátěžových testů](../test/load-test-results-summary-overview.md)
