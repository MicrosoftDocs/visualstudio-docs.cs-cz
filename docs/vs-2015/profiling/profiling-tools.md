---
title: Nástroje pro profilaci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcb230532da4a0b84ea0102d86534c28afe35558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686274"
---
# <a name="profiling-tools"></a>Nástroje pro profilaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje pro profilaci a diagnostiku vám pomohou diagnostikovat využití paměti a procesoru a další problémy na úrovni aplikace. Pomocí těchto nástrojů můžete shromažďovat data (například hodnoty proměnných, volání funkcí a události) v době, kdy spustíte aplikaci v ladicím programu. Stav aplikace můžete zobrazit v různých okamžicích během provádění kódu.  
  
 Podívejte se na shrnutí v dolní části a zjistěte, jaké nástroje jsou k dispozici pro váš typ projektu (například Desktop, UWP, ASP.NET).  
  
 K nástrojům pro profilaci můžete přistupovat pomocí příkazu **Debug/Windows/Show diagnostické nástroje** k použití nástrojů během relace ladění nebo pomocí **profileru ladění/výkonu** ... k provedení cílené analýzy výkonu.  Další informace o různých metodách naleznete v tématu [spuštění nástroje pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Další informace o nových funkcích této verze najdete [v tématu Novinky v nástroje pro profilaci](../profiling/what-s-new-in-profiling-tools.md) .  
  
 V následujících částech jsou popsány různé nástroje pro výkon, které jsou k dispozici v aplikaci Visual Studio.  
  
## <a name="memory-usage"></a>Využití paměti  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Při ladění pomocí nástroje **využití paměti** Najděte nevracení paměti a neefektivní paměť. Nástroj umožňuje pořizovat snímky haldy spravované a nativní paměti. Tento nástroj můžete použít u aplikací klasické pracovní plochy, univerzálních aplikací pro Windows a aplikací ASP.NET. Nástroj **využití paměti** lze spustit z okna **diagnostické nástroje** při ladění (**ladění/Windows/show diagnostické nástroje**) nebo mimo ladicí program (**Profiler ladění/výkon...**). Další informace najdete v tématu  [využití paměti](../profiling/memory-usage.md) a [využití paměti bez ladění](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) .  
  
## <a name="cpu-usage"></a>Využití procesoru  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 Nástroj **využití CPU** vám ukáže, kde CPU stráví čas, který spouští C++, C#/VB a javascriptový kód.  Tento nástroj můžete použít jak pro aplikace Desktop, tak pro univerzální aplikace pro Windows, tak i pro Azure App Services. Nástroj **využití CPU** lze spustit z okna **diagnostické nástroje** při ladění (**ladění/Windows/show diagnostické nástroje**) nebo mimo ladicí program (**Profiler ladění/výkon...**). Další informace najdete v tématu [využití procesoru](../profiling/cpu-usage.md) .  
  
## <a name="performance-explorer"></a>Prohlížeč výkonu  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Prohlížeč výkonu** (**ladění/Profiler/prohlížeč výkonu**) vám umožní používat spoustu různých nástrojů, včetně **vzorkování procesoru**, **instrumentace**, **alokace paměti .NET**a kolizí **prostředků**. Můžete použít nástroje Prohlížeč výkonu s aplikacemi klasické pracovní plochy a aplikací ASP.NET, ale ne univerzálními aplikacemi pro Windows. Další informace najdete v tématu [prohlížeč výkonu](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>Využití GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Použijte nástroj [využití GPU](../debugger/gpu-usage.md) k lepšímu pochopení vysokého využití hardwaru aplikace Direct3D. Tento nástroj můžete použít společně s aplikacemi Desktop i Windows Universal, ale ne s aplikacemi ASP.NET. Nástroj **využití GPU** lze spustit z okna **diagnostické nástroje** při ladění (**ladění/zobrazení diagnostické nástroje**) nebo mimo ladicí program (**ladit/výkon Profiler...**).  
  
## <a name="application-timeline"></a>Časová osa aplikace  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 Nástroj [Časová osa aplikace](../profiling/application-timeline.md) pomáhá zlepšit výkon aplikací XAML tím, že poskytuje podrobné zobrazení jejich spotřeby prostředků. Můžete použít **Časová osa aplikace** s aplikacemi Desktop a Windows Universal Apps, ale ne aplikace ASP.NET. Nástroj **Časová osa aplikace** lze spustit z okna **diagnostické nástroje** (**ladění/výkon Profiler**).  
  
## <a name="perftips"></a>Tipy pro výkon  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Když ladicí program zastaví provádění na operaci zarážky nebo krokování, uplynulý čas mezi přerušením a předchozí zarážkou se zobrazí jako Tip v okně editoru. Tyto [tipy pro výkon](../profiling/perftips.md) vám pomůžou monitorovat a analyzovat výkon aplikace při ladění. **Tipy pro výkon** můžete zobrazit v aplikacích Desktop, Windows Universal a ASP.NET.  
  
## <a name="javascript-memory"></a>Paměť (JavaScript)  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 Nástroj pro [paměť JavaScriptu](../profiling/javascript-memory.md) umožňuje měřit, vyhodnocovat a směrovat problémy související s výkonem v kódu tím, že shromažďují informace o časování na začátku a na konci jednotlivých funkcí v aplikaci. Tento nástroj můžete použít s aplikacemi Windows Universal HTML. Nástroj pro **časování funkcí JavaScriptu** se dá spustit z okna **diagnostické nástroje** (**ladění/výkon Profiler...**).  
  
## <a name="html-ui-responsiveness"></a>Odezva uživatelského rozhraní HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 Nástroj pro [odezvu uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md) pomáhá izolovat problémy s výkonem ve vašich aplikacích, včetně nedostatku odezvy, pomalé doby načítání a vizuálních aktualizací, které jsou méně časté, než se očekávalo. Tento nástroj můžete použít s aplikacemi Windows Universal HTML. Nástroj pro **odezvu uživatelského rozhraní HTML** se dá spustit z okna **diagnostické nástroje** (**ladit/výkon Profiler...**).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) umožňuje zaznamenávat konkrétní události, kontrolovat data v okně **místní** hodnoty během událostí ladicího programu a volání funkcí a ladit chyby, které je těžké regenerovat.  IntelliTrace je primárně Nástroj pro ladění, ale poskytuje také informace, které lze použít pro vyšetřování výkonu. Tento nástroj můžete použít jenom v Visual Studio Enterprise s aplikacemi Desktop, Windows Universal a ASP.NET C#. Při ladění můžete najít IntelliTrace v okně **diagnostické nástroje** (**ladění/Windows/zobrazit diagnostické nástroje**).  
  
## <a name="profiling-in-production"></a>Profilace v produkčním prostředí  
 Doporučený postup pro profilování v produkčním prostředí je profilování z [příkazového řádku pomocí vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) ke shromáždění profilu procesoru. Pro podporu vzdáleného profilování v Azure App Service můžete profilovat prostřednictvím [portálu Průzkumník serveru nebo Kudu](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Který nástroj mám použít?  
 Tady je tabulka, která obsahuje seznam různých nástrojů, které nabízí Visual Studio, a různé typy projektů, pomocí kterých můžete:  
  
|Nástroj Performance Tool|Plocha Windows|Windows Universal/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ne|  
|[Využití procesoru](../profiling/cpu-usage.md)|ano|ano|Pouze Azure App Service|  
|[Využití GPU](../debugger/gpu-usage.md)|ano|ano|ne|  
|[Časová osa aplikace](../profiling/application-timeline.md)|ano|ano|ne|  
|[Tipy pro výkon](../profiling/perftips.md)|ano|Ano pro XAML, ne pro HTML|ne|  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|ano|ne|ano|  
|[IntelliTrace](../debugger/intellitrace.md)|Jenom .NET Enterprise|Jenom .NET Enterprise|Jenom .NET Enterprise|  
|[Rychlost odezvy uživatelského rozhraní (HTML)](../profiling/html-ui-responsiveness.md)|ne|Ano pro HTML, ne pro XAML|ne|  
|[Paměť JavaScriptu](../profiling/javascript-memory.md)|ne|Ano pro HTML, ne pro XAML|ne|  
  
## <a name="see-also"></a>Viz také  
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)
