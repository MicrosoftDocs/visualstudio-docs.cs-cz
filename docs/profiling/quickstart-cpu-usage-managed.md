---
title: Analýza dat o využití procesoru (C#, Visual Basic)
description: Měření výkonu aplikace v jazyce C# a Visual Basic pomocí nástroje pro diagnostiku využití procesoru
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 056996782d2b38adb96ee53250cc3ea0c0f75596
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761157"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Rychlý start: Analýza dat o využití procesoru v Visual Studio (C#, Visual Basic)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce. Tady se podíváme na nástroj pro identifikaci kritických míst výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud zde **popsaný** nástroj Využití procesoru neposkytuje datová data, která potřebujete, další nástroje [pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které vám můžou být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Aplikace Profiler výkonu nabízí spoustu dalších možností pro záznam a analýzu tohoto typu dat. [PerfTips](../profiling/perftips.md), další nástroj pro profilaci integrovaný do ladicího programu, také umožňuje procházet kód a identifikovat, jak dlouho trvá dokončení konkrétních funkcí nebo bloků kódu.

Windows 8 spuštění nástrojů pro profilaci pomocí ladicího programu **(v** Diagnostické nástroje okně). Ve Windows 7 a novějších verzích můžete použít nástroj post-Profiler výkonu [.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

   V dialogovém **okně Nový** projekt v levém podokně rozbalte **C#** **nebo Visual Basic** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Konzolová aplikace (.NET Core).** Pak projekt *pojmechte MyProfilerApp*.

   Pokud šablonu projektu Konzolová aplikace **(.NET Core)** nevidíte, zvolte odkaz Otevřít **Instalační program pro Visual Studio** v levém podokně dialogového okna **Nový** projekt. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Pokud úvodní okno není otevřené, zvolte **Úvodní** > **okno souboru**.

   V úvodním okně zvolte **Vytvořit nový projekt.**

   V **okně Vytvořit nový projekt** zadejte nebo zadejte *do* vyhledávacího pole konzolu. Dále zvolte **C#** **nebo Visual Basic** ze seznamu Jazyk a pak v seznamu Platforma zvolte Windows. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Konzolová aplikace** pro .NET Core a pak zvolte **Další.**

   > [!NOTE]
   > Pokud šablonu Konzolová **aplikace nevidíte,** můžete ji nainstalovat z okna Vytvořit **nový** projekt. Ve **zprávě Nehledáte** to, co hledáte? zvolte odkaz Instalovat **další** nástroje a funkce. Potom v části Instalační program pro Visual Studio úlohu **Vývoj pro různé platformy v .NET Core.**

   V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole Project name **(Název projektu)** zadejte nebo zadejte *MyProfilerApp.* Pak zvolte **Další.**

   Zvolte doporučenou cílovou rozhraní (.NET Core 3.1) nebo .NET 5 a pak zvolte **Vytvořit.**

   ::: moniker-end

   Visual Studio nový projekt otevřete.

2. Otevřete *soubor Program.cs* a nahraďte veškerý kód následujícím kódem:

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
    > V Visual Basic se ujistěte, že je spouštěcí objekt nastavený na `Sub Main` hodnotu (**Vlastnosti**  >  **Spouštěcí**  >  **objekt aplikace**).

## <a name="step-1-collect-profiling-data"></a>1. krok: Shromáždění profilačních dat

1. Nejprve nastavte zarážku v aplikaci na tento řádek kódu ve `Main` funkci :

    `for (int i = 0; i < 200; i++)`

    nebo pro Visual Basic:

    `For i As Integer = 0 To 199`

    Zarážku nastavíte kliknutím na okap vlevo od řádku kódu.

2. Dále nastavte druhou zarážku na uzavírací složenou závorku na konci `Main` funkce:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints.png "Nastavení zarážek pro profilaci")

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3. Okno **Diagnostické nástroje** je již viditelné, pokud jste ho nevy vypnuli. Pokud chcete okno znovu zobrazit, klikněte na  >  **Ladit systém Windows** Zobrazit  >  **Diagnostické nástroje**.

4. Klikněte **na Ladit** a spustit ladění  >   **(nebo spustit** na panelu nástrojů nebo **F5).**

     Po dokončení načítání aplikace se **zobrazí souhrnné** zobrazení diagnostických nástrojů.

5. Když je ladicí program pozastavený, povolte shromažďování dat o využití procesoru tak, že zvolíte Zaznamenat **profil procesoru** a pak otevřete kartu **Využití** PROCESORU.

     ![Diagnostické nástroje – Povolení profilace procesoru](../profiling/media/quickstart-cpu-usage-summary.png "Diagnostické nástroje – Povolení profilace procesoru")

     Když je shromažďování dat povolené, zobrazí se na tlačítku záznamu červený kruh.

     Když zvolíte Zaznamenat **profil PROCESORU,** Visual Studio začne zaznamenávat funkce a kolik času jejich provedení bude trvat, a také zobrazí graf časové osy, který můžete použít k zaměření na konkrétní segmenty relace vzorkování. Tato shromážděná data můžete zobrazit pouze v případě, že se aplikace zastaví na zarážce.

6. Stisknutím **klávesy F5** spusťte aplikaci na druhou zarážku.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a> 2. krok: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklikejte na `ServerClass::GetNumber` funkci.

    Když na funkci dvakrát kliknete, otevře se v levém podokně zobrazení Volající/Volaný. 

    ![Zobrazení Volající volaný v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví a v poli **Aktuální** funkce ( `GetNumber` v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo 2856 z 2863 ms stráveno v těle funkce a zbývající čas (<20 ms) byl stráven v externím kódu s názvem touto funkcí). Skutečné hodnoty se budou lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)a identifikujte kritické body výkonu.
- [Podrobnější informace o](../profiling/cpu-usage.md) nástroji využití procesoru najdete v analýze využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo cílení na spuštěnou aplikaci – Další informace najdete v tématu Shromažďování [dat profilace](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) bez ladění v tématu Spuštění [nástrojů pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md)s ladicím programem nebo bez něj.

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
