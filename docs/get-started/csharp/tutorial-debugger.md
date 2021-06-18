---
title: 'Kurz: Ladění kódu jazyka C#'
description: Seznamte se s funkcemi Visual Studio ladicího programu a zjistěte, jak spustit ladicí program, procházet kód a kontrolovat data v aplikaci jazyka C#.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 04/23/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cbc35eaabec2dae8bd8b97ba22f55a50fc436c3
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308451"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Kurz: Naučte se ladit kód jazyka C# pomocí Visual Studio

Tento článek představuje funkce ladicího Visual Studio v podrobném návodu. Pokud chcete zobrazit funkce ladicího programu na vyšší úrovni, podívejte se nejprve na [ladicí program.](../../debugger/debugger-feature-tour.md) Při ladění *aplikace obvykle znamená,* že aplikaci používáte s připojeným ladicím programem. Když to použijete, ladicí program poskytuje mnoho způsobů, jak zobrazit, co váš kód dělá, zatímco běží. Můžete si projít kód a podívat se na hodnoty uložené v proměnných, nastavit u proměnných sledujete, abyste viděli, kdy se hodnoty mění, můžete prozkoumat cestu provádění kódu, zjistit, jestli je spuštěná větev kódu atd. Pokud jste se pokusili ladit kód poprvé, možná si [](../../debugger/debugging-absolute-beginners.md) budete chtít před tímto článkem přečíst ladění pro absolutní začátečníky.

I když je ukázková aplikace C#, většina funkcí se vztahuje na jazyky C++, Visual Basic, F#, Python, JavaScript a další jazyky podporované jazykem Visual Studio (jazyk F# nepodporuje úpravy a pokračování. Jazyk F# a JavaScript nepodporují **okno Automatické** zápisy. Snímky obrazovky jsou v jazyce C#.

V tomto kurzu:

> [!div class="checklist"]
> * Spusťte ladicí program a stiskněte zarážky.
> * Naučte se příkazy pro krokování kódu v ladicím programu.
> * Kontrola proměnných v datových tipech a oknech ladicího programu
> * Prozkoumání zásobníku volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou Visual Studio 2019 a úlohu vývoj pro **různé platformy v .NET Core.**

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou Visual Studio 2017 a úlohu vývoj pro **různé platformy v .NET Core.**

::: moniker-end

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio 2022 Preview, přejděte na stránku [stahování Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) a nainstalujte si ji zdarma.

::: moniker-end

Pokud potřebujete tuto úlohu nainstalovat, ale Visual Studio, přejděte na **Nástroje** Získat nástroje a funkce. Otevře se  >  Instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt konzolové aplikace .NET Core. Typ projektu se dodává se všemi soubory šablony, které budete potřebovat, ještě než budete něco přidávat.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

3. V dialogovém **okně Nový** projekt v levém podokně rozbalte **C#** a pak zvolte **.NET Core.** V prostředním podokně zvolte **Konzolová aplikace (.NET Core).** Pak projekt *pojmechte get-started-debugging*.

     Pokud šablonu projektu Konzolová aplikace **(.NET Core)** nevidíte, zvolte odkaz Otevřít **Instalační program pro Visual Studio** v levém podokně dialogového okna **Nový** projekt.

     Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Pokud úvodní okno není otevřené, zvolte **Úvodní** > **okno souboru**.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

1. V **okně Vytvořit nový projekt** zadejte nebo zadejte *do* vyhledávacího pole konzolu. Potom v seznamu Jazyk zvolte **C#** a pak **v** seznamu Platforma zvolte Windows. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Konzolová aplikace** pro .NET Core a pak zvolte **Další.**

   ![Zvolte šablonu jazyka C# pro konzolovou aplikaci.](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Pokud šablonu Konzolová **aplikace nevidíte,** můžete ji nainstalovat z **okna Vytvořit nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce. Potom v části Instalační program pro Visual Studio úlohu **Vývoj pro různé platformy v .NET Core.**

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole Project name (Název **projektu)** zadejte nebo zadejte *GetStartedDebugging.* Pak zvolte **Další.**

1. Zvolte doporučené cílové rozhraní (.NET Core 3.1) nebo .NET 5 a pak zvolte **Vytvořit.**

   Visual Studio nový projekt otevřete.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *souboru Program.cs* nahraďte veškerý výchozí kód následujícím kódem:

    ```csharp
    using System;
    class ArrayExample
    {
        static void Main()
        {
            char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
            string name = "";
            int[] a = new int[10];
            for (int i = 0; i < letters.Length; i++)
            {
                name += letters[i];
                a[i] = i + 1;
                SendMessage(name, a[i]);
            }
            Console.ReadKey();
        }
        static void SendMessage(string name, int msg)
        {
            Console.WriteLine("Hello, " + name + "! Count to " + msg);
        }
    }
    ```

## <a name="start-the-debugger"></a>Spusťte ladicí program!

1. Na panelu nástrojů ladění **>** klávesu **F5** ( ![](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") Spustit ladění ) nebo tlačítko Spustit ladění. 

     **F5** spustí aplikaci s ladicím programem připojeným k procesu aplikace, ale teď jsme ještě neudělali nic zvláštního pro prozkoumání kódu. Aplikace se tedy načte a zobrazí se výstup konzoly.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     V tomto kurzu se na tuto aplikaci podíváme blíže pomocí ladicího programu a podíváme se na funkce ladicího programu.

2. Zastavte ladicí program stisknutím červeného tlačítka ![Zastavit ladění](../../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") (**Shift**  +  **F5**).

3. V okně konzoly stisknutím klávesy zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavení zarážky a spuštění ladicího programu

1. Ve `for` smyčce funkce nastavte zarážku kliknutím na `Main` levý okraj následujícího řádku kódu:

    `name += letters[i];`

    Zarážka s ![červeným kruhem](../../debugger/media/dbg-breakpoint.png "Bodu") se zobrazí tam, kde nastavíte zarážku.

    Zarážky jsou jednou z nejzákladnějších a nejzákladnějších funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte **klávesu F5** nebo **tlačítko** Spustit ladění Spustit ladění ![,](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění")spustí se aplikace a ladicí program se spustí na řádku kódu, kde nastavíte zarážku.

    ![Nastavení a přístup k zarážce](../csharp/media/get-started-set-breakpoint.gif)

    Žlutá šipka představuje příkaz, na kterém se ladicí program pozastavil, což také pozastaví provádění aplikace ve stejném bodě (tento příkaz se ještě nespouštěl).

     Pokud aplikace ještě není spuštěná, **F5** spustí ladicí program a zastaví se na první zarážce. V opačném **případě bude F5** pokračovat ve spouštění aplikace až k další zarážce.

    Zarážky jsou užitečnou funkcí, pokud znáte řádek kódu nebo část kódu, kterou chcete podrobně prozkoumat. Informace o různých typech zarážek, které můžete nastavit, například podmíněné zarážky, najdete v tématu [Použití zarážek](../../debugger/using-breakpoints.md).

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Procházení kódu a kontrola dat pomocí datových tipů

Většinou tady používáme klávesové zkratky, protože je to dobrý způsob, jak rychle spustit aplikaci v ladicím programu (ekvivalentní příkazy, jako jsou příkazy nabídky, se zobrazují v závorkách).

1. Při pozastavení příkazu najeďte myší na proměnnou a zobrazí se výchozí hodnota, hodnota prvního prvku v `name += letters[i]` `letters` poli `char[10]` .

     Funkce, které umožňují kontrolovat proměnné, jsou jednou z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to udělat. Často se při pokusu o ladění problému pokoušíte zjistit, jestli proměnné ukládají hodnoty, které očekáváte, že budou mít v konkrétním čase.

1. Rozbalte `letters` proměnnou a zobrazte její vlastnosti, které zahrnují všechny prvky, které proměnná obsahuje.

     ![Snímek obrazovky Visual Studio Debugger se zvýrazněnou volbou name+= letters[I] a rozevíracím seznamem zobrazující prvky v poli písmen](../csharp/media/get-started-view-data-tip.png)

1. Potom najeďte myší na proměnnou a zobrazí `name` se její aktuální hodnota – prázdný řetězec.

1. Dvakrát **stiskněte klávesu F10** **(nebo > Krok** přes ) a pak znovu stiskněte klávesu `SendMessage` **F10.**

     F10 přejde ladicí program na další příkaz bez krokování do funkcí nebo metod v kódu aplikace (kód se stále provádí). Stisknutím klávesy F10 při volání metody jsme přeskočili kód implementace pro (což nás možná zrovna `SendMessage` `SendMessage` nezajímá).

1. Několikrát **stiskněte klávesu F10** (nebo Ladit krok přes ), aby se několikrát iteroval smyčkou, znovu se pozasouvá na zarážku a pokaždé na proměnnou najede myší a zkontroluje se její   >   `for` `name` hodnota.

     ![Animovaný snímek obrazovky Visual Studio Debugger znázorňující účinek stisknutí klávesy F10 na "Krok přes" a iterace smyčkou během ladění.](../csharp/media/get-started-data-tip.gif)

     Hodnota proměnné se mění při každé iteraci smyčky a zobrazuje hodnoty `for` , pak , a tak `f` `fr` `fre` dále. Pokud chcete v tomto scénáři ladicí program projít smyčkou rychleji, můžete místo dalšího příkazu stisknout **klávesu F5** (nebo vybrat Pokračovat v ladění). Tím přejdete na  >  zarážku.

     Při ladění často potřebujete rychlý způsob, jak zkontrolovat hodnoty vlastností proměnných, abyste viděli, jestli ukládají hodnoty, které očekáváte, že budou uloženy, a datové tipy jsou dobrým způsobem, jak to udělat.

1. Pozastavené ve smyčce v metodě stiskněte `for` `Main` klávesu **F11** (nebo zvolte Ladit **> Krokovat s** krokem do ), dokud se nepozastavíte při volání `SendMessage` metody.

     Měli byste být na tomto řádku kódu:

     `SendMessage(name, a[i]);`

1. Dalším **stisknutím klávesy F11** zakrokte do `SendMessage` metody .

     Žlutý ukazatel přejde do `SendMessage` metody .

     ![Použití klávesy F11 ke kroku do kódu](../csharp/media/get-started-f11.png "F10 Krokovat s vnořením")

     F11 je příkaz **Step Into (Krokovat** s krokem do) a postupuje provádění aplikace po jednom příkazu. F11 je dobrý způsob, jak podrobněji prozkoumat tok provádění. Ve výchozím nastavení ladicí program přeskočí kód bez uživatele (pokud chcete další podrobnosti, podívejte se [na Pouze můj kód](../../debugger/just-my-code.md)).

     Řekněme, že jste skončili s prozkoumáním metody a chcete se z metody dostat, ale `SendMessage` zůstat v ladicím programu. Můžete to provést pomocí příkazu **Krok ven.**

1. Stiskněte **Klávesu Shift**  +  **F11** (nebo > Krok **ven**).

     Tento příkaz pokračuje v provádění aplikace (a pokračuje v ladicím programu), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste se vrátit do `for` smyčky v `Main` metodě, pozastavena při `SendMessage` volání metody. Další informace o různých způsobech, jak přesouvat kód, naleznete v tématu [Navigace v kódu v ladicím programu](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Procházení kódu pomocí rutiny Run to Click

1. Stisknutím klávesy **F5** přejděte znovu ke zarážce.

1. V editoru kódu se posuňte dolů a najeďte na `Console.WriteLine` metodu v `SendMessage` metodě až do ![kliknutí](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") na tlačítko zeleného **běhu do kliknutí** na tlačítko se zobrazí vlevo. V popisu tlačítka se zobrazí text spustit provádění na tomto místě.

     ![Použití funkce spustit pro kliknutí](../csharp/media/get-started-run-to-click.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **Spustit pro kliknutí** je v nástroji nového [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] . (Pokud nevidíte zelenou šipku tlačítka, použijte klávesu **F11** v tomto příkladu, aby se ladicí program napředal na správné místo.)

2. Kliknutím na tlačítko **Spustit pro** klikněte na tlačítko ![Spustit](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Ladicí program přejde do `Console.WriteLine` metody.

    Použití tohoto tlačítka je podobné nastavení dočasné zarážky. **Možnost spustit pro** je užitečná pro rychlé seznámení v rámci viditelné oblasti kódu aplikace (můžete kliknout na libovolný otevřený soubor).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**).

Po stisknutí tlačítka **restartovat** ušetří čas oproti zastavování aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážce, která je dosaženo spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili uvnitř `for` smyčky.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken automatické hodnoty a místní hodnoty

1. Podívejte se na okno **Automatické** hodnoty v dolní části editoru kódu.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu, a to volbou **ladit**  >  **okna**  >  **Automatické** hodnoty.

    V okně **Automatické** hodnoty vidíte proměnné a jejich aktuální hodnotu. Okno **Automatické** hodnoty zobrazuje všechny proměnné, které se používají na aktuálním řádku nebo na předchozím řádku (podívejte se na dokumentaci pro specifické chování jazyka).

1. Pak v okně **místní** hodnoty se podívejte na kartu vedle okna **Automatické** hodnoty.

1. Rozbalte `letters` proměnnou pro zobrazení prvků, které obsahuje.

     ![Kontrola proměnných v okně místních hodnot](../csharp/media/get-started-locals-window.png "Okno místních hodnot")

    V okně **místní** hodnoty se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), tj. aktuálním kontextem spuštění.

## <a name="set-a-watch"></a>Nastavení kukátka

1. V hlavním okně editoru kódu klikněte pravým tlačítkem na `name` proměnnou a vyberte **Přidat kukátko**.

    V dolní části editoru kódu se otevře okno **kukátko** . Okno **kukátka** můžete použít k určení proměnné (nebo výrazu), pro kterou chcete zachovat oči.

    Teď máte pro proměnnou nastavenou kukátko `name` a při procházení ladicího programu můžete zobrazit jeho změnu hodnoty. Na rozdíl od ostatních oken proměnných se v okně **kukátka** vždy zobrazuje proměnné, které sledujete (v případě nedostatku rozsahu jsou šedé).

## <a name="examine-the-call-stack"></a>Kontrola zásobníku volání

1. Při pozastavení ve `for` smyčce klikněte na okno **zásobník volání** , které je ve výchozím nastavení otevřené v pravém dolním podokně.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu výběrem možnosti **ladit**  >    >  **zásobník volání** systému Windows.

2. Klikněte několikrát na klávesu **F11** , dokud se nezobrazí pozastavení ladicího programu v `SendMessage` metodě. Podívejte se do okna **zásobník volání** .

    ![Kontrola zásobníku volání](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    Okno **zásobník volání** zobrazuje pořadí, ve kterém jsou metody a funkce volány. V horním řádku se zobrazuje aktuální funkce ( `SendMessage` metoda v této aplikaci). Druhý řádek ukazuje, který `SendMessage` byl volán z `Main` metody a tak dále.

   > [!NOTE]
   > Okno **zásobník volání** je podobné perspektivě ladění v některých prostředích, jako je například zatmění.

    Zásobník volání je dobrým způsobem, jak prostudovat a pochopit tok spuštění aplikace.

    Dvakrát klikněte na řádek kódu, abyste se mohli podívat na zdrojový kód a zároveň změnit aktuální rozsah, který je kontrolován ladicím programem. Tato akce nepřejde do ladicího programu.

    Můžete také použít nabídky kliknutím pravým tlačítkem z okna **zásobník volání** k provedení dalších akcí. Můžete například vložit zarážky do určených funkcí, pokračovat v ladicím programu pomocí funkce **Run to Cursor** a přejít na zdrojový kód. Další informace naleznete v tématu [How to: Prohlédněte si zásobník volání](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku spuštění

1. Stisknutím klávesy **F11** dvakrát spusťte `Console.WriteLine` metodu.

1. Když je ladicí program pozastaven ve `SendMessage` volání metody, použijte myš k navýšení žluté šipky (ukazatel spuštění) vlevo a přesuňte žlutou šipku o jeden řádek nahoru, zpět na `Console.WriteLine` .

1. Stiskněte klávesu **F11**.

    Ladicí program znovu spustí `Console.WriteLine` metodu (uvidíte ji ve výstupu okna konzoly).

    Změnou toku spuštění můžete provádět akce, jako je například testování různých cest spuštění kódu nebo opětovné spuštění kódu bez restartování ladicího programu.

    > [!WARNING]
    > Tuto funkci často potřebujete pečlivě a v popisu se zobrazí upozornění. Můžou se zobrazit i další upozornění. Přesunutí ukazatele nemůže vrátit aplikaci do dřívějšího stavu aplikace.

1. Stisknutím klávesy **F5** pokračujte v používání aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Můžete chtít získat nejdůležitější pohled na funkce ladicího programu společně s odkazy na Další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
