---
title: Analýza dat o využití procesoru (C++)
description: Měření výkonu aplikací v jazyce C++ pomocí nástroje diagnostiky využití procesoru
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
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2020
ms.locfileid: "80412011"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Úvodní příručka: Analýza dat o využití procesoru v sadě Visual Studio (C++)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomohou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma poskytuje rychlý způsob, jak se naučit některé základní funkce. Zde se podíváme na nástroj k identifikaci kritických bodů výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud nástroj **využití procesoru** popsaný zde neposkytuje data, která potřebujete, [ostatní profilovací nástroje](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které by vám mohly být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat. [PerfTips](../profiling/perftips.md), další profilovací nástroj integrovaný v ladicím programu, také umožňuje krokovat kód a určit, jak dlouho trvá dokončení určitých funkcí nebo bloků kódu.

Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna). V systému Windows 7 a novějších můžete použít nástroj post-mortem, [Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

   V dialogovém okně **Nový projekt** v levém podokně rozbalte **visual c++** a pak zvolte **Plochu windows**. V prostředním podokně zvolte **Aplikace konzoly systému Windows**. Potom pojmenujte projekt *Diagnostics_Get_Started_Native*.

   Pokud šablonu projektu **aplikace konzoly systému Windows** nevidíte, zvolte odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt.** Spustí se instalační program pro Visual Studio. Zvolte vývoj plochy s úlohami **C++** a pak zvolte **Změnit**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Pokud úvodní okno není otevřené, zvolte Počáteční okno **souboru** > **Start Window**.

   V počátečním okně zvolte **Vytvořit nový projekt**.

   V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **C++** ze seznamu Jazyk a pak zvolte **Windows** ze seznamu Platform.

   Po použití filtrů jazyka a platformy zvolte šablonu **Konzolové aplikace** a pak zvolte **Další**.

   > [!NOTE]
   > Pokud šablonu **konzolové aplikace** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?** Potom v Instalační službě Visual Studia zvolte vývoj plochy s úlohami **jazyka C++.**

   V okně **Konfigurovat nový projekt** zadejte nebo zadejte *Diagnostics_Get_Started_Native* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ::: moniker-end

   Visual Studio otevře nový projekt.

1. V *Diagnostics_Get_Started_Native*nahraďte následující kód

    ```c++
    int main()
    {
        return 0;
    }
    ```

    s tímto kódem `#include "stdafx.h"`(neodstraňujte ):

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

1. Nejprve nastavte zarážku ve vaší aplikaci `main` na tomto řádku kódu ve funkci:

    `for (int i = 0; i < 10; ++i) {`

    Nastavte zarážku klepnutím na hřbet vlevo od řádku kódu.

2. Dále nastavte druhou zarážku na uzavírací `main` závorku na konci funkce:

     ![Nastavení zarážek pro profilování](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Nastavení zarážek pro profilování")

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. Okno **Diagnostické nástroje** je již viditelné, pokud jste ho nevypnuli. Chcete-li okno znovu vyvolat, klepněte na tlačítko **Ladit** > **diagnostické nástroje služby****Windows** > Show .

4. Klepněte na **tlačítko Ladění** > **zahájit ladění** (nebo **Začít** na panelu nástrojů nebo **F5**).

     Po dokončení načítání aplikace se zobrazí **souhrnné** zobrazení nástrojů diagnostiky.

5. Když je ladicí program pozastaven, povolte shromažďování dat využití procesoru výběrem **možnosti Zaznamenat profil procesoru**a otevřete kartu **Využití procesoru.**

     ![Diagnostické nástroje povolují profilování procesoru](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostické nástroje povolují profilování procesoru")

     Pokud je povoleno shromažďování dat, tlačítko záznamu zobrazí červený kruh.

     Zvolíte-li **možnost Zaznamenat profil procesoru**, začne visual studio zaznamenávat vaše funkce a dobu, po kterou se spustí, a také poskytne graf časové osy, který můžete použít k zaměření na určité segmenty vzorkovací relace. Tato shromážděná data lze zobrazit pouze v případě, že je aplikace zastavena v zarážky.

6. Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a> 2. krok: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru nástroje diagnostiky](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "Karta DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklepejte `getNumber` na funkci.

    Po poklepání na funkci se v levém podokně otevře zobrazení **Volající/Volaný.**

    ![Zobrazení volajícího volacího volání nástroje pro diagnostiku](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví`getNumber`a v poli Aktuální **funkce** ( , v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo v těle funkce vynaloženo 119 ze 43602 ms a zbývající čas byl stráven v jiném kódu volaného touto funkcí). Skutečné hodnoty se budou velmi lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)k identifikaci kritických bodů výkonu.
- [Analyzujte využití procesoru](../profiling/cpu-usage.md) pro podrobnější informace o nástroji pro využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo cílením na spuštěnou aplikaci – další informace naleznete v [tématu Shromažďování dat profilování bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [nástrojích profilování spustit s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
