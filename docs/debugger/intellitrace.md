---
title: IntelliTrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2ee2e3662e550e013b2f8436cc32ee9585a419d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825412"
---
# <a name="intellitrace"></a>IntelliTrace

Věnovat méně času laděním aplikace, zaznamenávejte a trasujte historii prostřednictvím spouštění vašeho kódu pomocí nástroje IntelliTrace. Chyby můžete snadno najít, protože nástroj IntelliTrace umožňuje:

- Zaznamenat konkrétní události

   Prozkoumat související kód, data, která se zobrazí **lokální** okno během událostí ladicího programu a informace o voláních funkcí

- Ladit chyby, které je těžké reprodukovat nebo kterým dochází při nasazení

Můžete použít nástroj IntelliTrace v sadě Visual Studio Enterprise edition (ale ne edice Professional nebo Community).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

|||
|-|-|
|**Ladit aplikaci pomocí nástroje IntelliTrace:**<br /><br /> -Zobrazit minulé události.<br />-Zobrazit informace o s minulými událostmi volání.<br />-Uložte relaci nástroje IntelliTrace.<br />-Řízení dat, která nástroj IntelliTrace shromažďuje.|- [Kontrola předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md)<br />- [Návod: Použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Funkce IntelliTrace](../debugger/intellitrace-features.md)<br />- [Historické ladění](../debugger/historical-debugging.md)|
|**Shromažďovat IntelliTrace data během testovací relace v nástroji Test Manager**|- [Shromažďování více diagnostických dat v manuálních testů](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|
|**Shromažďovat IntelliTrace data z nasazené aplikace**|- [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Spuštění ladění ze souboru protokolu IntelliTrace (soubor .iTrace).**|- [Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> Které aplikace můžete ladit pomocí nástroje IntelliTrace?

| | |
|---------------------| - |
| **Plná podpora** | -Jazyka Visual Basic a Visual C# aplikace, které používají rozhraní .NET Framework 2.0 nebo vyšší verze.<br/>Můžete ladit většinu aplikací, včetně ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 a 64bitové aplikace.<br/>Ladění aplikací SharePoint pomocí nástroje IntelliTrace naleznete v tématu [návod: ladění aplikace SharePoint pomocí IntelliTrace pomocí](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Chcete-li ladit aplikace pro Microsoft Azure s použitím technologie IntelliTrace, přečtěte si téma [ladění publikované cloudové služby pomocí nástroje IntelliTrace a sady Visual Studio](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services). |
| **Omezená podpora** | – Nativní aplikace určené pro podporu Windows zobrazení snímků pomocí zpětného kroku IntelliTrace. Podporují se jenom události ladicího programu a výjimek.<br />– .NET core a ASP.NET Core aplikace podporované pro určité události pouze (kontroler MVC, ADO.NET a HTTPClicent události) v místní ladění. Samostatný kolektor není podporována pro aplikace .NET Core nebo ASP.NET Core.<br />– Aplikace F # na experimentální bázi<br />– Aplikace UWP podporované pouze pro události |
| **Nepodporuje se** | -Ostatní jazyky a skript<br />– Windows Services, Silverlight, Xbox nebo [!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)] aplikace |

> [!NOTE]
> Pokud chcete ladit proces, který je již spuštěna, lze shromažďovat pouze události IntelliTrace (žádné informace volání). Můžete připojit k 32bitové nebo 64bitové proces v místním počítači. Shromažďují se události, ke kterým dojde před připojit k procesu.

##  <a name="IntelliTraceVSTraditional"></a> Proč ladit pomocí nástroje IntelliTrace?

Tradiční nebo *live* ladění zobrazuje pouze aplikace aktuální stav, s omezenými daty o minulých událostech. Buď musíte odvodit tyto události na základě aktuálního stavu aplikace, nebo musíte znovu vyvolat tyto události opětovného spuštění aplikace.

Nástroj IntelliTrace rozšiřuje toto tradiční ladění zaznamenáváním určitých událostí a dat v těchto bodech v čase. Díky tomu můžete zjistit, co se stalo ve vaší aplikaci bez restartování, zejména v případě, že jste již překročili kde je chyba. Nástroj IntelliTrace je ve výchozím nastavení zapnutý při tradičním ladění a shromažďuje data automaticky a transparentně. To umožňuje snadno přepínat mezi tradičním laděním a laděním pomocí nástroje IntelliTrace a zobrazovat zaznamenané informace. Zobrazit [funkce IntelliTrace](../debugger/intellitrace-features.md) a [jaká data shromažďuje nástroj IntelliTrace?](#WhatData)

Nástroj IntelliTrace vám také může pomoci ladit chyby, které je těžké reprodukovat nebo ke kterým dochází při nasazování. Můžete shromažďovat data IntelliTrace a ukládat je do souboru protokolu IntelliTrace (soubor .iTrace). Soubor .iTrace obsahuje podrobnosti o výjimkách, událostech souvisejících s výkonem, webových požadavcích, testovacích datech, vláknech, modulech a další systémové informace. Tento soubor otevřít v sadě Visual Studio Enterprise, vyberte nějakou položku a začít ladit nástrojem IntelliTrace. To vám umožní přejít na libovolnou událost v souboru a zobrazit konkrétní podrobnosti o vaší aplikaci v daném okamžiku v čase.

Můžete ukládat data IntelliTrace z těchto zdrojů:

- Relace IntelliTrace v systému Visual Studio 2017 Enterprise, Visual Studio 2015 Enterprise ani předchozích verzích sady Visual Studio Ultimate.

- Testovací relace v nástroji Microsoft Test Manager

- Webové aplikace ASP.NET jsou hostovány službou IIS, nebo SharePoint 2010 a SharePoint 2013 spuštěnými v nasazení při použití nástroje Microsoft Monitoring Agent, buď samostatně, nebo s nástrojem System Center 2012. Zobrazit [použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) a [sledování pomocí agenta Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).

  Zde je několik příkladů, jak nástroj IntelliTrace může pomoci s laděním:

- Vaše aplikace má poškozený datový soubor, ale nevíte, kdy k této události došlo.

     Bez nástroje IntelliTrace prohledat kód a najít všechny možné přístupy k souboru, umístit na tyto přístupy zarážky a znovu spusťte aplikaci najít, kde k problému došlo. Pomocí nástroje IntelliTrace zobrazí se všechny události shromážděné přístup k souborům a konkrétní podrobnosti o vaší aplikaci při každé události došlo.

- Dochází k výjimce.

     Bez nástroje IntelliTrace se zobrazí zpráva o výjimce, ale nemáte množství informací o událostech, které vedly k výjimce. Můžete prozkoumat zásobník volání a podívat se na řetězec volání, která vedla k výjimce, ale nelze zobrazit posloupnost událostí, ke kterým došlo během těchto volání. Pomocí nástroje IntelliTrace můžete zkoumat události, ke kterým došlo před výjimkou.

- Vaše aplikace dojde k chybě v testovacím počítači, ale funguje na vývojovém počítači.

     Můžete shromáždit data IntelliTrace z nástroje Microsoft Test Manager, uložit tato data do souboru .iTrace a připojit tento soubor k pracovní položce serveru Team Foundation Server pro pozdější zkoumání. Zobrazit [shromažďování více diagnostických dat v manuálních testech](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts) a [použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md).

- K chybě nebo selhání dochází v nasazené aplikaci.

     Pro aplikace Microsoftu založené na Azure můžete nakonfigurovat shromažďování dat IntelliTrace před publikováním aplikace. Zatímco je vaše aplikace spuštěná, IntelliTrace ukládá data do souboru .iTrace. Zobrazit [ladění publikované cloudové služby pomocí nástroje IntelliTrace a sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).

     V případě webových aplikací ASP.NET hostovaných ve službě IIS 7.0, 7.5 a 8.0 a aplikací služby SharePoint 2010 a SharePoint 2013 použijte nástroj Microsoft Monitoring Agent samotný nebo s nástrojem System Center 2012 k ukládání dat nástroje IntelliTrace do souboru .iTrace.

     To je užitečné, pokud chcete diagnostikovat problémy s aplikacemi v nasazení. Zobrazit [použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

##  <a name="WhatData"></a> Jaká data shromažďuje nástroj IntelliTrace?

**Shromažďování informací o události**

Ve výchozím nastavení nástroj IntelliTrace zaznamenává pouze události IntelliTrace: ladicí program událostmi, výjimkami, události rozhraní .NET Framework a další systémové události, které mohou pomoci s laděním. Můžete zvolit druhy událostí IntelliTrace, které chcete shromažďovat. Události ladicího programu a výjimky jsou shromažďovány vždy. Zobrazit [funkce IntelliTrace](../debugger/intellitrace-features.md).

- **Události ladicího programu**

     Nástroj IntelliTrace vždy zaznamenává události, ke kterým dochází v ladicím programu sady Visual Studio. Například spuštění vaší aplikace je událost ladicího programu. Další události ladicího programu patří události zastavení, které způsobují přerušení provádění aplikace. Například váš program narazí na zarážku, zarážku s trasováním nebo provede **krok** příkazu.

     Ve výchozím nastavení které vám pomůžou s výkonu, nezaznamenává nástroj IntelliTrace každou možnou hodnotu události ladicího programu. Zaznamenává pouze tyto hodnoty:

  - Hodnoty v **lokální** okna. Zachovat **lokální** otevřené pro tyto hodnoty vidět okno.

  - Hodnoty v **automatické hodnoty** okno pouze tehdy, pokud **automatické hodnoty** je otevřeno okno

  - Hodnoty v Datových tipech, které se zobrazují při přesunutí ukazatele myši nad proměnnou v okně zdroje s cílem zobrazit její hodnotu. Nástroj IntelliTrace neshromažďuje hodnoty v připnutých Datových tipech.

    Když je povolený režim události IntelliTrace a snímky, nástroj IntelliTrace se pořídit snímek proces aplikací na každý ladicí program **zarážku** a **krok** událostí. To bude zaznamenávat hodnoty v **lokální**, **automatické hodnoty**, a **Watch** windows, bez ohledu na to, jestli jsou systému windows otevřete nebo ne. Shromažďují se také hodnot v jakékoli připnutých datových tipech.

- **Výjimky**

     Nástroj IntelliTrace zaznamenává typ výjimky a zprávu pro tyto druhy výjimek:

    - Zpracované výjimky, když je výjimka vyvolána a zachycena

    - Nezpracované výjimky

- **Události rozhraní .NET framework**

   Standardně nástroj IntelliTrace zaznamenává nejběžnější události rozhraní .NET Framework. Například zkoušeného případě události zaškrtnutí políčka, nástroj IntelliTrace shromažďuje stav zaškrtávacího políčka a text.

- **Události aplikace SharePoint 2010 a SharePoint 2013**

     Můžete zaznamenat události uživatelského profilu a podmnožinu událostí sjednoceného systému protokolování (ULS) pro aplikace SharePoint 2010 a 2013 spuštěné mimo aplikaci Visual Studio. Tyto události můžete uložit do souboru .iTrace. Vyžaduje Visual Studio Enterprise 2017, Visual Studio Enterprise 2015, předchozí verze sady Visual Studio Ultimate, nebo [agenta Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) používané **trasování** režimu.

     Po otevření souboru .iTrace zadejte ID korelace SharePoint a najděte odpovídající webový požadavek, zobrazte zaznamenané události a spusťte ladění od určité události. Obsahuje-li soubor neošetřené výjimky, lze ID korelace vybrat pro ladění výjimky.

     Další informace:

    - [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)

    - [Návod: Ladění aplikace SharePoint s použitím technologie IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Zachycení snímků**

Můžete nakonfigurovat IntelliTrace k zachycení snímků na každé zarážce a kroku události ladicího programu. Nástroj IntelliTrace zaznamenává úplném stavu aplikace v jednotlivých snímků, které vám umožní zobrazit proměnné komplexní a vyhodnocujte výrazy.

Zobrazit [kontrolovat předchozí nové aplikace pomocí nástroje IntelliTrace](../debugger/view-historical-application-state.md).

**Shromažďovat informace o voláních funkcí**

Nástroj IntelliTrace můžete nakonfigurovat na shromažďování informací o volání funkcí. Tyto informace umožňují zobrazit historii zásobníku volání a umožňují krokovat zpět a vpřed mezi voláními v kódu. Pro každé volání funkce nástroj IntelliTrace zaznamenává tato data:

- Název funkce
- Hodnoty primitivních datových typů předané jako parametry na vstupech funkcí a vrácené na výstupech funkcí
- Hodnoty automatických vlastností při jejich čtení nebo změně
- Ukazatele na podřízené objekty první úrovně, avšak nikoli jejich hodnoty, ale pouze to, zda je jejich hodnota null

> [!NOTE]
> IntelliTrace shromažďuje pouze prvních 256 objektů v polích a prvních 256 znaků v řetězcích.

Zobrazit [Kontrola aplikace s využitím historického ladění](../debugger/historical-debugging-inspect-app.md).

**Shromažďování informací o modulech**

Pro řízení množství informací o voláních shromažďovaných nástrojem IntelliTrace zadejte pouze ty moduly, které vás zajímají. To může pomoci zvýšit výkon vaší aplikace během shromažďování. V části [řízení množství informací, které nástroj IntelliTrace shromažďuje](../debugger/intellitrace-features.md#ControlCallData) v funkce technologie IntelliTrace.

## <a name="AffectPerformance"></a> Moje aplikace zpomalí nástroj IntelliTrace?

Nástroj IntelliTrace standardně shromažďuje pouze data pro vybrané události IntelliTrace. To může nebo nemusí zpomalit aplikaci v závislosti na struktuře a organizaci kódu. Například pokud nástroj IntelliTrace zaznamenává událost často, může to zpomalit vaši aplikaci. Může mít také můžete zvážení refaktoringu vaší aplikace.

Shromažďování informací o voláních může aplikaci výrazně zpomalit. Může také dojít ke zvětšení všech souborů protokolu IntelliTrace (.iTrace) ukládaných na disk. Pro minimalizaci negativních dopadů shromažďujte informace o volání pouze u modulů, které vás zajímají.  Chcete-li změnit maximální velikost souborů .iTrace, přejděte na **nástroje**, **možnosti**, **IntelliTrace**, **Upřesnit**.

## <a name="in-this-section"></a>V tomto oddílu

[Funkce IntelliTrace](../debugger/intellitrace-features.md)

[Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md)

[Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)

### <a name="blogs"></a>Blogy

[Microsoft DevOps](https://blogs.msdn.microsoft.com/devops/)

### <a name="forums"></a>Diskuzní fóra

[Diagnostika sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)
