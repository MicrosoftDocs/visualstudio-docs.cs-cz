---
title: Analýza dat o využití procesoru (ASP.NET Core)
description: Měření výkonu aplikací v aplikacích ASP.NET Core pomocí nástroje diagnostika využití procesoru
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
- aspnet
ms.openlocfilehash: bb1d5fc769254f112e3a4cb757b173e0dbded3bb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550097"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Úvodní příručka: Analýza dat o využití procesoru ve Visual Studiu (ASP.NET Core)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomohou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma poskytuje rychlý způsob, jak se naučit některé základní funkce. Zde se podíváme na nástroj k identifikaci kritických bodů výkonu z důvodu vysokého využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud nástroj **využití procesoru** popsaný zde neposkytuje data, která potřebujete, [ostatní profilovací nástroje](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které by vám mohly být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku.

Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna). V systému Windows 7 a novějších můžete použít nástroj post-mortem, [Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

   V dialogovém okně **Nový projekt** v levém podokně rozbalte **položku Visual C#** a pak zvolte **Web**. V prostředním podokně zvolte **ASP.NET Web Application (.NET Core).** Potom pojmenujte projekt *MyProfilingApp_MVC*.

   > [!NOTE]
   > Pokud šablonu projektu **ASP.NET webovou aplikaci (.NET Core)** nevidíte, zvolte odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt.** Spustí se instalační program pro Visual Studio. Zvolte **ASP.NET a zatížení vývoje webu** a pak zvolte **Změnit**.

   V zobrazeném dialogovém okně zvolte **mvc** v prostředním podokně a klepněte na tlačítko **OK**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Pokud úvodní okno není otevřené, zvolte Počáteční okno **souboru** > **Start Window**.

   V počátečním okně zvolte **Vytvořit nový projekt**.

   V okně **Vytvořit nový projekt** zadejte nebo zadejte *asp.net* do vyhledávacího pole. Dále zvolte **C#** ze seznamu jazyk a pak zvolte **Windows** ze seznamu platformy.

   Po použití filtrů jazyka a platformy zvolte šablonu **ASP.NET Web Application (.NET Core)** a pak zvolte **Další**.

   > [!NOTE]
   > Pokud šablonu **ASP.NET webové aplikace (.NET Core)** nevidíte, můžete ji nainstalovat z okna Vytvořit nový **projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?** Potom v Instalační službě sady Visual Studio zvolte **úlohu ASP.NET a vývoj webových** aplikací.

   V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MyProfilingApp_MVC* do pole **Název projektu.** Potom zvolte **Vytvořit**.

   V okně, které se zobrazí, zvolte **Webová aplikace (Model-View-Controller)** a pak zvolte **Vytvořit**.

   ::: moniker-end

   Visual Studio otevře nový projekt.

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na složku Modely a zvolte **Přidat** > **třídu**.

1. Pojmenujte `Data.cs` novou třídu a zvolte **Přidat**.

1. V Průzkumníku `Models/Data.cs` řešení otevřete `using` a přidejte do horní části souboru následující příkaz:

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

1. V Průzkumníku řešení *otevřete Controller/HomeControllers.cs*a nahraďte následující kód:

   ::: moniker range="vs-2017"

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

    ::: moniker-end
    ::: moniker range="vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    s tímto kódem:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>1. krok: Shromáždění profilačních dat

1. Nejprve nastavte zarážku ve vaší aplikaci `Simple` na tomto řádku kódu v konstruktoru:

    `for (int i = 0; i < 200; i++)`

    Nastavte zarážku klepnutím na hřbet vlevo od řádku kódu.

1. Dále nastavte druhou zarážku na uzavírací `Simple` závorku na konci konstruktoru:

     ![Nastavení zarážek pro profilování](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

    >[!TIP]
    > Při pozastavení na zarážku nebo krokování kódu operace, můžete také analyzovat výkon pomocí [PerfTips](../profiling/perftips.md).

1. Okno **Diagnostické nástroje** je již viditelné, pokud jste ho nevypnuli. Chcete-li okno znovu vyvolat, klepněte na tlačítko **Ladit** > **diagnostické nástroje služby****Windows** > Show .

1. Klepněte na **tlačítko Ladění** > **zahájit ladění** (nebo **Začít** na panelu nástrojů nebo **F5**).

1. Po dokončení načítání aplikace klikněte na příslušný odkaz v horní části webové stránky a spusťte nový kód.

   ::: moniker range="vs-2017"
   V Sadě Visual Studio 2017 klikněte na odkaz **Informace** a spusťte kód.
   ::: moniker-end
   ::: moniker range="vs-2019"
   V Visual Studiu 2019 klikněte na odkaz **Soukromí** a spusťte kód.
   ::: moniker-end

1. Podívejte se na **souhrnné** zobrazení nástrojů diagnostiky.

1. Když je ladicí program pozastaven, povolte shromažďování dat využití procesoru výběrem **možnosti Zaznamenat profil procesoru**a otevřete kartu **Využití procesoru.**

     ![Diagnostické nástroje povolují profilování procesoru](../profiling/media/quickstart-cpu-usage-summary.png)

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

     ![Karta Využití procesoru nástroje pro diagnostiku](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklepejte `MyProfilingApp_MVC.Models.ServerClass::GetNumber` na funkci.

    Po poklepání na funkci se v levém podokně otevře zobrazení **Volající/Volaný.**

    ![Diagnostické nástroje Zobrazení volajícího/volaní](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví`ServerClass::GetNumber`a v poli Aktuální **funkce** ( , v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo v těle funkce vynaloženo 2220 z 2235 ms a zbývající čas (<20 ms) byl vynaložen v externím kódu volaného touto funkcí). Skutečné hodnoty se budou lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)k identifikaci kritických bodů výkonu.
- [Analyzujte využití procesoru](../profiling/cpu-usage.md) pro podrobnější informace o nástroji pro využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo cílením na spuštěnou aplikaci – další informace naleznete v [tématu Shromažďování dat profilování bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [nástrojích profilování spustit s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
