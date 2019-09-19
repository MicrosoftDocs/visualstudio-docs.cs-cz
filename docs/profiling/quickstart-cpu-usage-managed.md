---
title: Analýza dat využití procesoru (C#, Visual Basic)
description: Měření výkonu aplikace v C# a Visual Basic pomocí nástroje Diagnostika využití CPU
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d13a97c3fb228cb72040313c98b70e14fc44099
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128198"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Rychlý start: Analýza dat využití procesoru v aplikaci Visual StudioC#(Visual Basic)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce. Tady se podíváme na nástroj a Identifikujte problémová místa výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud nástroj **využití procesoru** , který je zde popsaný, neposkytuje potřebná data, [ostatní nástroje pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které vám mohou být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat.

Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno). Ve Windows 7 a novějších verzích můžete použít nástroj pro následné povýšení, [Profiler výkonu](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vyberte **soubor** > **Nový projekt**.

2. V **části C# vizuál** nebo **Visual Basic**zvolte **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .

    Pokud nevidíte šablonu projektu **konzolové aplikace** , klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoj desktopových** aplikací pro .NET a pak zvolte **Upravit**.

3. Zadejte název jako **MyProfilerApp** a klikněte na **OK**.

    Visual Studio vytvoří projekt.

2. Otevřete *program.cs* a nahraďte celý kód následujícím kódem:

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
    > V Visual Basic se ujistěte, že je spouštěcí objekt nastavený na `Sub Main` (**vlastnosti** > **spouštěcí objekt** **aplikace** > ).

## <a name="step-1-collect-profiling-data"></a>Krok 1: Shromažďování dat profilace

1. Nejdřív v aplikaci nastavte zarážku na tomto řádku kódu ve `Main` funkci:

    `for (int i = 0; i < 200; i++)`

    nebo pro Visual Basic:

    `For i As Integer = 0 To 199`

    Nastavte zarážku kliknutím na hřbet nalevo od řádku kódu.

2. Dále nastavte druhou zarážku na pravou složenou závorku na konci `Main` funkce:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints.png "Nastavení zarážek pro profilaci")

    > [!TIP]
    > Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. **Diagnostické nástroje** okno je již viditelné, pokud jste ho neaktivovali. Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

4. Klikněte na tlačítko **ladění** > **spustit ladění** (nebo **Start** na panelu nástrojů nebo **F5**).

     Po dokončení načítání aplikace se zobrazí **souhrnné** zobrazení diagnostických nástrojů.

5. I když je ladicí program pozastaven, povolte shromažďování dat o využití procesoru výběrem možnosti **zaznamenat profil procesoru**a pak otevřete kartu **využití CPU** .

     ![Diagnostické nástroje povolují profilaci procesoru](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostické nástroje povolují profilaci procesoru")

     Když je povolené shromažďování dat, na tlačítku záznamu se zobrazí červené kolečko.

     Když vyberete možnost **zaznamenat profil procesoru**, Visual Studio zahájí zaznamenávání vašich funkcí a množství času, které je potřeba provést, a také graf časové osy, pomocí kterého se můžete soustředit na konkrétní segmenty relace vzorkování. Tato shromážděná data můžete zobrazit pouze v případě, že dojde k zastavení aplikace na zarážce.

6. Stisknutím klávesy **F5** ke spuštění aplikace na druhém zarážku.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analyzovat data o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí dvakrát klikněte `ServerClass::GetNumber` na funkci.

    Když dvakrát kliknete na funkci, otevře se zobrazení **volající/volaný** v levém podokně.

    ![Zobrazení Volající/volaný v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví a v poli **aktuální funkce** (`GetNumber`v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo vyčerpáno 2856 z 2863 MS v těle funkce a zbývající čas (< 20 MS) byl vyčerpán v externím kódu, který tato funkce volala). Skutečné hodnoty se budou lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analýza využití paměti](../profiling/memory-usage.md)identifikovat kritické body výkonu.
- [Analýza využití procesoru](../profiling/cpu-usage.md) další podrobné informace o nástroj využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo zacílení na spuštěnou aplikaci – další informace najdete v tématu [shromažďování dat profilace bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [nástrojích pro profilaci spuštění s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také:

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
