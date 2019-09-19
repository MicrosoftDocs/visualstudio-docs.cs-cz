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
ms.openlocfilehash: f5dd3b1dc758a9b4f7634d4b6e73ab294289d6cd
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128292"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Měřit výkon aplikace díky analýze využití procesoru

Nástroje pro profilaci v sadě Visual Studio můžete použít k analýze problémů s výkonem aplikace. V tomto postupu si ukážeme, jak používat kartu **Využití procesoru** v diagnostických nástrojích k získání dat o výkonu vaší aplikace.

Když se ladicí program pozastaví, shromáždí nástroj **Využití procesoru** informace o funkcích spuštěných ve vaší aplikaci. Nástroj zobrazí seznam funkcí, které pracovaly, a nabídce graf s časovou osou, který můžete použít k podrobnému řešení konkrétních úseků vzorkovací relace.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud potřebná data nezískáte nástrojem **Využití procesoru**, použijte [jiné nástroje pro profilaci](../profiling/profiling-feature-tour.md), které nabízejí různé druhy užitečných informací. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat.

> [!Important]
> Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

V tomto článku probereme analýza využití procesoru v normální ladicí pracovní postup. Využití procesoru také můžete analyzovat bez připojeného ladicího programu nebo se můžete zaměřit na spuštěnou aplikaci. Další informace najdete v tématu věnovaném [shromažďování profilačních dat bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v článku o [spuštění nástrojů pro profilaci s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Můžete použít profilovací nástroje bez ladicího programu s Windows 7 a novější. Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno).

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Shromažďovat data o využití procesoru
> * Analyzovat data o využití procesoru

## <a name="step-1-collect-profiling-data"></a>Krok 1: Shromažďování dat profilace

1. Otevřete projekt, který chcete v sadě Visual Studio ladit, a nastavte v aplikaci zarážku do bodu, kde chcete prověřit využití procesoru.

2. Druhou zarážku nastavte na konec funkce nebo oblasti kódu, kterou chcete analyzovat.

    > [!TIP]
    > Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

4. Na panelu nástrojů v nastavení **Vybrat nástroje** můžete vybrat, jestli chcete zobrazit [Využití procesoru](../profiling/Memory-Usage.md), **Využití paměti** nebo obojí. Pokud používáte Visual Studio Enterprise, můžete také povolit nebo zakázat nástroje IntelliTrace v **nástroje** > **možnosti** > **IntelliTrace**.

     ![Zobrazení diagnostických nástrojů](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     Zaměříme se hlavně na využití procesoru. Zkontrolujte, že je zapnuté **Využití procesoru** (je zapnuté automaticky).

5. Klikněte na tlačítko **ladění** > **spustit ladění** (nebo **Start** na panelu nástrojů nebo **F5**).

     Jakmile se aplikace načte, zobrazí se souhrnný přehled diagnostických nástrojů. Pokud potřebujete okno otevřít, klikněte na tlačítko **ladit** > **Windows** > **show diagnostické nástroje**.

     ![Karta Souhrn v diagnostických nástrojích](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Další informace o událostech najdete v tématu [vyhledávání a filtrování na kartě události okna diagnostické nástroje](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Spusťte scénář, který se zastaví u první zarážky.

7. Jakmile se ladicí program pozastaví, zapněte shromažďování dat o využití procesoru a pak otevřete kartu **Využití procesoru**.

     ![Diagnostické nástroje povolit profilaci procesoru](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     Když zvolíte **Zaznamenat profil CPU**, Visual Studio začne nahrávat funkce a zjistí dobu potřebnou k jejich provedení. Shromážděná data můžete zobrazit, jen když se aplikace zastaví na zarážce.

8. Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     ![Příprava vláken v diagnostických nástrojích](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Pokud chcete vybrat konkrétnější oblast kódu k analýze, vyberte oblast v časové ose procesoru (musí se jednat o oblast, která zobrazuje data profilace).

     ![Výběr časového úseku v diagnostických nástrojích](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analyzovat data o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

    ![Seznam funkcí v diagnostických nástrojích na kartě Využití procesoru](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklikejte na některou funkci aplikace, která pracuje nejvíce.

    Když na ni poklikáte, otevře se v levém podokně zobrazení **Volající/volaný**.

    ![Zobrazení Volající/volaný v diagnostických nástrojích](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví i v poli **Aktuální funkce** (v tomto příkladu je to GetNumber). Funkce, která se nazývá aktuální funkce, je zobrazena vlevo pod položkou **volání funkce**a všechny funkce, které jsou volány aktuální funkcí, jsou zobrazeny v poli **nazvané funkce** na pravé straně. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.
    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (V tomto příkladu bylo vyčerpáno 2367 z 2389 MS v těle funkce a zbylé 22 MS bylo vyčerpáno v externím kódu, který tato funkce volá).

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

3. Chcete-li zobrazit zobrazení vyšší úrovně znázorňující pořadí, ve kterém jsou funkce volány, v rozevíracím seznamu v horní části podokna vyberte možnost **strom volání** .

    Každé číslo na následujícím obrázku odpovídá některému kroku v postupu.

    ::: moniker range=">=vs-2019"
    ![Strom volání v diagnostických nástrojích](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Strom volání v diagnostických nástrojích](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |||
    |-|-|
    |![1. krok](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Nejvyšší uzel ve stromech volání Využití procesoru je fiktivní.|
    |![2. krok](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Ve většině aplikací, ve kterých zakážete možnost [Zobrazit externí kód](#view-external-code), je v druhé úrovni uzel **[Externí kód]** , který obsahuje systémový kód a kód architektury, který spouští a zastavuje aplikaci, vykresluje uživatelské rozhraní, řídí plánování podprocesů a na nejnižší úrovni zajišťuje pro aplikaci další služby.|
    |![3. krok](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|
    |![4. krok](../profiling/media/ProcGuid_4.png "ProcGuid_4")|Podřízené uzly metody obsahují jenom data pro volání nadřízené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]** .|

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

## <a name="view-external-code"></a>Zobrazit externí kód

Externím kódem se rozumí funkce systémových komponent a komponent architektury, které jsou spouštěné vámi napsaným kódem. Externí kód zahrnuje funkce, které spouštějí a zastavují aplikaci, vykreslují uživatelské rozhraní, řídí dělení na podprocesy a na nejnižší úrovni zajišťuje pro aplikaci další služby. Externí kód vás většinou nebude zajímat, a proto nástroj Využití procesoru shromažďuje externí funkce metody uživatele do jednoho uzlu **[Externí kód]** .

Pokud se chcete podívat na cesty volání externího kódu, vyberte v seznamu **filtru zobrazení** možnost **Zobrazit externí kód** a pak zvolte **Použít**.

![Filtr zobrazení s vybranou možností Zobrazit externí kód](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

Myslete na to, že řetězy volání externího kódu je většinou hluboko vnořené, takže šířka sloupce Název funkce může na většině počítačových monitorů – s výjimkou těch největších – přesáhnout šířku zobrazení. V takovém případě se názvy funkcí zobrazují jako **[...]** .

K nalezení hledaného uzlu použijte vyhledávací pole a pak použijte k zobrazení dat vodorovný posuvník.

> [!TIP]
> Pokud profilujete externí kód, který volá funkce Windows, by měl Ujistěte se, že máte nejnovější. *pdb* soubory. Bez těchto souborů se v zobrazeních sestav zobrazí seznam funkcí Windows, jejichž názvy jsou nesrozumitelné a obtížně pochopitelné. Další informace o tom, abyste měli jistotu, že máte soubory, které potřebujete, najdete v části [zadání symbolu (.pdb) a zdrojových souborů v ladicím programu](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili shromažďovat data o využití procesoru a analyzovat je. Pokud jste již dokončili [nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md), možná budete chtít získat rychlý přehled postupu k analýze využití paměti v aplikacích.

> [!div class="nextstepaction"]
> [Využití paměti profilu v sadě Visual Studio](../profiling/memory-usage.md)
