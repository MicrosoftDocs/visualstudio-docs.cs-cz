---
title: Používání uložených dat IntelliTrace | Microsoft Docs
description: Použijte soubor IntelliTrace (. iTrace) pro spuštění ladění v určitém bodě provádění. Soubor obsahuje informace, které IntelliTrace zaznamenané od spuštění vaší aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42f355a0a8d04e48a2b9d14d0d62edf2cd949a87
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150935"
---
# <a name="using-saved-intellitrace-data-c-visual-basic-c"></a>Použití uložených dat IntelliTrace (C#, Visual Basic, C++)

Když začnete ladit ze souboru protokolu IntelliTrace (. iTrace), přejdete ke konkrétním bodům v provádění vaší aplikace. Tento soubor může obsahovat události výkonu, výjimky, vlákna, testovací kroky, moduly a další systémové informace, které IntelliTrace záznamy při spuštění aplikace.

 Ujistěte se, zda máte následující:

- Pro váš kód aplikace se shodují zdrojové soubory a soubory symbolů (PDB). V opačném případě Visual Studio nedokáže přeložit zdrojová umístění a zobrazí zprávu "symboly nebyly nalezeny". Viz [určení symbolu (PDB) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) a [diagnostikování problémů po nasazení](../debugger/diagnose-problems-after-deployment.md).

- Visual Studio Enterprise (ale ne edice Professional nebo Community) na vašem vývojovém počítači nebo jiném počítači pro otevření souborů. iTrace

- Soubor. iTrace z jednoho z těchto zdrojů:

    |**Zdroj**|**Si**|
    |----------------|-------------|
    |IntelliTrace relace v Visual Studio Enterprise (ale ne edice Professional nebo Community)|[Funkce IntelliTrace](../debugger/intellitrace-features.md)|
    |Microsoft Monitoring Agent buď samostatně, nebo s nástrojem System Center 2012 R2 Operations Manager pro webové aplikace ASP.NET a aplikace služby SharePoint spuštěné v nasazení|-   [Diagnostikovat problémy po nasazení](../debugger/diagnose-problems-after-deployment.md)<br />-   [Co je nového pro System Center 2012 R2 Operations Manager](/previous-versions/system-center/system-center-2012-R2/dn249700(v=sc.12))|

## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Co chcete udělat?

- [Otevření protokolu IntelliTrace](#Open)

- [Pochopení protokolu IntelliTrace](#Understand)

- [Spustit ladění z protokolu IntelliTrace](#StartDebugging)

## <a name="open-an-intellitrace-log"></a><a name="Open"></a> Otevření protokolu IntelliTrace
 V počítači s Visual Studio Enterprise otevřete soubor. iTrace.

- Dvakrát klikněte na soubor. iTrace mimo aplikaci Visual Studio nebo ho otevřete v rámci sady Visual Studio.

     \- ani

- Pokud je soubor. iTrace připojen k pracovní položce Team Foundation Server, postupujte podle těchto kroků v pracovní položce:

  - V části **všechny odkazy** vyhledejte soubor. iTrace. Otevřete ji.

    \- ani

  - V části **reprodukci kroky** klikněte na odkaz **IntelliTrace** .

> [!TIP]
> Pokud jste soubor IntelliTrace zavřeli během ladění, můžete ho snadno otevřít. Přejděte do nabídky **ladění** , vyberte **IntelliTrace**, **Zobrazit souhrn protokolu**. V okně **IntelliTrace** můžete také zvolit **Zobrazit souhrn protokolu** . Toto je k dispozici pouze při ladění pomocí IntelliTrace.

## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> Pochopení protokolu IntelliTrace
 Některé z následujících sekcí souboru. iTrace se zobrazí pouze v případě, že jste shromáždili data z určitého zdroje, například z aplikací služby SharePoint.

|**Sekce**|**Zobrazí**|**Zdroj kolekce**|
|-----------------|------------------|---------------------------|
|[Narušení výkonu](#Performance)|Události související s výkonem volání funkcí, které překračují nakonfigurovanou prahovou hodnotu|Microsoft Monitoring Agent buď samostatného kolektoru, nebo s nástrojem System Center 2012 R2 Operations Manager pro webové aplikace ASP.NET hostované ve službě IIS|
|[Data výjimky](#ExceptionData)|Výjimky, včetně úplného zásobníku volání pro každou výjimku|Všechny zdroje|
|[Výsledcích](#Analysis)|Pouze pro aplikace SharePoint 2010 a SharePoint 2013. Diagnostikujte události IntelliTrace a SharePointu, jako jsou události ladicího programu, události ULS, neošetřené výjimky a další data, která Microsoft Monitoring Agent nahrála.|Microsoft Monitoring Agent buď samostatného kolektoru, nebo pomocí nástroje System Center 2012 R2 Operations Manager|
|[Systémové informace](#SystemInfo)|Nastavení a specifikace hostitelského systému|Všechny zdroje|
|[Seznam vláken](#ThreadsList)|Vlákna, která běžela během shromažďování|Všechny zdroje|
|[Moduly](#Modules)|Moduly, které cílový proces načte v pořadí, v jakém byly načteny.|Všechny zdroje|
|[Webový požadavek](#Modules)|Data webových požadavků pro produkční webové aplikace IIS a SharePoint 2010 a SharePoint 2013|Microsoft Monitoring Agent a samostatný kolektor|

 Tady je několik tipů, které vám pomůžou najít informace v jednotlivých částech:

- Vyberte záhlaví sloupce k řazení dat.

- Data můžete filtrovat pomocí vyhledávacího pole. Hledání v prostém textu funguje ve všech sloupcích kromě časových sloupců. Můžete také filtrovat hledání do konkrétního sloupce s jedním filtrem na sloupec. Zadejte název sloupce bez mezer, dvojtečky (**:**) a vyhledávací hodnoty. Pro přidání dalšího sloupce a hodnoty hledání použijte středník (**;**).

     Pokud například chcete najít události výkonu, které mají ve sloupci **Description** (pomalá) slovo "pomalé", zadejte:

     `Description:slow`

## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> Spustit ladění z protokolu IntelliTrace

### <a name="performance-violations"></a><a name="Performance"></a> Narušení výkonu
 Zkontrolujte události výkonu, které byly zaznamenány pro vaši aplikaci. Události, ke kterým dochází často, můžete skrýt.

##### <a name="to-start-debugging-from-a-performance-event"></a>Spuštění ladění z události výkonu

1. V části **narušení výkonu** Zkontrolujte zaznamenané události výkonu, jejich celkové časy spuštění a další informace o událostech. Pak přejděte hlouběji do metod, které byly volány během konkrétní události výkonu.

     ![Zobrazit podrobnosti události výkonu](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Můžete také pouze dvakrát kliknout na událost.

2. Na stránce události zkontrolujte časy spuštění těchto volání. Vyhledejte pomalé volání ve stromu spuštění.

     Pokud máte více volání vnořených nebo jiných, zobrazují se nejpomalejší volání ve vlastním oddílu.

3. Rozbalením tohoto volání zkontrolujte všechna vnořená volání a hodnoty parametrů, které byly zaznamenány v daném časovém okamžiku.

     (Klávesnice: Chcete-li zobrazit nebo skrýt vnořené volání, stiskněte klávesu **šipka vpravo** nebo **šipka vlevo** v uvedeném pořadí. Chcete-li zobrazit a skrýt hodnoty parametrů pro vnořené volání, stiskněte klávesu **MEZERNÍK** .

     Spustit ladění volání.

     ![Spustit ladění z volání metody](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Můžete také pouze dvakrát kliknout na volání nebo stisknout klávesu **ENTER** .

     Pokud je metoda v kódu aplikace, sada Visual Studio přejde na tuto metodu.

     ![Přejít na kód aplikace z události výkonu](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání, krokovat kód, nebo použít okno **IntelliTrace** pro [pohyb zpět nebo vpřed "v čase" mezi jinými metodami](../debugger/intellitrace.md) , které byly volány během této události výkonu.

### <a name="exception-data"></a><a name="ExceptionData"></a> Data výjimky
 Zkontrolujte výjimky, které byly vyvolány a zaznamenány pro vaši aplikaci. Můžete seskupit výjimky, které mají stejný typ a zásobník volání, aby se zobrazila pouze nejaktuálnější výjimka.

##### <a name="to-start-debugging-from-an-exception"></a>Spuštění ladění z výjimky

1. V části **data výjimky** Zkontrolujte zaznamenané události výjimky, jejich typy, zprávy a případy, kdy došlo k výjimkám. Pokud se chcete dostat hlouběji do kódu, spusťte ladění od poslední události ve skupině výjimek.

     ![Spustit ladění z události výjimky](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Můžete také pouze dvakrát kliknout na událost. Pokud se události neseskupí, vyberte možnost **Ladit tuto událost**.

     Pokud došlo k výjimce v kódu aplikace, sada Visual Studio pokračuje tam, kde došlo k výjimce.

     ![Přejít na kód aplikace z události výjimky](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Nyní můžete zkontrolovat další zaznamenané hodnoty, zásobník volání nebo použít okno **IntelliTrace** pro [pohyb zpět nebo vpřed "v čase" mezi ostatními zaznamenanými událostmi](../debugger/intellitrace.md), souvisejícím kódem a hodnotami zaznamenanými v těchto okamžicích v čase.

    |**Sloupec**|**Zobrazuje**|
    |----------------|-------------------|
    |**Typ**|Typ rozhraní .NET výjimky|
    |**Nejnovější zpráva** pro seskupené výjimky nebo **zprávy** pro neseskupené výjimky|Zpráva poskytnutá výjimkou|
    |**Počet** pro seskupené výjimky|Počet, kolikrát byla výjimka vyvolána|
    |**ID vlákna** pro neseskupené výjimky|ID vlákna, které vyvolalo výjimku|
    |Čas **nejnovější události** nebo **čas události**|Časové razítko zaznamenané při vyvolání výjimky|
    |**Zásobník volání**|Zásobník volání pro výjimku.<br /><br /> Chcete-li zobrazit zásobník volání, v seznamu vyberte výjimku. Zásobník volání se zobrazí pod seznamem výjimek.|

### <a name="analysis"></a><a name="Analysis"></a> Výsledcích
 Diagnostikujte problémy s aplikacemi SharePoint 2010 a SharePoint 2013 pomocí ID korelace SharePointu nebo zkontrolujte všechny neošetřené výjimky, které Microsoft Monitoring Agent nalezené.

- K vyhledání odpovídajícího webového požadavku a událostí použijte ID korelace SharePointu. Zvolte událost a potom spusťte ladění v místě, kde a kdy k události došlo.

- Pokud Microsoft Monitoring Agent našla neošetřené výjimky, zvolte výjimku a potom spusťte ladění v místě, kde a kdy k výjimce došlo.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Spuštění ladění s ID korelace SharePoint

1. Zkopírujte ID korelace SharePoint z jeho zdroje.

    Příklad:

    ![ID korelace &#45; IntelliTrace &#45; SharePointu](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. Otevřete soubor. iTrace, přejděte na **Analýza** a zadejte ID korelace SharePointu, abyste zkontrolovali, který webový požadavek a zaznamenané události se shodují.

    ![&#45; protokolu IntelliTrace zadejte ID korelace SharePointu.](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")

3. V části **události žádosti** prověřte události. Od začátku se události zobrazí v pořadí, v jakém byly provedeny.

   1. Kliknutím na událost zobrazíte její podrobnosti.

   2. Chcete-li spustit ladění v místě, kde došlo k události, vyberte možnost **Spustit ladění** .

      ![IntelliTrace souboru protokolu &#45; zobrazení událostí &#43; webového požadavku](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   Tyto typy událostí služby SharePoint můžete zobrazit společně s událostmi IntelliTrace:

- **Události uživatelského profilu**

     K těmto událostem dochází, když SharePoint načte profil uživatele a když se vlastnosti profilu uživatele čtou nebo mění.

- **Události sjednoceného systému protokolování (ULS)**

     Microsoft Monitoring Agent zaznamenává podmnožinu událostí ULS služby SharePoint a těchto polí:

    |**Pole IntelliTrace**|**Pole SharePoint ULS**|
    |----------------------------|------------------------------|
    |**ID**|**ID události**|
    |**Obsah**|**Obsah**|
    |**ID kategorie**|**ID kategorie**|
    |**Kategorie**|**Kategorie**|
    |**Plošný**|**Product** (Produkt)|
    |**Výstup**|**Zpráva**|
    |**ID korelace**|**ID korelace**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>Spuštění ladění z nezpracované výjimky

1. Vyberte ID korelace SharePointu pro výjimku. Výjimky jsou seskupeny podle typu a zásobníku volání.

2. Volitelné Rozbalením **zásobníku volání** zobrazíte zásobník volání pro skupinu výjimek.

3. Vyberte možnost **výjimka ladění** pro spuštění ladění v místě, kde a kdy k výjimce došlo.

    ![Neošetřené výjimky protokolu IntelliTrace &#45; služby SharePoint](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Návod naleznete v tématu [Návod: ladění aplikace služby SharePoint pomocí IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md). Typy dat, která Agent zaznamenává, najdete v tématu [funkce IntelliTrace](../debugger/intellitrace-features.md).

### <a name="threads-list"></a><a name="ThreadsList"></a> Seznam vláken
 Prověřte zaznamenaná vlákna, která byla spuštěna v cílovém procesu. Můžete spustit ladění z první platné události IntelliTrace ve vybraném vlákně.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Spuštění ladění z konkrétního vlákna

1. V **seznamu vlákna** vyberte vlákno.

2. V dolní části **seznamu vláken** vyberte možnost **Spustit ladění**. Můžete také dvakrát kliknout na vlákno.

    Chcete-li spustit ladění z místa, kde aplikace začíná, dvakrát klikněte na **hlavní vlákno**. Viz [funkce IntelliTrace](../debugger/intellitrace-features.md).

   Data vlákna vytvořená uživatelem mohou být užitečnější než vlákna, která server vytváří a spravuje pro webové aplikace hostované službou IIS.

|**Sloupec**|**Zobrazuje**|
|----------------|-------------------|
|**ID**|Číslo ID vlákna|
|**Název**|Název vlákna. Nepojmenovaná vlákna se zobrazí jako " \<No Name> ".|
|**Čas spuštění**|Čas vytvoření vlákna|
|**Čas ukončení**|Čas, kdy bylo vlákno dokončeno|

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Spuštění ladění z konkrétního kroku testu

1. Rozbalte **mřížku testovacích kroků**. Vyberte krok testu.

2. V dolní části **mřížky testovacích kroků** vyberte možnost **Spustit ladění**. Můžete také dvakrát kliknout na testovací krok.

     Tím se spustí ladění z první platné události IntelliTrace po vybraném kroku testu.

     Když existují testovací data, IntelliTrace se pokusí přeložit přidružené sestavení Team Foundation Server, které bylo použito k provedení testovacího běhu. Pokud je sestavení nalezeno, přidružené symboly pro aplikaci budou automaticky vyřešeny.

|**Pole**|**Zobrazuje**|
|---------------|-------------------|
|**Testovací relace**|Testovací relace, které byly zaznamenány. Obvykle je k dispozici pouze jeden. Tento seznam je prázdný, pokud byla testovací data vytvořena pomocí manuálního průzkumného testu.|
|**Testovací případ**|Testovací případy z vybrané testovací relace. Tento seznam je prázdný, pokud byla testovací data vytvořena pomocí manuálního průzkumného testu.|
|**Mřížka kroků testu**|Testovací kroky, které byly zaznamenány s výsledkem testu úspěch nebo neúspěch|

### <a name="system-info"></a><a name="SystemInfo"></a> Systémové informace
 V této části se dozvíte podrobnosti o systému, který hostuje aplikaci, například o hardwaru, operačním systému, prostředí a informacích týkajících se ochrany životního prostředí a procesu.

### <a name="modules"></a><a name="Modules"></a> Aktualizuj
 V této části jsou uvedeny moduly, které jsou načteny cílovým procesem. Moduly se zobrazí v pořadí, v jakém byly načteny.

|**Sloupec**|**Zobrazuje**|
|----------------|-------------------|
|**Název modulu**|Název souboru modulu|
|**Cesta k modulu**|Místo na disku, kde se modul načetl|
|**ID modulu**|Jedinečný identifikátor modulu, který je specifický pro verzi a přispívá k souborům odpovídajícího symbolu (PDB). Viz [hledání souborů symbolů (. pdb) a zdrojových souborů](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).|

### <a name="where-can-i-get-more-information"></a>Zdroje dalších informací
 [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [Funkce IntelliTrace](../debugger/intellitrace-features.md)

 [Shromažďování více diagnostických dat v ručních testech](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Fóra
 [Visual Studio – ladicí program](https://social.msdn.microsoft.com/Forums/en-US/home)

#### <a name="guidance"></a>Pokyny
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 6: testovací sada nástrojů](/previous-versions/msp-n-p/jj159337(v=pandp.10))
