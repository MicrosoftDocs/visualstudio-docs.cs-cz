---
title: Analýza dat o využití procesoru (C#, Visual Basic)
description: Měření výkonu aplikace v jazyce C# a visual basicu pomocí nástroje diagnostiky využití procesoru
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b4d36d9b758e0171452a909d85c799503389a1a9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550078"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Úvodní příručka: Analýza dat o využití procesoru v sadě Visual Studio (C#, Visual Basic)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomohou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma poskytuje rychlý způsob, jak se naučit některé základní funkce. Zde se podíváme na nástroj k identifikaci kritických bodů výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud nástroj **využití procesoru** popsaný zde neposkytuje data, která potřebujete, [ostatní profilovací nástroje](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které by vám mohly být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat.

Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna). V systému Windows 7 a novějších můžete použít nástroj post-mortem, [Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

   V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku C#** nebo **Visual Basic**a zvolte **.NET Core**. V prostředním podokně zvolte **Console App (.NET Core)**. Pak pojmenujte projekt *MyProfilerApp*.

   Pokud šablonu projektu **Console App (.NET Core)** nevidíte, zvolte odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt.** Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Pokud úvodní okno není otevřené, zvolte Počáteční okno **souboru** > **Start Window**.

   V počátečním okně zvolte **Vytvořit nový projekt**.

   V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **C#** nebo **Visual Basic** ze seznamu jazyk a pak zvolte **Windows** ze seznamu platformy.

   Po použití filtrů jazyka a platformy zvolte šablonu **Console App (.NET Core)** a pak zvolte **Další**.

   > [!NOTE]
   > Pokud šablonu **Console App (.NET Core)** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?** Potom v Instalační službě sady Visual Studio zvolte vývojové úlohy **.NET Core napříč platformami.**

   V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MyProfilerApp* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   ::: moniker-end

   Visual Studio otevře nový projekt.

2. Otevřete *Program.cs* a nahraďte celý kód následujícím kódem:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > V jazyce Visual Basic zkontrolujte, `Sub Main` zda je spouštěcí objekt nastaven na **(Vlastnosti** > **objektu spuštění****aplikace** > ).

## <a name="step-1-collect-profiling-data"></a>1. krok: Shromáždění profilačních dat

1. Nejprve nastavte zarážku ve vaší aplikaci `Main` na tomto řádku kódu ve funkci:

    `for (int i = 0; i < 200; i++)`

    nebo v jazyce Visual Basic:

    `For i As Integer = 0 To 199`

    Nastavte zarážku klepnutím na hřbet vlevo od řádku kódu.

2. Dále nastavte druhou zarážku na uzavírací `Main` závorku na konci funkce:

     ![Nastavení zarážek pro profilování](../profiling/media/quickstart-cpu-usage-breakpoints.png "Nastavení zarážek pro profilování")

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

    >[!TIP]
    > Při pozastavení na zarážku nebo krokování kódu operace, můžete také analyzovat výkon pomocí [PerfTips](../profiling/perftips.md).

3. Okno **Diagnostické nástroje** je již viditelné, pokud jste ho nevypnuli. Chcete-li okno znovu vyvolat, klepněte na tlačítko **Ladit** > **diagnostické nástroje služby****Windows** > Show .

4. Klepněte na **tlačítko Ladění** > **zahájit ladění** (nebo **Začít** na panelu nástrojů nebo **F5**).

     Po dokončení načítání aplikace se zobrazí **souhrnné** zobrazení nástrojů diagnostiky.

5. Když je ladicí program pozastaven, povolte shromažďování dat využití procesoru výběrem **možnosti Zaznamenat profil procesoru**a otevřete kartu **Využití procesoru.**

     ![Diagnostické nástroje povolují profilování procesoru](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostické nástroje povolují profilování procesoru")

     Pokud je povoleno shromažďování dat, tlačítko záznamu zobrazí červený kruh.

     Zvolíte-li **možnost Zaznamenat profil procesoru**, začne visual studio zaznamenávat vaše funkce a dobu, po kterou se spustí, a také poskytne graf časové osy, který můžete použít k zaměření na určité segmenty vzorkovací relace. Tato shromážděná data lze zobrazit pouze v případě, že je aplikace zastavena v zarážky.

6. Stisknutím **klávesy F5** spusťte aplikaci na druhou zarážku.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a> 2. krok: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru nástroje diagnostiky](../profiling/media/quickstart-cpu-usage-cpu.png "Karta DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklepejte `ServerClass::GetNumber` na funkci.

    Po poklepání na funkci se v levém podokně otevře zobrazení **Volající/Volaný.**

    ![Zobrazení volajícího volacího volání nástroje pro diagnostiku](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví`GetNumber`a v poli Aktuální **funkce** ( , v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo v těle funkce vynaloženo 2856 z 2863 ms a zbývající čas (<20 ms) byl vynaložen v externím kódu volaného touto funkcí). Skutečné hodnoty se budou lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)k identifikaci kritických bodů výkonu.
- [Analyzujte využití procesoru](../profiling/cpu-usage.md) pro podrobnější informace o nástroji pro využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo cílením na spuštěnou aplikaci – další informace naleznete v [tématu Shromažďování dat profilování bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [nástrojích profilování spustit s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
