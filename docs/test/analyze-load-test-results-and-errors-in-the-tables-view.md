---
title: Analýza Výsledky testů načítání a chyb
description: Naučte se zobrazovat podokna, která poskytují různé způsoby analýzy výsledků zátěžového testu, jako je například graf v čase nebo podrobné tabulky.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.openlocfilehash: 5b501cef5360be08f1b283e9064617b649a33da9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878016"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analýza výsledků zátěžových testů a chyb v zobrazení tabulky analyzátoru zátěžového testu

Když zobrazíte výsledky spuštění zátěžového testu, můžete zobrazit různá podokna, která vám poskytnou různé způsoby analýzy dat. Data můžete zobrazit jako graf, abyste viděli, jak se v průběhu času mění, nebo můžete zobrazit data jako podrobné tabulky.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Chcete-li přepnout na zobrazení tabulky, vyberte možnost **tabulky** na panelu nástrojů **zátěžového testu** . Chcete-li přepínat mezi různými tabulkami, použijte rozevírací seznam **tabulka** na panelu nástrojů nad mřížkou tabulky. V tabulkovém zobrazení můžete najednou zobrazit až čtyři tabulky. Další informace najdete v [tabulkách zátěžových testů dlaždic](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) v tomto tématu.

Většina číselných hodnot zobrazených v tabulce pro čítače výkonu je po celý běh zátěžového testu kumulativní. Sloupce s názvem **Last** jsou výjimkou a představují hodnotu z posledního intervalu vzorkování.

> [!NOTE]
> Sloupce s názvem **Last** jsou k dispozici pouze během provádění zátěžového testu. Po dokončení zátěžového testu nejsou tyto sloupce k dispozici.

Většinu tabulek můžete seřadit tak, že vyberete název sloupce, který chcete seřadit. Ve výchozím nastavení některé tabulky nezobrazují všechny dostupné sloupce. Sloupce můžete přidat do tabulek, pokud jsou sloupce k dispozici. Chcete-li přidat sloupce, klikněte pravým tlačítkem myši na tabulku a zvolte možnost **Přidat nebo odebrat sloupce**.

> [!NOTE]
> Data z tabulky můžete kopírovat do jiných aplikací, jako je například Excel, pro další analýzu.

## <a name="the-load-test-tables"></a>Tabulky zátěžových testů

V následující tabulce jsou uvedeny tabulky, které jsou k dispozici pro analýzu spuštění zátěžového testu.

|Název tabulky|Description|
|-|-|
|Chyby|Zobrazí seznam chyb, ke kterým došlo během běhu zátěžového testu. Další informace naleznete v [tabulce Errors](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) v tomto tématu a v tématu [Analýza výsledků zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Stránky|Zobrazí seznam stránek, které byly během běhu zátěžového testu k dispozici. Některá data v této tabulce jsou k dispozici až po dokončení zátěžového testu. Další informace najdete v tématu [Postup: zobrazení odpovědi na webovou stránku](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Žádosti|Zobrazí podrobnosti o jednotlivých žádostech vydaných během zátěžového testu. To zahrnuje všechny požadavky HTTP a závislé požadavky, jako jsou například obrázky. Další informace najdete v [tabulce požadavky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) v tomto tématu.|
|Trasování SQL|Zobrazí výsledky trasování SQL. Tato tabulka je dostupná až po dokončení zátěžového testu a jenom v případě, že se během testu použilo trasování SQL. Další informace najdete v [tabulce dat trasování SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) v tomto tématu.|
|Testy|Zobrazí podrobnosti pro jednotlivé testy spouštěné během zátěžového testu. Další informace najdete v [tabulce testy](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) v tomto tématu.|
|Prahové hodnoty|Zobrazuje seznam porušení pravidel mezních hodnot, ke kterým došlo během běhu zátěžového testu. Další informace najdete v tématu [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transakce|Zobrazí seznam transakcí, ke kterým došlo během běhu zátěžového testu. Další informace najdete v [tabulce transakcí](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) v tomto tématu.|
|Agenti|Zobrazí se pouze v případě, že zátěžový test používá testovací kontrolér a testovací agenty. Zobrazuje seznam agentů, které byly použity při spuštění zátěžového testu. Tabulka agentů obsahuje počet požadavků testovaných agentem a jejich žádostí, počet selhání. Kromě toho tabulka agentů obsahuje počet testů v poměru testů zátěžových testů, které Agent testovaný a z nich zjistil, kolik selhalo.|
|Podrobnosti testu|Zobrazí podrobnosti o testech obsažených v poměru testů pro zátěžový test. Mezi podrobnosti patří název testu, scénář, ve kterém byl test, čas spuštění testu, doba, po kterou byl test spuštěn, a výsledek testu, který označuje, zda test proběhl úspěšně nebo selhal. Pokud se test nezdařil, nachází se odkaz ve sloupci **podrobností** . Můžete vybrat odkaz, který vás převezme na Editor testu výkonnosti webu se zvýrazněným požadavkem.|

## <a name="collect-percentile-data"></a>Shromáždit data percentilu

Některé tabulky zátěžových testů mohou obsahovat další sloupce, které zahrnují data percentilu a doby odezvy rozdělené do skupin na základě emulace sítě. Ve výchozím nastavení se tato data neshromažďují. Data percentilu jsou k dispozici pouze v případě, že ukládáte výsledky do databáze a ne když ukládáte místně. Další informace najdete v tématu [Správa výsledků zátěžových testů v úložišti load výsledky testů](../test/manage-load-test-results-in-the-load-test-results-repository.md). Kromě toho ke shromáždění těchto dat v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte konkrétní uzel nastavení spuštění, který se má změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **StatisticsOnly** nebo **AllIndividualDetails**. Další informace najdete v tématu [Postup: zobrazení odpovědi na webovou stránku](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>Tabulka požadavků

V tabulce s **požadavky** se zobrazují podrobnosti o jednotlivých žádostech vydaných během zátěžového testu. To zahrnuje všechny požadavky HTTP a závislé požadavky, jako jsou například obrázky. Tabulka obsahuje seznam požadavků podle testů a scénářů, protože jeden požadavek může být zahrnut v mnoha testech a scénářích.

V následující tabulce jsou uvedeny sloupce v tabulce **requests** :

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|**Žádost**|Adresa URL požadavku Například *home.html* nebo *orange-arrow.gif*.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Test**|Název testu.|Ano|
|**Celkem**|Celkový počet této žádosti testu výkonnosti webu vydaný během běhu zátěžového testu. Celkový součet zahrnuje úspěšné a neúspěšné požadavky, ale nezahrnuje požadavky uložené v mezipaměti, protože nejsou vydané webovému serveru.|Ano|
|**Předaný**|Počet, kolikrát byl požadavek vydán a předán.|Ne|
|**Neúspěšný**|Počet vydaných a neúspěšných požadavků. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete vybrat libovolný hypertextový odkaz a zobrazit seznam jednotlivých chyb v dialogovém okně **chyby zátěžového testu** . Další informace naleznete v tématu [Analýza výsledků zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ano|
|**V mezipaměti**|Celkový počet, kolikrát již byl požadavek uložen do mezipaměti.|Ne|
|**Počet požadavků za sekundu**|Sazba za sekundu žádosti během běhu zátěžového testu.|Ne|
|**Úspěšné za sekundu**|Sazba za sekundu této žádosti během běhu zátěžového testu pro instance této žádosti, které prošly.|Ne|
|**Selhání za sekundu**|Sazba za sekundu této žádosti během běhu zátěžového testu pro instance této žádosti, která selhala.|Ne|
|**Čas prvního bajtu**|Průměrná doba pro přijetí prvního bajtu odpovědi měřená od doby, kdy byla žádost odeslána webovému serveru. Jednotky jsou sekundy.|Ne|
|**Doba odezvy**|Průměrná doba pro přijetí celé odpovědi na žádost měřená od doby, kdy byla žádost odeslána webovému serveru. Jednotky jsou sekundy.|Ano|
|**Délka obsahu**|Průměrná délka obsahu odpovědi na požadavek. Jednotky jsou bajty.|Ano|

## <a name="the-tests-table"></a>Tabulka testů

Tabulka **testy** zobrazuje podrobnosti pro jednotlivé testy spouštěné během zátěžového testu. Tabulka obsahuje seznam testů podle testů a scénářů, protože jeden test může být zahrnut v mnoha scénářích.

V následující tabulce jsou uvedeny sloupce v tabulce **testy** .

|Sloupec|Popis|Ve výchozím nastavení viditelné|
|-|-|-|
|**Test**|Název testu.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Celkem**|Celkový počet spuštění testu ve scénáři. To zahrnuje počet úspěšných a neúspěšných testů.|Ano|
|**Předaný**|Počet spuštění testu ve scénáři a úspěch.|Ano|
|**Neúspěšný**|Počet spuštění testu ve scénáři a selhání. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete vybrat libovolný hypertextový odkaz a zobrazit seznam jednotlivých chyb v dialogovém okně **chyby zátěžového testu** . Další informace naleznete v tématu [Analýza výsledků zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Ano|
|**Testy za sekundu**|Sazba za sekundu testu během běhu zátěžového testu.|Ano|
|**Úspěšné za sekundu**|Sazba za sekundu tohoto testu během běhu zátěžového testu pro výskyty tohoto testu, který proběhl úspěšně.|Ne|
|**Selhání za sekundu**|Sazba za sekundu tohoto testu během běhu zátěžového testu pro instance tohoto testu, které selhaly.|Ne|
|**Čas testu**|Průměrná doba spuštění testu během běhu zátěžového testu. Jednotky jsou sekundy.|Ano|
|**90% testovacího času**|Hodnota devadesáte percentilu pro dobu testování.|Ne|
|**95% testovacího času**|Hodnota percentilu 95. pro testovací čas|Ano|
|**Žádosti a testování**|Průměrný počet požadavků v testu, pokud se jedná o test výkonnosti webu.|Ne|

## <a name="the-transactions-table"></a>Tabulka transakcí

Tabulka **transakcí** zobrazuje seznam transakcí, ke kterým došlo během běhu zátěžového testu. Transakce odkazují buď na transakce definované v testu výkonnosti webu, nebo na časovače definované v testu jednotek. Transakce neodkazuje na transakce databáze.

V následující tabulce jsou uvedeny sloupce v tabulce **transakcí** .

> [!NOTE]
> Chcete-li zobrazit všechny sloupce, je nutné povolit vlastnost úložiště podrobností časování, která je přidružena k aktivnímu nastavení běhu. Další informace najdete v tématu [Postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Sloupec|Popis|Viditelné bez podrobností časování|
|-|-|-|
|**Transakce**|Název transakce.|Ano|
|**Scénář**|Název scénáře.|Ano|
|**Test**|Název testu.|Ano|
|**Celkem**|Celkový počet transakcí vydaných během běhu zátěžového testu.|Ano|
|**Čas transakce**|Čas spuštění transakce během zátěžového testu. V případě testů výkonnosti webu je čas zamyslení zahrnut do výpočtu. Jednotky jsou sekundy.|Ne|
|**Doba odezvy**|Doba odezvy pro transakci testu výkonnosti webu v běhu zátěžového testu. Doba odezvy se liší od času transakce v této době odezvy nezahrnuje čas pomýšlení, ke kterému došlo během transakce. Jednotky jsou sekundy.|Ne|
|**Ave. Transaction – čas**|Průměrná doba transakce. Tato doba zahrnuje dobu přemýšlení. Například pokud máte tři požadavky a každý z nich má čas promýšlení, bude tato doba zahrnovat tyto časy a skutečný čas pro spuštění požadavků.|Ne|
|**Ave. doba odezvy**|Průměrná doba odezvy pro transakci testu výkonnosti webu v běhu zátěžového testu. Doba odezvy se liší od času transakce v této době odezvy nezahrnuje čas pomýšlení, ke kterému došlo během transakce. Jednotky jsou sekundy.|Ne|
|**Minimální doba odezvy**|Nezahrnuje dobu přemýšlení.|Ne|
|**Maximální doba odezvy**|Nezahrnuje dobu přemýšlení.|Ne|
|**Medián doby odezvy**|Nezahrnuje dobu přemýšlení.|Ne|
|**90% doba odezvy**|Hodnota devadesáte percentilu pro čas transakce. Nezahrnuje dobu přemýšlení. **Poznámka:**  To se liší od programu Visual Studio Team System 2008 Test Load Agent, který použil hodnotu **času transakce 90%** .|Ne|
|**95% doba odezvy**|Hodnota percentilu 95. pro čas transakce Nezahrnuje dobu přemýšlení. **Poznámka:**  To se liší od programu Visual Studio Team System 2008 Test Load Agent, který použil hodnotu **času transakce 95%** .|Ne|
|**99% doba odezvy**|Hodnota percentilu 99 pro čas transakce Nezahrnuje dobu přemýšlení.|Ne|
|**Doba odezvy std pro vývojáře**|Nezahrnuje dobu přemýšlení.|Ne|

## <a name="the-errors-table"></a>Tabulka chyb

Při spuštění zátěžového testu můžete analyzovat chyby, ke kterým dojde. Analýza chyb a úpravy testů jsou důležitou součástí procesu zátěžového testu. Pokud dojde k chybám, zobrazí se na stavovém řádku test zátěže hypertextový odkaz **chyby** a určí počet chyb, ke kterým došlo. Chcete-li zobrazit tabulku chyb, vyberte hypertextový odkaz.

Tabulka Errors seskupuje chyby, ke kterým došlo během zátěžového testu, typem a podtypem chyby. V tabulce je také **Celková** čára, která určuje celkový počet všech chyb, ke kterým došlo.

Tabulka Errors obsahuje následující sloupce:

|Sloupec|Popis|Při výchozím nastavení viditelné|
|-|-|-|
|Typ|Typ chyby Například HttpError.|Ano|
|Podtyp|Podtyp chyby. Například LoadTestException.|Ano|
|Počet|Počet chyb tohoto typu, ke kterým došlo během zátěžového testu. Položky v tomto sloupci se zobrazí jako hypertextové odkazy. Můžete vybrat libovolný hypertextový odkaz a zobrazit tak seznam jednotlivých chyb.|Ano|
|Poslední zpráva|Zpráva popisující chybu Například 404 – NotFound.|Ano|

Další informace naleznete v tématu [práce s tabulkami zátěžových testů](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Přechod k podrobnostem v seznamu chyb

Tabulka Errors seskupuje chyby podle typu a podtypu chyby. Chcete-li zobrazit tabulku jednotlivých chyb, zobrazí se dialogové okno **chyby zátěžového testu** . Chcete-li zobrazit dialogové okno, vyberte hypertextový odkaz ve sloupci **počet** v tabulce chyby. Dialogové okno můžete zobrazit také tak, že kliknete pravým tlačítkem na řádek v tabulce chyby, která je naplněná, a zvolíte **chyby**.

> [!NOTE]
> Shromažďují se jenom první 1 000 instance libovolného typu chyby a kombinace podtypu. Po zobrazení dialogového okna **chyby zátěžového testu** se zobrazí maximálně prvních 1 000 instancí, u kterých došlo k chybě.

Tabulka **chyby zátěžového testu** obsahuje následující sloupce:

|Sloupec|Popis|
|-|-|
|**Čas**|Čas v průběhu zátěžového testu, při kterém došlo k chybě.|
|**Agenta**|Název počítače agenta, na kterém došlo k chybě. To je důležité při spuštění zátěžových testů pomocí testovacích kontrolérů a testovacích agentů. Další informace najdete v tématu [instalace a konfigurace testovacích agentů](../test/lab-management/install-configure-test-agents.md).|
|**Test**|Název testu výkonnosti webu, v němž došlo k chybě.|
|**Scénář**|Název scénáře, ve kterém došlo k chybě.|
|**Žádost**|Adresa URL požadavku, ve kterém došlo k chybě.|
|**Typ**|Typ chyby Například HttpError.|
|**Podtyp**|Podtyp chyby. Například LoadTestException.|
|**Text**|Text chybové zprávy Například 404 – NotFound.|
|**Zásobník**|Položky v tomto sloupci buď nejsou prázdné, nebo je jako hypertextový odkaz formátována **sada** Word. Kliknutím na hypertextový odkaz můžete zobrazit trasování zásobníku chyby.|
|**Podrobnosti**|Položky v tomto sloupci buď nejsou prázdné, nebo je slovo **TestLog** formátováno jako hypertextový odkaz. Tento odkaz vám může přispět k izolaci chyb v zátěžovém testu. Například volba odkazu **TestLog** na chybu žádosti testu výkonnosti webu otevře výsledky testu výkonnosti webu v prohlížeči výsledky testůho webového výkonu a zvýrazní chybu žádosti.|

> [!NOTE]
> Tabulku můžete seřadit výběrem záhlaví sloupců.

## <a name="the-sql-trace-data-table"></a>Tabulka dat trasování SQL

Data trasování SQL můžete shromažďovat během běhu zátěžového testu a analyzovat je později. Shromažďování dat trasování vám umožní identifikovat nejpomalejší běžící dotazy a uložené procedury v testované databázi SQL Server.

Pokud je povoleno trasování SQL, vytvoří se soubor během spuštění zátěžového testu, který obsahuje data trasování. Tato data se automaticky uloží do úložiště Load Výsledky testů na konci testovacího běhu a trasovací soubor se odstraní. Data trasování můžete analyzovat v tabulce **trasování SQL** po dokončení zátěžového testu.

### <a name="to-view-sql-trace-data"></a>Zobrazení dat trasování SQL

1. V analyzátoru zátěžového testu klikněte na tlačítko **tabulky** na panelu nástrojů a ujistěte se, že je zobrazena mřížka tabulky.

2. V rozevíracím seznamu **tabulka** vyberte položku **trasování SQL**.

3. Data trasování, která byla shromážděna během běhu, se zobrazí v mřížce. V tabulce jsou uvedeny nejpomalejší běžící operace SQL seřazené podle doby trvání, která je nejpomalejší v horní části. Obvykle je sloupec **Trvání** prvním sloupcem, který chcete prošetřit. Data se zobrazí v milisekundách.

   Zobrazené sloupce jsou následující:

    - **Event – třída**

    - **Doba trvání**

    - **Procesor**

    - **Čtení**

    - **Zápisy**

    - **TextData**

    - **StartTime**

    - **EndTime**

   Chcete-li trasovat události SQL jiné než data identifikovaná v těchto sloupcích, můžete nastavit vlastní trasování SQL pomocí nástroje SQL Profiler, který je oddělený od sady Visual Studio.

## <a name="tile-load-test-tables"></a>Tabulky zátěžových testů dlaždic

Při zobrazení výsledků zátěžového testu můžete zobrazit data jako podrobné tabulky. Chcete-li přepnout na zobrazení tabulky, vyberte možnost **tabulky** na panelu nástrojů **zátěžového testu** . Dostupné tabulky jsou **chyby**, **stránky**, **požadavky**, **trasování SQL**, **testy**, **prahové hodnoty** a **transakce**. Další informace naleznete v tématu [práce s tabulkami zátěžových testů](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

V tabulkovém zobrazení můžete zobrazit až čtyři tabulky najednou, aniž by se tabulky překrývaly.

### <a name="to-tile-tables"></a>K tabulkám dlaždic

1. Na panelu nástrojů **analyzátor zátěžového testu** vyberte možnost **tabulky**.

     Otevře se zobrazení tabulky. Výchozím rozložením jsou dva horizontální panely.

2. Na panelu nástrojů **analyzátor zátěžového testu** klikněte na tlačítko **rozložení** a pak zvolte jednu z následujících možností:

    - **Jeden panel**

    - **Dva vodorovné panely**

    - **Tři horizontální panely**

    - **Čtyři vodorovné panely**

3. Chcete-li přepínat mezi různými tabulkami, použijte rozevírací seznam nad mřížkou tabulky na každém panelu.

    > [!NOTE]
    > Nemůžete zobrazit stejnou tabulku ve více než jednom panelu. Změníte-li tabulku zobrazenou na jednom panelu na tabulku, která je již zobrazena na jiném panelu, tabulky přepínají panely.

## <a name="see-also"></a>Viz také

- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)
- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Správa výsledků zátěžového testu v úložišti Výsledky testů zatížení](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Přehled souhrnu výsledků zátěžového testu](../test/load-test-results-summary-overview.md)
