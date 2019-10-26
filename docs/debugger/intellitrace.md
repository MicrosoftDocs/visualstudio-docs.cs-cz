---
title: IntelliTrace | Microsoft Docs
ms.date: 09/19/2018
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
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2be69003d14d2c246f95249b5db0b1fa7d470598
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911441"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>IntelliTrace pro Visual Studio Enterprise (C#, Visual Basic, C++)

Můžete strávit méně času laděním aplikace, když použijete IntelliTrace k záznamu a trasování historie spouštění kódu. Chyby lze snadno najít, protože vám IntelliTrace umožňuje:

- Zaznamenat konkrétní události

- Kontrola souvisejícího kódu, data zobrazená v okně **místní** hodnoty během událostí ladicího programu a informace o volání funkce

- Ladění chyb, které je těžké reprodukována nebo ke které dochází v nasazení

IntelliTrace můžete použít v edici Visual Studio Enterprise (ale ne v edicích Professional nebo Community).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

|||
|-|-|
|**Ladit moje aplikace pomocí IntelliTrace:**<br /><br /> -Zobrazit minulé události.<br />-Zobrazit informace o volání s minulými událostmi.<br />-Uložit moji relaci IntelliTrace.<br />– Řízení dat, která IntelliTrace shromažďuje.|- [zkontrolovat předchozí stavy aplikace pomocí IntelliTrace](../debugger/view-historical-application-state.md)<br />- [Návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [funkce IntelliTrace](../debugger/intellitrace-features.md)<br />- [historické ladění](../debugger/historical-debugging.md)|
|**Shromažďovat data IntelliTrace z nasazených aplikací**|- [používání samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Spustí ladění ze souboru protokolu IntelliTrace (soubor. iTrace).**|- [pomocí uložených dat IntelliTrace](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a>Jaké aplikace je možné ladit pomocí IntelliTrace?

| | |
|---------------------| - |
| **Plná podpora** | – Visual Basic a vizuální C# aplikace, které používají .NET Framework 2,0 nebo vyšší verze.<br/>Můžete ladit většinu aplikací, včetně ASP.NET, Microsoft Azure, model Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 a 64-bit Apps.<br/>Chcete-li ladit aplikace služby SharePoint pomocí IntelliTrace, přečtěte si [Návod: ladění aplikace služby SharePoint pomocí IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Pokud chcete ladit Microsoft Azure aplikace pomocí IntelliTrace, přečtěte si téma [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Omezená podpora** | – C++ aplikace cílené na podporu systému Windows zobrazení snímků pomocí IntelliTrace kroků zpět. Jsou podporovány pouze události ladicího programu a výjimky.<br />– Rozhraní .NET Core a aplikace ASP.NET Core podporují jenom určité události (kontroler MVC, ADO.NET a HTTPClient události) v místním ladění. Samostatný kolektor není pro aplikace .NET Core ani ASP.NET Core podporován.<br />– F# aplikace na experimentální bázi<br />– Aplikace pro UWP podporované jenom pro události |
| **Nepodporováno** | – Ostatní jazyky a skript<br />– Služby Windows, Silverlight, Xbox nebo Windows Mobile Apps |

> [!NOTE]
> Pokud chcete ladit proces, který je již spuštěn, můžete shromažďovat pouze události IntelliTrace (žádné informace o volání). K procesu 32 nebo 64 se můžete připojit pouze v místním počítači. Události, ke kterým dojde před připojením k procesu, nejsou shromažďovány.

## <a name="IntelliTraceVSTraditional"></a>Proč ladit pomocí IntelliTrace?

Tradiční nebo *živé* ladění zobrazuje pouze aktuální stav vaší aplikace s omezenými daty o minulých událostech. Buď musíte tyto události odvodit na základě aktuálního stavu aplikace, nebo musíte tyto události znovu vytvořit tak, že aplikaci znovu spustíte.

Nástroj IntelliTrace rozšiřuje toto tradiční ladění zaznamenáváním určitých událostí a dat v těchto bodech v čase. To vám umožní zjistit, co se stalo ve vaší aplikaci, aniž byste je museli restartovat, zejména pokud jste v minulosti poznamenali chybu. Nástroj IntelliTrace je ve výchozím nastavení zapnutý při tradičním ladění a shromažďuje data automaticky a transparentně. To umožňuje snadno přepínat mezi tradičním laděním a laděním pomocí nástroje IntelliTrace a zobrazovat zaznamenané informace. Podívejte se na [funkce IntelliTrace](../debugger/intellitrace-features.md) a [jaká data shromažďuje IntelliTrace?](#WhatData)

Nástroj IntelliTrace vám také může pomoci ladit chyby, které je těžké reprodukovat nebo ke kterým dochází při nasazování. Můžete shromažďovat data IntelliTrace a ukládat je do souboru protokolu IntelliTrace (soubor .iTrace). Soubor .iTrace obsahuje podrobnosti o výjimkách, událostech souvisejících s výkonem, webových požadavcích, testovacích datech, vláknech, modulech a další systémové informace. Tento soubor můžete otevřít v Visual Studio Enterprise, vybrat položku a spustit ladění pomocí IntelliTrace. To vám umožní přejít na libovolnou událost v souboru a zobrazit konkrétní podrobnosti o vaší aplikaci v daném časovém okamžiku.

Můžete ukládat data IntelliTrace z těchto zdrojů:

- Relace IntelliTrace v aplikaci Visual Studio 2015 Enterprise nebo novějších verzích nebo v předchozích verzích Visual Studio Ultimate.

- Webové aplikace ASP.NET jsou hostovány službou IIS, nebo SharePoint 2010 a SharePoint 2013 spuštěnými v nasazení při použití nástroje Microsoft Monitoring Agent, buď samostatně, nebo s nástrojem System Center 2012. Viz [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) a [monitorování pomocí Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).

Zde je několik příkladů, jak nástroj IntelliTrace může pomoci s laděním:

- Vaše aplikace má poškozený datový soubor, ale nevíte, kde k této události došlo.

  Bez IntelliTrace je nutné projít kód, abyste našli všechny možné přístupy k souborům, vložili zarážky do těchto přístupů a znovu spustíte aplikaci, abyste zjistili, kde k problému došlo. Pomocí IntelliTrace můžete zobrazit všechny shromážděné události přístupu k souboru a konkrétní podrobnosti o vaší aplikaci, kdy došlo k každé události.

- Dochází k výjimce.

  Bez IntelliTrace obdržíte zprávu o výjimce, ale nemáte mnoho informací o událostech, které vedly k výjimce. Můžete prozkoumávat zásobník volání a zobrazit řetěz volání, která vedla k výjimce, ale nelze zobrazit posloupnost událostí, ke kterým došlo během těchto volání. Pomocí nástroje IntelliTrace můžete zkoumat události, ke kterým došlo před výjimkou.

- K chybě nebo selhání dojde v nasazené aplikaci.

  Pro aplikace založené na Microsoft Azure můžete nakonfigurovat shromažďování dat IntelliTrace před publikováním aplikace. Když je vaše aplikace spuštěná, IntelliTrace ukládá data do souboru. iTrace. Viz [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

  V případě webových aplikací ASP.NET hostovaných ve službě IIS 7.0, 7.5 a 8.0 a aplikací služby SharePoint 2010 a SharePoint 2013 použijte nástroj Microsoft Monitoring Agent samotný nebo s nástrojem System Center 2012 k ukládání dat nástroje IntelliTrace do souboru .iTrace.

  To je užitečné, pokud chcete diagnostikovat problémy s aplikacemi v nasazení. Viz [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="WhatData"></a>Jaká data shromažďuje IntelliTrace?

**Shromažďovat informace o událostech**

Ve výchozím nastavení IntelliTrace zaznamenává pouze události IntelliTrace: události ladicího programu, výjimky, události .NET Framework a další systémové události, které vám mohou při ladění pomáhat. Můžete zvolit druhy událostí IntelliTrace, které chcete shromažďovat. Události ladicího programu a výjimky jsou shromažďovány vždy. Viz [funkce IntelliTrace](../debugger/intellitrace-features.md).

- **Události ladicího programu**

  Nástroj IntelliTrace vždy zaznamenává události, ke kterým dochází v ladicím programu sady Visual Studio. Například spuštění aplikace je událost ladicího programu. Mezi další události ladicího programu patří události zastavení, které způsobují přerušení provádění vaší aplikace. Například váš program narazí na zarážku, narazí na zarážka s trasováním nebo provede příkaz **kroku** .

  Ve výchozím nastavení IntelliTrace nezaznamenává všechny možné hodnoty události ladicího programu. Zaznamenává pouze tyto hodnoty:

  - Hodnoty v okně **místních** hodnot. Ponechte okno **místní** hodnoty otevřené, aby se zobrazily tyto hodnoty.

  - Hodnoty v okně **Automatické** hodnoty, pokud je okno **Automatické** hodnoty otevřené.

  - Hodnoty v Datových tipech, které se zobrazují při přesunutí ukazatele myši nad proměnnou v okně zdroje s cílem zobrazit její hodnotu. Nástroj IntelliTrace neshromažďuje hodnoty v připnutých Datových tipech.

    Když je povolený IntelliTrace událost a režim snímků, IntelliTrace pořídí snímek procesu aplikace v každé **zarážce** ladicího programu a událost **kroku** . Tato akce zaznamená hodnoty v oknech **místní**hodnoty, **Automatické**hodnoty a **kukátka** bez ohledu na to, zda jsou okna otevřená nebo nikoli. Budou se shromažďovat i hodnoty v jakýchkoli připnutých popisech dat.

- **Výjimky**

  Nástroj IntelliTrace zaznamenává typ výjimky a zprávu pro tyto druhy výjimek:

  - Zpracované výjimky, když je výjimka vyvolána a zachycena

  - Nezpracované výjimky

- **Události .NET Framework**

  Standardně nástroj IntelliTrace zaznamenává nejběžnější události rozhraní .NET Framework. Například pro událost <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> shromažďuje IntelliTrace stav zaškrtávacího políčka a text.

- **Události aplikace SharePoint 2010 a SharePoint 2013**

  Můžete zaznamenat události uživatelského profilu a podmnožinu událostí sjednoceného systému protokolování (ULS) pro aplikace SharePoint 2010 a 2013 spuštěné mimo aplikaci Visual Studio. Tyto události můžete uložit do souboru .iTrace. Vyžaduje Visual Studio Enterprise 2015 nebo novější verze, předchozí verzi Visual Studio Ultimate nebo [Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316) spuštěnou v režimu **trasování** .

  Po otevření souboru .iTrace zadejte ID korelace SharePoint a najděte odpovídající webový požadavek, zobrazte zaznamenané události a spusťte ladění od určité události. Obsahuje-li soubor neošetřené výjimky, lze ID korelace vybrat pro ladění výjimky.

  Další informace:

  - [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)

  - [Návod: Ladění aplikace SharePoint s použitím technologie IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Zachytit snímky**

IntelliTrace můžete nakonfigurovat tak, aby zachytí snímky při každé události zarážky a kroku ladicího programu. IntelliTrace zaznamenává úplný stav aplikace v každém snímku, který umožňuje zobrazit složité proměnné a vyhodnotit výrazy.

> [!NOTE]
> [Samostatný kolektor IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) nepodporuje zachytávání snímků.

Podívejte se na téma [Kontrola předchozích stavů aplikace pomocí IntelliTrace](../debugger/view-historical-application-state.md).

**Shromáždit informace o volání funkce**

Nástroj IntelliTrace můžete nakonfigurovat na shromažďování informací o volání funkcí. Tyto informace umožňují zobrazit historii zásobníku volání a umožňují krokovat zpět a vpřed mezi voláními v kódu. Pro každé volání funkce nástroj IntelliTrace zaznamenává tato data:

- Název funkce
- Hodnoty primitivních datových typů předané jako parametry na vstupech funkcí a vrácené na výstupech funkcí
- Hodnoty automatických vlastností při jejich čtení nebo změně
- Ukazatele na podřízené objekty první úrovně, avšak nikoli jejich hodnoty, ale pouze to, zda je jejich hodnota null

> [!NOTE]
> IntelliTrace shromažďuje pouze prvních 256 objektů v polích a prvních 256 znaků v řetězcích.

Podívejte [se na téma Kontrola aplikace pomocí historických ladění](../debugger/historical-debugging-inspect-app.md).

**Shromáždit informace o modulu**

Pro řízení množství informací o voláních shromažďovaných nástrojem IntelliTrace zadejte pouze ty moduly, které vás zajímají. To může pomoci vylepšit výkon aplikace během shromažďování. V části najdete [informace o tom, kolik informací IntelliTrace shromažďuje](../debugger/intellitrace-features.md#ControlCallData) ve funkcích IntelliTrace.

## <a name="AffectPerformance"></a>Bude IntelliTrace zpomalit aplikaci?

Nástroj IntelliTrace standardně shromažďuje pouze data pro vybrané události IntelliTrace. To může nebo nemusí zpomalit aplikaci v závislosti na struktuře a organizaci kódu. Například pokud IntelliTrace eviduje událost často, může to zpomalit vaši aplikaci. Také může být vhodné zvážit refaktoring vaší aplikace.

Shromažďování informací o voláních může výrazně zpomalit vaši aplikaci. Může také dojít ke zvětšení všech souborů protokolu IntelliTrace (.iTrace) ukládaných na disk. Pro minimalizaci negativních dopadů shromažďujte informace o volání pouze u modulů, které vás zajímají.  Chcete-li změnit maximální velikost souborů. iTrace, přejděte na **nástroje**, **Možnosti**, **IntelliTrace**, **Upřesnit**.

### <a name="blogs"></a>Blogy

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Diskuzní fóra

[Diagnostika sady Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)
