---
title: Analýza spotřeby prostředků v aplikacích XAML
description: Pomocí nástroje Časová osa aplikace Profiler můžete najít problémy s výkonem v aplikacích XAML. Můžete analyzovat čas strávený na různých úlohách v různých scénářích.
ms.custom: SEO-VS-2020
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d352c118bd8b21b9dcbf62f7dd32eaf2999ed471
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388019"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Aktivita analýzy využití prostředků a vlákna uživatelského rozhraní (XAML)

Pomocí nástroje **Časová osa aplikace** Profiler můžete vyhledat a opravit související problémy s výkonem v aplikacích XAML v interakci s aplikací. Tento nástroj pomáhá zlepšit výkon aplikace XAML zobrazením podrobného zobrazení spotřeby prostředků aplikací. Můžete analyzovat čas strávený vaší aplikací při přípravě rámců uživatelského rozhraní (rozložení a vykreslování), obsluhování síťových a diskových požadavků a ve scénářích, jako je spuštění aplikace, načítání stránky a změna velikosti oken.

**Časová osa aplikace** je jedním z nástrojů, které můžete spustit pomocí příkazu **ladit**  >  **výkon profileru** .

Tento nástroj nahrazuje nástroj **rychlost odezvy UI XAML** , který byl součástí diagnostické sady nástrojů pro Visual Studio 2013.

Tento nástroj můžete použít na následujících platformách:

- Univerzální aplikace pro Windows (ve Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.NET 4,0 a vyšší)
- Windows 7

> [!NOTE]
> Můžete shromažďovat a analyzovat data o využití procesoru a údaje o spotřebě energie společně s **ApplicationTimeline** daty. Viz [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="collect-application-timeline-data"></a>Shromažďovat data časové osy aplikace

Můžete profilovat rychlost odezvy vaší aplikace na místním počítači, připojeném zařízení, simulátoru nebo emulátorech sady Visual Studio nebo na vzdáleném zařízení. Viz [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Pokud je to možné, spusťte aplikaci přímo na zařízení. Výkon aplikace zjištěný simulátorem nebo prostřednictvím připojení ke vzdálené ploše nemusí být stejný jako skutečný výkon na zařízení. Na druhé straně shromažďování dat pomocí nástrojů Visual Studio Remote Tools neovlivní data výkonu.

Zde jsou základní kroky:

1. Otevřete aplikaci XAML.

2. Klikněte na **ladit/Profiler výkonu**. V okně. diagsession by se měl zobrazit seznam nástrojů pro profilaci.

3. Vyberte **Časová osa aplikace** a potom v dolní části okna klikněte na tlačítko **Spustit** .

   ![Vybraný nástroj Časová osa aplikace](../profiling/media/apptimelineselect.png "Nástroj Časová osa aplikace")

   > [!NOTE]
   > Může se zobrazit okno Řízení uživatelských účtů požadující vaše oprávnění ke spuštění *VsEtwCollector.exe*. Klikněte na **Ano**.

4. Pokud chcete shromažďovat údaje o výkonu, spusťte scénář, který vás zajímá při profilaci ve vaší aplikaci.

5. Pokud chcete profilaci zastavit, přepněte zpátky do okna. diagsession a v horní části okna klikněte na **zastavit** .

   Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.

   ![Sestava profileru časové osy](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analýza dat profilace časových os

Chcete-li spustit analýzu, řiďte se po shromáždění profilačních dat těmito kroky:

1. Prohlédněte si informace v grafech **využití vlákna uživatelského rozhraní** a **Vizuální propustnost (FPS)** a pak pomocí navigačních panelů pro časovou osu vyberte časový rozsah, který chcete analyzovat.

2. Pomocí informací v grafech **využití vlákna uživatelského rozhraní** nebo **Vizuální propustnost (FPS)** zkontrolujte podrobnosti v zobrazení **Details Timeline** , abyste zjistili možné příčiny nedostatku odezvy.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a> Scénáře, kategorie a události sestav

Nástroj **Časová osa aplikace** zobrazuje data časování pro scénáře, kategorie a události, které souvisejí s výkonem XAML.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a> Časová osa relace diagnostiky

![Časová osa výkonu a diagnostiky](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Pravítko v horní části stránky zobrazuje časovou osu pro profilované informace. Tato časová osa se vztahuje na graf **využití vlákna uživatelského rozhraní** i na graf pro **Vizuální propustnost** . Přetažením navigačních panelů na časové ose můžete vybrat určitou část časové osy a zúžit tak rozsah sestavy.

Časová osa taky zobrazuje všechny uživatelské značky, které jste vložili, a události životního cyklu aktivace aplikace.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a> Graf využití vlákna uživatelského rozhraní

![Graf využití procesoru](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

Graf **využití vlákna UI (%)** je pruhový graf, který zobrazuje relativní dobu strávenou v kategorii pro v rámci rozsahu kolekce.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a> Graf vizuální propustnost (FPS)

![Graf propustnosti vizuálů](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

Spojnicový graf **Vizuální propustnost (FPS)** zobrazuje počet snímků za sekundu (FPS) v uživatelském rozhraní a vlákně kompozice pro aplikaci.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a> Podrobnosti časové osy

V zobrazení podrobností je místo, kde strávíte většinu času analýzou sestavy. Zobrazuje využití procesoru vaší aplikací, které jsou zařazeny do kategorie pomocí subsystému uživatelského rozhraní nebo systémové součásti, která CPU využila.

Podporují se tyto události:

|Název|Description|
|-|-|
|**Analýze**|Čas strávený analýzou souborů XAML a vytváření objektů<br /><br /> Rozbalením uzlu **analýzy** v **podrobnostech časové osy** se zobrazí řetězec závislosti všech souborů XAML, které byly analyzovány z důvodu kořenové události. Tento tip vám umožní identifikovat nepotřebnou analýzu souborů a vytvoření objektu ve scénářích citlivých na výkon a optimalizovat.|
|**Rozložení**|Ve velkých aplikacích lze na obrazovce zobrazit tisíce prvků současně. Tento displej může mít za následek tempo snímků uživatelského rozhraní a odpovídající nedostatečnou odezvu aplikace. Událost rozložení přesně určuje náklady na rozložení každého prvku (to znamená čas strávený při uspořádání, měření, ApplyTemplate, ArrangeOverride a MeasureOverride). Vytvoří také vizuální stromy, které byly součástí průchodu rozložení. Tuto vizualizaci můžete použít k určení, které logické stromy se mají vyřadit, nebo k vyhodnocení jiných mechanismů odložení pro optimalizaci úspěšnosti rozložení.|
|**Vykreslování**|Čas strávený vykreslováním prvků XAML na obrazovce|
|**I/0**|Čas strávený načítáním dat z místního disku nebo ze síťových prostředků, které jsou dostupné prostřednictvím [rozhraní Microsoft Windows Internet (WinInet) API](/windows/desktop/WinInet/portal).|
|**Kód aplikace**|Čas strávený prováděním kódu aplikace (uživatele), který není v souvislosti s analýzou nebo rozložením.|
|**XAML – ostatní**|Čas strávený spouštěním kódu XAML runtime.|

> [!TIP]
> Když spustíte profilování pro zobrazení metod aplikace, které se spouštějí ve vlákně uživatelského rozhraní, vyberte nástroj **využití CPU** společně s nástrojem **Časová osa aplikace** . Přesun dlouhotrvajícího kódu aplikace do vlákna na pozadí může zlepšit rychlost odezvy uživatelského rozhraní.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a> Přizpůsobení podrobností časové osy

Pomocí panelu nástrojů **Podrobnosti časové osy** můžete seřadit, filtrovat a zadat poznámky k **podrobnostem zobrazení na časové ose** .

|Název|Description|
|-|-|
|**Seřadit podle**|Seřaďte data podle času zahájení nebo délky událostí.|
|![Seskupit události podle rámce](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Přidá nebo odebere kategorii **rámce** nejvyšší úrovně, která seskupuje události podle rámce.|
|![Filtrovat seznam podrobností časové osy](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Vyfiltruje seznam podle vybraných kategorií a délky událostí.|
|![Přizpůsobení informací o podrobnostech časové osy](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umožňuje zadat poznámky pro události.|

## <a name="see-also"></a>Viz také

- [Blog týmu WPF: nový nástroj pro analýzu výkonu uživatelského rozhraní pro aplikace WPF](/archive/blogs/wpf/new-ui-performance-analysis-tool-for-wpf-applications)
- [Osvědčené postupy výkonu pro aplikace pro UWP pomocí C++, C# a Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optimalizace výkonu aplikace WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)