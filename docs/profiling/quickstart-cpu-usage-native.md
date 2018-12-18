---
title: Analýza dat o využití procesoru (C++)
description: Měřit výkon aplikace v jazyce C++ pomocí diagnostického nástroje využití CPU
ms.custom: ''
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c4cf51a4961d6b9139d4f8fdbfd6c5df2ab0052c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42624085"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Rychlý start: Analýza dat o využití procesoru v aplikaci Visual Studio (C++)

Visual Studio poskytuje mnoha výkonným funkcím, které vám pomůžou analyzovat problémy s výkonem v aplikaci. Toto téma poskytuje rychlý způsob, jak Seznamte se s některými základními funkcemi. Tady podíváme na nástroj, který identifikovat kritické body výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud **využití procesoru** nástroj je zde popsáno, vám neuděluje data, která budete potřebovat, [jiných nástrojů pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které může být pro vás užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat.

Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno). Ve Windows 7 a novější, můžete použít nástroj a dodatečně [Profiler výkonu](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. V sadě Visual Studio, zvolte **souboru** > **nový projekt**.

2. V části **Visual C++**, zvolte **Windows Desktop**a potom v prostředním podokně vyberte **Konzolová aplikace Windows**.

    Pokud se nezobrazí **Konzolová aplikace Windows** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací pomocí C++** úloh, klikněte na tlačítko **změnit**.

3. Zadejte název, například **Diagnostics_Get_Started_Native** a klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

4. V *MyDbgApp.cpp*, nahraďte následující kód

    ```c++
    int main()
    {
        return 0;
    }
    ```

    s tímto kódem (neodebírejte `#include "stdafx.h"`):

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
  
## <a name="step-1-collect-profiling-data"></a>Krok 1: Shromáždění profilačních dat 
  
1.  Nejprve nastavte zarážku v aplikaci na tomto řádku kódu v `main` funkce:

    `for (int i = 0; i < 10; ++i) {`

    Po kliknutí na ovládací prvek vlevo od řádku kódu, nastavte zarážku.

2.  Dále nastavte zarážku druhý na pravou složenou závorku na konci `main` funkce:

     ![Nastavení zarážek pro profilování](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "nastavit zarážky pro profilaci")

    > [!TIP]
    > Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.
  
3.  **Diagnostické nástroje** okno již viditelné, pokud jste ji vypnuli. Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

4.  Klikněte na tlačítko **ladění** > **spustit ladění** (nebo **Start** na panelu nástrojů nebo **F5**).

     Po dokončení načítání, aplikace **Souhrn** zobrazí diagnostické nástroje.

5.  Když ladicí program je pozastavený, Povolit shromažďování dat o využití procesoru výběrem **profil CPU záznam**a pak otevřete **využití procesoru** kartu.

     ![Diagnostické nástroje povolit profilaci procesoru](../profiling/media/quickstart-cpu-usage-summary.png "diagnostické nástroje povolit profilaci procesoru")

     Když je povolené shromažďování dat, tlačítko záznam zobrazí červený kruh.

     Při výběru **profil CPU záznam**, Visual Studio bude nahráváním vašich funkcí a jak dlouho jim trvá spuštění a také obsahuje graf časové osy vám umožní zaměřit se na určité segmenty relace odběru vzorků. Tato shromážděná data můžete zobrazit pouze, když vaše aplikace je zastaven na zarážce.

6.  Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.
  
     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí dvakrát klikněte `getNumber` funkce.

    Když dvakrát kliknete funkce **volající/volaný** zobrazení se otevře v levém podokně. 

    ![Zobrazení Volající/volaný v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    V tomto zobrazení vybrané funkce se zobrazí v záhlaví a **aktuální funkci** pole (`getNumber`, v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku 119 z 43602 ms byly stráví v těle funkce a zbývající dobu se využilo na jiný kód volaných touto funkcí). Skutečné hodnoty budou velmi liší v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analýza využití paměti](../profiling/memory-usage.md)identifikovat kritické body výkonu.
- [Analýza využití procesoru](../profiling/cpu-usage.md) další podrobné informace o nástroj využití procesoru.
- Analýza využití procesoru bez připojen jiný ladicí program, nebo cílení na spuštění aplikace – Další informace najdete v tématu [shromažďovat data profilování bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také:  

 [Profilace v sadě Visual Studio](../profiling/index.md)  
 [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
