---
title: Analýza dat o využití procesoru (spravovaný kód)
description: Měřit výkon aplikace v C# a Visual Basic pomocí diagnostického nástroje využití CPU
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 35c6fd1ea079dd95367bcb7763787f0b06839ecb
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42624252"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-managed-code"></a>Rychlý start: Analýza dat o využití procesoru v aplikaci Visual Studio (spravovaný kód)

Visual Studio poskytuje mnoha výkonným funkcím, které vám pomůžou analyzovat problémy s výkonem v aplikaci. Toto téma poskytuje rychlý způsob, jak Seznamte se s některými základními funkcemi. Tady podíváme na nástroj, který identifikovat kritické body výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud **využití procesoru** nástroj je zde popsáno, vám neuděluje data, která budete potřebovat, [jiných nástrojů pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které může být pro vás užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. Diagnostické centrum nabízí řadu dalších možností, jak data tohoto druhu zaznamenávat a analyzovat.

Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno). Ve Windows 7 a novější, můžete použít nástroj a dodatečně [Profiler výkonu](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. V sadě Visual Studio, zvolte **souboru** > **nový projekt**.

2. V části **Visual C#** nebo **jazyka Visual Basic**, zvolte **Windows Desktop**a potom v prostředním podokně vyberte **Konzolová aplikace (.NET Framework)**.

    Pokud se nezobrazí **konzolovou aplikaci** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte **.NET Desktop development** úloh, klikněte na tlačítko **změnit**.

3. Zadejte název, například **MyProfilerApp** a klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

2. Otevřít *Program.cs* a nahraďte kód následujícím kódem:

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
    > V jazyce Visual Basic, ujistěte se, že spouštěcí objekt je nastavena na `Sub Main` (**vlastnosti** > **aplikace** > **spouštěcí objekt**).

##  <a name="step-1-collect-profiling-data"></a>Krok 1: Shromáždění profilačních dat

1.  Nejprve nastavte zarážku v aplikaci na tomto řádku kódu v `Main` funkce:

    `for (int i = 0; i < 200; i++)`

    nebo v jazyce Visual Basic:

    `For i As Integer = 0 To 199`

    Po kliknutí na ovládací prvek vlevo od řádku kódu, nastavte zarážku.

2.  Dále nastavte zarážku druhý na pravou složenou závorku na konci `Main` funkce:

     ![Nastavení zarážek pro profilování](../profiling/media/quickstart-cpu-usage-breakpoints.png "nastavit zarážky pro profilaci")

    > [!TIP]
    > Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

3.  **Diagnostické nástroje** okno již viditelné, pokud jste ji vypnuli. Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

4.  Klikněte na tlačítko **ladění** > **spustit ladění** (nebo **Start** na panelu nástrojů nebo **F5**).

     Po dokončení načítání, aplikace **Souhrn** zobrazí diagnostické nástroje.

5.  Když ladicí program je pozastavený, Povolit shromažďování dat o využití procesoru výběrem **profil CPU záznam**a pak otevřete **využití procesoru** kartu.

     ![Diagnostické nástroje povolit profilaci procesoru](../profiling/media/quickstart-cpu-usage-summary.png "diagnostické nástroje povolit profilaci procesoru")

     Když je povolené shromažďování dat, tlačítko záznam zobrazí červený kruh.

     Při výběru **profil CPU záznam**, Visual Studio bude nahráváním vašich funkcí a jak dlouho jim trvá spuštění a také obsahuje graf časové osy vám umožní zaměřit se na určité segmenty relace odběru vzorků. Tato shromážděná data můžete zobrazit pouze, když vaše aplikace je zastaven na zarážce.

6.  Stisknutím klávesy **F5** ke spuštění aplikace na druhém zarážku.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analýza dat o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí dvakrát klikněte `ServerClass::GetNumber` funkce.

    Když dvakrát kliknete funkce **volající/volaný** zobrazení se otevře v levém podokně.

    ![Zobrazení Volající/volaný v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    V tomto zobrazení vybrané funkce se zobrazí v záhlaví a **aktuální funkci** pole (`GetNumber`, v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku 2856 mimo 2863 ms byly trvání tělo funkce a zbývající dobu (< 20 ms) se využilo na externí kód volaných touto funkcí). Skutečné hodnoty se liší v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analýza využití paměti](../profiling/memory-usage.md)identifikovat kritické body výkonu.
- [Analýza využití procesoru](../profiling/cpu-usage.md) další podrobné informace o nástroj využití procesoru.
- Analýza využití procesoru bez připojen jiný ladicí program, nebo cílení na spuštění aplikace – Další informace najdete v tématu [shromažďovat data profilování bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také:

- [Profilace v sadě Visual Studio](../profiling/index.md)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)