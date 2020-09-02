---
title: Měření využití procesoru v aplikacích
description: V ladicím programu jsou integrované diagnostické nástroje, které můžete použít k analýze problémů s výkonem procesoru.
ms.custom: seodec18
ms.date: 04/03/2019
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3a7c5eb8aa489da9ced0803e0f83855734825ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537368"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Měření výkonu aplikace analýzou využití CPU

Nástroje pro profilaci v sadě Visual Studio můžete použít k analýze problémů s výkonem aplikace. Tento článek ukazuje, jak použít kartu **využití procesoru** diagnostických nástrojů k získání údajů o výkonu pro vaši aplikaci.

Když se ladicí program pozastaví, shromáždí nástroj **Využití procesoru** informace o funkcích spuštěných ve vaší aplikaci. Nástroj zobrazí seznam funkcí, které pracovaly, a nabídce graf s časovou osou, který můžete použít k podrobnému řešení konkrétních úseků vzorkovací relace.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud potřebná data nezískáte nástrojem **Využití procesoru**, použijte [jiné nástroje pro profilaci](../profiling/profiling-feature-tour.md), které nabízejí různé druhy užitečných informací. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat.

> [!Important]
> Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

V tomto článku probereme analýzu využití CPU v normálním pracovním postupu ladění. Můžete také analyzovat využití procesoru bez připojeného ladicího programu nebo zacílení na spuštěnou aplikaci. Další informace najdete v tématu [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Můžete také použít jiný nástroj pro profilaci, [tipy pro výkon](../profiling/perftips.md), ke krokování kódu a určit, jak dlouho trvá konkrétní funkce nebo bloky kódu, které mají být dokončeny.

Nástroje pro profilaci bez ladicího programu můžete používat se systémem Windows 7 nebo novějším. Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Shromažďovat data o využití procesoru
> * Analyzovat data o využití procesoru

## <a name="step-1-collect-profiling-data"></a>1. krok: Shromáždění profilačních dat

1. Otevřete projekt, který chcete v sadě Visual Studio ladit, a nastavte v aplikaci zarážku do bodu, kde chcete prověřit využití procesoru.

2. Druhou zarážku nastavte na konec funkce nebo oblasti kódu, kterou chcete analyzovat.

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Chcete-li okno znovu zobrazit, klikněte na tlačítko **ladit**  >  **Windows**  >  **show diagnostické nástroje**.

4. Na panelu nástrojů v nastavení **Vybrat nástroje** můžete vybrat, jestli chcete zobrazit [Využití procesoru](../profiling/Memory-Usage.md), **Využití paměti** nebo obojí. Pokud používáte Visual Studio Enterprise, můžete taky povolit nebo zakázat IntelliTrace v **nabídce**  >  **Možnosti**nástrojů  >  **IntelliTrace**.

     ![Zobrazit diagnostické nástroje](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Zaměříme se hlavně na využití procesoru. Zkontrolujte, že je zapnuté **Využití procesoru** (je zapnuté automaticky).

5. Klikněte na **ladění**  >  **Spustit ladění** (nebo **Spusťte** na panelu nástrojů nebo **F5**).

     Jakmile se aplikace načte, zobrazí se souhrnný přehled diagnostických nástrojů. Pokud potřebujete okno otevřít, klikněte na tlačítko **ladit**  >  **Windows**  >  **show diagnostické nástroje**.

     ![Karta souhrn nástrojů pro diagnostiku](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Další informace o událostech naleznete v tématu [hledání a filtrování karty události v okně diagnostické nástroje](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Spusťte scénář, který se zastaví u první zarážky.

7. Jakmile se ladicí program pozastaví, zapněte shromažďování dat o využití procesoru a pak otevřete kartu **Využití procesoru**.

     ![Diagnostické nástroje povolují profilaci procesoru](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     Když zvolíte **Zaznamenat profil CPU**, Visual Studio začne nahrávat funkce a zjistí dobu potřebnou k jejich provedení. Shromážděná data můžete zobrazit, jen když se aplikace zastaví na zarážce.

8. Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     ![Diagnostické nástroje připravují vlákna](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     ![Karta využití CPU pro diagnostické nástroje](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Pokud chcete vybrat konkrétnější oblast kódu k analýze, vyberte oblast v časové ose procesoru (musí se jednat o oblast, která zobrazuje data profilace).

     ![Diagnostické nástroje, které vyberou časový segment](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     Teď můžete začít analyzovat data.

     > [!TIP]
     >  Při pokusu o identifikaci problémů s výkonem Vezměte v úvahu více měření. Výkon se přirozeně liší od spuštění po spuštění a cesty kódu obvykle běží pomaleji z důvodu jednorázové práce při inicializaci, jako je načítání knihoven DLL, metod kompilace JIT a inicializace mezipamětí. Díky většímu množství měření získáte lepší představu o rozsahu a mediánu zobrazené metriky, které vám umožní porovnat první čas oproti ustálenému stavu v oblasti kódu.

## <a name="step-2-analyze-cpu-usage-data"></a> 2. krok: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

    ![Seznam funkcí využití CPU pro diagnostické nástroje](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklikejte na některou funkci aplikace, která pracuje nejvíce.

    Když na ni poklikáte, otevře se v levém podokně zobrazení **Volající/volaný**.

    ![Zobrazení volajícího volaných nástrojů pro diagnostiku](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví i v poli **Aktuální funkce** (v tomto příkladu je to GetNumber). Funkce, která se nazývá aktuální funkce, je zobrazena vlevo pod položkou **volání funkce**a všechny funkce, které jsou volány aktuální funkcí, jsou zobrazeny v poli **nazvané funkce** na pravé straně. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.
    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (V tomto příkladu bylo vyčerpáno 2367 z 2389 MS v těle funkce a zbylé 22 MS bylo vyčerpáno v externím kódu, který tato funkce volá).

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

3. Chcete-li zobrazit zobrazení vyšší úrovně znázorňující pořadí, ve kterém jsou funkce volány, v rozevíracím seznamu v horní části podokna vyberte možnost **strom volání** .

    Každé číslo na následujícím obrázku odpovídá některému kroku v postupu.

    ::: moniker range=">=vs-2019"
    ![Strom volání diagnostických nástrojů](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Strom volání diagnostických nástrojů](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Image|Popis|
    |-|-|
    |![Krok 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Nejvyšší uzel ve stromech volání Využití procesoru je fiktivní.|
    |![Krok 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Ve většině aplikací, ve kterých zakážete možnost [Zobrazit externí kód](#view-external-code), je v druhé úrovni uzel **[Externí kód]**, který obsahuje systémový kód a kód architektury, který spouští a zastavuje aplikaci, vykresluje uživatelské rozhraní, řídí plánování podprocesů a na nejnižší úrovni zajišťuje pro aplikaci další služby.|
    |![Krok 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|
    |![Krok 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Podřízené uzly metody obsahují jenom data pro volání nadřízené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]**.|

    Další informace k hodnotám ve sloupcích:

    - **Celkový čas procesoru**: Kolik práce vykonala funkce spolu se všemi dalšími funkcemi, které volala. Vysoké hodnoty znamenají, že tyto funkce patří k těm nejnáročnějším.

    - **Vlastní čas procesoru**: Kolik práce vykonal kód v těle funkce po odečtení práce vykonané volanými funkcemi. Vysoké hodnoty **vlastního času procesoru** pravděpodobně odpovídají kritickému místu ve funkci.

    - **Moduly**: Název modulu, který funkci obsahuje, nebo počet modulů obsahujících funkce v uzlu [Externí kód].

    ::: moniker range=">=vs-2019"
    Chcete-li zobrazit volání funkce, která používají nejvyšší procento CPU ve stromovém zobrazení volání, klikněte na možnost **Rozbalit cestu k pochodu**.

    ![Horká cesta nástrojů pro diagnostiku](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Pokud se ve stromu volání zobrazí kód označený jako "porušený" kód nebo "Projděte" zásobník ", znamená to, že události trasování událostí pro Windows (ETW) byly pravděpodobně vyřazeny. Zkuste shromáždit stejné trasování podruhé, aby se problém vyřešil.

## <a name="view-external-code"></a>Zobrazení externího kódu

Externím kódem se rozumí funkce systémových komponent a komponent architektury, které jsou spouštěné vámi napsaným kódem. Externí kód zahrnuje funkce, které spouštějí a zastavují aplikaci, vykreslují uživatelské rozhraní, řídí dělení na podprocesy a na nejnižší úrovni zajišťuje pro aplikaci další služby. Externí kód vás většinou nebude zajímat, a proto nástroj Využití procesoru shromažďuje externí funkce metody uživatele do jednoho uzlu **[Externí kód]**.

Pokud se chcete podívat na cesty volání externího kódu, vyberte v seznamu **filtru zobrazení** možnost **Zobrazit externí kód** a pak zvolte **Použít**.

![Zvolte možnost zobrazení filtru a pak zobrazit externí kód.](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

Myslete na to, že řetězy volání externího kódu je většinou hluboko vnořené, takže šířka sloupce Název funkce může na většině počítačových monitorů – s výjimkou těch největších – přesáhnout šířku zobrazení. V takovém případě se názvy funkcí zobrazují jako **[...]**.

K nalezení hledaného uzlu použijte vyhledávací pole a pak použijte k zobrazení dat vodorovný posuvník.

> [!TIP]
> Pokud profilovat externí kód, který volá funkce systému Windows, měli byste se ujistit, že máte aktuální. soubory *PDB* . Bez těchto souborů se v zobrazeních sestav zobrazí seznam funkcí Windows, jejichž názvy jsou nesrozumitelné a obtížně pochopitelné. Další informace o tom, jak se ujistit, že máte soubory, které potřebujete, najdete v tématu [určení symbolu (. pdb) a zdrojových souborů v ladicím programu](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili shromažďovat data o využití procesoru a analyzovat je. Pokud jste už dokončili [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md), možná budete chtít rychle zobrazit, jak analyzovat využití paměti ve vašich aplikacích.

> [!div class="nextstepaction"]
> [Využití paměti profilu v sadě Visual Studio](../profiling/memory-usage.md)
