---
title: Analýza dat o využití procesoru (ASP.NET Core)
description: Měření výkonu aplikace v ASP.NET Core pomocí nástroje pro diagnostiku využití procesoru
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
- aspnet
ms.openlocfilehash: aa0c95e3a9f3598cd6399b565adb75faccac22a8
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761144"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Rychlý start: Analýza dat o využití procesoru v Visual Studio (ASP.NET Core)

Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou analyzovat problémy s výkonem ve vaší aplikaci. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce. Tady se podíváme na nástroj pro identifikaci kritických míst výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud zde **popsaný** nástroj Využití procesoru neposkytuje datová data, která potřebujete, další nástroje [pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které vám můžou být užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku. [PerfTips](../profiling/perftips.md), další nástroj pro profilaci integrovaný do ladicího programu, také umožňuje procházet kód a identifikovat, jak dlouho trvá dokončení konkrétních funkcí nebo bloků kódu.

Windows 8 spuštění nástrojů pro profilaci pomocí ladicího programu **(v** Diagnostické nástroje okně). Ve Windows 7 a novějších verzích můžete použít nástroj post-Profiler výkonu [.](../profiling/profiling-feature-tour.md)

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete Visual Studio a vytvořte projekt.

   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

   V dialogovém **okně Nový** projekt v levém podokně rozbalte položku **Visual C#** a pak zvolte **Web**. V prostředním podokně zvolte **ASP.NET aplikace (.NET Core).** Pak projekt *pojmnte MyProfilingApp_MVC*.

   > [!NOTE]
   > Pokud šablonu projektu webová aplikace **ASP.NET (.NET Core)** nevidíte, zvolte odkaz Otevřít **Instalační program pro Visual Studio** v levém podokně dialogového okna **Nový** projekt. Spustí se instalační program pro Visual Studio. Zvolte **úlohu ASP.NET a vývoje** webu a pak zvolte **Upravit.**

   V dialogovém okně, které se zobrazí, zvolte **MVC** v prostředním podokně a potom klikněte na **OK.**
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   V Visual Studio 2019 zvolte **v** úvodním okně Vytvořit nový projekt. Pokud úvodní okno není otevřené, zvolte **Úvodní**  >  **okno souboru** a pak zvolte Vytvořit nový **projekt**.

   Do **vyhledávacího** pole zadejte webová aplikace, jako jazyk zvolte **C#,** **zvolte ASP.NET Core Web Application (Model-View-Controller) a** pak zvolte **Další.** Na další obrazovce zadejte název projektu *MyProfilingApp_MVC* a pak zvolte **Další.**

   Zvolte doporučenou cílovou rozhraní (.NET Core 3.1) nebo .NET 5 a pak zvolte **Vytvořit.**

   > [!NOTE]
   > Pokud šablonu webové aplikace **ASP.NET (.NET Core)** nevidíte, můžete ji nainstalovat z okna Vytvořit **nový** projekt. Ve **zprávě Nehledáte** to, co hledáte? zvolte odkaz Instalovat **další** nástroje a funkce. Potom v Instalační program pro Visual Studio úlohy ASP.NET **a web.**
   ::: moniker-end

   Visual Studio vytvoří a otevře nový projekt.

1. V Průzkumník řešení klikněte pravým tlačítkem na složku Models (Modely) a zvolte **Add**  >  **Class (Přidat třídu).**

1. Pojmete novou `Data.cs` třídu a zvolte **Přidat.**

1. V Průzkumník řešení otevřete a na začátek souboru přidejte `Models/Data.cs` `using` následující příkaz:

    ```csharp
    using System.Threading;
    ```

1. V souboru Data.cs nahraďte následující kód:

    ```csharp
    public class Data
    {
    }
    ```

    tímto kódem:

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

1. V Průzkumník řešení *controller/HomeControllers.cs* a nahraďte následující kód:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    tímto kódem:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range=">=vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    tímto kódem:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>1. krok: Shromáždění profilačních dat

1. Nejprve v aplikaci nastavte zarážku na tento řádek kódu v `Simple` konstruktoru :

    `for (int i = 0; i < 200; i++)`

    Zarážku nastavíte kliknutím na okap vlevo od řádku kódu.

1. Dále nastavte druhou zarážku na uzavírací složenou závorku na konci `Simple` konstruktoru:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.

1. Okno **Diagnostické nástroje** je již viditelné, pokud jste ho nevy vypnuli. Pokud chcete okno znovu zobrazit, klikněte na  >  **Ladit systém Windows** Zobrazit  >  **Diagnostické nástroje**.

1. Klikněte **na Ladit** a spustit ladění  >   **(nebo spustit** na panelu nástrojů nebo **F5).**

1. Po dokončení načítání aplikace kliknutím na příslušný odkaz v horní části webové stránky spusťte nový kód.

   ::: moniker range="vs-2017"
   V Visual Studio 2017 spusťte  kód kliknutím na odkaz O aplikaci.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   V Visual Studio 2019 spusťte kód  kliknutím na odkaz Ochrana osobních údajů.
   ::: moniker-end

1. Podívejte se **na souhrnné** zobrazení diagnostických nástrojů.

1. Když je ladicí program pozastavený, povolte shromažďování dat o využití procesoru tak, že zvolíte Zaznamenat **profil procesoru** a pak otevřete kartu **Využití** PROCESORU.

     ![Diagnostické nástroje – Povolení profilace procesoru](../profiling/media/quickstart-cpu-usage-summary.png)

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

     ![Karta Využití procesoru v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí poklikejte na `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkci.

    Když na funkci dvakrát kliknete, otevře se v levém podokně zobrazení Volající/Volaný. 

    ![Zobrazení Volající/Volaný v diagnostických nástrojích](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    V tomto zobrazení se vybraná funkce zobrazí v záhlaví a v poli **Aktuální** funkce ( `ServerClass::GetNumber` v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku bylo 2220 z 2235 ms stráveno v těle funkce a zbývající čas (<20 ms) byl stráven v externím kódu s názvem touto funkcí). Skutečné hodnoty se budou lišit v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analyzujte využití paměti](../profiling/memory-usage.md)a identifikujte kritické body výkonu.
- [Podrobnější informace o](../profiling/cpu-usage.md) nástroji využití procesoru najdete v analýze využití procesoru.
- Analýza využití procesoru bez připojeného ladicího programu nebo cílení na spuštěnou aplikaci – Další informace najdete v tématu Shromažďování [dat profilace](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) bez ladění v tématu Spuštění [nástrojů pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md)s ladicím programem nebo bez něj.

## <a name="see-also"></a>Viz také

- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
