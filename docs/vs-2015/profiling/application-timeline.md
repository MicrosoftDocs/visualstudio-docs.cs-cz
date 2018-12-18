---
title: Časová osa aplikace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d3a8edb0a2bf7809fc125812b5d541ba008547a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751429"
---
# <a name="application-timeline"></a>Časová osa aplikace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití **časová osa aplikace** profiler k nalezení a opravení interakce aplikace související s problémy s výkonem v aplikacích XAML. Tento nástroj pomůže zlepšit výkon aplikací XAML tím, že poskytuje podrobné zobrazení využití prostředků aplikace. Můžete analyzovat času stráví přípravou snímků uživatelského rozhraní (rozložení a vykreslení), zpracování síťových a diskových požadavků aplikace a scénáře, jako je spuštění aplikace, načtení stránky a Windows změny velikosti.  
  
 **Časová osa aplikace** je jedním z nástrojů můžete začít s **ladění / Profiler výkonu...**  příkazu.  
  
 Tento nástroj nahrazuje **rychlost odezvy UI XAML** nástroj, který byl součástí diagnostických nástrojů pro Visual Studio 2013.  
  
 Tento nástroj můžete použít na následujících platformách:  
  
1.  Aplikace pro Universal Windows (ve Windows 10)  
  
2.  Windows Store 8.1  
  
3.  Windows Phone 8.1 (společnou platformu XAML)  
  
4.  Windows Presentation Foundation (.Net 4.0 a novější)  
  
5.  Windows 7  
  
> [!NOTE]
>  Můžete shromažďovat a analyzovat data o využití procesoru a data o spotřebě energie spolu s **ApplicationTimeline** data. Zobrazit [spustit profilovací nástroje bez ladění](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
##  <a name="BKMK_Collect_Timeline_data_for_your_app"></a> Shromažďování dat časová osa aplikace  
 Rychlost odezvy své aplikace na místním počítači, připojené zařízení, simulátoru sady Visual Studio nebo emulátory nebo vzdáleného zařízení. Zobrazit [spustit profilovací nástroje bez ladění](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
> [!TIP]
>  Pokud je to možné spusťte aplikaci přímo v zařízení. Výkon aplikace pozorovaný na simulátoru nebo prostřednictvím připojení ke vzdálené ploše nemusí být stejný jako skutečný výkon v zařízení. Shromažďování dat pomocí Visual Studio Remote Tools na druhé straně neovlivní údaje o výkonu.  
  
 Zde jsou základní kroky:  
  
1.  Otevření aplikace XAML.  
  
2.  Klikněte na tlačítko **ladění / Profiler výkonu...** . Zobrazí se seznam v okně .diagsession nástroje pro profilaci.  
  
3.  Vyberte **časová osa aplikace** a potom klikněte na tlačítko **Start** v dolní části okna.  
  
    > [!NOTE]
    >  Může se zobrazit okno Řízení uživatelských účtů ke spuštění VsEtwCollector.exe. Klikněte na tlačítko **Ano**.  
  
4.  Spusťte scénář zájem o profilování ve vaší aplikaci ke shromažďování dat výkonu.  
  
5.  Pokud chcete profilaci zastavit, přepněte zpět do okna .diagsession a klikněte na tlačítko **Zastavit** v horní části okna.  
  
     Aplikace Visual Studio analyzuje shromážděná data a zobrazuje výsledky.  
  
     ![Sestava profileru časová osa](../profiling/media/timeline-base.png "TIMELINE_Base")  
  
##  <a name="BKMK_Analyze_Timeline_profiling_data"></a> Analyzujte data profilování časové osy  
 Chcete-li spustit analýzu, řiďte se po shromáždění profilačních dat těmito kroky:  
  
1.  Zkontrolujte informace v **využití vlákna UI** a **vizuální propustnost (FPS)** grafů a pak pomocí navigačních panelů časové ose vyberte časový rozsah, který chcete analyzovat.  
  
2.  Podle informací uvedených v **využití vlákna UI** nebo **vizuální propustnost (FPS)** grafů, zkontrolujte podrobnosti v **podrobnosti časové osy** zobrazení zjistíte tak možné příčiny náhledech rychlost odezvy.  
  
###  <a name="BKMK_Report_scenarios_categories_and_events"></a> Sestava scénáře, kategorie a události  
 **Časová osa aplikace** nástroj zobrazí data o časování pro scénáře, kategorie a události, které se vztahují k výkonu XAML.  
  
###  <a name="BKMK_Diagnostic_session_timeline"></a> Časová osa diagnostiky  
 ![Výkon a Diagnostika časová osa](../profiling/media/diaghub-timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 Pravítka v horní části stránky zobrazuje časovou osu profilovaných informací. Tato časová osa platí jak **využití vlákna UI** grafu a **vizuální propustnost** grafu. Přetažením navigačních panelů na časové ose můžete vybrat určitou část časové osy a zúžit tak rozsah sestavy.  
  
 Na časové ose se také zobrazují všechny uživatelské značky, které jste tam vložili, a události z aktivačního životního cyklu aplikace.  
  
###  <a name="BKMK_UI_thread_utilization_graph"></a> Graf využití vlákna UI  
 ![Graf využití procesoru](../profiling/media/timeline-cpuutilization.png "TIMELINE_CpuUtilization")  
  
 **Využití vlákna UI (%)** graf je pruhový graf, který zobrazuje relativní množství času stráveného v kategorii během zadané kolekce.  
  
###  <a name="BKMK_Visual_throughput_FPS_graph"></a> Vizuální propustnost (FPS) grafu  
 ![Vizuální propustnost grafu](../profiling/media/timeline-visualthroughput.png "TIMELINE_VisualThroughput")  
  
 **Vizuální propustnost (FPS)** spojnicový graf zobrazuje počet snímků za sekundu (FPS) ve vlákně uživatelského rozhraní a složení aplikace.  
  
###  <a name="BKMK_Timeline_details_"></a> Podrobnosti časové osy  
 Zobrazení podrobností je, kde bude útraty většinu svého času analýza sestavy. Zobrazuje podrobné zobrazení využití procesoru aplikace zařazený do kategorie službou subsystému architekturu uživatelského rozhraní nebo součást systému provedla spotřebovávaného procesoru.  
  
 Podporují se následující události:  
  
|||  
|-|-|  
|**Analýza kódu**|Čas strávený analýzou soubory XAML a vytváření objektů.<br /><br /> Rozbalení **analýza** uzel v **podrobnosti časové osy** zobrazí řetězec závislostí všech souborů XAML, které se v důsledku události kořenové zparsoval. To vám umožní identifikovat nepotřebného souboru analýzy a objekt vytváření ve scénářích citlivé výkonu a optimalizovat je.|  
|**Rozložení**|U velkých aplikací může tisíce prvky uvedené na obrazovce ve stejnou dobu. To může způsobit nízká Snímková frekvence uživatelského rozhraní a odezvu odpovídajícím způsobem nízký aplikace. Událost rozvržení přesně určuje náklady na vytváření rozložení jednotlivých prvků (tj. čas strávený v uspořádat, míry, ApplyTemplate, ArrangeOverride a ArrangeOverride) a sestaví vizuální stromové struktury, které účastnilo předání rozložení. Tato vizualizace můžete určit, které logické stromů musí vyřazení nebo jiných mechanismů odložení optimalizovat pasu rozložení vyhodnotit.|  
|**Vykreslení**|Čas strávený výkresu prvky XAML na obrazovku.|  
|**MŮŽU / 0**|Doba trvání načtení dat z místního disku nebo ze síťové prostředky, které jsou přístupné prostřednictvím [Microsoft Windows Internet (WinINet) rozhraní API](https://msdn.microsoft.com/library/windows/desktop/aa385331.aspx).|  
|**Kód aplikace**|Čas strávený prováděním kódu aplikace (uživatel), který nesouvisí s analýzou ani rozložením.|  
|**XAML – ostatní**|Čas strávený prováděním kódu modulu runtime XAML.|  
  
> [!TIP]
>  Zvolte **využití procesoru** společně s nástroji **časová osa aplikace** nástroj při spuštění profilace zobrazit aplikace metody, které jsou spouštěny na vlákně UI. Přesunutí kódu dlouho běžící aplikace do vlákna na pozadí může zvýšit rychlost odezvy UI.  
  
####  <a name="BKMK_Customizing_Timeline_details_"></a> Přizpůsobení podrobnosti časové osy  
 Použití **podrobnosti časové osy** nástrojů můžete řadit, filtrovat a zadejte poznámky o **podrobnosti časové osy** zobrazení položek.  
  
|||  
|-|-|  
|**Seřadit podle:**|Seřadit podle počáteční čas nebo délka události.|  
|![Skupiny událostí podle rámce](../profiling/media/timeline-groupbyframes.png "TIMELINE_GroupByFrames")|Přidá nebo odebere na nejvyšší úrovni **rámce** kategorie, které jsou seskupeny události podle rámce.|  
|![Seznam podrobností filtr časové osy](../profiling/media/timeline-filter.png "TIMELINE_Filter")|Vyfiltruje seznam vybraných kategorií a délka události.|  
|![Upravit informace o časové osy](../profiling/media/timeline-viewsettings.png "TIMELINE_ViewSettings")|Umožňuje určit poznámky k události.|  
  
## <a name="see-also"></a>Viz také  
 [Blog týmu WPF: Nové uživatelské rozhraní nástroj pro analýzu výkonu aplikace WPF](http://blogs.msdn.com/b/wpf/archive/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications.aspx)   
 [Osvědčené postupy z hlediska výkonu pro aplikace Windows Store pomocí jazyka C++, C# a Visual Basic](http://msdn.microsoft.com/en-us/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [Optimalizace výkonu aplikace WPF](http://msdn.microsoft.com/library/ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf)



