---
title: Analýza dat využití procesoru (ASP.NET)
description: Měření výkonu aplikací v aplikacích ASP.NET pomocí nástroje Diagnostika využití CPU
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
- aspnet
ms.openlocfilehash: cbaaa53fe737761fdd938b7861c371e8e5619acc
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128165"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Rychlý start: Analýza dat využití procesoru v aplikaci Visual Studio (ASP.NET)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce. Tady se podíváme na nástroj, který identifikuje problémová místa výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud nástroj **využití procesoru** , který je zde popsaný, neposkytuje potřebná data, [ostatní nástroje pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které vám mohou být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku.

Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno). Ve Windows 7 a novějších verzích můžete použít nástroj pro následné povýšení, [Profiler výkonu](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. V aplikaci Visual Studio vyberte **soubor** > **Nový projekt**.

1. V **části C#vizuál** zvolte **Web**a potom v prostředním podokně zvolte **ASP.NET webová aplikace (.NET Framework)** .

    Pokud nevidíte šablonu projektu **webové aplikace ASP.NET** , klikněte na odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu a** pak zvolte **Upravit**.

1. Zadejte název jako **MyProfilingApp_MVC** a klikněte na **OK**.

1. V dialogovém okně, které se zobrazí, zvolte **MVC** v prostředním podokně a pak klikněte na **OK**.

    Visual Studio vytvoří projekt. Průzkumník řešení (pravé podokno) zobrazí soubory projektu.

1. V Průzkumník řešení klikněte pravým tlačítkem na složku modely a vyberte **Přidat** > **třídu**.

1. Pojmenujte novou `Data.cs` třídu a klikněte na **Přidat**.

1. V Průzkumník řešení otevřete `Models/Data.cs` a přidejte na začátek souboru `using` následující příkaz:

    ```csharp
    using System.Threading;
    ```

1. V Data.cs nahraďte následující kód:

    ```csharp
    public class Data
    {
    }
    ```

    s tímto kódem:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
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
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. V Průzkumník řešení otevřete *Controller/HomeControllers. cs*a nahraďte následující kód:

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    s tímto kódem:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

## <a name="step-1-collect-profiling-data"></a>Krok 1: Shromažďování dat profilace

1. Nejdřív v aplikaci nastavte zarážku na tomto řádku kódu v `Simple` konstruktoru:

    `for (int i = 0; i < 200; i++)`

    Nastavte zarážku kliknutím na hřbet nalevo od řádku kódu.

1. Dále nastavte druhou zarážku na pravou složenou závorku na konci `Simple` konstruktoru:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

1. **Diagnostické nástroje** okno je již viditelné, pokud jste ho neaktivovali. Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

1. Klikněte na tlačítko **ladění** > **spustit ladění** (nebo **Start** na panelu nástrojů nebo **F5**).

1. Po dokončení načítání aplikace klikněte na odkaz **o informace** v horní části webové stránky a začněte používat nový kód.

1. Podívejte se na **souhrnné** zobrazení diagnostických nástrojů.

1. I když je ladicí program pozastaven, povolte shromažďování dat o využití procesoru výběrem možnosti **zaznamenat profil procesoru**a pak otevřete kartu **využití CPU** .

     ![Diagnostické nástroje povolují profilaci procesoru](../profiling/media/quickstart-cpu-usage-summary.png)

     Když je povolené shromažďování dat, na tlačítku záznamu se zobrazí červené kolečko.

     Když vyberete možnost **zaznamenat profil procesoru**, Visual Studio zahájí zaznamenávání vašich funkcí a množství času, které je potřeba provést, a také graf časové osy, pomocí kterého se můžete soustředit na konkrétní segmenty relace vzorkování. Tato shromážděná data můžete zobrazit pouze v případě, že dojde k zastavení aplikace na zarážce.

6. Stiskněte klávesu F5, kterou spustíte aplikaci až ke druhé zarážce.

     Teď máte údaje o výkonu aplikace přesně pro oblast kódu spuštěnou mezi dvěma zarážkami.

     Profiler začne připravovat údaje o vlákně. Počkejte, až skončí.

     V nástroji Využití procesoru se na kartě **Využití procesoru** zobrazí sestava.

     Teď můžete začít analyzovat data.

## <a name="step-2-analyze-cpu-usage-data"></a>Krok 2: Analyzovat data o využití procesoru

Analýzu dat doporučujeme začít tím, že zkontrolujete seznam funkcí na kartě Využití procesoru. Zjistěte nejaktivnější funkce a pak se na každou z nich podívejte podrobněji.

1. V seznamu funkcí se podívejte, jaké funkce vykonávají většinu práce.

     ![Karta využití CPU pro diagnostické nástroje](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí dvakrát klikněte `MyProfilingApp_MVC.Models.ServerClass::GetNumber` na funkci.

    Když dvakrát kliknete na funkci, otevře se zobrazení **volající/volaný** v levém podokně.

    ![Zobrazení volající/volaný diagnostické nástroje](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví a v poli **aktuální funkce** (`ServerClass::GetNumber`v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo vyčerpáno 2220 z 2235 MS v těle funkce a zbývající čas (< 20 MS) byl vyčerpán v externím kódu, který tato funkce volala). Skutečné hodnoty se budou lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analýza využití paměti](../profiling/memory-usage.md)identifikovat kritické body výkonu.
- [Analýza využití procesoru](../profiling/cpu-usage.md) další podrobné informace o nástroj využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo zacílení na spuštěnou aplikaci – další informace najdete v tématu [shromažďování dat profilace bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [nástrojích pro profilaci spuštění s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také:

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
