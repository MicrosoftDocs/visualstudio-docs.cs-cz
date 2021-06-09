---
title: Analýza dat o využití procesoru (C++)
description: Měření výkonu aplikace v jazyce C++ pomocí nástroje pro diagnostiku využití procesoru
ms.date: 02/14/2020
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8c68cc67d768dbe2b1c42671a02360e5cef2b56b
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760936"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Rychlý start: Analýza dat o využití procesoru v Visual Studio (C++)

Rozhraní Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce. Tady se podíváme na nástroj pro identifikaci kritických míst výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud zde **popsaný** nástroj Využití procesoru neposkytuje datová data, která potřebujete, ostatní nástroje [pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které vám můžou být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Aplikace Profiler výkonu nabízí spoustu dalších možností pro záznam a analýzu tohoto typu dat. [PerfTips](../profiling/perftips.md), další nástroj pro profilaci integrovaný do ladicího programu, také umožňuje procházet kód a identifikovat, jak dlouho trvá dokončení konkrétních funkcí nebo bloků kódu.

Windows 8 spuštění nástrojů pro profilaci pomocí ladicího programu **(v** Diagnostické nástroje okně). Ve Windows 7 a novějších verzích můžete použít nástroj post- Profiler výkonu [.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

   V dialogovém **okně Nový** projekt v levém podokně rozbalte **Visual C++** a pak zvolte **Windows Desktop.** V prostředním podokně zvolte **Konzolová aplikace systému Windows**. Pak projekt *pojmnte Diagnostics_Get_Started_Native*.

   Pokud šablonu projektu Konzolová aplikace **systému Windows** nevidíte, zvolte odkaz Otevřít **Instalační program pro Visual Studio** v levém podokně dialogového okna **Nový** projekt. Spustí se instalační program pro Visual Studio. Zvolte **úlohu Vývoj desktopových aplikací** pomocí C++ a pak zvolte **Upravit.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Pokud úvodní okno není otevřené, zvolte **Úvodní** > **okno souboru**.

   V úvodním okně zvolte **Vytvořit nový projekt.**

   V **okně Vytvořit nový projekt** zadejte nebo zadejte *do* vyhledávacího pole konzolu. Potom v seznamu Jazyk zvolte **C++** a pak **v** seznamu Platforma zvolte Windows.

   Po použití filtrů jazyka a platformy zvolte šablonu **Konzolová aplikace** a pak zvolte **Další.**

   > [!NOTE]
   > Pokud šablonu Konzolová **aplikace nevidíte,** můžete ji nainstalovat z okna Vytvořit **nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce. Potom v části Instalační program pro Visual Studio úlohu **Vývoj desktopových aplikací pomocí C++.**

   V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo *Diagnostics_Get_Started_Native* do pole Project **name (Název** projektu). Pak zvolte **Vytvořit.**

   ::: moniker-end

   Visual Studio nový projekt otevřete.

1. V *Diagnostics_Get_Started_Native* nahraďte následující kód.

    ```c++
    int main()
    {
        return 0;
    }
    ```

    tímto kódem (neodebírat `#include "stdafx.h"` ):

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

1. Nejprve nastavte zarážku ve vaší aplikaci na tento řádek kódu ve `main` funkci :

    `for (int i = 0; i < 10; ++i) {`

    Zarážku nastavíte kliknutím na okap vlevo od řádku kódu.

2. Dále nastavte druhou zarážku na uzavírací složenou závorku na konci `main` funkce:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Nastavení zarážek pro profilaci")

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. Okno **Diagnostické nástroje** je již viditelné, pokud jste ho nevy vypnuli. Pokud chcete okno znovu zobrazit, klikněte na  >  **Ladit systém Windows** Zobrazit  >  **Diagnostické nástroje**.

4. Klikněte **na Ladit** a spustit ladění  >   **(nebo spustit** na panelu nástrojů nebo **F5).**

     Po dokončení načítání aplikace se **zobrazí souhrnné** zobrazení diagnostických nástrojů.

5. Když je ladicí program pozastavený, povolte shromažďování dat o využití procesoru tak, že zvolíte Zaznamenat **profil procesoru** a pak otevřete kartu **Využití** PROCESORU.

     ![Diagnostické nástroje – Povolení profilace procesoru](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostické nástroje – Povolení profilace procesoru")

     Když je shromažďování dat povolené, zobrazí se na tlačítku záznamu červený kruh.

     Když zvolíte Zaznamenat **profil PROCESORU,** Visual Studio začne zaznamenávat funkce a kolik času jejich provedení bude trvat, a také zobrazí graf časové osy, který můžete použít k zaměření na konkrétní segmenty relace vzorkování. Tato shromážděná data můžete zobrazit pouze v případě, že se aplikace zastaví na zarážce.

6. Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a> 2. krok: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklikejte na `getNumber` funkci.

    Když na funkci dvakrát kliknete, otevře se v levém podokně zobrazení Volající/Volaný. 

    ![Zobrazení Volající Volaný v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví a v poli **Aktuální** funkce ( `getNumber` v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo 119 z 43602 ms stráveno v těle funkce a zbývající čas byl strávený v jiném kódu s názvem touto funkcí). Skutečné hodnoty se budou velmi lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)a identifikujte kritické body výkonu.
- [Podrobnější informace o](../profiling/cpu-usage.md) nástroji využití procesoru najdete v analýze využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo cílení na spuštěnou aplikaci – Další informace najdete v tématu Shromažďování [dat profilace](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) bez ladění v tématu Spuštění [nástrojů pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md)s ladicím programem nebo bez něj.

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
