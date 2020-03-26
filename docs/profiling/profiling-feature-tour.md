---
title: Měření výkonu pomocí nástrojů pro profilování
description: Podívejte se na různé diagnostické nástroje, které jsou k dispozici v sadě Visual Studio.
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2d23620a1861396971c79551088b898c9b77c86
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233099"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Úvodní příručka: První pohled na nástroje profilování

Visual Studio poskytuje celou řadu nástrojů pro profilování, které vám pomohou diagnostikovat různé druhy problémů s výkonem v závislosti na typu aplikace.

Nástroje profilování, ke kterým máte přístup během relace ladění, jsou k dispozici v okně Diagnostické nástroje. Okno Diagnostické nástroje se zobrazí automaticky (pokud jste ho nevypnuli). Chcete-li okno vyvolat, klepněte na tlačítko **Ladění / Windows / Zobrazit diagnostické nástroje**. S otevřeným oknem můžete vybrat nástroje, pro které chcete shromažďovat data.

![Okno Diagnostické nástroje](../profiling/media/prof-tour-diagnostic-tools.png "Diagnostické nástroje")

Při ladění můžete použít okno Diagnostické **nástroje** k analýze využití procesoru a paměti a můžete zobrazit události, které zobrazují informace související s výkonem.

![Souhrnné zobrazení diagnostických nástrojů](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Souhrn diagnostických nástrojů")

Okno **Diagnostické nástroje** je často upřednostňovaným způsobem profilování aplikací, ale pro sestavení release můžete místo toho provést také analýzu po smrti vaší aplikace. Pokud chcete více informací o různých přístupech, přečtěte si informace [o nástrojích profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Pokud chcete zobrazit podporu profilovacího nástroje pro různé typy aplikací, přečtěte si informace o [tom, který nástroj mám použít?](#which-tool-should-i-use).

> [!NOTE]
> Můžete použít post-mortem nástroje se systémem Windows 7 a novější. Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna).

## <a name="analyze-cpu-usage"></a>Analýza využití procesoru

Nástroj využití procesoru je vhodné místo pro zahájení analýzy výkonu aplikace. To vám řekne více o prostředky procesoru, které vaše aplikace spotřebovává. Podrobnější návod nástroje využití procesoru najdete v tématu [Měření výkonu aplikace analýzou využití procesoru](../profiling/beginners-guide-to-performance-profiling.md).

V **souhrnném** zobrazení diagnostických nástrojů zvolte **Povolit profilování procesoru** (musíte být v relaci ladění).

![Povolení využití procesoru v diagnostických nástrojích](../profiling/media/prof-tour-enable-cpu-profiling.png "Diagnostické nástroje povolují využití procesoru")

Chcete-li nástroj používat co nejefektivněji, nastavte v kódu dvě zarážky, jednu na začátku a jednu na konci funkce nebo oblast kódu, kterou chcete analyzovat. Zkontrolujte data profilování, když jste pozastavena na druhé zarážky.

Zobrazení **Využití procesoru** zobrazuje seznam funkcí seřazených podle nejdelšího běhu s nejdelší spuštěnou funkcí nahoře. To vám může pomoci k funkcím, kde dochází k kritickým bodům výkonu.

![Zobrazení využití procesoru diagnostických nástrojů](../profiling/media/prof-tour-cpu-usage.png "Využití procesoru diagnostických nástrojů")

Poklepejte na funkci, která vás zajímá, a uvidíte podrobnější tří-panel "motýl" pohled, s vybranou funkcí ve středu okna, volající funkce na levé straně, a volal funkce na pravé straně. Část **Tělo funkce** zobrazuje celkovou dobu (a procento času) stráveného v těle funkce s výjimkou času stráveného voláním a voláním funkcí. Tato data vám mohou pomoci vyhodnotit, zda samotná funkce je problémové místo výkonu.

![Diagnostické nástroje volající volaný "motýl" pohled](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Diagnostické nástroje zobrazení volajícího volacího volání")

> [!TIP]
> Chcete-li analyzovat výkon, můžete také použít [PerfTips](#examine-performance-events-using-perftips) krokovat kód a určit, jak dlouho trvá konkrétní funkce nebo bloky kódu k dokončení.

## <a name="examine-performance-events-using-perftips"></a>Prozkoumejte události výkonu pomocí perftips

Nejjednodušší způsob zobrazení informací o výkonu je často použití [tipů PerfTips](../profiling/perftips.md). Pomocí perftips můžete zobrazit informace o výkonu při interakci s kódem. Můžete zkontrolovat informace, jako je například doba trvání události (měřeno od kdy byl ladicí program naposledy pozastaven, nebo kdy byla aplikace spuštěna). Pokud například krokujete kód (F10, F11), perfTips zobrazí dobu trvání běhu aplikace od předchozí operace kroku k aktuálnímu kroku.

![Profilování Popisy prohlídek](../profiling/media/prof-tour-perf-tips.png "Profilování Popisy prohlídek")

Pomocí kláves PerfTips můžete zkontrolovat, jak dlouho trvá spuštění bloku kódu nebo jak dlouho trvá dokončení jedné funkce.

PerfTips zobrazit stejné události, které se také zobrazí v zobrazení **Události** diagnostické nástroje. V zobrazení **Události** můžete zobrazit různé události, ke kterým dochází při ladění, jako je například nastavení zarážky nebo krokování kódu operace.

![Zobrazení události diagnostických nástrojů](../profiling/media/prof-tour-events.png "Diagnostické nástroje zobrazit události")

 > [!NOTE]
 > Pokud máte Visual Studio Enterprise, můžete také zobrazit [intelliTrace události](../debugger/intellitrace.md) na této kartě.

## <a name="analyze-memory-usage"></a>Analýza využití paměti

Diagnostické **nástroje** okno také umožňuje vyhodnotit využití paměti v aplikaci pomocí nástroje **využití paměti.** Můžete se například podívat na počet a velikost objektů na haldě. Podrobnější pokyny k analýze paměti naleznete v [tématu Analýza využití paměti](../profiling/memory-usage.md). Jiný nástroj pro analýzu paměti, [nástroj pro alokaci objektů .NET](../profiling/dotnet-alloc-tool.md), vám pomůže identifikovat vzory přidělení a anomálie v kódu .NET.

Chcete-li analyzovat využití paměti s ladicím programem integrované využití paměti příliš, je třeba provést alespoň jeden snímek paměti. Často je nejlepší způsob, jak analyzovat paměť je vzít dva snímky; první právo před podezření na problém paměti a druhý snímek hned po podezření na problém paměti dojde. Pak můžete zobrazit rozdíl dvou snímků a přesně vidět, co se změnilo.

![Pořízení snímku v diagnostických nástrojích](../profiling/media/prof-tour-take-snapshots.gif "Diagnostické nástroje pořizovat snímky")

Když vyberete jeden z odkazů se šipkami, dostanete rozdílové zobrazení haldy (červená šipka nahoru ![Zvýšení využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zvýšení využití paměti") zobrazuje rostoucí počet objektů (vlevo) nebo rostoucí velikost haldy (vpravo)). Pokud klepnete na pravé propojení, získáte zobrazení rozdílové haldy seřazené objekty, které zvýšily nejvíce ve velikosti haldy. To vám může pomoci určit problémy s pamětí. Například na obrázku níže bajtů `ClassHandlersStore` používaných objekty zvýšil o 3 492 bajtů v druhém snímku.

![Zobrazení rozdílu haldy diagnostických nástrojů](../profiling/media/prof-tour-mem-usage-diff-heap.png "Zobrazení rozdílu haldy diagnostických nástrojů")

Pokud místo toho klepnete na odkaz vlevo v zobrazení **Využití paměti,** bude zobrazení haldy uspořádáno podle počtu objektů. objekty určitého typu, které zvýšily nejvíce v počtu jsou zobrazeny v horní části (seřazené podle **sloupce Počet rozdílů).**

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a>Sestavení verze profilu bez ladicího programu

Profilování nástroje, jako je využití procesoru a využití paměti lze použít s ladicím programem (viz předchozí části), nebo můžete spustit profilování nástroje post-mortem pomocí profilování výkonu, který je určen k poskytování analýzy pro **sestavení verze.** V profileru výkonu můžete shromažďovat diagnostické informace, když je aplikace spuštěná, a poté zkontrolovat shromážděné informace po zastavení aplikace. Další informace o těchto různých přístupech naleznete [v tématu Spuštění profilovacích nástrojů s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Další nástroje, jako je [například nástroj pro přidělení objektů .NET,](../profiling/dotnet-alloc-tool.md) jsou také k dispozici v nástroji Profiler výkonu.

![Profiler výkonu](../profiling/media/prof-tour-performance-profiler.png "Profiler výkonu")

Otevřete profilovač výkonu výběrem **ladění** > **profilování výkonu**.

Okno vám umožní vybrat více nástrojů profilování v některých scénářích. Nástroje, jako je využití procesoru může poskytnout doplňková data, která můžete použít k nápovědě při analýze. Profiler [příkazového řádku](../profiling/profile-apps-from-command-line.md) můžete také použít k povolení scénářů zahrnujících více nástrojů profilování.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Zkontrolujte události výkonu a usnadnění přístupu u nového prostředí (UPW)

V aplikacích UPW můžete povolit **analýzu ui v** okně **Diagnostické nástroje.** Nástroj vyhledá běžné problémy s výkonem nebo usnadněním přístupu a zobrazí je v zobrazení **Události** při ladění. Popisy událostí poskytují informace, které mohou pomoci vyřešit problémy.

![Zobrazení událostí analýzy ui v diagnostických nástrojích](../profiling/media/prof-tour-ui-analysis.png "Diagnostické nástroje zobrazit události analýzy ui")

## <a name="analyze-resource-consumption-xaml"></a>Analýza spotřeby prostředků (XAML)

V aplikacích XAML, jako jsou aplikace WPF pro stolní počítače windows a aplikace UPW, můžete analyzovat spotřebu prostředků pomocí nástroje Časová osa aplikace. Můžete například analyzovat čas strávený aplikací při přípravě rámců uživatelského rozhraní (rozložení a vykreslení), obsluhující síťové a diskové požadavky a ve scénářích, jako je spuštění aplikace, načtení stránky a změna velikosti okna. Chcete-li nástroj použít, zvolte **Časovou osu aplikace** v nástroji Profilování výkonu a pak zvolte **Start**. Ve vaší aplikaci projděte scénář s podezřením na problém se spotřebou prostředků a pak zvolte **Zastavit kolekci** pro generování sestavy.

Nízké snímkové frekvence v grafu **vizuální propustnosti** může odpovídat vizuální problémy, které se zobrazí při spuštění aplikace. Podobně vysoká čísla v grafu **využití vlákna uživatelského rozhraní** může také odpovídat problémům s odezvou uživatelského rozhraní. V sestavě můžete vybrat časové období s podezřením na problém s výkonem a potom prozkoumat podrobné aktivity vlákna uživatelského rozhraní v zobrazení podrobností časové osy (dolní podokno).

![Nástroj profilování časové osy aplikace](../profiling/media/prof-tour-application-timeline.gif "Profilování časové osy aplikace prohlídky")

V zobrazení podrobností časové osy můžete najít informace, jako je typ aktivity (nebo prvek ui zapojen) spolu s dobou trvání aktivity. Například na obrázku **rozložení** události pro grid ovládacíprvek trvá 57,53 ms.

Další informace naleznete v [tématu Časová osa aplikace](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analýza využití GPU (Direct3D)

V aplikacích Direct3D (komponenty Direct3D musí být v Jazyce C++) můžete prozkoumat aktivitu na GPU a analyzovat problémy s výkonem. Další informace naleznete [v tématu Využití GPU](/visualstudio/debugger/graphics/gpu-usage). Chcete-li nástroj použít, zvolte **využití GPU** v nástroji Profilování výkonu a pak zvolte **Start**. Ve své aplikaci projděte scénář, který vás zajímá profilování a pak zvolte **Zastavit kolekci** pro generování sestavy.

Když v grafech vyberete časové období a zvolíte **podrobnosti zobrazení**, zobrazí se v dolním podokně podrobné zobrazení. V podrobném zobrazení můžete prozkoumat, kolik aktivity se děje na každém procesoru a GPU. Vyberte události v nejnižším podokně, abyste získali vyskakovací okno na časové ose. Vyberte například **událost Prezentovat,** chcete-li zobrazit vyskakovací okno **volání prezentovat.** (Světle šedé svislé řádky Vsync lze použít jako odkaz k pochopení, zda některé **volání Present** zmeškané Vsync. Musí existovat jeden **přítomný** hovor mezi každými dvěma Vsyncs, aby aplikace neustále dosáhla 60 FPS.)

![Nástroj pro profilování využití GPU](../profiling/media/prof-tour-gpu-usage.png "Použití diag GPU")

Grafy můžete také použít k určení, zda existují kritické body výkonu vázané na procesor nebo GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analýza výkonu (JavaScript UPW)

Pro aplikace UPW můžete použít nástroj JavaScript Memory a nástroj odezvy uživatelského rozhraní HTML.

Nástroj JavaScript Memory je podobný nástroji Využití paměti, který je k dispozici pro jiné typy aplikací. Tento nástroj můžete použít k pochopení využití paměti a najít nevracení paměti ve vaší aplikaci. Další podrobnosti o nástroji naleznete v [tématu JavaScript Memory](../profiling/javascript-memory.md).

![Nástroj pro profilování paměti JavaScript](../profiling/media/diagjsmemory.png "DiagJSPaměť")

Chcete-li diagnostikovat odezvu uživatelského rozhraní, pomalou dobu načítání a pomalé vizuální aktualizace v aplikacích UPW, použijte nástroj odezvy uživatelského rozhraní HTML. Použití je podobné nástroji Časové osy aplikací pro jiné typy aplikací. Další informace naleznete v [tématu odezva uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md).

![Nástroj pro profilování odezvy uživatelského rozhraní HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analýza využití sítě (UPW)

V aplikacích UPW můžete analyzovat síťové `Windows.Web.Http` operace prováděné pomocí rozhraní API. Tento nástroj vám může pomoci vyřešit problémy, jako je přístup a ověřování problémy, nesprávné použití mezipaměti a špatný výkon zobrazení a stahování. Chcete-li nástroj použít, zvolte **Síť** v nástroji Profilování výkonu a pak zvolte **Start**. Ve vaší aplikaci projděte `Windows.Web.Http`scénář, který používá , a pak zvolte **Zastavit kolekci** pro generování sestavy.

![Nástroj pro profilování využití sítě](../profiling/media/prof-tour-network-usage.png "Diag využití sítě")

Vyberte operaci v souhrnném zobrazení, chcete-li zobrazit další podrobnosti.

![Podrobné informace v nástroji Používání sítě](../profiling/media/prof-tour-network-usage-details.png "Podrobnosti o využití diag sítě")

Další informace naleznete v [tématu Usage Network](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analýza výkonu (starší nástroje)

::: moniker range="vs-2017"
Pokud potřebujete funkce, jako je instrumentace, které nejsou aktuálně k dispozici v nástrojích využití procesoru nebo využití paměti a používáte desktop nebo ASP.NET aplikace, můžete použít Průzkumník výkonu pro profilování. (Není podporováno v aplikacích UPW). Další informace naleznete v [tématu Performance Explorer](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
V sadě Visual Studio 2019 byly starší nástroje Performance Explorer a související nástroje profilování, jako je Například Průvodce výkonem, přeloženy do nástroje Profilování výkonu, který můžete otevřít pomocí **nástroje Ladění** > **profilu výkonu**. V nástroji Profilování výkonu závisí dostupné diagnostické nástroje na zvoleném cíli a aktuálním projektu spuštění. Nástroj využití procesoru poskytuje možnost vzorkování dříve podporovanou v Průvodci výkonem. Nástroj instrumentace poskytuje možnost instrumentovanéprofilování (pro přesné počty volání a doby trvání), která byla v Průvodci výkonem. Další paměťové nástroje se také zobrazí v profileru výkonu.
::: moniker-end

![Nástroj Průzkumník výkonu](../profiling/media/prof-tour-performance-explorer.png "Prohlížeč výkonu")

## <a name="which-tool-should-i-use"></a>Který nástroj mám použít?

Zde je tabulka se seznamem různých nástrojů, které Visual Studio nabízí, a různých typů projektů, se kterými je můžete použít:

::: moniker range=">=vs-2019"
|Nástroj výkon|Plocha Windows|UWP|ASP.NET/ASP.NET jádro|
|----------------------|---------------------|-------------|-------------|
|[Využití procesoru](../profiling/cpu-usage.md)|ano|ano|ano|
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ano|
|[Přidělení objektu .NET](../profiling/dotnet-alloc-tool.md)|ano (pouze.NET)|ano|ano|
|[Využití GPU](/visualstudio/debugger/graphics/gpu-usage)|ano|ano|ne|
|[Časová osa aplikace](../profiling/application-timeline.md)|ano|ano|ne|
|[Tipy pro výkon](../profiling/perftips.md)|ano|ano pro XAML, ne pro HTML|ano|
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|ano|ne|ano|
|[IntelliTrace](../debugger/intellitrace.md)|Rozhraní .NET pouze s visual studio enterprise|Rozhraní .NET pouze s visual studio enterprise|Rozhraní .NET pouze s visual studio enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Nástroj výkon|Plocha Windows|UWP|ASP.NET/ASP.NET jádro|
|----------------------|---------------------|-------------|-------------|
|[Využití procesoru](../profiling/cpu-usage.md)|ano|ano|ano|
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ano|
|[Využití GPU](/visualstudio/debugger/graphics/gpu-usage)|ano|ano|ne|
|[Časová osa aplikace](../profiling/application-timeline.md)|ano|ano|ne|
|[Tipy pro výkon](../profiling/perftips.md)|ano|ano pro XAML, ne pro HTML|ano|
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|ano|ne|ano|
|[IntelliTrace](../debugger/intellitrace.md)|Rozhraní .NET pouze s visual studio enterprise|Rozhraní .NET pouze s visual studio enterprise|Rozhraní .NET pouze s visual studio enterprise|
|[Využití sítě](../profiling/network-usage.md)|ne|ano|ne|
|[Rychlost odezvy uživatelského rozhraní (HTML)](../profiling/html-ui-responsiveness.md)|ne|ano pro HTML, ne pro XAML|ne|
|[Paměť JavaScriptu](../profiling/javascript-memory.md)|ne|ano pro HTML, ne pro XAML|ne|
::: moniker-end


## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md)
