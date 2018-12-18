---
title: Analýza spotřeby prostředků v aplikacích XAML
ms.custom: seodec18
ms.date: 11/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 32368b280faf7b87aa128865cf169c7675a58c95
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059175"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analýza využití prostředků a aktivita vlákno uživatelského rozhraní (XAML)

Použití **časová osa aplikace** profiler k nalezení a opravení interakce aplikace související s problémy s výkonem v aplikacích XAML. Tento nástroj pomůže zlepšit výkon aplikace XAML tím, že zobrazuje podrobné zobrazení využití prostředků aplikace. Můžete analyzovat času stráví přípravou snímků uživatelského rozhraní (rozložení a vykreslení), zpracování síťových a diskových požadavků aplikace a scénáře, jako je spuštění aplikace, načtení stránky a změna velikosti Windows.

**Časová osa aplikace** je jedním z nástrojů můžete začít s **ladění** > **Profiler výkonu** příkazu.

Tento nástroj nahrazuje **rychlost odezvy UI XAML** nástroj, který byl součástí diagnostických nástrojů pro Visual Studio 2013.

Tento nástroj můžete použít na následujících platformách:

- Aplikace pro Universal Windows (ve Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 a novější)
- Windows 7

> [!NOTE]
> Můžete shromažďovat a analyzovat data o využití procesoru a data o spotřebě energie spolu s **ApplicationTimeline** data. Zobrazit [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
## <a name="collect-application-timeline-data"></a>Shromažďování dat časová osa aplikace

Rychlost odezvy své aplikace na místním počítači, připojené zařízení, simulátoru sady Visual Studio nebo emulátory nebo vzdáleného zařízení. Zobrazit [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Pokud je to možné spusťte aplikaci přímo v zařízení. Výkon aplikace pozorovaný na simulátoru nebo prostřednictvím připojení ke vzdálené ploše nemusí být stejný jako skutečný výkon v zařízení. Na druhé straně shromažďování dat pomocí Visual Studio Remote Tools nemá vliv na data výkonu.  

Zde jsou základní kroky:  

1. Otevření aplikace XAML.

2. Klikněte na tlačítko **ladění / Profiler výkonu**. Zobrazí se seznam v okně .diagsession nástroje pro profilaci.

3. Vyberte **časová osa aplikace** a potom klikněte na tlačítko **Start** v dolní části okna.

   > [!NOTE]
   > Může se zobrazit okno Řízení uživatelských účtů ke spuštění *VsEtwCollector.exe*. Klikněte na tlačítko **Ano**.

4. Spusťte scénář zájem o profilování ve vaší aplikaci ke shromažďování dat výkonu.

5. Pokud chcete profilaci zastavit, přepněte zpět do okna .diagsession a klikněte na tlačítko **Zastavit** v horní části okna.

   Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.

   ![Sestava profileru časová osa](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Analyzujte data profilování časové osy

Chcete-li spustit analýzu, řiďte se po shromáždění profilačních dat těmito kroky:  
  
1. Prohlédněte si informace **využití vlákna UI** a **vizuální propustnost (FPS)** grafů a pak pomocí navigačních panelů časové ose vyberte časový rozsah, který chcete analyzovat.  
  
2. Podle informací uvedených v **využití vlákna UI** nebo **vizuální propustnost (FPS)** grafů, zkontrolujte podrobnosti v **podrobnosti časové osy** zobrazení najít možné způsobí, že pro rozpor seeming rychlost odezvy.
  
### <a name="BKMK_Report_scenarios_categories_and_events"></a> Sestava scénáře, kategorie a události  

**Časová osa aplikace** nástroj zobrazí data o časování pro scénáře, kategorie a události, které se vztahují k výkonu XAML.  

### <a name="BKMK_Diagnostic_session_timeline"></a> Časová osa diagnostiky  

![Výkon a Diagnostika časová osa](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  

Pravítka v horní části stránky zobrazuje časovou osu profilovaných informací. Tato časová osa platí jak **využití vlákna UI** grafu a **vizuální propustnost** grafu. Přetažením navigačních panelů na časové ose můžete vybrat určitou část časové osy a zúžit tak rozsah sestavy.  

Na časové ose se zobrazí také všechny uživatelské značky, které jste vložili a události z aktivačního životního aplikace.  

### <a name="BKMK_UI_thread_utilization_graph"></a> Graf využití vlákna UI

![Graf využití procesoru](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")  

**Využití vlákna UI (%)** graf je pruhový graf, který zobrazuje relativní množství času stráveného v kategorii během zadané kolekce.  

### <a name="BKMK_Visual_throughput_FPS_graph"></a> Vizuální propustnost (FPS) grafu  

![Vizuální propustnost grafu](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")  

**Vizuální propustnost (FPS)** spojnicový graf zobrazuje počet snímků za sekundu (FPS) ve vlákně uživatelského rozhraní a složení aplikace.  

### <a name="BKMK_Timeline_details_"></a> Podrobnosti časové osy  

Zobrazení podrobností je, kde strávíte nejvíce času analýza sestavy. Zobrazuje využití procesoru v aplikaci zařazený do kategorie službou subsystému architekturu uživatelského rozhraní nebo součást systému provedla spotřebovávaného procesoru.

Podporují se následující události:  

|||  
|-|-|  
|**Analýza kódu**|Čas strávený analýzou soubory XAML a vytváření objektů.<br /><br /> Rozbalení **analýza** uzel v **podrobnosti časové osy** zobrazí řetězec závislostí všech souborů XAML, které byly analyzovat z důvodu kořenové události. Tento tip vám umožní identifikovat nepotřebného souboru analýzy a objekt vytváření ve scénářích citlivé výkonu a optimalizovat je.|  
|**Rozložení**|U velkých aplikací může tisíce prvky uvedené na obrazovce ve stejnou dobu. Toto zobrazení může způsobit nízká Snímková frekvence uživatelského rozhraní a odezvu odpovídajícím způsobem nízký aplikace. Událost rozvržení lze přesně určit, náklady na každý prvek rozložení (to znamená, doba trvání uspořádat, míry, ApplyTemplate, ArrangeOverride a MeasureOverride). Zároveň vytvoří vizuální stromové struktury, které účastnilo předání rozložení. Chcete-li určit, které logické stromové struktury, chcete-li vyřadit nebo k vyhodnocení jiné mechanismy odložení optimalizovat pasu rozložení můžete použít tuto vizualizaci.|  
|**Vykreslení**|Čas strávený výkresu prvky XAML na obrazovku.|  
|**MŮŽU / 0**|Doba trvání načtení dat z místního disku nebo ze síťové prostředky, které jsou přístupné prostřednictvím [Microsoft Windows Internet (WinINet) rozhraní API](/windows/desktop/WinInet/portal).|  
|**Kód aplikace**|Čas strávený prováděním kódu aplikace (uživatel), který nesouvisí s analýzou ani rozložením.|  
|**XAML – ostatní**|Čas strávený prováděním kódu modulu runtime XAML.|  
  
> [!TIP]
> Zvolte **využití procesoru** společně s nástroji **časová osa aplikace** nástroj při spuštění profilace zobrazit aplikace metody, které jsou spouštěny na vlákně UI. Přesunutí kódu dlouho běžící aplikace do vlákna na pozadí může zvýšit rychlost odezvy UI.  
  
#### <a name="BKMK_Customizing_Timeline_details_"></a> Přizpůsobení podrobnosti časové osy  

Použití **podrobnosti časové osy** nástrojů můžete řadit, filtrovat a zadejte poznámky o **podrobnosti časové osy** zobrazení položek.  
  
|||  
|-|-|  
|**Seřadit podle:**|Seřadit podle počáteční čas nebo délka události.|  
|![Skupiny událostí podle rámce](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Přidá nebo odebere na nejvyšší úrovni **rámce** kategorie, které jsou seskupeny události podle rámce.|  
|![Seznam podrobností filtr časové osy](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Vyfiltruje seznam vybraných kategorií a délka události.|  
|![Upravit informace o časové osy](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Umožňuje určit poznámky k události.|  
  
## <a name="see-also"></a>Viz také:

- [Blog týmu WPF: nástroj pro analýzu výkonu nové uživatelské rozhraní pro aplikace WPF](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)  
- [Osvědčené postupy z hlediska výkonu pro aplikace pro UPW pomocí jazyka C++, C# a Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Optimalizace výkonu aplikace WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
- [Profilace v sadě Visual Studio](../profiling/index.md)  
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
