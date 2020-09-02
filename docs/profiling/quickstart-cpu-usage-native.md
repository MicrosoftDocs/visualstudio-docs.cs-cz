---
title: Analýza dat využití procesoru (C++)
description: Měření výkonu aplikace v jazyce C++ pomocí nástroje pro diagnostiku využití CPU
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 602a185b598410de47dc9d3c98ca2b0ae3c45633
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80412011"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Rychlý Start: Analýza dat využití procesoru v aplikaci Visual Studio (C++)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce. Tady se podíváme na nástroj a Identifikujte problémová místa výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud nástroj **využití procesoru** , který je zde popsaný, neposkytuje potřebná data, [ostatní nástroje pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které vám mohou být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat. [Tipy pro výkon](../profiling/perftips.md), další nástroj pro profilaci integrovaný v ladicím programu, vám také umožní procházet kód a určit, jak dlouho trvá konkrétní funkce nebo bloky kódu, které mají být dokončeny.

Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější. Ve Windows 7 a novějších verzích můžete použít nástroj pro následné povýšení, [Profiler výkonu](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

   V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual C++** a pak zvolte možnost **plocha systému Windows**. V prostředním podokně vyberte **Konzolová aplikace systému Windows**. Pak zadejte název projektu *Diagnostics_Get_Started_Native*.

   Pokud nevidíte šablonu projektu **Konzolová aplikace systému Windows** , vyberte odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Zvolte **desktopový vývoj s** využitím úlohy C++ a pak zvolte **Upravit**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Pokud okno Start není otevřeno, klikněte **na tlačítko** > **Start okna**.

   V okně Start vyberte možnost **vytvořit nový projekt**.

   V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Potom v seznamu jazyk vyberte **C++** a v seznamu platforma zvolte **Windows** .

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly** a klikněte na tlačítko **Další**.

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Pak v Instalační program pro Visual Studio zvolte **vývoj desktopových aplikací pomocí C++** .

   V okně **Konfigurovat nový projekt** zadejte nebo zadejte *Diagnostics_Get_Started_Native* do pole **název projektu** . Pak zvolte **vytvořit**.

   ::: moniker-end

   Visual Studio otevře nový projekt.

1. V *Diagnostics_Get_Started_Native*nahraďte následující kód

    ```c++
    int main()
    {
        return 0;
    }
    ```

    s tímto kódem (neodstraňujte `#include "stdafx.h"` ):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>

    //.cpp file code:

    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;

    int getNumber()
    {

        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();

        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here
        // to increase CPU usage
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }

    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;

        auto x = getNumber();
    }

    int main()
    {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

## <a name="step-1-collect-profiling-data"></a>1. krok: Shromáždění profilačních dat

1. Nejdřív v aplikaci nastavte zarážku na tomto řádku kódu ve `main` funkci:

    `for (int i = 0; i < 10; ++i) {`

    Nastavte zarážku kliknutím na hřbet nalevo od řádku kódu.

2. Dále nastavte druhou zarážku na pravou složenou závorku na konci `main` funkce:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Nastavení zarážek pro profilaci")

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. **Diagnostické nástroje** okno je již viditelné, pokud jste ho neaktivovali. Chcete-li okno znovu zobrazit, klikněte na tlačítko **ladit**  >  **Windows**  >  **show diagnostické nástroje**.

4. Klikněte na **ladění**  >  **Spustit ladění** (nebo **Spusťte** na panelu nástrojů nebo **F5**).

     Po dokončení načítání aplikace se zobrazí **souhrnné** zobrazení diagnostických nástrojů.

5. I když je ladicí program pozastaven, povolte shromažďování dat o využití procesoru výběrem možnosti **zaznamenat profil procesoru**a pak otevřete kartu **využití CPU** .

     ![Diagnostické nástroje povolují profilaci procesoru](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostické nástroje povolují profilaci procesoru")

     Když je povolené shromažďování dat, na tlačítku záznamu se zobrazí červené kolečko.

     Když vyberete možnost **zaznamenat profil procesoru**, Visual Studio zahájí zaznamenávání vašich funkcí a množství času, které je potřeba provést, a také graf časové osy, pomocí kterého se můžete soustředit na konkrétní segmenty relace vzorkování. Tato shromážděná data můžete zobrazit pouze v případě, že dojde k zastavení aplikace na zarážce.

6. Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a> 2. krok: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta využití CPU pro diagnostické nástroje](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí dvakrát klikněte na `getNumber` funkci.

    Když dvakrát kliknete na funkci, otevře se zobrazení **volající/volaný** v levém podokně.

    ![Zobrazení volajícího volaných nástrojů pro diagnostiku](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví a v poli **aktuální funkce** ( `getNumber` v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo vyčerpáno 119 z 43602 MS v těle funkce a zbývající čas byla vyčerpána v jiném kódu, který tato funkce volá). Skutečné hodnoty se v závislosti na vašem prostředí budou velmi lišit.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)a Identifikujte problém s výkonem.
- Podrobné informace o nástroji využití CPU najdete v části [Analýza využití procesoru](../profiling/cpu-usage.md) .
- Analýza využití procesoru bez připojeného ladicího programu nebo zacílení na spuštěnou aplikaci – další informace najdete v tématu [shromažďování dat profilace bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [nástrojích pro profilaci spuštění s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
