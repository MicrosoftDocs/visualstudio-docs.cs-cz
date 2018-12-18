---
title: Nástroje pro profilaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 380e98a8cd52fe77486dae245eee910a65a41057
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782099"
---
# <a name="profiling-tools"></a>Nástroje pro profilaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profilace a Diagnostika nástroje pomáhají diagnostikovat paměť a využití procesoru a dalších problémů na úrovni aplikací. Pomocí těchto nástrojů můžete shromažďování dat (třeba hodnoty proměnných, volání funkce a událostí) za čas, kdy spustíte svou aplikaci v ladicím programu. Můžete zobrazit stav vaší aplikace v různých fázích během provádění kódu.  
  
 Podívejte se na souhrn v dolní části můžete zobrazit, jaké nástroje jsou k dispozici pro váš typ projektu (například plocha, UPW, technologie ASP.NET).  
  
 Dostanete pomocí nástrojů pro profilaci **ladění / Windows / zobrazit diagnostické nástroje** při použití nástroje během vaší relace ladění nebo s použitím **ladění / Profiler výkonu...**  jak provádět analýzu cílené výkonu.  Zobrazit [spuštění profilování nástroje s nebo bez ladicího programu](../profiling/running-profiling-tools-with-or-without-the-debugger.md) Další informace o různých přístupů.  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Zobrazit [co je nového v nástrojích pro profilaci](../profiling/what-s-new-in-profiling-tools.md) Další informace o nových funkcích pro tuto verzi.  
  
 Následující části popisují jiné výkonové nástroje, které jsou k dispozici v sadě Visual Studio.  
  
## <a name="memory-usage"></a>Využití paměti  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Vyhledání nevrácené paměti a neefektivní paměti během ladění s **využití paměti** nástroj. Nástroj umožňuje pořizovat snímky paměti spravovaný a nativní haldě. Tento nástroj můžete použít s aplikací klasické pracovní plochy, Windows Universal apps a aplikací ASP.NET. **Využití paměti** nástroj můžete spustit z **diagnostické nástroje** okno při ladění (**ladění / Windows / zobrazit diagnostické nástroje**) nebo mimo ladicí program (**Ladění / Profiler výkonu...**). Zobrazit [využití paměti](../profiling/memory-usage.md) a [využití paměti bez ladění](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) Další informace.  
  
## <a name="cpu-usage"></a>Využití procesoru  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **Využití procesoru** nástroj ukazuje, kde procesor stráví doba provádění C++, C# / VB a kód jazyka JavaScript.  Tento nástroj můžete použít s jak desktop a Windows Universal apps, tak i aplikací Azure App Services. **Využití procesoru** nástroj můžete spustit z **diagnostické nástroje** okno při ladění (**ladění / Windows / zobrazit diagnostické nástroje**) nebo mimo ladicí program (**Ladění / Profiler výkonu...**). Zobrazit [využití procesoru](../profiling/cpu-usage.md) Další informace.  
  
## <a name="performance-explorer"></a>Prohlížeč výkonu  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Prohlížeč výkonu** (**ladění / Profiler a prohlížeč výkonu**) umožňuje použít řadu různých nástrojů, včetně **vzorkování procesoru**,  **Instrumentace**, **alokaci paměti .NET**, a **kolize prostředků**. Pomocí nástrojů prohlížeče výkonu s aplikací klasické pracovní plochy a aplikace v ASP.NET, ale ne Windows Universal apps. Další informace najdete v tématu [prohlížeč výkonu](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>Využití GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Použití [využití GPU](../debugger/gpu-usage.md) nástroje pro lepší pochopení využití vysoké úrovně hardwaru aplikace Direct3D. Tento nástroj můžete použít s desktop a Windows Universal apps ale není aplikace v ASP.NET. **Využití GPU** nástroj můžete spustit z **diagnostické nástroje** okno při ladění (**ladění / zobrazit diagnostické nástroje**) nebo mimo ladicí program (**Ladění / Profiler výkonu...**).  
  
## <a name="application-timeline"></a>Časová osa aplikace  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Časová osa aplikace](../profiling/application-timeline.md) nástroj pomáhá zlepšit výkon aplikací XAML tím, že poskytuje podrobné zobrazení využití prostředků. Můžete použít **časová osa aplikace** s desktop a Windows Universal apps, ale ne aplikace technologie ASP.NET. **Časová osa aplikace** nástroj můžete spustit z **diagnostické nástroje** okno (**ladění / Profiler výkonu...** ).  
  
## <a name="perftips"></a>Tipy pro výkon  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Pokud ladicí program zastaví provedení u zarážky a krokování operace, uplynulý čas přerušení od předchozí zarážky se zobrazí jako popis tlačítka v okně editoru. Tyto [tipy pro výkon](../profiling/perftips.md) dozvíte, jak monitorovat a analyzovat výkon vaší aplikace během ladění. Můžete zobrazit **tipy pro výkon** v desktopu, Windows Universal a aplikací ASP.NET.  
  
## <a name="javascript-memory"></a>Paměti jazyka JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [Paměti jazyka JavaScript](../profiling/javascript-memory.md) nástroj umožňuje měřit, vyhodnotit a řešit problémy související s výkonem ve vašem kódu pomocí shromažďování informací o časování v vstupu a výstupu jednotlivých funkcí ve vaší aplikaci. Tento nástroj můžete použít s aplikacemi pro Windows Universal HTML. **Časování funkcí jazyka JavaScript** nástroj můžete spustit z **diagnostické nástroje** okno (**ladění / Profiler výkonu...** ).  
  
## <a name="html-ui-responsiveness"></a>Rychlost odezvy HTML UI  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [Rychlost odezvy HTML UI](../profiling/html-ui-responsiveness.md) nástroj pomáhá izolovat problémy s výkonem v aplikacích, včetně nedostatečné rychlost odezvy, pomalé načítání času, a časté vizuální aktualizace, které jsou menší, než se očekávalo. Tento nástroj můžete použít s aplikacemi pro Windows Universal HTML. **Rychlosti odezvy uživatelského rozhraní HTML** nástroj můžete spustit z **diagnostické nástroje** okno (**ladění / Profiler výkonu...** ).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) umožňuje zaznamenat konkrétní události, zkontrolujte data v **lokální** okno během událostí ladicího programu a volání funkce a debug – chyby, které je těžké reprodukovat.  Nástroj IntelliTrace je primárně ladicí nástroj, ale také poskytuje informace, které lze použít pro vyšetřování výkonu. Tento nástroj v sadě Visual Studio Enterprise, můžete použít s plochy, Windows Universal a aplikace C# ASP.NET. Můžete najít v IntelliTrace **diagnostické nástroje** okno při ladění (**ladění / Windows / zobrazit diagnostické nástroje**).  
  
## <a name="profiling-in-production"></a>Profilace v produkčním prostředí  
 Doporučený postup pro profilování v produkčním prostředí, je provádět profilaci z [příkazového řádku pomocí vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) shromažďovat profil využití procesoru. Podpora vzdáleného profilování ve službě Azure App Service, můžete provádět profilaci prostřednictvím [Průzkumníku serveru nebo webu Kudu Portal](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Jaké nástroje můžu použít?  
 Tady je tabulka, která obsahuje seznam různých nástrojů, které nabízí Visual Studio a různých typech projektů je můžete využít s:  
  
|Nástroje výkonu|Plocha Windows|Windows Universal/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Využití paměti](../profiling/memory-usage.md)|Ano|Ano|Ne|  
|[Využití procesoru](../profiling/cpu-usage.md)|Ano|Ano|Pouze Azure App Service|  
|[Využití GPU](../debugger/gpu-usage.md)|Ano|Ano|Ne|  
|[Časová osa aplikace](../profiling/application-timeline.md)|Ano|Ano|Ne|  
|[Tipy pro výkon](../profiling/perftips.md)|Ano|Ano pro XAML, ne pro kód HTML|Ne|  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ano|Ne|Ano|  
|[IntelliTrace](../debugger/intellitrace.md)|Pouze .NET Enterprise|Pouze .NET Enterprise|Pouze .NET Enterprise|  
|[Rychlost odezvy uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md)|Ne|Ano pro kód HTML, ne pro XAML|Ne|  
|[Paměť JavaScriptu](../profiling/javascript-memory.md)|Ne|Ano pro kód HTML, ne pro XAML|Ne|  
  
## <a name="see-also"></a>Viz také  
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)



