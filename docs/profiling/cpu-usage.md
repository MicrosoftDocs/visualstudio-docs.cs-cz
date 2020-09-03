---
title: Analýza využití procesoru | Microsoft Docs
ms.custom: seodec18
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5ab97f3db8e5d44aa649455c313a5681ed93c8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543387"
---
# <a name="analyze-cpu-usage"></a>Analýza využití procesoru

Dobrým způsobem, jak začít prozkoumat problémy s výkonem ve vaší aplikaci, je pochopit využití CPU. Nástroj výkon **procesoru** zobrazuje čas procesoru a procento strávené prováděním kódu v aplikacích C++, C# webový Basic a JavaScriptu.

Nástroj **využití CPU** může běžet na otevřeném projektu sady Visual Studio, na nainstalované Microsoft Store aplikaci nebo připojeném ke spuštěné aplikaci nebo procesu. Další informace najdete v tématu [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Nástroj **využití CPU** můžete spustit s laděním nebo bez něj. V ladicím programu můžete profilaci procesoru zapnout a vypnout a zobrazit rozpis využití procesoru podle funkce. Můžete zobrazit výsledky využití procesoru při pozastavení provádění, například na zarážce.

Následující pokyny ukazují, jak používat nástroj **využití CPU** bez ladicího programu, pomocí **profileru výkonu**sady Visual Studio. V příkladech se používá sestavení pro vydání na místním počítači. Sestavení vydaných verzí poskytují nejlepší pohled na skutečný výkon aplikace. Analýza využití procesoru pomocí sestavení pro ladění najdete v tématu [Příručka pro začátečníky k profilaci výkonu](../profiling/beginners-guide-to-performance-profiling.md).

Obvykle místní počítač nejlépe replikuje nainstalovaná aplikace. V případě aplikací Windows Phone aplikace shromažďují data přímo ze zařízení a poskytují nejpřesnější data. Pokud chcete shromažďovat data ze vzdáleného zařízení, spusťte aplikaci přímo na zařízení, ne přes Připojení ke vzdálené ploše.

>[!NOTE]
>Pro použití [profileru výkonu](../profiling/profiling-feature-tour.md)se vyžaduje Windows 7 nebo novější.

## <a name="collect-cpu-usage-data"></a>Shromažďovat data o využití procesoru

1. V projektu sady Visual Studio nastavte možnost konfigurace řešení na **release** a jako cíl nasazení vyberte **místní ladicí program systému Windows** (nebo **místní počítač**).

    ![Vybrat vydanou verzi a místní počítač](../profiling/media/cpuuse_selectreleaselocalmachine.png "Vybrat vydanou verzi a místní počítač")

1. Vyberte **ladit**  >  **výkon profileru**.

1. V části **dostupné nástroje**vyberte **využití CPU**a pak vyberte **Spustit**.

    ![Vybrat využití CPU](../profiling/media/cpuuse_lib_choosecpuusage.png "Vybrat využití CPU")

4. Po spuštění aplikace se v relaci diagnostiky spustí a zobrazí data o využití procesoru. Až budete hotovi s shromažďováním dat, vyberte **Zastavit shromažďování**.

   ![Zastavit shromažďování dat využití procesoru](../profiling/media/cpu_use_wt_stopcollection.png "Zastavit shromažďování dat využití procesoru")

   Nástroj využití CPU analyzuje data a zobrazí sestavu.

   ![Sestava využití procesoru](../profiling/media/cpu_use_wt_report.png "Sestava využití procesoru")

## <a name="analyze-the-cpu-usage-report"></a>Analýza sestavy využití CPU

Diagnostická sestava je seřazená podle **celkového využití CPU**od nejvyšších po nejnižší. Výběrem záhlaví sloupců změňte pořadí řazení nebo sloupec řazení. Pomocí rozevíracího seznamu **Filtr** vyberte nebo zrušte výběr zobrazovaného vlákna a pomocí **vyhledávacího** pole vyhledejte konkrétní vlákno nebo uzel.

::: moniker range=">=vs-2019"
Počínaje verzí Visual Studio 2019 můžete kliknout na tlačítko **Rozbalit cestu k Hotu** a zobrazit kritickou **cestu** a zobrazit tak volání funkcí, která používají nejvyšší procento procesoru v zobrazení stromu volání.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> Sloupce dat využití procesoru

|Název|Popis|
|-|-|
|**Celkový čas procesoru [jednotka,%]**|![Total% data Equation – rovnice](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Hodnoty milisekund a CPU používané voláním funkce a funkce volané funkcí ve vybraném časovém rozsahu. To se liší od grafu časová osa **využití procesoru** , který porovnává celkovou dostupnou CPU v časovém rozsahu s celkovým DOSTUPNÝm procesorem.|
|**Samotný procesor [jednotka,%]**|![% Rovnice sebe](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Hodnoty milisekund a CPU využívané voláním funkce ve vybraném časovém rozsahu s výjimkou funkcí volaných funkcí.|
|**Modul**|Název modulu, který obsahuje funkci.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> Strom volání využití CPU

Chcete-li zobrazit strom volání, vyberte v sestavě nadřazený uzel. Stránka **využití CPU** se otevře v zobrazení **volající/volaný** . V rozevíracím seznamu **aktuální zobrazení** vyberte možnost **strom volání**.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Stromová struktura volání

::: moniker range=">=vs-2019"
![Stromová struktura volání](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Stromová struktura volání")
::: moniker-end
::: moniker range="vs-2017"
![Stromová struktura volání](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Stromová struktura volání")
::: moniker-end

|Image|Popis|
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Uzel nejvyšší úrovně ve stromech volání využití CPU je pseudo uzel.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Pokud je v aplikaci většina aplikací zakázaná možnost **Zobrazit externí kód** , je uzel druhé úrovně uzlem **[externí kód]** . Uzel obsahuje kód systému a rozhraní, který spustí a zastaví aplikaci, nakreslí uživatelské rozhraní, řídí plánování vláken a poskytuje aplikaci další služby nižší úrovně.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Podřízené uzly metody mají data pouze pro volání nadřazené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]**.|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Externí kód

Funkce systému a rozhraní, které jsou spouštěny vaším kódem, se nazývají *externí kód*. Funkce externího kódu spouštějí a zastavují aplikaci, nakreslí uživatelské rozhraní, řídí vlákna a poskytují do aplikace další služby nižší úrovně. Ve většině případů nebudete mít zájem o externí kód, takže strom volání využití CPU shromáždí externí funkce uživatelské metody do jednoho uzlu **[externí kód]** .

Chcete-li zobrazit cesty volání externího kódu, na hlavní stránce diagnostické sestavy (pravé podokno) vyberte možnost **Zobrazit externí kód** v rozevíracím seznamu **filtru** a pak vyberte **použít**. Zobrazení **stromové struktury volání** stránky **využití CPU** pak rozbalí volání externího kódu. (Rozevírací seznam **Filtr** je k dispozici na hlavní stránce diagnostiky, nikoli v podrobných zobrazeních.)

![Zobrazit externí kód](../profiling/media/cpu_use_wt_filterview.png "Zobrazit externí kód")

Mnoho řetězců volání externího kódu je hluboce vnořeno, takže Šířka řetězu může přesáhnout šířku zobrazení sloupce **název funkce** . Názvy funkcí se pak zobrazí jako **...**.

![Vnořený externí kód ve stromu volání](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Vnořený externí kód ve stromu volání")

Pokud chcete najít název funkce, kterou hledáte, použijte vyhledávací pole. Najeďte myší na vybraný řádek nebo k zobrazení dat použijte vodorovný posuvník.

::: moniker range=">=vs-2019"
![Hledání vnořeného externího kódu](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "Hledání vnořeného externího kódu")
::: moniker-end
::: moniker range="vs-2017"
![Hledání vnořeného externího kódu](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Hledání vnořeného externího kódu")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Asynchronní funkce ve stromu volání využití CPU

 Když kompilátor narazí na asynchronní metodu, vytvoří skrytou třídu pro řízení provádění metody. V koncepční úrovni je třída Stavový počítač. Třída obsahuje funkce generované kompilátorem, které asynchronně volají původní metody a zpětná volání, Scheduler a iterátory potřebné ke spuštění. Když nadřazená metoda volá původní metodu, kompilátor odebere metodu z kontextu spuštění nadřazeného objektu a spustí skryté třídy v kontextu systému a kódu rozhraní, který řídí provádění aplikace. Asynchronní metody jsou často, ale ne vždy, spouštěny v jednom nebo více různých vláknech. Tento kód se zobrazí ve stromu volání **využití CPU** jako podřízené objekty v uzlu **[External Code]** bezprostředně pod horním uzlem stromu.

V následujícím příkladu jsou první dva uzly v **[External Code]** metody generované kompilátorem třídy stavového stroje. Třetí uzel je volání původní metody.

![Asynchronní uzel](media/cpu_use_wt_getmaxnumberasync_selected.png "Asynchronní uzel")

Rozbalte vygenerované metody, aby se zobrazily informace o tom, co se prochází:

![Rozbalený asynchronní uzel](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Rozbalený asynchronní uzel")

- `MainPage::GetMaxNumberAsyncButton_Click` pouze spravuje seznam hodnot úkolů, vypočítá maximum výsledků a zobrazí výstup.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zobrazuje aktivitu nutnou k naplánování a spuštění úloh 48, které zabalí volání `GetNumberAsync` .

- `MainPage::<GetNumberAsync>b__b` zobrazuje aktivitu úkolů, které volají `GetNumber` .
