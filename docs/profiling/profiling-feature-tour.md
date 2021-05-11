---
title: Začínáme s nástroji pro profilaci
description: Krátce se podívejte na různé diagnostické nástroje dostupné v Visual Studio.
ms.custom: ''
ms.date: 02/18/2021
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5fb35c1cd30f872d2a58504f73596357cc60025
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729322"
---
# <a name="first-look-at-profiling-tools"></a>První seznámení s nástroji pro profilaci

Visual Studio poskytuje celou řadu nástrojů pro profilaci, které vám pomůžou diagnostikovat různé druhy problémů s výkonem v závislosti na typu vaší aplikace. V tomto článku se rychle podíváme na nejběžnější nástroje pro profilaci.

Informace o podpoře nástrojů pro profilaci pro různé typy aplikací najdete v tématu [Který nástroj mám použít?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Měření výkonu při ladění

Nástroje pro profilaci, ke které máte přístup během ladicí relace, jsou k dispozici v Diagnostické nástroje okně. Okno Diagnostické nástroje se zobrazí automaticky (pokud jste ho nevypnuli). Okno zobrazíte kliknutím na Ladit **/ Windows / Zobrazit Diagnostické nástroje** (nebo stiskněte **Ctrl**  +  **Alt**  +  **F2).** Když je okno otevřené, můžete vybrat nástroje, pro které chcete shromažďovat data.

![Diagnostické nástroje okno](../profiling/media/prof-tour-diagnostic-tools.png "Diagnostické nástroje")

Během ladění můžete pomocí okna  Diagnostické nástroje analyzovat využití procesoru a paměti a zobrazit události, které zobrazují informace související s výkonem.

![Diagnostické nástroje zobrazení souhrnu](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Diagnostické nástroje souhrnu")

Okno **Diagnostické nástroje** běžným způsobem profilování aplikací, ale u sestavení pro vydání můžete také provést postaplikační analýzu aplikace. Další informace o různých přístupech najdete v tématu [Spouštění nástrojů pro profilaci s ladicím programem nebo bez něj.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) Informace o podpoře nástrojů pro profilaci pro různé typy aplikací najdete v tématu [Který nástroj mám použít?](#which-tool-should-i-use)

Mezi nástroje dostupné v Diagnostické nástroje okně nebo během relace ladění patří:
- [Využití procesoru](../profiling/beginners-guide-to-performance-profiling.md)
- [Využití paměti](../profiling/memory-usage.md)
- [Tipy pro výkon](../profiling/perftips.md)

> [!NOTE]
> Windows 8 spuštění nástrojů pro profilaci pomocí ladicího programu **(v** Diagnostické nástroje okně). S Windows 7 a novějšími verzemi můžete použít [post-sématové](#post_mortem) nástroje. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Měření výkonu v sestaveních pro vydání

Nástroje v Profiler výkonu jsou určené k poskytování analýzy sestavení **pro** vydání. V profileru výkonu můžete shromažďovat diagnostické informace, když je aplikace spuštěná, a potom po zastavení aplikace prohlédnout shromážděné informace (analýza po porážce).

Otevřete Profiler výkonu kliknutím na **ladit**  >  **Performance Profiler** (nebo **ALT + F2**).

![Profiler výkonu](../profiling/media/prof-tour-performance-profiler.png "Profiler výkonu")

Další informace o použití nástroje využití CPU nebo využití paměti v profileru výkonu vs. nástroje integrované v ladicím programu naleznete v tématu [spuštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

K dispozici jsou nástroje v profileru výkonu:

- [Využití procesoru](../profiling/cpu-usage.md)
- [Alokace objektů .NET](../profiling/dotnet-alloc-tool.md)
- [Využití paměti](../profiling/memory-usage-without-debugging2.md)
- [.NET Async – nástroj](../profiling/analyze-async.md)
- [Databázový nástroj](../profiling/analyze-database.md)
- [Využití GPU](../profiling/gpu-usage.md)

Pokud chcete zobrazit podporu nástrojů pro profilaci pro různé typy aplikací, přečtěte si téma [který nástroj mám použít?](#which-tool-should-i-use)

V některých případech okno umožňuje vybrat [více nástrojů pro profilaci](../profiling/use-multiple-profiler-tools-simultaneously.md). Nástroje, jako je využití CPU, můžou poskytovat doplňková data, která můžete použít k usnadnění analýzy. Pomocí [profileru příkazového řádku](../profiling/profile-apps-from-command-line.md) můžete také povolit scénáře zahrnující více nástrojů pro profilaci.

## <a name="examine-performance-using-perftips"></a>Kontrola výkonu pomocí tipy pro výkon

Nejjednodušší způsob, jak zobrazit informace o výkonu, je často použití [tipy pro výkon](../profiling/perftips.md). Pomocí tipy pro výkon můžete zobrazit informace o výkonu při interakci s vaším kódem. Můžete kontrolovat informace, jako je například doba trvání události (měřeno od okamžiku, kdy byl ladicí program naposledy pozastaven nebo když byla aplikace spuštěna). Pokud například projdete kód (F10, F11), tipy pro výkon zobrazí dobu trvání aplikace z předchozího kroku operace s aktuálním krokem.

![Tipy pro výkon Tour profilace](../profiling/media/prof-tour-perf-tips.png "Profilace – popisy pro prohlídku")

Tipy pro výkon můžete použít ke kontrole, jak dlouho trvá spuštění bloku kódu, nebo jak dlouho trvá dokončení jedné funkce.

Tipy pro výkon zobrazí stejné události, které se také zobrazí v zobrazení **události** diagnostické nástroje. V zobrazení **Události** můžete zobrazit různé události, ke kterým dochází při ladění, například nastavení zarážky nebo operace krokování kódu.

![Diagnostické nástroje události](../profiling/media/prof-tour-events.png "Diagnostické nástroje zobrazení událostí")

 > [!NOTE]
 > Pokud máte Visual Studio Enterprise, můžete také zobrazit události [IntelliTrace](../debugger/intellitrace.md) na této kartě.

## <a name="analyze-cpu-usage"></a>Analýza využití procesoru

Nástroj Využití procesoru je dobrým místem, kde můžete začít analyzovat výkon vaší aplikace. Zobrazí se další informace o náccích procesoru, které vaše aplikace spotřebovává. Můžete použít nástroj [využití procesoru integrovaný s](../profiling/beginners-guide-to-performance-profiling.md) ladicím programem nebo nástroj pro využití procesoru s [posouvem.](../profiling/cpu-usage.md)

Při použití nástroje využití procesoru integrovaného s ladicím programem otevřete okno Diagnostické nástroje (pokud je zavřené, zvolte Ladit **/ Windows / Zobrazit Diagnostické nástroje**). Během ladění otevřete zobrazení **Souhrn a** vyberte Zaznamenat **profil procesoru.**

![Povolení využití procesoru v Diagnostické nástroje](../profiling/media/prof-tour-enable-cpu-profiling.png "Diagnostické nástroje povolení využití procesoru")

Jedním ze způsobů, jak tento nástroj použít, je nastavit dvě zarážky v kódu, jednu na začátku a jednu na konci funkce nebo oblast kódu, kterou chcete analyzovat. Zkontrolujte data profilace, když jste pozastaveni na druhé zarážce.

V **zobrazení Využití** procesoru se zobrazí seznam funkcí seřazených podle nejdelšího běhu s nejdelší spuštěnou funkcí v horní části. To vás může navede na funkce, u kterých dochází k kritickým místům výkonu.

![Diagnostické nástroje využití procesoru](../profiling/media/prof-tour-cpu-usage.png "Diagnostické nástroje využití procesoru")

Poklikejte na funkci, která vás zajímá, a zobrazí se podrobnější třísokenové zobrazení s vybranou funkcí uprostřed okna, volající funkcí vlevo a volána funkce vpravo. Část **Tělo funkce** zobrazuje celkovou dobu (a procento času) strávenou v těle funkce s výjimkou času stráveného voláním a voláním funkcí. Tato data vám můžou pomoct vyhodnotit, jestli je samotná funkce kritickým bodem výkonu.

![Diagnostické nástroje volajícího volaný zobrazení](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Diagnostické nástroje zobrazení Volající volaný")

## <a name="analyze-memory-usage"></a>Analýza využití paměti

Okno **diagnostické nástroje** také umožňuje vyhodnotit využití paměti ve vaší aplikaci pomocí nástroje **využití paměti** . Například můžete se podívat na počet a velikost objektů v haldě. Můžete použít [Nástroj pro použití paměti integrovaného ladicího programu](../profiling/memory-usage.md) nebo [Nástroj pro využití paměti po porážce](../profiling/memory-usage-without-debugging2.md) v profileru výkonu.

Vývojáři rozhraní .NET mohou volit buď mezi [nástrojem pro přidělování objektů rozhraní .NET](../profiling/dotnet-alloc-tool.md) nebo nástrojem [využití paměti](../profiling/memory-usage.md) .

- Nástroj pro **přidělování objektů .NET** vám pomůže identifikovat vzory přidělení a anomálie v kódu .NET a pomáhá identifikovat běžné problémy s uvolňováním paměti. Tento nástroj se spouští jenom jako nástroj po porážce. Tento nástroj můžete spustit na místních nebo vzdálených počítačích.
- Nástroj **využití paměti** je užitečný při identifikaci nevracení paměti, které nejsou obvykle běžné v aplikacích .NET. Pokud potřebujete používat funkce ladicího programu při kontrole paměti, jako je například krokování prostřednictvím kódu, doporučuje se nástroj [pro integrované využití paměti ladicího programu](../profiling/beginners-guide-to-performance-profiling.md) .

Chcete-li analyzovat využití paměti nástrojem **využití paměti** , je třeba provést alespoň jeden snímek paměti. Nejlepším způsobem, jak analyzovat paměť, je často provedení dvou snímků. první napravo před problémem s podezřelou pamětí a druhý snímek hned po výskytu problému s podezřelou pamětí. Pak můžete zobrazit rozdíl dvou snímků a podívat se přesně, co se změnilo. Na následujícím obrázku je znázorněno pořízení snímku pomocí nástroje integrovaného s ladicím programem.

![Pořídit snímek v Diagnostické nástroje](../profiling/media/prof-tour-take-snapshots.gif "Diagnostické nástroje pořizování snímků")

Když vyberete jednu z odkazů na šipky, získáte rozdílové zobrazení haldy (červená šipka ![zvětšení využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zvýšení využití paměti") ukazuje zvýšení počtu objektů (vlevo) nebo zvýšení velikosti haldy (vpravo). Pokud kliknete na odkaz vpravo, dostanete zobrazení rozdílové haldy seřazené podle objektů, které zvýšily velikost haldy. To vám může pomáhat identifikovat problémy s pamětí. Například na obrázku níže jsou bajty používané `ClassHandlersStore` objekty zvyšovány o 3 492 bajtů ve druhém snímku.

![Diagnostické nástroje rozdílu haldy](../profiling/media/prof-tour-mem-usage-diff-heap.png "Diagnostické nástroje rozdílové zobrazení haldy")

Pokud kliknete na odkaz vlevo v zobrazení **Využití** paměti, je zobrazení haldy uspořádané podle počtu objektů. Objekty určitého typu, které zvýšily nejvíce čísel, se zobrazují v horní části (seřazené podle **sloupce Count Diff).**

## <a name="analyze-resource-consumption-xaml"></a>Analýza spotřeby prostředků (XAML)

V aplikacích XAML, jako jsou desktopové aplikace WPF pro Windows a aplikace pro UPW, můžete analyzovat spotřebu prostředků pomocí Časová osa aplikace windows. Můžete například analyzovat čas strávený přípravou snímků uživatelského rozhraní (rozložení a vykreslení), údržbou síťových a diskových požadavků a ve scénářích, jako je spuštění aplikace, načtení stránky a změna velikosti okna. Pokud chcete nástroj použít, **zvolte Časová osa aplikace** v Profiler výkonu a pak zvolte **Spustit.** V aplikaci si prohlédněte scénář s podezřelým problémem se spotřebou prostředků a pak zvolte **Zastavit** shromažďování a vygenerování sestavy.

Nízké snímkové rychlosti v grafu **propustnosti** vizuálu mohou odpovídat vizuálním problémům, které se zobrazí při spuštění aplikace. Podobně platí, že vysoké počty v grafu **využití** vlákna uživatelského rozhraní mohou také odpovídat problémům s odezvou uživatelského rozhraní. V sestavě můžete vybrat časové období s podezřelým problémem s výkonem a pak prozkoumat podrobné aktivity vlákna uživatelského rozhraní v zobrazení podrobností časové osy (dolní podokno).

![Časová osa aplikace profilace](../profiling/media/prof-tour-application-timeline.gif "Profilace průvodce Časová osa aplikace")

V zobrazení podrobnosti časové osy můžete najít informace, jako je typ aktivity (nebo prvek uživatelského rozhraní), spolu s dobou trvání aktivity. Například na obrázku trvá událost **rozložení** ovládacího prvku Grid 57,53 ms.

Další informace najdete v tématu [Časová osa aplikace](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Prozkoumání událostí aplikace

Prohlížeč [](../profiling/events-viewer.md) obecných událostí umožňuje zobrazit aktivitu vaší aplikace prostřednictvím seznamu událostí, jako je zatížení modulu, spuštění vlákna a konfigurace systému, a pomáhá lépe diagnostikovat výkon aplikace přímo v rámci Visual Studio profileru. Tento nástroj je k dispozici v profileru výkonu. Otevřete Profiler výkonu kliknutím na **ladit**  >  **Performance Profiler** (nebo **ALT + F2**).

Nástroj zobrazuje jednotlivé události v zobrazení seznamu. Sloupce obsahují informace o každé události, jako je název události, časové razítko a ID procesu.

![Trasování Prohlížeč událostí](../profiling/media/eventviewertrace.png "Prohlížeč událostí trasování")

## <a name="analyze-asynchronous-code-net"></a>Analyzovat asynchronní kód (.NET)

[Nástroj .NET Async](../profiling/analyze-async.md) umožňuje analyzovat výkon asynchronního kódu v aplikaci. Tento nástroj je k dispozici v profileru výkonu. Otevřete Profiler výkonu kliknutím na **ladit**  >  **Performance Profiler** (nebo **ALT + F2**).

Nástroj zobrazuje jednotlivé asynchronní operace v zobrazení seznamu. Můžete zobrazit informace, jako je čas spuštění, čas ukončení a celková doba asynchronní operace.

![Asynchronní nástroj .NET se zastavil.](../profiling/media/async-tool-opened.png ".NET Async zastavení nástroje")

## <a name="analyze-database-performance-net-core"></a>Analýza výkonu databáze (.NET Core)

V případě aplikací .NET Core, které používají ADO.NET nebo Entity Framework Core, vám [databázový nástroj](../profiling/analyze-database.md) umožňuje zaznamenávat databázové dotazy, které vaše aplikace vytváří během relace diagnostiky. Pak můžete analyzovat informace o jednotlivých dotazech, aby bylo možné najít místa, kde lze zlepšit výkon aplikace. Tento nástroj je k dispozici v profileru výkonu. Otevřete Profiler výkonu kliknutím na **ladit**  >  **Performance Profiler** (nebo **ALT + F2**).

Nástroj zobrazí každý dotaz v zobrazení seznamu. Můžete zobrazit informace, jako je čas zahájení a doba trvání dotazu.

![Vyhrazen](./media/db-gotosource.png "Přidělování")

## <a name="visualize-net-counters-net-core"></a>Vizualizace čítačů .NET (.NET Core)

Od verze Visual Studio 2019 verze 16.7 můžete čítače [.NET](../profiling/dotnet-counters-tool.md) použít v nástroji Visual Studio k vizualizaci čítačů výkonu. Čítače vytvořené pomocí čítačů [dotnet můžete vizualizovat.](/dotnet/core/diagnostics/dotnet-counters) Čítače dotnet podporují mnoho čítačů, například využití procesoru a velikost haldy systému uvolňování paměti.

Nástroj zobrazuje živé hodnoty pro každý čítač v zobrazení seznamu.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Shromažďování nástrojů čítačů .NET.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Prozkoumání událostí výkonu a přístupnosti uživatelského rozhraní (UPW)

V aplikacích pro UPW můžete povolit analýzu **uživatelského rozhraní** **v** Diagnostické nástroje okně. Nástroj vyhledá běžné problémy s výkonem nebo přístupností a během ladění je zobrazí v zobrazení Události.  Popisy událostí obsahují informace, které vám můžou pomoct při řešení problémů.

![Zobrazení událostí analýzy uživatelského rozhraní v diagnostických nástrojích](../profiling/media/prof-tour-ui-analysis.png "Diagnostické nástroje zobrazení událostí analýzy uživatelského rozhraní")

## <a name="analyze-gpu-usage-direct3d"></a>Analýza využití GPU (Direct3D)

V aplikacích Direct3D (komponenty Direct3D musí být v jazyce C++) můžete prozkoumat aktivitu gpu a analyzovat problémy s výkonem. Další informace najdete v tématu Využití [GPU.](./gpu-usage.md) Pokud chcete tento nástroj použít, zvolte **využití GPU** v Profiler výkonu a pak zvolte **Spustit**. V aplikaci si prohlédněte scénář, který vás zajímá profilace, a pak zvolte Zastavit shromažďování a vygenerování sestavy. 

Když v grafech vyberete časové období a zvolíte **zobrazit** podrobnosti, zobrazí se v dolním podokně podrobné zobrazení. V podrobném zobrazení můžete zjistit, k jaké aktivitě dochází na jednotlivých procesorech a GPU. Výběrem událostí v nejnižším podokně zobrazíte automaticky otevíraná okna na časové ose. Například výběrem události **Present (Prezentovat)** zobrazíte **automaticky otevíraná** okna Present call (Prezentovat volání). (Světlé šedé svislé VSync čáry lze použít jako referenci pro pochopení, zda některá **přítomná** volání vynechala vsync. Aby aplikace neustále dosáhla 60 FPS, musí **existovat jedno volání** mezi dvěma VSyncs.)

![Nástroj pro profilaci využití GPU](../profiling/media/prof-tour-gpu-usage.png "Diagnostika využití GPU")

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

V aplikacích pro UWP můžete analyzovat síťové operace prováděné pomocí `Windows.Web.Http` rozhraní API. Tento nástroj vám může pomáhat vyřešit problémy, jako jsou problémy s přístupem a ověřováním, nesprávné použití mezipaměti a špatný výkon zobrazení a stahování. Chcete-li použít nástroj, zvolte v profileru výkonu položku **síť** a pak zvolte možnost **Spustit**. Ve své aplikaci Projděte scénář, který používá `Windows.Web.Http` , a pak zvolte možnost **Zastavit shromažďování** pro vygenerování sestavy.

![Nástroj pro profilaci využití sítě](../profiling/media/prof-tour-network-usage.png "Diagnostika využití sítě")

Výběrem operace v souhrnném zobrazení zobrazíte další podrobnosti.

![Podrobné informace v nástroji Využití sítě](../profiling/media/prof-tour-network-usage-details.png "Podrobnosti o využití sítě pomocí nástroje Diag")

Další informace najdete v tématu [Využití sítě.](../profiling/network-usage.md)
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analýza výkonu (starší verze nástrojů)

::: moniker range="vs-2017"
Pokud potřebujete funkce, jako je instrumentace, které v současné době nejsou k dispozici v nástrojích využití procesoru nebo paměti, a používáte desktopové nebo ASP.NET aplikace, můžete použít Prohlížeč výkonu pro profilaci. (Nepodporuje se v aplikacích pro UPW). Další informace najdete v tématu [Prohlížeč výkonu](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
V Visual Studio 2019 byly starší verze Prohlížeč výkonu a související nástroje pro profilaci, jako je Průvodce výkonem, sbalené do Profiler výkonu, který můžete otevřít pomocí nástroje  >  **Ladění Profiler výkonu**. V Profiler výkonu dostupné diagnostické nástroje závisejí na zvoleném cíli a aktuálním otevřeném projektu po spuštění. Nástroj Využití PROCESORU poskytuje možnost vzorkování, která se dříve podporovala v Průvodci výkonem. Nástroj instrumentace poskytuje instrumentované funkce profilace (pro přesné počty volání a doby trvání), které byly v Průvodci výkonem. Další paměťové nástroje se zobrazí také v Profiler výkonu.
::: moniker-end

![Prohlížeč výkonu nástroje](../profiling/media/prof-tour-performance-explorer.png "Prohlížeč výkonu")

## <a name="which-tool-should-i-use"></a>Který nástroj mám použít?

Tady je tabulka, která uvádí různé nástroje, Visual Studio nabízí, a různé typy projektů, které můžete použít s:

::: moniker range=">=vs-2019"
|Nástroj pro výkon|Plocha Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Tipy pro výkon](../profiling/perftips.md)|ano|ano|ano|
|[Využití procesoru](../profiling/beginners-guide-to-performance-profiling.md)|ano|ano|ano|
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ano|
|[Přidělování objektů .NET](../profiling/dotnet-alloc-tool.md)|ano (pouze .NET)|ano|ano|
|[Využití GPU](./gpu-usage.md)|ano|ano|ne|
|[Časová osa aplikace](../profiling/application-timeline.md)|Ano (XAML)|ano|ne|
|[Prohlížeč událostí](../profiling/events-viewer.md)|ano|ano|ano|
|[.NET Async](../profiling/analyze-async.md)|Ano (jenom .NET)|ano|ano|
|[Čítače .NET](../profiling/dotnet-counters-tool.md)|Ano (jenom .NET Core)|ne|Ano (jenom ASP.NET Core)|
|[Databáze](../profiling/analyze-database.md)|Ano (jenom .NET Core)|ne|Ano (jenom ASP.NET Core)|
|[Prohlížeč výkonu](#analyze-performance-legacy-tools)|ne|ne|ne|
|[IntelliTrace](../debugger/intellitrace.md)|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Nástroj Performance Tool|Plocha Windows|UWP|Jádro ASP.NET/ASP.NET|
|----------------------|---------------------|-------------|-------------|
|[Využití CPU](../profiling/beginners-guide-to-performance-profiling.md)|ano|ano|ano|
|[Využití paměti](../profiling/memory-usage.md)|ano|ano|ano|
|[Využití GPU](./gpu-usage.md)|ano|ano|ne|
|[Časová osa aplikace](../profiling/application-timeline.md)|Ano (XAML)|ano|ne|
|[Tipy pro výkon](../profiling/perftips.md)|ano|Ano pro XAML, ne pro HTML|ano|
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|ano|ne|ano|
|[IntelliTrace](../debugger/intellitrace.md)|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|.NET jenom s Visual Studio Enterprise|
|[Využití sítě](../profiling/network-usage.md)|ne|ano|ne|
|[Rychlost odezvy uživatelského rozhraní (HTML)](../profiling/html-ui-responsiveness.md)|ne|Ano pro HTML, ne pro XAML|ne|
|[Paměť JavaScriptu](../profiling/javascript-memory.md)|ne|ano pro HTML, ne pro XAML|ne|
::: moniker-end


## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/debugger-feature-tour.md)