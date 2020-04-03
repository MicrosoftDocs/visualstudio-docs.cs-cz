---
title: Analýza využití procesoru | Dokumenty společnosti Microsoft
ms.custom: seodec18
ms.date: 04/02/2020
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88272af1733dbbaf7f46743388a8ecb6522e9f1a
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638835"
---
# <a name="analyze-cpu-usage"></a>Analýza využití procesoru

Dobrým způsobem, jak začít vyšetřovat problémy s výkonem ve vaší aplikaci, je pochopit jeho využití procesoru. Nástroj **výkon využití procesoru** zobrazuje čas a procento procesoru strávené prováděním kódu v aplikacích C++, C#/Visual Basic a JavaScript.

Nástroj **využití procesoru** lze spustit v otevřeném projektu Sady Visual Studio, v nainstalované aplikaci Microsoft Store nebo připojené ke spuštěné aplikaci nebo procesu. Další informace naleznete [v tématu Spuštění nástrojů profilování s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Nástroj využití **procesoru** můžete spustit s laděním nebo bez něj. V ladicím programu můžete zapínat a vypínat profilování procesoru a zobrazit rozpis využití procesoru podle funkce. Výsledky využití procesoru můžete zobrazit při pozastavení provádění, například v zarážky.

Následující pokyny ukazují, jak používat nástroj **využití procesoru** bez ladicího programu pomocí nástroje Visual Studio **Performance Profiler**. Příklady používají vydání sestavení na místním počítači. Vydání sestavení poskytují nejlepší přehled o skutečném výkonu aplikace. Chcete-li analyzovat využití procesoru pomocí sestavení ladění, [přečtěte si příručku pro začátečníky k profilování výkonu](../profiling/beginners-guide-to-performance-profiling.md).

Obvykle místní počítač nejlépe replikuje nainstalované spuštění aplikace. Pro aplikace pro Windows Phone poskytuje shromažďování dat přímo ze zařízení nejpřesnější data. Chcete-li shromažďovat data ze vzdáleného zařízení, spusťte aplikaci přímo v zařízení, nikoli přes připojení ke vzdálené ploše.

>[!NOTE]
>Systém Windows 7 nebo novější je nutné použít [nástroj Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="collect-cpu-usage-data"></a>Shromažďovat data o využití procesoru

1. V projektu Sady Visual Studio nastavte konfiguraci řešení na **Release** a jako cíl nasazení vyberte **místní debugger systému Windows** (nebo místní **počítač).**

    ![Vybrat uvolnění a místní počítač](../profiling/media/cpuuse_selectreleaselocalmachine.png "Vybrat uvolnění a místní počítač")

1. Vyberte **možnost Ladění** > **profileru výkonu**.

1. V části **Dostupné nástroje**vyberte **Využití procesoru**a pak vyberte **Start**.

    ![Vybrat využití procesoru](../profiling/media/cpuuse_lib_choosecpuusage.png "Vybrat využití procesoru")

4. Po spuštění aplikace začne diagnostická relace a zobrazí data o využití procesoru. Po dokončení shromažďování dat vyberte **Zastavit shromažďování**.

   ![Zastavit shromažďování dat o využití procesoru](../profiling/media/cpu_use_wt_stopcollection.png "Zastavit shromažďování dat o využití procesoru")

   Nástroj využití procesoru analyzuje data a zobrazí sestavu.

   ![Sestava využití procesoru](../profiling/media/cpu_use_wt_report.png "Sestava využití procesoru")

## <a name="analyze-the-cpu-usage-report"></a>Analýza sestavy využití procesoru

Diagnostická sestava je seřazena podle **celkového procesoru**od nejvyššího k nejnižšímu. Změňte pořadí řazení nebo sloupec řazení výběrem záhlaví sloupců. Rozevírací **seznam Filtr** slouží k výběru nebo zrušení výběru vláken, které chcete zobrazit, a pomocí pole **Hledat** k vyhledání určitého vlákna nebo uzlu.

::: moniker range=">=vs-2019"
Počínaje Visual Studio 2019, můžete kliknout **rozbalit aktivní cestu** a **zobrazit horké cesty** tlačítka zobrazíte volání funkce, které používají nejvyšší procento procesoru v zobrazení stromu volání.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a>Sloupce dat o využití procesoru

|||
|-|-|
|**Celkový procesor [jednotka, %]**|![Rovnice celkových % dat](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Milisekundy a procento procesoru používané voláním funkce a funkce mivolavky volaný funkcí ve vybraném časovém rozsahu. To se liší od grafu časové osy **využití procesoru,** který porovnává celkovou aktivitu procesoru v časovém rozsahu s celkovým dostupným procesorem.|
|**Vlastní procesor [jednotka, %]**|![Vlastní % rovnice](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Milisekundy a procento procesoru používané voláním funkce ve vybraném časovém rozsahu, s výjimkou funkcí volaných funkcí.|
|**Modul**|Název modulu obsahujícího funkci.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a>Strom volání využití procesoru

Chcete-li zobrazit strom volání, vyberte nadřazený uzel v sestavě. Stránka **Využití procesoru** se otevře v zobrazení **Volající/Volaný.** V rozevíracím přehledu **Aktuální zobrazení** vyberte **Strom volání**.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a>Struktura stromu volání

::: moniker range=">=vs-2019"
![Struktura stromu volání](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Struktura stromu volání")
::: moniker-end
::: moniker range="vs-2017"
![Struktura stromu volání](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Struktura stromu volání")
::: moniker-end

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Uzel nejvyšší úrovně ve stromech volání využití procesoru je pseudouzel.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Ve většině aplikací, když je zakázána možnost **Zobrazit externí kód,** uzel druhé úrovně je uzel **[Externí kód].** Uzel obsahuje systémový a framework kód, který spustí a zastaví aplikaci, nakreslí uživatelské rozhraní, řídí plánování vláken a poskytuje další služby nižší úrovně do aplikace.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Podřízené uzly metody mají data pouze pro volání nadřazené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]**.|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a>Externí kód

Systémové a rámcové funkce, které jsou spouštěny vaším kódem, se nazývají *externí kód*. Funkce externího kódu spustí a zastaví aplikaci, nakreslí uživatelské rozhraní, řídí podprocesy a poskytuje aplikaci další nízkoúrovňové služby. Ve většině případů vás nezajímá externí kód, takže strom volání využití procesoru shromažďuje externí funkce uživatelské metody do jednoho uzlu **[externí kód].**

Chcete-li zobrazit cesty volání externího kódu, na stránce hlavní diagnostické sestavy (pravé podokno) vyberte v rozevíracím souboru **Filtr** zobrazit **externí kód** a pak vyberte **Použít**. Zobrazení **Stromvolání** na stránce **Využití procesoru** pak rozbalí volání externího kódu. (Rozevírací **seznam Filtr** je k dispozici na hlavní diagnostické stránce, nikoli na podrobných zobrazeních.)

![Zobrazit externí kód](../profiling/media/cpu_use_wt_filterview.png "Zobrazit externí kód")

Mnoho řetězců volání externího kódu je hluboce vnořeno, takže šířka řetězu může překročit šířku zobrazení sloupce **Název funkce.** Názvy funkcí se pak zobrazí jako **...**.

![Vnořený externí kód ve stromu volání](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Vnořený externí kód ve stromu volání")

Chcete-li najít název funkce, kterou hledáte, použijte vyhledávací pole. Najeďte přes vybranou čáru nebo pomocí vodorovného posuvníku zobrazte data.

::: moniker range=">=vs-2019"
![Hledání vnořeného externího kódu](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "Hledání vnořeného externího kódu")
::: moniker-end
::: moniker range="vs-2017"
![Hledání vnořeného externího kódu](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Hledání vnořeného externího kódu")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>Asynchronní funkce ve stromu volání využití procesoru

 Když kompilátor narazí na asynchronní metodu, vytvoří skrytou třídu pro řízení spuštění metody. Koncepčně je třída stavový počítač. Třída má kompilátor generované funkce, které asynchronně volat původní metody a zpětná volání, plánovač a iterátory potřebné k jejich spuštění. Když nadřazená metoda volá původní metodu, kompilátor odebere metodu z kontextu spuštění nadřazeného a spustí metody skryté třídy v kontextu systémového a frameworkového kódu, který řídí spuštění aplikace. Asynchronní metody jsou často, ale ne vždy, spuštěny v jednom nebo více různých vláknech. Tento kód se zobrazí ve stromu volání **využití procesoru** jako podřízené uzel **[Externí kód]** bezprostředně pod horním uzlem stromu.

V následujícím příkladu jsou první dva uzly v rámci **[Externí kód]** metody generované kompilátorem třídy stavového počítače. Třetí uzel je volání původní metody.

![Asynchronní uzel](media/cpu_use_wt_getmaxnumberasync_selected.png "Asynchronní uzel")

Rozbalte generované metody a zobrazte tak, co se děje:

![Rozšířený asynchronní uzel](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Rozšířený asynchronní uzel")

- `MainPage::GetMaxNumberAsyncButton_Click`pouze spravuje seznam hodnot úkolů, vypočítá maximum výsledků a zobrazí výstup.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext`zobrazuje aktivitu potřebnou k naplánování a spuštění 48 úkolů, které zalomí volání . `GetNumberAsync`

- `MainPage::<GetNumberAsync>b__b`zobrazuje aktivitu úkolů, `GetNumber`které volají .
