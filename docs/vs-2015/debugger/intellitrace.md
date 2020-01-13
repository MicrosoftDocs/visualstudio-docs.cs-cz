---
title: IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8c0a4269dcc2b7e647effb10432a984396f395d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918010"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější verzi tohoto tématu najdete na adrese [IntelliTrace](/visualstudio/debugger/intellitrace) .  
  
Můžete strávit méně času laděním aplikace, když použijete IntelliTrace k záznamu a trasování historie spouštění kódu. Chyby lze snadno najít, protože vám IntelliTrace umožňuje:  
  
- Zaznamenat konkrétní události  
  
   Kontrola souvisejícího kódu, data zobrazená v okně **místní** hodnoty během událostí ladicího programu a informace o volání funkce  
  
- Ladění chyb, které je těžké reprodukována nebo ke které dochází v nasazení  
  
  IntelliTrace můžete použít v edici Visual Studio Enterprise (ale ne v edicích Professional nebo Community).  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
|||  
|-|-|  
|**Ladit moje aplikace pomocí IntelliTrace:**<br /><br /> -Zobrazit minulé události.<br />-Zobrazit informace o volání s minulými událostmi.<br />-Uložit moji relaci IntelliTrace.<br />– Řízení dat, která IntelliTrace shromažďuje.|-   [Návod: použití IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Funkce IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Konfigurace IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [historické ladění](../debugger/historical-debugging.md)|  
|**Shromažďovat data IntelliTrace během testovací relace v Test Manager**|-   [shromažďovat další diagnostická data v ručních testech](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Shromažďovat data IntelliTrace z nasazených aplikací**|-   [používání samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Spustí ladění ze souboru protokolu IntelliTrace (soubor. iTrace).**|-   [pomocí uložených dat IntelliTrace](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="IntelliTraceSupport"></a>Jaké aplikace je možné ladit pomocí IntelliTrace?  
  
|||  
|-|-|  
|**Podporuje se**|– Visual Basic a vizuální C# aplikace, které používají .NET Framework 2,0 nebo vyšší verze.<br />     Můžete ladit většinu aplikací, včetně ASP.NET, Microsoft Azure, model Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 a 64-bit Apps.<br />     Chcete-li ladit aplikace služby SharePoint pomocí IntelliTrace, přečtěte si [Návod: ladění aplikace služby SharePoint pomocí IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Pokud chcete ladit Microsoft Azure aplikace pomocí IntelliTrace, přečtěte si téma [Ladění publikované cloudové služby pomocí IntelliTrace a sady Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Omezená podpora**|– F# aplikace na experimentální bázi<br />– Aplikace pro Windows Store podporované jenom pro události|  
|**Nepodporuje se**|– C++, jiné jazyky a skript<br />– Služby Windows, Silverlight, Xbox nebo [!INCLUDE[winmobile](../includes/winmobile-md.md)] aplikací|  
  
> [!NOTE]
> Pokud chcete ladit proces, který je již spuštěn, nelze použít nástroj IntelliTrace. Nástroj IntelliTrace je nutné spustit při spuštění procesu.  
  
## <a name="IntelliTraceVSTraditional"></a>Proč ladit pomocí IntelliTrace?  
 Tradiční nebo *živé* ladění zobrazuje pouze aktuální stav vaší aplikace s omezenými daty o minulých událostech. Buď musíte tyto události odvodit na základě aktuálního stavu aplikace, nebo musíte tyto události znovu vytvořit tak, že aplikaci znovu spustíte.  
  
 Nástroj IntelliTrace rozšiřuje toto tradiční ladění zaznamenáváním určitých událostí a dat v těchto bodech v čase. To vám umožní zjistit, co se stalo ve vaší aplikaci, aniž byste je museli restartovat, zejména pokud jste v minulosti poznamenali chybu. Nástroj IntelliTrace je ve výchozím nastavení zapnutý při tradičním ladění a shromažďuje data automaticky a transparentně. To umožňuje snadno přepínat mezi tradičním laděním a laděním pomocí nástroje IntelliTrace a zobrazovat zaznamenané informace. Podívejte se na [funkce IntelliTrace](../debugger/intellitrace-features.md) a [jaká data shromažďuje IntelliTrace?](#WhatData)  
  
 Nástroj IntelliTrace vám také může pomoci ladit chyby, které je těžké reprodukovat nebo ke kterým dochází při nasazování. Můžete shromažďovat data IntelliTrace a ukládat je do souboru protokolu IntelliTrace (soubor .iTrace). Soubor .iTrace obsahuje podrobnosti o výjimkách, událostech souvisejících s výkonem, webových požadavcích, testovacích datech, vláknech, modulech a další systémové informace. Tento soubor můžete otevřít v Visual Studio Enterprise, vybrat položku a spustit ladění pomocí IntelliTrace. To vám umožní přejít na libovolnou událost v souboru a zobrazit konkrétní podrobnosti o vaší aplikaci v daném časovém okamžiku.  
  
 Můžete ukládat data IntelliTrace z těchto zdrojů:  
  
- Relace IntelliTrace v aplikaci Visual Studio 2015 Enterprise nebo předchozích verzích Visual Studio Ultimate.  
  
- Testovací relace v Microsoft Test Manager  
  
- Webové aplikace ASP.NET jsou hostovány službou IIS, nebo SharePoint 2010 a SharePoint 2013 spuštěnými v nasazení při použití nástroje Microsoft Monitoring Agent, buď samostatně, nebo s nástrojem System Center 2012. Viz [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) a [monitorování pomocí Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
  Zde je několik příkladů, jak nástroj IntelliTrace může pomoci s laděním:  
  
- Vaše aplikace má poškozený datový soubor, ale nevíte, kde k této události došlo.  
  
   Bez IntelliTrace je nutné projít kód, abyste našli všechny možné přístupy k souborům, vložili zarážky do těchto přístupů a znovu spustíte aplikaci, abyste zjistili, kde k problému došlo. Pomocí IntelliTrace můžete zobrazit všechny shromážděné události přístupu k souboru a konkrétní podrobnosti o vaší aplikaci, kdy došlo k každé události.  
  
- Dochází k výjimce.  
  
   Bez nástroje IntelliTrace se zobrazí zpráva o výjimce, nemáte ale mnoho informací o událostech, které k výjimce vedly. Můžete prozkoumat zásobník volání a podívat se na řetězec volání, která vedla k výjimce, ale nelze zobrazit posloupnost událostí, ke kterým došlo během těchto volání. Pomocí nástroje IntelliTrace můžete zkoumat události, ke kterým došlo před výjimkou.  
  
- Vaše aplikace selže na testovacím počítači, ale je úspěšně spuštěna ve vývojovém počítači.  
  
   Můžete shromáždit data IntelliTrace z nástroje Microsoft Test Manager, uložit tato data do souboru .iTrace a připojit tento soubor k pracovní položce serveru Team Foundation Server pro pozdější zkoumání. Viz [shromažďování více diagnostických dat v ručních testech](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) a [používání uložených IntelliTrace dat](../debugger/using-saved-intellitrace-data.md).  
  
- K chybě nebo selhání dojde v nasazené aplikaci.  
  
   Pro aplikace založené na Microsoft Azure můžete nakonfigurovat shromažďování dat IntelliTrace před publikováním aplikace. Když je vaše aplikace spuštěná, IntelliTrace ukládá data do souboru. iTrace. Zobrazit [ladění publikované cloudové služby pomocí nástroje IntelliTrace a sady Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   V případě webových aplikací ASP.NET hostovaných ve službě IIS 7.0, 7.5 a 8.0 a aplikací služby SharePoint 2010 a SharePoint 2013 použijte nástroj Microsoft Monitoring Agent samotný nebo s nástrojem System Center 2012 k ukládání dat nástroje IntelliTrace do souboru .iTrace.  
  
   To je užitečné, pokud chcete diagnostikovat problémy s aplikacemi v nasazení. Viz [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a>Jaká data shromažďuje IntelliTrace?  
 **Shromažďování informací o událostech**  
  
 Ve výchozím nastavení IntelliTrace zaznamenává pouze události IntelliTrace: události ladicího programu, výjimky, události .NET Framework a další systémové události, které vám mohou při ladění pomáhat. Můžete zvolit druhy událostí IntelliTrace, které chcete shromažďovat. Události ladicího programu a výjimky jsou shromažďovány vždy. Viz [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Události ladicího programu**  
  
   Nástroj IntelliTrace vždy zaznamenává události, ke kterým dochází v ladicím programu sady Visual Studio. Například spuštění aplikace je událost ladicího programu. Mezi další události ladicího programu patří události zastavení, které způsobují přerušení provádění vaší aplikace. Například váš program narazí na zarážku, narazí na zarážka s trasováním nebo provede příkaz **kroku** .  
  
   Aby nedocházelo k poklesu výkonu, nezaznamenává nástroj IntelliTrace každou možnou hodnotu události ladicího programu. Zaznamenává pouze tyto hodnoty:  
  
  - Hodnoty v okně **místních** hodnot. Ponechte okno **místní** hodnoty otevřené, aby se zobrazily tyto hodnoty.  
  
  - Hodnoty v okně **Automatické** hodnoty, pokud je okno **Automatické** hodnoty otevřené.  
  
  - Hodnoty v Datových tipech, které se zobrazují při přesunutí ukazatele myši nad proměnnou v okně zdroje s cílem zobrazit její hodnotu. Nástroj IntelliTrace neshromažďuje hodnoty v připnutých Datových tipech.  
  
- **Výjimky**  
  
   Nástroj IntelliTrace zaznamenává typ výjimky a zprávu pro tyto druhy výjimek:  
  
  - Zpracované výjimky, když je výjimka vyvolána a zachycena  
  
  - Nezpracované výjimky  
  
- **Události .NET Framework**  
  
   Standardně nástroj IntelliTrace zaznamenává nejběžnější události rozhraní .NET Framework. Příklad:  
  
  - V případě události Přístup k souboru nástroj IntelliTrace shromažďuje název souboru.  
  
  - V případě události Zaškrtnutí políčka shromažďuje nástroj IntelliTrace stav zaškrtávacího políčka a text.  
  
- **Události aplikace SharePoint 2010 a SharePoint 2013**  
  
   Můžete zaznamenat události uživatelského profilu a podmnožinu událostí sjednoceného systému protokolování (ULS) pro aplikace SharePoint 2010 a 2013 spuštěné mimo aplikaci Visual Studio. Tyto události můžete uložit do souboru .iTrace. Vyžaduje Visual Studio Enterprise 2015, předchozí verzi Visual Studio Ultimate nebo [Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkID=309771) spuštěnou v režimu **trasování** .  
  
   Po otevření souboru .iTrace zadejte ID korelace SharePoint a najděte odpovídající webový požadavek, zobrazte zaznamenané události a spusťte ladění od určité události. Obsahuje-li soubor neošetřené výjimky, lze ID korelace vybrat pro ladění výjimky.  
  
   Další informace:  
  
  - [Použití samostatného kolektoru IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
  - [Návod: Ladění aplikace SharePoint s použitím technologie IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Shromažďování informací o volání funkcí**  
  
  Nástroj IntelliTrace můžete nakonfigurovat na shromažďování informací o volání funkcí. Tyto informace umožňují zobrazit historii zásobníku volání a umožňují krokovat zpět a vpřed mezi voláními v kódu. Pro každé volání funkce nástroj IntelliTrace zaznamenává tato data:  
  
- Název funkce  
  
- Hodnoty primitivních datových typů předané jako parametry na vstupech funkcí a vrácené na výstupech funkcí  
  
- Hodnoty automatických vlastností při jejich čtení nebo změně  
  
- Ukazatele na podřízené objekty první úrovně, avšak nikoli jejich hodnoty, ale pouze to, zda je jejich hodnota null  
  
> [!NOTE]
> IntelliTrace shromažďuje pouze prvních 256 objektů v polích a prvních 256 znaků v řetězcích.  
  
 Viz [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Shromažďují se informace o modulu.**  
  
 Pro řízení množství informací o voláních shromažďovaných nástrojem IntelliTrace zadejte pouze ty moduly, které vás zajímají. To může pomoci vylepšit výkon aplikace během shromažďování. Viz [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a>Bude IntelliTrace zpomalit aplikaci?  
 Nástroj IntelliTrace standardně shromažďuje pouze data pro vybrané události IntelliTrace. To může nebo nemusí zpomalit aplikaci v závislosti na struktuře a organizaci kódu. Například pokud IntelliTrace eviduje událost často, může to zpomalit vaši aplikaci. Také může být vhodné zvážit refaktoring vaší aplikace.  
  
 Shromažďování informací o voláních může výrazně zpomalit vaši aplikaci. Může také dojít ke zvětšení všech souborů protokolu IntelliTrace (.iTrace) ukládaných na disk. Pro minimalizaci negativních dopadů shromažďujte informace o volání pouze u modulů, které vás zajímají.  Chcete-li změnit maximální velikost souborů. iTrace, přejděte na **nástroje**, **Možnosti**, **IntelliTrace**, **Upřesnit**. Viz [Configure IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Konfigurace IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Zahrnutí diagnostických dat trasování s chybami, které se obtížně reprodukovaly](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnostika problémů po nasazení](../debugger/diagnose-problems-after-deployment.md)  
  
 [Použití uložených dat řešení IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogy  
 [Visual Studio ALM + Team Foundation Server](https://blogs.msdn.com/b/visualstudioalm)  
  
### <a name="forums"></a>Diskuzní fóra  
 [Diagnostika sady Visual Studio](https://social.msdn.microsoft.com/Forums/vsdebug)
