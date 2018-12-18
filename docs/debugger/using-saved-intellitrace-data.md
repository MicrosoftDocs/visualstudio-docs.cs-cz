---
title: Použití uložených dat řešení IntelliTrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad584ac350038ced460b42a4e63d2b140d8396d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912965"
---
# <a name="using-saved-intellitrace-data"></a>Použití dat uložených nástrojem IntelliTrace
Přejdete na konkrétní okamžiky provádění vaší aplikace při spuštění ladění od souboru protokolu IntelliTrace (.iTrace). Tento soubor může obsahovat události související s výkonem, výjimky, vlákna, kroky testu, moduly a další systémové informace, že nástroj IntelliTrace zaznamenává za běhu aplikace.

 Ujistěte se, zda máte následující:

-   Odpovídající zdrojové soubory a soubory symbolů (PDB) pro kód aplikace. V opačném případě sady Visual Studio nelze rozpoznat zdrojová umístění a zobrazí zprávu "Symboly nebyly nalezeny." Zobrazit [zadejte symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) a [Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).

-   Visual Studio Enterprise (ale ne Professional nebo Community edice) na svém vývojovém počítači nebo jiném počítači pro otevření souborů .iTrace

-   Soubor .iTrace z jednoho z těchto zdrojů:

    |**Zdroj**|**V tématu**|
    |----------------|-------------|
    |Relace IntelliTrace v sadě Visual Studio Enterprise (ale ne Professional nebo Community edice)|[Funkce IntelliTrace](../debugger/intellitrace-features.md)|
    |Testovací relace v nástroji Microsoft Test Manager. Tato možnost připojuje soubor .iTrace k pracovní položce serveru Team Foundation Server.|[Shromažďování více diagnostických dat v manuálních testů](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|
    |Microsoft Monitoring Agent, buď samostatně nebo pomocí System Center 2012 R2 Operations Manager pro technologii ASP.NET webové aplikace a služby SharePoint spuštěnými v nasazení|-   [Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md)<br />-   [Co je nového pro System Center 2012 R2 Operations Manager](http://technet.microsoft.com/library/dn249700.aspx)|

##  <a name="GetStarted"></a> Co chcete udělat?

-   [Otevření protokolu nástroje IntelliTrace](#Open)

-   [Principy protokolu IntelliTrace](#Understand)

-   [Spuštění ladění z protokolu IntelliTrace](#StartDebugging)

##  <a name="Open"></a> Otevření protokolu nástroje IntelliTrace
 Na počítači s Visual Studio Enterprise otevřete soubor .iTrace.

-   Poklikejte na soubor .iTrace mimo sadu Visual Studio, nebo otevřete soubor v rámci sady Visual Studio.

     \- nebo –

-   Pokud soubor .iTrace připojen k pracovní položce serveru Team Foundation Server, postupujte podle těchto kroků v pracovní položce:

    -   V části **všechny odkazy**, najděte soubor .iTrace. Otevřete jej.

         \- nebo –

    -   V části **kroky pro reprodukci**, zvolte **IntelliTrace** odkaz.

> [!TIP]
>  Pokud jste zavřeli soubor IntelliTrace během ladění, můžete lze jej snadno znovu otevřít. Přejděte **ladění** nabídce zvolte **IntelliTrace**, **zobrazit souhrn protokolu**. Můžete také zvolit **zobrazit souhrn protokolu** v **IntelliTrace** okna. To je k dispozici pouze při ladění pomocí IntelliTrace.

##  <a name="Understand"></a> Principy protokolu IntelliTrace
 Některé z těchto částí v souboru .iTrace zobrazí pouze v případě, že byla data shromážděna z určitého zdroje, například z nástroje Test Manager nebo z aplikace služby SharePoint.

|**Oddíl**|**Obsahuje**|**Zdroj kolekce**|
|-----------------|------------------|---------------------------|
|[Narušení výkonu](#Performance)|Události výkonu pomocí volání funkce, která překročí nakonfigurovanou prahovou hodnotu|Microsoft Monitoring Agent, buď samostatného kolektoru nebo pomocí System Center 2012 R2 Operations Manager pro webových aplikací ASP.NET hostovaných ve službě IIS|
|[Data výjimky](#ExceptionData)|Výjimky, včetně úplného zásobníku volání pro jednotlivé výjimky|Všechny zdroje|
|[Analýza](#Analysis)|SharePoint 2010 a SharePoint 2013 pouze pro aplikace. Diagnostika události IntelliTrace a SharePoint, jako je například události ladicího programu, události ULS, neošetřené výjimky a jiná data, která zaznamenávají agenta Microsoft Monitoring Agent.|Microsoft Monitoring Agent, buď samostatného kolektoru nebo pomocí System Center 2012 R2 Operations Manager|
|[Systémové informace](#SystemInfo)|Nastavení a specifikace hostitelského systému|Všechny zdroje|
|[Seznam vláken](#ThreadsList)|Vlákna spuštěná během shromažďování|Všechny zdroje|
|[Testovací Data](#TestData)|Kroky testu a jejich výsledky z testovací relace|Test Manager|
|[Moduly](#Modules)|Moduly, které načtené cílovým procesem v pořadí, ve kterém byly načteny.|Všechny zdroje|
|[Webový požadavek](#Modules)|Webové žádosti o data pro produkční prostředí služby IIS webová aplikace a služby SharePoint 2010 a SharePoint 2013|Microsoft Monitoring Agent a samostatného kolektoru|

 Tady je několik užitečných tipů k vám pomůžou najít informace v každé části:

-   Vyberte záhlaví sloupce seřadíte data.

-   Pomocí vyhledávacího pole filtrovat data. Hledání ve formátu prostého textu funguje napříč všechny sloupce kromě sloupce čas. Můžete také filtrovat hledání v určitém sloupci s jeden filtr na sloupec. Zadejte název sloupce bez mezer, dvojtečkou (**:**) a hledanou hodnotu. Použít tento oddělte středníkem. (**;**) můžete přidat jinou hodnotu sloupce a hledání.

     Například vyhledejte události výkonu, které obsahují slovo "pomalé" v **popis** sloupců, typ:

     `Description:slow`

##  <a name="StartDebugging"></a> Spuštění ladění z protokolu IntelliTrace

###  <a name="Performance"></a> Narušení výkonu
 Zkontrolujte události výkonu, které byly zaznamenány pro vaši aplikaci. Skrýt události, které často nedojde.

##### <a name="to-start-debugging-from-a-performance-event"></a>Spuštění ladění od události výkonu

1.  V části **narušení výkonu**, zkontrolujte zaznamenané události výkonu, jejich celkové časy spuštění a další informace o události. Pak přejděte hlouběji do metod, které byly volány během konkrétní události výkonu.

     ![Zobrazit podrobnosti o událostech výkonu](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Můžete také pouze dvakrát kliknout na událost.

2.  Na stránce události zkontrolujte časy spuštění těchto volání. Vyhledejte pomalé volání ve stromu spuštění.

     Pokud máte více volání vnořených nebo jiných, zobrazují se nejpomalejší volání ve vlastním oddílu.

3.  Rozbalte možnost, že volání účelem kontroly všech vnořených volání a hodnot parametrů, které byly zaznamenány v daném okamžiku v čase.

     (Klávesnice: Chcete-li zobrazit nebo skrýt vnořená volání, stiskněte **šipka vpravo** nebo **šipka vlevo** klíče v uvedeném pořadí. Chcete-li zobrazit nebo skrýt hodnoty parametrů pro vnořená volání, stiskněte **místo** klíč.)

     Spuštění ladění od volání.

     ![Spuštění ladění od volání metody](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Můžete také pouze dvakrát kliknout na volání nebo stisknutím klávesy **Enter** klíč.

     Pokud je metoda v kódu aplikace, sada Visual Studio přejde na tuto metodu.

     ![Přejděte ke kódu aplikace od události výkonu](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání, procházet kódem nebo použít **IntelliTrace** okno [přesune zpět nebo vpřed "v čase" mezi ostatními metodami](../debugger/intellitrace.md) , které byly volány během této události výkonu.

###  <a name="ExceptionData"></a> Data výjimky
 Kontrola výjimky, které byly vyvolány a pro vaši aplikaci zaznamenané. Můžete seskupit výjimky, které mají stejného typu a zásobníku volání, takže uvidíte pouze aktuální výjimky.

##### <a name="to-start-debugging-from-an-exception"></a>Spuštění ladění od výjimku

1.  V části **Data výjimky**, zkontrolujte zaznamenané události výjimky, jejich typy, zprávy, a kdy výjimka nastala. Pokud se chcete dostat hlouběji do kódu, spusťte ladění od poslední události ve skupině výjimek.

     ![Spuštění ladění od události výjimky](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Můžete také pouze dvakrát kliknout na událost. Pokud nejsou seskupeny události, zvolte **Ladit tuto událost**.

     Pokud došlo k výjimce v kódu aplikace, sada Visual Studio pokračuje tam, kde došlo k výjimce.

     ![Přejděte na kód aplikace z události výjimky](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání, nebo použít **IntelliTrace** okno [přesune zpět nebo vpřed "v čase" mezi ostatními zaznamenanými událostmi](../debugger/intellitrace.md), souvisejícím kódem a zaznamenanými hodnotami v Tyto body v čase.

    |**Sloupec**|**Ukazuje,**|
    |----------------|-------------------|
    |**Typ**|Typ .NET výjimky|
    |**Nejnovější zpráva** seskupit výjimky nebo **zpráva** Neseskupená výjimek|Zprávu poskytnutou výjimkou|
    |**Počet** seskupit výjimky|Počet pokusů, které byla vyvolána výjimka|
    |**ID vlákna** Neseskupená výjimek|ID vlákna, které vyvolalo výjimku|
    |**Čas nejnovější události** nebo **čas události**|Časové razítko zaznamenané, kdy byla vyvolána výjimka|
    |**Zásobník volání**|Zásobník volání pro výjimku.<br /><br /> Chcete-li zobrazit zásobník volání, zvolte výjimku v seznamu. Zásobník volání se zobrazuje pod seznamem výjimek.|

###  <a name="Analysis"></a> Analýza
 Diagnostikovat problémy s aplikací SharePoint 2010 a SharePoint 2013 pomocí ID korelace SharePoint nebo zkontrolovat jakékoli neošetřené výjimky, které najít agenta Microsoft Monitoring Agent.

-   Použijte Identifikátor korelace služby SharePoint k nalezení jeho odpovídající webové žádosti a události. Zvolit událost a spustit ladění v místě, kde a kdy k události došlo.

-   Pokud agenta Microsoft Monitoring Agent nalezl neošetřené výjimky, zvolte výjimku a spustit ladění v místě, kde a kdy k výjimce došlo.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Spuštění ladění s ID korelace SharePoint

1. Zkopírujte ID korelace SharePoint z jeho zdroje.

    Příklad:

    ![IntelliTrace &#45; chyba SharePoint &#45; ID korelace](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. Otevřete soubor .iTrace, potom přejděte na stránku **analýzy** a zadejte ID korelace SharePoint ke kontrole odpovídající webový požadavek a zaznamenané události.

    ![Protokol IntelliTrace &#45; ID korelace SharePoint zadat](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")

3. V části **události požadavku**, prozkoumejte události. Počínaje shora, události se zobrazí v pořadí, v jakém k nim došlo.

   1. Zvolte událost zobrazíte její podrobnosti.

   2. Zvolte **spustit ladění** spustit ladění na místě, kde k události došlo.

      ![Soubor protokolu IntelliTrace &#45; zobrazení webový požadavek &#43; události](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   Zobrazí se tyto typy událostí SharePoint spolu s událostmi IntelliTrace:

-   **Události uživatelského profilu**

     K těmto událostem dochází při načtení uživatelského profilu SharePoint a při čtení nebo změně vlastnosti profilu uživatele.

-   **Události jednotného systému protokolování (ULS)**

     Microsoft Monitoring Agent zaznamenává podmnožinu událostí SharePoint ULS a tato pole:

    |**Pole IntelliTrace**|**Pole SharePoint ULS**|
    |----------------------------|------------------------------|
    |**ID**|**ID události**|
    |**úroveň**|**úroveň**|
    |**Id kategorie**|**Id kategorie**|
    |**Kategorie**|**Kategorie**|
    |**Oblast**|**Produkt**|
    |**Output**|**Zpráva**|
    |**Id korelace**|**Id korelace**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>Spuštění ladění z nezpracované výjimky

1. Vyberte Identifikátor korelace služby SharePoint pro výjimku. Výjimky jsou seskupeny dle typu a zásobníku volání.

2. (Volitelné) Rozbalte **zásobník volání** zobrazíte zásobník volání pro skupinu výjimek.

3. Zvolte **ladit výjimku** pro spuštění ladění v místě, kde a kdy k výjimce došlo.

    ![Protokol IntelliTrace &#45; SharePoint neošetřené výjimky](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Návod, naleznete v tématu [návod: ladění aplikace SharePoint pomocí IntelliTrace pomocí](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md). Pro různé druhy dat, která najdete v článku záznamy agenta [funkce IntelliTrace](../debugger/intellitrace-features.md).

###  <a name="ThreadsList"></a> Seznam vláken
 Prozkoumejte zaznamenaná vlákna spuštěná v cílovém procesu. Můžete spustit ladění od první platné události IntelliTrace ve zvoleném vlákně.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Pro spuštění ladění od konkrétního vlákna

1. V části **seznam vláken**, zvolte vlákno.

2. V dolní části **seznam vláken**, zvolte **spustit ladění**. Můžete také dvakrát kliknout na vlákno.

    Pro spuštění ladění od začátku aplikace, klikněte dvakrát na **hlavní vlákno**. Zobrazit [funkce IntelliTrace](../debugger/intellitrace-features.md).

   Data vláken vytvořená uživatelem mohou být užitečnější než vlákna, která serveru vytváří a spravuje pro webovou aplikaci hostovanou službu IIS.

|**Sloupec**|**Ukazuje,**|
|----------------|-------------------|
|**ID**|Číslo ID vlákna|
|**Jméno**|Název vlákna. Nepojmenovaná vlákna se zobrazují jako "\<bez názvu >".|
|**Čas spuštění**|Čas vytvoření vlákna|
|**Koncový čas**|Čas, kdy vlákno bylo dokončeno.|

###  <a name="TestData"></a> Testovací Data
 Prozkoumejte data IntelliTrace, které Test Manager poznamenali během testování vaší aplikace.

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Spuštění ladění od konkrétního kroku testu

1.  Rozbalte **mřížku kroků testu**. Zvolte krok testu.

2.  V dolní části **mřížku kroků testu**, zvolte **spustit ladění**. Můžete také dvakrát kliknout na krok testu.

     Spustí se ladění od první platné události IntelliTrace po vybraný testovací krok.

     Pokud existují data testu IntelliTrace se pokusí přeložit přidružené sestavení Team Foundation Server, který byl použit k provedení testovacího běhu. Pokud je sestavení nalezeno, jsou přidružené symboly aplikace rozpoznány automaticky.

|**Pole**|**Ukazuje,**|
|---------------|-------------------|
|**Testovací relace**|Testovací relace, které byly zaznamenány. Obvykle je zaznamenána pouze jedna. Tento seznam je prázdný, pokud byla testovací data vytvořena pomocí ručního průzkumného testu.|
|**Testovací případ**|Testovací případy z vybrané testovací relace. Tento seznam je prázdný, pokud byla testovací data vytvořena pomocí ručního průzkumného testu.|
|**Mřížka kroků testu**|Testovací kroky, které byly zaznamenány s výsledkem testu průchodu nebo selhání|

###  <a name="SystemInfo"></a> Systémové informace
 Tato část obsahuje podrobnosti o systému, který je hostitelem aplikace, například hardware, operační systém, informace o prostředí a specifické pro proces.

###  <a name="Modules"></a> Moduly
 Tato část popisuje, moduly, které načtené cílovým procesem. Moduly jsou uvedeny v pořadí, ve kterém byly načteny.

|**Sloupec**|**Ukazuje,**|
|----------------|-------------------|
|**Název modulu**|Název souboru modulu|
|**Cesta modulu**|Umístění disku, kde byl modul načten|
|**ID modulu**|Jedinečný identifikátor modulu, který je specifický pro verzi a přispívá k odpovídající soubory symbolů (PDB). Zobrazit [hledání souborů symbolů (PDB) a zdrojové soubory](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).|

### <a name="where-can-i-get-more-information"></a>Kde lze získat další informace?
 [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [Funkce IntelliTrace](../debugger/intellitrace-features.md)

 [Shromažďování více diagnostických dat v manuálních testů](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Diskuzní fóra
 [Ladicí program sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)

#### <a name="guidance"></a>Doprovodné materiály
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 6: testovací sady nástrojů](http://go.microsoft.com/fwlink/?LinkID=255203)