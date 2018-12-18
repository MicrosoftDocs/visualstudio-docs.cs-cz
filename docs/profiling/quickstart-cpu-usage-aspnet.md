---
title: Analýza dat o využití procesoru (ASP.NET)
description: Měřit výkon aplikace v aplikacích ASP.NET pomocí diagnostického nástroje využití CPU
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
- aspnet
ms.openlocfilehash: 4d4f2382814cabbd26f93db27301ffa9b8d1c658
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42624106"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Rychlý start: Analýza dat o využití procesoru v aplikaci Visual Studio (ASP.NET)

Visual Studio poskytuje mnoha výkonným funkcím, které vám pomůžou analyzovat problémy s výkonem v aplikaci. Toto téma poskytuje rychlý způsob, jak Seznamte se s některými základními funkcemi. Tady podíváme na nástroj, který umožňuje identifikovat kritické body výkonu kvůli vysokému využití procesoru. Diagnostické nástroje jsou podporované pro vývoj rozhraní .NET v sadě Visual Studio, včetně ASP.NET, nativního vývoje a vývoje v jazyce C++.

Diagnostické centrum nabízí řadu dalších možností, jak spustit a spravovat diagnostické relace. Pokud **využití procesoru** nástroj je zde popsáno, vám neuděluje data, která budete potřebovat, [jiných nástrojů pro profilaci](../profiling/profiling-feature-tour.md) poskytují různé druhy informací, které může být pro vás užitečné. V řadě případů může být kritickým bodem aplikace něco jiného než procesor, třeba paměť, vykreslování uživatelského rozhraní nebo dlouhá odezva síťového požadavku.

Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno). Ve Windows 7 a novější, můžete použít nástroj a dodatečně [Profiler výkonu](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Vytvoření projektu

1. V sadě Visual Studio, zvolte **souboru** > **nový projekt**.

1. V části **Visual C#**, zvolte **webové**a potom v prostředním podokně vyberte **webová aplikace ASP.NET (.NET Framework)**.

    Pokud se nezobrazí **webová aplikace ASP.NET** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte **vývoj pro ASP.NET a web** úloh, klikněte na tlačítko **změnit**.

1. Zadejte název, například **MyProfilingApp_MVC** a klikněte na tlačítko **OK**.

1. V dialogovém okně, které se zobrazí, zvolte **MVC** v prostředním podokně a pak klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt. Průzkumník řešení (pravé podokno) zobrazuje soubory projektu.

1. V Průzkumníku řešení klikněte pravým tlačítkem na složku modely a zvolte **přidat** > **třídy**.

1. Pojmenujte novou třídu `Data.cs` a zvolte **přidat**.

1. V Průzkumníku řešení otevřete `Models/Data.cs` a přidejte následující `using` příkaz do horní části souboru:

    ```csharp
    using System.Threading;
    ```

1. V Data.cs nahraďte následujícím kódem:

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

1. V Průzkumníku řešení otevřete *Controller/HomeControllers.cs*a nahraďte následujícím kódem:

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

##  <a name="step-1-collect-profiling-data"></a>Krok 1: Shromáždění profilačních dat 
  
1.  Nejprve nastavte zarážku v aplikaci na tomto řádku kódu v `Simple` konstruktor:

    `for (int i = 0; i < 200; i++)`

    Po kliknutí na ovládací prvek vlevo od řádku kódu, nastavte zarážku.

1.  Dále nastavte zarážku druhý na pravou složenou závorku na konci `Simple` konstruktor:

     ![Nastavení zarážek pro profilaci](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Nastavením dvou zarážek omezíte shromažďování dat jenom na analyzovanou část kódu.
  
1.  **Diagnostické nástroje** okno již viditelné, pokud jste ji vypnuli. Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

1.  Klikněte na tlačítko **ladění** > **spustit ladění** (nebo **Start** na panelu nástrojů nebo **F5**).

1.  Po dokončení načítání aplikace klikněte na tlačítko **o** odkazu v horní části webové stránky spustit nový kód.

1.  Podívejte se na **Souhrn** zobrazí diagnostické nástroje.

1.  Když ladicí program je pozastavený, Povolit shromažďování dat o využití procesoru výběrem **profil CPU záznam**a pak otevřete **využití procesoru** kartu.

     ![Diagnostické nástroje povolit profilaci procesoru](../profiling/media/quickstart-cpu-usage-summary.png)

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

     ![Karta Diagnostika nástroje procesoru využití](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Funkce jsou seřazené od nejvíce pracujících po nejméně pracující (nejsou seřazené podle pořadí, v jakém byly volány). Pomůže vám to rychle identifikovat funkce, které běží nejdéle.

2. V seznamu funkcí dvakrát klikněte `MyProfilingApp_MVC.Models.ServerClass::GetNumber` funkce.

    Když dvakrát kliknete funkce **volající/volaný** zobrazení se otevře v levém podokně. 

    ![Zobrazení volající/volaný nástroje diagnostiky](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    V tomto zobrazení vybrané funkce se zobrazí v záhlaví a **aktuální funkci** pole (`ServerClass::GetNumber`, v tomto příkladu). Funkce, která volala aktuální funkci, se zobrazí vlevo v části **Volající funkce** a všechny funkce volané aktuální funkcí se zobrazí vpravo v poli **Volané funkce**. (Pokud chcete aktuální funkci změnit, vyberte libovolné pole.)

    V tomto zobrazení vidíte celkový čas (ms) a procento z celkové doby spuštění aplikace, kterou funkce potřebovala k dokončení.

    **Tělo funkce** také zobrazuje celkovou dobu (a procento času) spotřebovanou tělem funkce, ale bez doby spotřebované volajícími a volanými funkcemi. (Na tomto obrázku 2220 mimo 2235 ms byly trvání tělo funkce a zbývající dobu (< 20 ms) se využilo na externí kód volaných touto funkcí). Skutečné hodnoty se liší v závislosti na vašem prostředí.

    > [!TIP]
    > Vysoké hodnoty v **těle funkce** pravděpodobně znamenají kritické místo výkonu samotné funkce.

## <a name="next-steps"></a>Další kroky

- [Analýza využití paměti](../profiling/memory-usage.md)identifikovat kritické body výkonu.
- [Analýza využití procesoru](../profiling/cpu-usage.md) další podrobné informace o nástroj využití procesoru.
- Analýza využití procesoru bez připojen jiný ladicí program, nebo cílení na spuštění aplikace – Další informace najdete v tématu [shromažďovat data profilování bez ladění](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) v [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Viz také:  

 [Profilace v sadě Visual Studio](../profiling/index.md)  
 [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)
