---
title: Analýza spotřeby prostředků v aplikacích XAML
ms.custom: seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a368a9b8f6d25753993a2cc10ea9ca94734d6709
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128280"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analýza spotřeby prostředků a aktivity vlákna uživatelského rozhraní (XAML)

Pomocí profileru **časové osy aplikace** vyhledejte a opravte problémy s výkonem související s interakcí aplikací v aplikacích XAML. Tento nástroj pomáhá zlepšit výkon aplikace XAML zobrazením podrobného zobrazení spotřeby prostředků aplikací. Můžete analyzovat čas strávený aplikací při přípravě rámců uživatelského rozhraní (rozložení a vykreslení), obsluhovat síťové a diskové požadavky a ve scénářích, jako je spuštění aplikace, načítání stránky a změna velikosti systému Windows.

**Časová osa aplikace** je jedním z nástrojů, které můžete začít pomocí příkazu **Ladění** > **profilu výkonu.**

Tento nástroj nahrazuje nástroj **odezvy uživatelského rozhraní XAML,** který byl součástí diagnostické sady nástrojů pro Visual Studio 2013.

Tento nástroj můžete použít na následujících platformách:

- Univerzální aplikace pro Windows (ve Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 a vyšší)
- Windows 7

> [!NOTE]
> Můžete shromažďovat a analyzovat data o využití procesoru a spotřeby energie spolu s daty **ApplicationTimeline.** Viz [Spuštění nástrojů profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="collect-application-timeline-data"></a>Shromažďování dat časové osy aplikace

Můžete profilovat odezvu aplikace na místním počítači, připojeném zařízení, simulátoru sady Visual Studio nebo emulátorech nebo vzdáleném zařízení. Viz [Spuštění nástrojů profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Pokud je to možné, spusťte aplikaci přímo na zařízení. Výkon aplikace pozorovaný na simulátoru nebo prostřednictvím připojení ke vzdálené ploše nemusí být stejný jako skutečný výkon v zařízení. Na druhou stranu shromažďování dat pomocí vzdálené nástroje sady Visual Studio nemá vliv na data o výkonu.

Zde jsou základní kroky:

1. Otevřete aplikaci XAML.

2. Klepněte na **položku Ladění / Profilování výkonu**. V okně diagsession by se měl zobrazit seznam nástrojů pro profilování.

3. Vyberte **Časová osa aplikace** a v dolní části okna klikněte na **Start.**

   > [!NOTE]
   > Může se zobrazit okno Řízení uživatelských účtů požadující vaše oprávnění ke spuštění souboru *VsEtwCollector.exe*. Klepněte na tlačítko **Ano**.

4. Spusťte scénář, který vás zajímá profilování ve vaší aplikaci ke shromažďování dat o výkonu.

5. Profilování můžete ukončit, přepněte zpět do okna DiagSession a v horní části okna klepněte na **tlačítko Zastavit.**

   Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.

   ![Sestava profileru časové osy](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analýza dat profilování časové osy

Chcete-li spustit analýzu, řiďte se po shromáždění profilačních dat těmito kroky:

1. Zobrazte informace v **grafech využití vlákna uživatelského rozhraní** a **vizuální propustnosti (FPS)** a potom pomocí navigačních panelů časové osy vyberte časový rozsah, který chcete analyzovat.

2. Pomocí informací v **grafech využití vlákna uživatelského rozhraní** nebo **vizuální propustnosti (FPS)** zkontrolujte podrobnosti v zobrazení **podrobnosti časové osy** a vyhledejte možné příčiny jakékoli zdánlivé neodezvy.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a>Sestavy scénářů, kategorií a událostí

Nástroj **Časová osa aplikace** zobrazuje data časování pro scénáře, kategorie a události, které souvisejí s výkonem XAML.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a>Časová osa diagnostické relace

![Časová osa výkonu a diagnostiky](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Pravítko v horní části stránky zobrazuje časovou osu profilovaných informací. Tato časová osa platí pro graf **využití vlákna uživatelského rozhraní** i **propustnost visual.** Přetažením navigačních panelů na časové ose můžete vybrat určitou část časové osy a zúžit tak rozsah sestavy.

Časová osa také zobrazuje všechny uživatelské značky, které jste vložili, a události životního cyklu aktivace aplikace.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a>Graf využití vlákna uživatelského rozhraní

![Graf využití procesoru](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

Graf **využití vlákna uživatelského rozhraní (%)** je pruhový graf, který zobrazuje relativní množství času stráveného v kategorii během rozsahu kolekce.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a>Graf vizuální propustnost (FPS)

![Graf vizuální propustnosti](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

**Graf čáry vizuální propustnost (FPS)** zobrazuje snímky za sekundu (FPS) v uživatelském rozhraní a složení vlákna pro aplikaci.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a>Podrobnosti o časové ose

Zobrazení podrobností je místo, kde trávíte většinu času analýzou sestavy. Zobrazuje využití procesoru vaší aplikací kategorizovanou podsystémem rozhraní UI Framework nebo systémovou komponentou, která procesor spotřebovává.

Podporovány jsou následující události:

|||
|-|-|
|**Analýzy**|Čas strávený analýzou souborů XAML a vytvářením objektů.<br /><br /> Rozbalení **množení** uzlu v **podrobnostech časové osy** zobrazí řetěz závislostí všech souborů XAML, které byly analyzovány z důvodu kořenové události. Tento tip umožňuje identifikovat nepotřebné analýzy souborů a vytváření objektů ve scénářích citlivých na výkon a optimalizovat je.|
|**Rozložení**|Ve velkých aplikacích mohou být na obrazovce současně zobrazeny tisíce prvků. Toto zobrazení může mít za následek nízkou kmitočet snímků uživatelského rozhraní a odpovídajícím způsobem špatnou odezvu aplikace. Layout událost přesně určuje náklady na rozložení každého prvku (to znamená, že čas strávený v Uspořádat, Rozměr, ApplyTemplate, ArrangeOverride a MeasureOverride). Také vytváří vizuální stromy, které se zúčastnily průchodu rozložení. Tuto vizualizaci můžete použít k určení, které logické stromy prořezávat, nebo vyhodnotit jiné mechanismy odkladu k optimalizaci průchodu rozložení.|
|**Vykreslování**|Čas strávený kreslením prvků XAML na obrazovku.|
|**I/0**|Čas strávený načítáním dat z místního disku nebo ze síťových prostředků, ke kterým se přistupuje prostřednictvím [rozhraní API WinINet (Microsoft Windows Internet).](/windows/desktop/WinInet/portal)|
|**Kód aplikace**|Čas strávený prováděním kódu aplikace (uživatele), který nesouvisí s analýzou nebo rozložením.|
|**Xaml Ostatní**|Čas strávený prováděním runtime kódu XAML.|

> [!TIP]
> Zvolte nástroj **využití procesoru** spolu s nástrojem **Časová osa aplikace,** když začnete profilování pro zobrazení metod aplikace, které se spouštějí ve vlákně uživatelského rozhraní. Přesunutí dlouho běžícího kódu aplikace do vlákna na pozadí může zlepšit odezvu uživatelského rozhraní.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a>Přizpůsobení podrobností časové osy

Panel nástrojů **Podrobnosti časové osy** slouží k řazení, filtrování a zadávání poznámek položek zobrazení **podrobností časové osy.**

|||
|-|-|
|**Řadit podle**|Seřaďte podle počátečního času nebo délky událostí.|
|![Seskupení událostí podle snímků](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Přidá nebo odebere kategorii **rámce** nejvyšší úrovně, která seskupuje události podle snímků.|
|![Filtrovat seznam podrobností časové osy](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtruje seznam podle vybraných kategorií a délky událostí.|
|![Přizpůsobení podrobností časové osy](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umožňuje určit poznámky k událostem.|

## <a name="see-also"></a>Viz také

- [WPF týmový blog: Nový nástroj pro analýzu výkonu ui pro wpf aplikace](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)
- [Doporučené postupy pro výkon pro aplikace UPW pomocí aplikací C++, C# a Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optimalizace výkonu aplikace WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
