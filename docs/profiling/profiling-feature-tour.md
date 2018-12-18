---
title: Měřit výkon pomocí nástroje pro profilaci
description: Stručný podívejte se na různé diagnostické nástroje, který je k dispozici v sadě Visual Studio.
ms.custom: mvc
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f884b92d03027782eed27f4583e06b1141341db
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356792"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Rychlý start: Nejdřív se podívejte na nástroje pro profilaci

Visual Studio poskytuje širokou škálu profilování nástroje, které pomáhají diagnostikovat různé druhy problémů s výkonem v závislosti na typu aplikace.

V okně diagnostické nástroje jsou k dispozici nástrojů pro profilaci, ke kterým může přistupovat během relace ladění. V okně diagnostické nástroje se zobrazí automaticky, pokud jste ji vypnuli. Otevřete okno, klikněte na tlačítko **ladění / Windows / zobrazit diagnostické nástroje**. V otevřeném okně můžete vybrat nástroje, pro které chcete shromažďovat data.

![Okno diagnostické nástroje](../profiling/media/prof-tour-diagnostic-tools.png "diagnostické nástroje")

Při ladění, můžete použít **diagnostické nástroje** okna k analýze procesoru a využití paměti a můžete zobrazit události, které obsahuje informace související s výkonem.

![Diagnostické nástroje souhrnné zobrazení](../profiling/media/prof-tour-cpu-and-memory-graph.gif "souhrn diagnostické nástroje")

**Diagnostické nástroje** okno je často preferovaný způsob, jak profil aplikace, ale pro buildy vydaných verzí. můžete také provést a dodatečně analyzovat aplikace místo. Pokud chcete další informace o různých přístupů, přečtěte si téma [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Profilace nástroj pro podporu různých typů aplikací najdete v tématu [který nástroj mám použít?](#which-tool-should-i-use).

> [!NOTE]
> Můžete použít nástroje a dodatečně s Windows 7 a novější. Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno).

## <a name="analyze-cpu-usage"></a>Analýza využití procesoru

Nástroj využití CPU je dobrým začátkem analýzu výkonu vaší aplikace. To zjistíte další informace o prostředky procesoru, které vaše aplikace spotřebovává. Podrobnější návod, nástroj využití CPU, naleznete v tématu [příručka začátečníka profilací výkonu](../profiling/beginners-guide-to-performance-profiling.md).

Z **Souhrn** zobrazení diagnostických nástrojů, zvolte **povolit profilaci procesoru** (musíte být v relaci ladění).

![Povolit využití procesoru v okně diagnostické nástroje](../profiling/media/prof-tour-enable-cpu-profiling.png "diagnostické nástroje povolit využití procesoru")

K co nejefektivnějšímu nástrojem nastavte dva zarážky v kódu, jeden na začátku a na konci funkce nebo oblasti kód, který chcete analyzovat. Když je pozastaveno na zarážce druhý, zkontrolujte dat profilování.

**Využití procesoru** zobrazení se zobrazí seznam funkcí, které jsou seřazené podle nejdelší spuštění s nejdelší dobou funkce v horní části. To vám pomůže funkcí kde jsou kritické body výkonu děje.

![Zobrazit diagnostické nástroje využití CPU](../profiling/media/prof-tour-cpu-usage.png "diagnostické nástroje využití CPU")

Poklikejte na funkci, že máte zájem, a zobrazí podrobnější pohled na tři podokna "motýlkový", s vybranou funkci uprostřed období, volání funkce na levé straně a volat funkce na pravé straně. **Tělo funkce** část ukazuje celkové množství času (a procentuální hodnotu času) strávený v těle funkce kromě času stráveného při volání funkce a funkce s názvem. Tato data můžou pomoct vyhodnotit, jestli nezpůsobuje výkonu samotné funkce.

![Diagnostické nástroje volající/volaný "motýlkový" zobrazení](../profiling/media/prof-tour-cpu-usage-caller-callee.png "diagnostické nástroje volající/volaný zobrazení")

## <a name="analyze-memory-usage"></a>Analýza využití paměti

**Diagnostické nástroje** okna také umožňuje vyhodnotit využití paměti v aplikaci. Například můžete si prohlédnout počtu a velikosti objektů na haldě. Podrobnější pokyny pro analýzu paměti najdete v článku [analýza využití paměti](../profiling/memory-usage.md).

Analýza využití paměti, budete muset trvat aspoň jeden snímek paměti během ladění. Často je nejlepší způsob, jak analyzovat paměti se dvěma snímky první těsně před paměti podezřelý problém a druhý snímek bezprostředně za podezřelý paměti problému dochází. Pak můžete zobrazit rozdíly ve dvou snímků a zobrazit, co přesně se změnilo.

![Pořízení snímku v okně diagnostické nástroje](../profiling/media/prof-tour-take-snapshots.gif "snímky trvat diagnostické nástroje")

Když vyberete jeden z odkazů šipku, budete mít rozdílové zobrazení haldy (červená šipka nahoru ![zvýšit využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "zvýšit využití paměti") ukazuje (vlevo) rostoucí počet objektů nebo zvýšení kapacity Velikost haldy (vpravo)). Pokud kliknete na odkaz vpravo, získáte haldy rozdílové zobrazení seřazené podle objekty, které se zvýšila maximální velikost haldy. To může pomoct identifikovat problémy s pamětí. Například na následující ilustraci bajty používané `ClassHandlersStore` objekty zvýšila 3,492 bajtů druhý snímek.

![Diagnostické nástroje v haldě rozdílové zobrazení](../profiling/media/prof-tour-mem-usage-diff-heap.png "diagnostické nástroje haldy rozdílové zobrazení")

Pokud místo toho klikněte na odkaz na levé straně v **využití paměti** zobrazení, zobrazení haldy je uspořádaný podle počet objektů; se v horní části zobrazí objekty určitého typu, která zvýšil největší číslo (seřazené podle **počet Diff** sloupec).

## <a name="examine-performance-events"></a>Zkoumat události související s výkonem

**Události** zobrazení v okně diagnostické nástroje se zobrazí jednotlivé události, ke kterým dochází při ladění, jako je například nastavení zarážky nebo operaci krokování kódu. Můžete zkontrolovat informace, jako je doba trvání události (měřená od kdy naposledy pozastavila ladicího programu, nebo při spuštění aplikace). Pokud můžete krokovat kód (F10, F11), například **události** Zobrazí dobu trvání modulu runtime aplikace z předchozího kroku operace pro stávající krok.

![Zobrazit události diagnostických nástrojů](../profiling/media/prof-tour-events.png "zobrazení události diagnostických nástrojů")

 > [!NOTE]
 > Pokud máte Visual Studio Enterprise, můžete také zobrazit [události IntelliTrace](../debugger/intellitrace.md) na této kartě.

Stejné události se také zobrazí v editoru kódu, který se zobrazí jako tipy pro výkon.

![Profilace tipy pro výkon Tour](../profiling/media/prof-tour-perf-tips.png "profilace Tour tipy pro výkon")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Zkoumat události uživatelského rozhraní výkon a usnadnění přístupu (UPW)

V aplikacích pro UWP můžete povolit **Analýza uživatelského prostředí** v **diagnostické nástroje** okna. Nástroj vyhledá běžné problémy výkonu nebo dostupnosti a zobrazí je v **události** zobrazení při ladění. Popisy událostí poskytují informace, které mohou přispět k vyřešení problémů.

![Zobrazit události analýzy uživatelského rozhraní v okně diagnostické nástroje](../profiling/media/prof-tour-ui-analysis.png "diagnostické nástroje události analýzy uživatelského rozhraní pro zobrazení")

## <a name="post_mortem"></a> Sestavení pro vydání profilu bez ladicího programu

Profilace nástrojů jako využití CPU a využití paměti je možné pomocí ladicího programu (najdete v dřívějších částech), nebo ji můžete spustit profilování nástroje následné pomocí Profiler výkonu, která je určená k zajištění analýzy pro **vydání** sestavení . V Profiler výkonu můžete shromažďovat diagnostické informace, když aplikace spuštěna a pak zkontrolujte shromážděných informací, jakmile je aplikace pozastavená. Další informace o těchto rozdílných přístupů najdete v tématu [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

![Profiler výkonu](../profiling/media/prof-tour-performance-profiler.png "Profiler výkonu")

Otevřít Profiler výkonu výběrem **ladění** > **Profiler výkonu**.

V okně vám umožní vybrat více nástrojů pro profilaci v některých scénářích. Nástroje, jako je využití procesoru může poskytovat doplňující data, která mohou používat ke v analýze.

## <a name="analyze-resource-consumption-xaml"></a>Analýza spotřeby prostředků (XAML)

V aplikacích XAML, například WPF aplikace klasické pracovní plochy Windows a aplikací pro UWP můžete analyzovat využití prostředků pomocí nástroje časová osa aplikace. Můžete třeba analyzovat dobu stráví přípravou snímků uživatelského rozhraní (rozložení a vykreslení), zpracování síťových a diskových požadavků aplikace a ve scénářích, jako je spuštění aplikace, stránek zatížení a změna velikosti okna. Chcete-li použít nástroj, zvolte **časová osa aplikace** v Profiler výkonu a klikněte na tlačítko **Start**. Ve vaší aplikaci projít scénář s problémem spotřeby prostředků podezřelého softwaru a klikněte na tlačítko **zastavit shromažďování** generování sestav.

Nedostatek framerates v **vizuální propustnost** graf může odpovídat vizuální problémy, které se zobrazí při spuštění aplikace. Podobně vysoké čísla ve **využití vlákna UI** graf může také odpovídají problémů s rychlostí odezvy uživatelského rozhraní. V sestavě můžete vybrat časové období se problému s výkonem podezřelého softwaru a pak zkontrolujte podrobné aktivity vlákno uživatelského rozhraní v podrobném zobrazení časové osy (dolní podokno).

![Profilace nástroj časová osa aplikace](../profiling/media/prof-tour-application-timeline.gif "časová osa aplikace profilace prohlídku")

V podrobném zobrazení časové osy najdete informace, jako je typ činnosti (nebo zahrnutých prvek uživatelského rozhraní) spolu s doba trvání aktivity. Například v ukázce **rozložení** události pro ovládací prvek mřížky trvá 57.53 ms.

Další informace najdete v tématu [časová osa aplikace](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analýza využití GPU (Direct3D)

V aplikacích rozhraní Direct3D (Direct3D součásti musí být v jazyce C++) můžete prozkoumat aktivity na GPU a analyzovat problémy s výkonem. Další informace najdete v tématu [využití GPU](../debugger/gpu-usage.md). Chcete-li použít nástroj, zvolte **využití GPU** v Profiler výkonu a klikněte na tlačítko **Start**. Ve vaší aplikaci, projděte si scénáře, který vás zajímá profilace a klikněte na tlačítko **zastavit shromažďování** do generování sestavy.

Když vyberete časové období na grafy a zvolte **podrobnosti**, podrobné zobrazení se zobrazí ve spodní části podokna. V podrobném zobrazení můžete zkontrolovat, kolik aktivit se děje každou CPU a GPU. Vyberte události v podokně nejnižší získat automaticky otevíraná okna na časové ose. Vyberte například **k dispozici** událost, abyste viděli **k dispozici** volání automaticky otevíraná okna. (Světle šedá svislé čáry impulsu VSync lze použít jako referenci pochopit, jestli některé **k dispozici** volání vynechalo impulsu Vsync. Musí obsahovat jeden **k dispozici** volání mezi každé dvě Vsyncs mohl aplikaci neustále narazila na 60 snímků za Sekundu.)

![Profilace nástroj využití GPU](../profiling/media/prof-tour-gpu-usage.png "Diag využití GPU")

V grafech můžete také použít k určení, zda jsou závislá na procesoru, nebo GPU vázán problémových míst výkonu.

## <a name="analyze-performance-javascript-uwp"></a>Analýza výkonu (UPW v JavaScriptu)

Pro aplikace pro UPW můžete použít nástroje paměti jazyka JavaScript a HTML rychlosti odezvy uživatelského rozhraní.

Nástroj paměti jazyka JavaScript je podobný nástroj využití paměti, která je k dispozici pro další typy aplikací. Tento nástroj můžete použít k pochopení způsobu využívání paměti a nevracení paměti v aplikaci najít. Další podrobnosti o tomto nástroji naleznete v tématu [paměti jazyka JavaScript](../profiling/javascript-memory.md).

![Nástroje pro profilaci paměti jazyka JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Diagnostikovat odezvu uživatelského rozhraní, pomalé načítání času a v aplikacích pro UPW, pomalé aktualizace sady visual použijte nástroj rychlost odezvy UI HTML. Využití je podobný nástroj časová osa aplikace pro další typy aplikací. Další informace najdete v tématu [rychlost odezvy HTML UI](../profiling/html-ui-responsiveness.md).

![Profilace nástroj rychlost odezvy UI HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>Analýza využití sítě (UPW)

V aplikacích pro UPW, můžete analyzovat pomocí provádí síťové operace `Windows.Web.Http` rozhraní API. Tento nástroj může pomoct vyřešit problémy, jako jsou problémy přístupu a ověřování, nesprávné použití mezipaměti a špatné zobrazení a stáhnout výkonu. Chcete-li použít nástroj, zvolte **sítě** v Profiler výkonu a klikněte na tlačítko **Start**. Ve vaší aplikaci, projděte si scénáře, který používá `Windows.Web.Http`a klikněte na tlačítko **zastavit shromažďování** generování sestav.

![Síť používání nástrojů pro profilaci](../profiling/media/prof-tour-network-usage.png "Diag využití sítě")

Vyberte operaci v souhrnné zobrazení zobrazte další podrobnosti.

![Podrobné informace o nástroji pro využití sítě](../profiling/media/prof-tour-network-usage-details.png "Diag podrobnosti o využití sítě")

Další informace najdete v tématu [využití sítě](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analýza výkonu (starší verze nástroje)

Pokud potřebujete funkce, jako je instrumentace, které se aktuálně nenachází v nástroje využití CPU nebo využití paměti a používáte desktop nebo aplikace v ASP.NET, můžete použít prohlížeč výkonu pro profilování. (Není podporováno v aplikacích pro UPW). Další informace najdete v tématu [prohlížeč výkonu](../profiling/performance-explorer.md).

![Nástroj Průzkumník výkonu](../profiling/media/prof-tour-performance-explorer.png "prohlížeč výkonu")

## <a name="which-tool-should-i-use"></a>Jaké nástroje můžu použít?  

Tady je tabulka, která obsahuje seznam různých nástrojů, které nabízí Visual Studio a různých typech projektů je můžete využít s:
  
|Nástroje výkonu|Plocha Windows|UWP|ASP.NET/ASP.NET Core| 
|----------------------|---------------------|-------------|-------------|  
|[Využití procesoru](../profiling/cpu-usage.md)|Ano|Ano|Ano|
|[Využití paměti](../profiling/memory-usage.md)|Ano|Ano|Ano| 
|[Využití GPU](../debugger/gpu-usage.md)|Ano|Ano|Ne| 
|[Časová osa aplikace](../profiling/application-timeline.md)|Ano|Ano|Ne|
|[Tipy pro výkon](../profiling/perftips.md)|Ano|Ano pro XAML, ne pro kód HTML|Ano|
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ano|Ne|Ano|
|[IntelliTrace](../debugger/intellitrace.md)|.NET se sadou Visual Studio Enterprise pouze|.NET se sadou Visual Studio Enterprise pouze|.NET se sadou Visual Studio Enterprise pouze|
|[Využití sítě](../profiling/network-usage.md)|Ne|Ano|Ne|
|[Rychlost odezvy uživatelského rozhraní HTML](../profiling/html-ui-responsiveness.md)|Ne|Ano pro kód HTML, ne pro XAML|Ne| 
|[Paměť JavaScriptu](../profiling/javascript-memory.md)|Ne|Ano pro kód HTML, ne pro XAML|Ne|

## <a name="see-also"></a>Viz také:  
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
