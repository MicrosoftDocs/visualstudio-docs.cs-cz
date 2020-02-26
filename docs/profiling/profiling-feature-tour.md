---
title: Měření výkonu pomocí nástrojů pro profilaci
description: Podívejte se na krátké zobrazení různých diagnostických nástrojů, které jsou k dispozici v aplikaci Visual Studio.
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
ms.openlocfilehash: 8e4868899af67ebeb25ae508cbe7e5b0c83137bf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578078"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Rychlý Start: první pohled na nástroje pro profilaci

Visual Studio poskytuje celou řadu nástrojů pro profilaci, které vám pomůžou s diagnostikou různých typů problémů s výkonem v závislosti na typu aplikace.

Nástroje pro profilaci, ke kterým můžete přistupovat během relace ladění, jsou k dispozici v okně Diagnostické nástroje. Okno Diagnostické nástroje se automaticky zobrazí, pokud jste ho nevypnuli. Okno zobrazíte kliknutím na **ladit/Windows/zobrazit diagnostické nástroje**. V otevřeném okně můžete vybrat nástroje, pro které chcete shromažďovat data.

![Diagnostické nástroje okno](../profiling/media/prof-tour-diagnostic-tools.png "Diagnostické nástroje")

Při ladění můžete použít okno **diagnostické nástroje** k analýze využití CPU a paměti a můžete zobrazit události, které zobrazují informace související s výkonem.

![Zobrazení souhrnu Diagnostické nástroje](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Souhrn Diagnostické nástroje")

**Diagnostické nástroje** okno je často upřednostňovaným způsobem, jak Profilovat aplikace, ale pro buildy vydaných verzí můžete místo toho provést i analýzu aplikace po porážce. Pokud chcete získat další informace o různých přístupech, přečtěte si téma [spuštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Pokud chcete zobrazit podporu nástrojů pro profilaci pro různé typy aplikací, přečtěte si téma [který nástroj mám použít?](#which-tool-should-i-use).

> [!NOTE]
> Můžete použít nástroje po porážce v systému Windows 7 nebo novějším. Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější.

## <a name="analyze-cpu-usage"></a>Analýza využití procesoru

Nástroj využití CPU je vhodným místem pro zahájení analýzy výkonu vaší aplikace. Dozvíte se víc o prostředcích procesoru, které vaše aplikace spotřebovává. Podrobnější návod k nástroji využití CPU najdete v tématu [měření výkonu aplikace analýzou využití CPU](../profiling/beginners-guide-to-performance-profiling.md).

V zobrazení **souhrnu** diagnostické nástroje vyberte **Povolit profilaci procesoru** (musíte být v relaci ladění).

![Povolit využití CPU v Diagnostické nástroje](../profiling/media/prof-tour-enable-cpu-profiling.png "Diagnostické nástroje povolit využití CPU")

Chcete-li použít nástroj efektivně, nastavte v kódu dvě zarážky, jeden na začátku a druhý na konci funkce nebo oblast kódu, který chcete analyzovat. Prohlédněte si data profilování při pozastavené druhé zarážce.

V zobrazení **využití CPU** se zobrazuje seznam funkcí seřazený podle nejdelšího běhu s nejdelší spuštěnou funkcí v horní části. To vám může pomáhat s funkcemi, kde dochází k kritickým bodům výkonu.

![Diagnostické nástroje zobrazení využití procesoru](../profiling/media/prof-tour-cpu-usage.png "Diagnostické nástroje využití CPU")

Dvakrát klikněte na funkci, kterou vás zajímá, a zobrazí se podrobnější zobrazení se třemi podokny "motýlku", ve kterém je vybraná funkce uprostřed okna, volání funkce na levé straně a volané funkce na pravé straně. Část **tělo funkce** ukazuje celkovou dobu (a procento času) strávenou v těle funkce s výjimkou času stráveného voláním a voláním funkce. Tato data vám pomohou vyhodnotit, zda se jedná o problém s výkonem samotné funkce.

![Diagnostické nástroje volající volal "škrticí" zobrazení](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Zobrazení volaný volající Diagnostické nástroje")

## <a name="analyze-memory-usage"></a>Analýza využití paměti

Okno **diagnostické nástroje** také umožňuje vyhodnotit využití paměti ve vaší aplikaci. Například můžete se podívat na počet a velikost objektů v haldě. Podrobnější pokyny k analýze paměti najdete v tématu [Analýza využití paměti](../profiling/memory-usage.md).

Chcete-li analyzovat využití paměti při ladění, je nutné provést alespoň jeden snímek paměti. Nejlepším způsobem, jak analyzovat paměť, je často provedení dvou snímků. první napravo před problémem s podezřelou pamětí a druhý snímek hned po výskytu problému s podezřelou pamětí. Pak můžete zobrazit rozdíl dvou snímků a podívat se přesně, co se změnilo.

![Pořídit snímek v Diagnostické nástroje](../profiling/media/prof-tour-take-snapshots.gif "Diagnostické nástroje pořizování snímků")

Když vyberete jednu z odkazů na šipky, získáte rozdílové zobrazení haldy (červená šipka ![zvětšení využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zvýšení využití paměti") ukazuje zvýšení počtu objektů (vlevo) nebo zvýšení velikosti haldy (vpravo). Pokud kliknete na odkaz vpravo, dostanete zobrazení rozdílové haldy seřazené podle objektů, které zvýšily velikost haldy. To vám může pomáhat identifikovat problémy s pamětí. Například na obrázku níže jsou bajty využívané `ClassHandlersStore` objekty zvyšovány o 3 492 bajtů ve druhém snímku.

![Zobrazení rozdílu Diagnostické nástroje haldy](../profiling/media/prof-tour-mem-usage-diff-heap.png "Zobrazení rozdílu Diagnostické nástroje haldy")

Pokud kliknete na odkaz vlevo místo v zobrazení **využití paměti** , zobrazení haldy se uspořádá podle počtu objektů; objekty konkrétního typu, které zvyšují číslo nejvíce v, jsou uvedeny v horní části (seřazené podle sloupce s **rozdílem podle počtu** ).

## <a name="examine-performance-events"></a>Kontrola událostí výkonu

Zobrazení **události** v diagnostické nástroje zobrazuje různé události, ke kterým dochází při ladění, jako je například nastavení zarážky nebo operace krokování kódu. Můžete kontrolovat informace, jako je například doba trvání události (měřeno od okamžiku, kdy byl ladicí program naposledy pozastaven nebo když byla aplikace spuštěna). Pokud například projdete kód (F10, F11), zobrazí se v zobrazení **události** doba běhu aplikace z operace předchozí krok do aktuálního kroku.

![Zobrazení Diagnostické nástrojech událostí](../profiling/media/prof-tour-events.png "Zobrazit události Diagnostické nástroje")

 > [!NOTE]
 > Pokud máte Visual Studio Enterprise, můžete na této kartě Zobrazit také [události IntelliTrace](../debugger/intellitrace.md) .

Stejné události jsou také zobrazeny v editoru kódu, které lze zobrazit jako tipy pro výkon.

![Tipy pro výkon Tour profilace](../profiling/media/prof-tour-perf-tips.png "Tipy pro výkon Tour profilace")

## <a name="post_mortem"></a>Sestavení pro vydání profilu bez ladicího programu

Nástroje pro profilaci, jako je využití procesoru a využití paměti, se dají použít spolu s ladicím programem (viz předchozí části) nebo můžete spouštět nástroje pro profilaci po porážce pomocí profileru výkonu, který je určený k poskytnutí analýzy pro sestavení vydaných **verzí** . V profileru výkonu můžete shromažďovat diagnostické informace, když je aplikace spuštěná, a potom po zastavení aplikace prohlédnout shromážděné informace. Další informace o těchto různých přístupůch naleznete v tématu [spuštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). V profileru výkonu jsou také k dispozici další nástroje, například [Nástroj pro přidělování objektů rozhraní .NET](../profiling/dotnet-alloc-tool.md) .

![Profiler výkonu](../profiling/media/prof-tour-performance-profiler.png "Profiler výkonu")

Kliknutím na **ladit** > **Performance Profiler**otevřete Profiler výkonu.

V některých scénářích můžete v tomto okně vybrat více nástrojů pro profilaci. Nástroje, jako je využití CPU, můžou poskytovat doplňková data, která můžete použít k usnadnění analýzy. Pomocí [profileru příkazového řádku](../profiling/profile-apps-from-command-line.md) můžete také povolit scénáře zahrnující více nástrojů pro profilaci.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Kontrola výkonu uživatelského rozhraní a událostí přístupnosti (UWP)

V aplikacích pro UWP můžete v **diagnostické nástroje** okně Povolit **analýzu uživatelského rozhraní** . Nástroj vyhledává běžné problémy s výkonem nebo přístupností a při ladění je zobrazuje v zobrazení **událostí** . Popis události poskytuje informace, které mohou pomáhat při řešení problémů.

![Zobrazení událostí analýzy uživatelského rozhraní v diagnostických nástrojích](../profiling/media/prof-tour-ui-analysis.png "Diagnostické nástroje zobrazit události analýzy uživatelského rozhraní")

## <a name="analyze-resource-consumption-xaml"></a>Analýza spotřeby prostředků (XAML)

V aplikacích XAML, jako jsou aplikace WPF pro Windows Desktop a aplikace pro UWP, můžete pomocí nástroje Časová osa aplikace analyzovat spotřebu prostředků. Můžete například analyzovat čas strávený vaší aplikací při přípravě rámců uživatelského rozhraní (rozložení a vykreslování), obsluhování síťových a diskových požadavků a ve scénářích, jako je spuštění aplikace, načítání stránky a změna velikosti okna. Chcete-li použít nástroj, zvolte možnost **Časová osa aplikace** v profileru výkonu a pak zvolte možnost **Spustit**. Ve své aplikaci Projděte scénář s podezřelým problémem spotřeby prostředků a pak zvolte možnost **Zastavit shromažďování** pro vygenerování sestavy.

Nízká framerates v grafu **propustnosti vizuálů** může odpovídat vizuálním problémům, které vidíte při spuštění aplikace. Podobně vysoké hodnoty v grafu **využití vlákna uživatelského rozhraní** můžou také odpovídat problémům s odezvou uživatelského rozhraní. V sestavě můžete vybrat časové období s podezřelým problémem s výkonem a pak prostudovat podrobné aktivity vlákna uživatelského rozhraní v zobrazení Podrobnosti časové osy (dolní podokno).

![Nástroj pro profilaci Časová osa aplikace](../profiling/media/prof-tour-application-timeline.gif "Časová osa aplikace prohlídka profilace")

V zobrazení podrobností časové osy můžete najít informace, jako je například typ aktivity (nebo související prvek uživatelského rozhraní) spolu s dobou trvání aktivity. Například na obrázku je událost **rozložení** ovládacího prvku mřížky převzata 57,53 MS.

Další informace najdete v tématu [Časová osa aplikace](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analýza využití GPU (Direct3D)

V aplikacích Direct3D (komponenty Direct3D musí být v C++) můžete prozkoumat činnost na GPU a analyzovat problémy s výkonem. Další informace najdete v tématu [využití GPU](/visualstudio/debugger/graphics/gpu-usage). Chcete-li použít nástroj, zvolte možnost **použití GPU** v profileru výkonu a pak zvolte možnost **Spustit**. Ve své aplikaci Projděte scénář, který vás zajímá, a pak zvolte **Zastavit shromažďování** pro vygenerování sestavy.

Když vyberete časové období v grafech a zvolíte **Zobrazit podrobnosti**, zobrazí se v dolním podokně podrobné zobrazení. V podrobném zobrazení můžete zjistit, kolik aktivit se děje na jednotlivých PROCESORech a GPU. Výběrem události v dolním podokně získáte místní nabídky na časové ose. Vyberte například **tuto událost k** zobrazení **současných** překryvných oken volání. (Světlé šedé svislé vsync čáry lze použít jako referenci pro pochopení, zda některá **přítomná** volání vynechala vsync. Aby aplikace neustále dosáhla 60 FPS, musí **existovat jedno volání** mezi dvěma Vsyncs.)

![Nástroj pro profilaci využití GPU](../profiling/media/prof-tour-gpu-usage.png "Využití GPU diagnostiky")

Pomocí grafů můžete také zjistit, zda jsou k dispozici slabá místa výkonu vázaného na procesor nebo GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analýza výkonu (JavaScript UWP)

Pro aplikace pro UWP můžete použít nástroj pro paměť v jazyce JavaScript a nástroj pro odezvu uživatelského rozhraní HTML.

Nástroj pro paměť JavaScriptu je podobný nástroji využití paměti, který je dostupný pro jiné typy aplikací. Tento nástroj můžete použít k pochopení využití paměti a nalezení nevracení paměti ve vaší aplikaci. Další informace o tomto nástroji najdete v tématu [paměť JavaScriptu](../profiling/javascript-memory.md).

![Nástroj pro profilaci paměti JavaScriptu](../profiling/media/diagjsmemory.png "DiagJSMemory")

K diagnostikování odezvy uživatelského rozhraní, pomalé doby načítání a pomalých vizuálních aktualizací v aplikacích pro UWP použijte nástroj pro odezvu uživatelského rozhraní HTML. Použití je podobné nástroji Časová osa aplikace pro jiné typy aplikací. Další informace najdete v tématu [odezva uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md).

![Nástroj pro profilaci odezvy uživatelského rozhraní HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analýza využití sítě (UPW)

V aplikacích pro UWP můžete analyzovat síťové operace prováděné pomocí rozhraní `Windows.Web.Http` API. Tento nástroj vám může pomáhat vyřešit problémy, jako jsou problémy s přístupem a ověřováním, nesprávné použití mezipaměti a špatný výkon zobrazení a stahování. Chcete-li použít nástroj, zvolte v profileru výkonu položku **síť** a pak zvolte možnost **Spustit**. Ve své aplikaci Projděte scénář, který používá `Windows.Web.Http`a pak zvolte možnost **Zastavit shromažďování** pro vygenerování sestavy.

![Nástroj pro profilaci využití sítě](../profiling/media/prof-tour-network-usage.png "Využití sítě diag")

Vyberte operaci v souhrnné zobrazení zobrazte další podrobnosti.

![Podrobné informace v nástroji využití sítě](../profiling/media/prof-tour-network-usage-details.png "Podrobnosti použití diagnostiky sítě")

Další informace najdete v tématu [využití sítě](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analýza výkonu (starší nástroje)

::: moniker range="vs-2017"
Pokud potřebujete funkce, jako je instrumentace, které aktuálně nejsou k dispozici v nástroji využití procesoru nebo paměti, a máte spuštěné aplikace Desktop nebo ASP.NET, můžete k profilaci použít Prohlížeč výkonu. (Nepodporováno v aplikacích pro UWP) Další informace najdete v tématu [prohlížeč výkonu](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
V aplikaci Visual Studio 2019 se starší Prohlížeč výkonu a související nástroje pro profilaci, jako je Průvodce výkonem, přeložily do profileru výkonu, který můžete otevřít pomocí nástroje **Debug** > **Performance Profiler**. V profileru výkonu jsou dostupné diagnostické nástroje závislé na vybraném cíli a na aktuálním otevřeném projektu po spuštění. Nástroj využití CPU nabízí funkci vzorkování, která byla dříve podporovaná v průvodci výkonem. Nástroj Instrumentace poskytuje instrumentované možnosti profilování (pro přesné počty volání a trvání), které byly v průvodci výkonem. V profileru výkonu se také zobrazí další nástroje paměti.
::: moniker-end

![Nástroj Prohlížeč výkonu](../profiling/media/prof-tour-performance-explorer.png "Prohlížeč výkonu")

## <a name="which-tool-should-i-use"></a>Který nástroj mám použít?

Tady je tabulka, která obsahuje seznam různých nástrojů, které nabízí Visual Studio, a různé typy projektů, pomocí kterých můžete:

::: moniker range=">=vs-2019"
|Nástroj Performance Tool|Plocha Windows|UWP|Jádro ASP.NET/ASP.NET|
|----------------------|---------------------|-------------|-------------|
|[Využití procesoru](../profiling/cpu-usage.md)|ano|ano|ano|
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ano|
|[Alokace objektů .NET](../profiling/dotnet-alloc-tool.md)|Ano (jenom .NET)|ano|ano|
|[Využití GPU](/visualstudio/debugger/graphics/gpu-usage)|ano|ano|ne|
|[Časová osa aplikace](../profiling/application-timeline.md)|ano|ano|ne|
|[Tipy pro výkon](../profiling/perftips.md)|ano|Ano pro XAML, ne pro HTML|ano|
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|ano|ne|ano|
|[IntelliTrace](../debugger/intellitrace.md)|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Nástroj Performance Tool|Plocha Windows|UWP|Jádro ASP.NET/ASP.NET|
|----------------------|---------------------|-------------|-------------|
|[Využití procesoru](../profiling/cpu-usage.md)|ano|ano|ano|
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ano|
|[Využití GPU](/visualstudio/debugger/graphics/gpu-usage)|ano|ano|ne|
|[Časová osa aplikace](../profiling/application-timeline.md)|ano|ano|ne|
|[Tipy pro výkon](../profiling/perftips.md)|ano|Ano pro XAML, ne pro HTML|ano|
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|ano|ne|ano|
|[IntelliTrace](../debugger/intellitrace.md)|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|
|[Využití sítě](../profiling/network-usage.md)|ne|ano|ne|
|[Rychlost odezvy uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md)|ne|Ano pro HTML, ne pro XAML|ne|
|[Paměť JavaScriptu](../profiling/javascript-memory.md)|ne|Ano pro HTML, ne pro XAML|ne|
::: moniker-end


## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md)
