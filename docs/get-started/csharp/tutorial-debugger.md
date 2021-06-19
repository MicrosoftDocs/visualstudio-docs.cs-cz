---
title: 'Kurz: ladění kódu C#'
description: Přečtěte si o funkcích ladicího programu sady Visual Studio a o tom, jak spustit ladicí program, krokovat kód a kontrolovat data v aplikaci C#.
ms.custom: debug-experiment, vs-acquisition, get-started
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
ms.openlocfilehash: 8fe0c698ce1263713a758bd98fba49433b3ff511
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390278"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Kurz: Naučte se ladit kód v jazyce C# pomocí sady Visual Studio

V tomto článku se seznámíte s funkcemi ladicího programu sady Visual Studio v podrobném podrobném návodu. Pokud chcete zobrazit vyšší úroveň funkcí ladicího programu, podívejte [se na téma první pohled na ladicí program](../../debugger/debugger-feature-tour.md). Při *ladění aplikace* obvykle znamená, že máte spuštěnou aplikaci s připojeným ladicím programem. Když to uděláte, ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód při spuštění dělá. Můžete krokovat kód a prohlédnout si hodnoty uložené v proměnných, můžete nastavit hodinky pro proměnné, abyste viděli, kdy se hodnoty mění, můžete zkontrolovat cestu spuštění kódu, zjistit, zda je spuštěna větev kódu a tak dále. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprosto začátečníky](../../debugger/debugging-absolute-beginners.md) .

I když je ukázková aplikace C#, většina funkcí platí pro C++, Visual Basic, F #, Python, JavaScript a další jazyky, které podporuje Visual Studio (F # nepodporuje funkci upravit a pokračovat. F # a JavaScript nepodporují okno **Automatické** hodnoty). Snímky obrazovky jsou v jazyce C#.

V tomto kurzu:

> [!div class="checklist"]
> * Spusťte ladicí program a zarážky volání.
> * Přečtěte si příkazy pro krokování kódu v ladicím programu
> * Kontrola proměnných v tipech k datům a v oknech ladicího programu
> * Kontrola zásobníku volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou aplikaci Visual Studio 2019 a úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou aplikaci Visual Studio 2017 a úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste ještě nenainstalovali Visual Studio 2022 Preview, nainstalujte ho zdarma na stránku [Visual studio 2022 Preview ke stažení](https://visualstudio.microsoft.com/vs/preview/vs2022) .

::: moniker-end

Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt konzolové aplikace .NET Core. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **C#** a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)**. Potom pojmenujte projekt *Get-Started-Debugging*.

     Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , vyberte odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** .

     Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Pokud okno Start není otevřeno, klikněte **na tlačítko** > **Start okna**.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Potom v seznamu jazyk vyberte **C#** a pak v seznamu platforma zvolte **Windows** . 

   Až použijete filtry jazyka a platformy, zvolte šablonu **Konzolová aplikace** pro .NET Core a pak zvolte **Další**.

   ![Zvolit šablonu C# pro konzolovou aplikaci](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *GetStartedDebugging* do pole **název projektu** . Pak klikněte na tlačítko **Další**.

1. Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *programu program. cs* místo toho nahraďte veškerý výchozí kód následujícím kódem:

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

## <a name="start-the-debugger"></a>Spusťte ladicí program.

1. Stiskněte klávesu **F5** (**ladění > spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../../debugger/media/dbg-tour-start-debugging.png "Spuštění ladění") na panelu nástrojů ladění.

     **F5** spustí aplikaci s ladicím programem připojeným k procesu aplikace, ale nyní jsme ještě neudělali cokoli, co by bylo možné zkontrolovat kód. Takže se aplikace jenom načte a zobrazí se výstup z konzoly.

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

     V tomto kurzu se podíváme na tuto aplikaci s použitím ladicího programu a zjistíme, jak se podívat na funkce ladicího programu.

2. Ukončete ladicí program stisknutím tlačítka červené zastavení ![Zastavit ladění](../../debugger/media/dbg-tour-stop-debugging.png "Zastavení ladění") (**SHIFT**  +  **F5**).

3. V okně konzoly stisknutím klávesy zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavit zarážku a spustit ladicí program

1. Ve `for` smyčce `Main` funkce nastavte zarážku kliknutím na levý okraj následujícího řádku kódu:

    `name += letters[i];`

    Zarážka ![červeného kruhu se](../../debugger/media/dbg-breakpoint.png "Zarážka") zobrazí tam, kde jste nastavili zarážku.

    Zarážky jsou jednou ze základních a základních funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../../debugger/media/dbg-tour-start-debugging.png "Spuštění ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde jste nastavili zarážku.

    ![Nastavení a volání zarážky](../csharp/media/get-started-set-breakpoint.gif)

    Žlutá šipka představuje příkaz, na kterém je ladicí program pozastaven, což také pozastavuje spuštění aplikace ve stejném bodě (Tento příkaz ještě nebyl proveden).

     Pokud aplikace ještě není spuštěná, spustí **F5** ladicí program a zastaví se na první zarážce. V opačném případě **F5** pokračuje v běhu aplikace na další zarážku.

    Zarážky jsou užitečnou funkcí, když znáte řádek kódu nebo oddíl kódu, který chcete podrobně prošetřit. Informace o různých typech zarážek, které lze nastavit, například podmíněné zarážky, naleznete v tématu [using zarážek](../../debugger/using-breakpoints.md).

## <a name="navigate-code-and-inspect-data-using-data-tips"></a>Navigace v kódu a kontrola dat pomocí tipů k datům

Většinou používáme klávesové zkratky, protože je dobrým způsobem, jak rychle rychle spustit aplikaci v ladicím programu (ekvivalentní příkazy, jako jsou příkazy nabídky, se zobrazují v závorkách).

1. Při pozastavení `name += letters[i]` příkazu, najeďte myší na `letters` proměnnou a vidíte její výchozí hodnotu, hodnotu prvního prvku v poli `char[10]` .

     Funkce, které umožňují kontrolu proměnných, jsou jedním z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to provést. Pokud se při pokusu o ladění problému často pokusíte zjistit, zda proměnné ukládají hodnoty, které mají být v určitou dobu k dispozici.

1. Rozbalením `letters` proměnné zobrazíte její vlastnosti, které zahrnují všechny prvky, které proměnná obsahuje.

     ![Snímek obrazovky ladicího programu sady Visual Studio se zvýrazněným příkazem název + = písmena [I] a rozevírací seznam zobrazující prvky v poli dopisy](../csharp/media/get-started-view-data-tip.png)

1. Potom najeďte myší na `name` proměnnou a uvidíte její aktuální hodnotu, prázdný řetězec.

1. Stiskněte **F10** (nebo zvolte možnost **ladění > krokovat** s), abyste mohli přejít ke `SendMessage` volání metody, a pak stiskněte **F10** ještě jednou.

     F10 posune ladicí program na další příkaz bez krokování do funkcí nebo metod v kódu aplikace (kód se pořád spustí). Stisknutím klávesy F10 ve `SendMessage` volání metody jsme přeskočili kód implementace pro `SendMessage` (což možná není zajímatme hned teď).

1. Několikrát stisknutím klávesy **F10** (nebo **ladění**  >  **krok za běhu**) několikrát projdete `for` smyčkou, přechodem znovu na zarážku a pokaždé, když se podíváte na `name` proměnnou pokaždé, aby zkontrolovala její hodnotu.

     ![Animovaný snímek obrazovky ladicího programu sady Visual Studio znázorňující efekt stisknutí klávesy F10 ke krokování a iterování prostřednictvím smyčky během ladění.](../csharp/media/get-started-data-tip.gif)

     Hodnota proměnné se mění v každé iteraci `for` smyčky, zobrazuje hodnoty `f` , potom `fr` , `fre` a tak dále. Chcete-li ladit ladicí program přes smyčku rychleji v tomto scénáři, můžete stisknout klávesu **F5** (nebo zvolit možnost pokračovat v **ladění**  >  ), která vás provede přechodem na zarážku namísto dalšího příkazu.

     Při ladění budete často potřebovat rychlý způsob kontroly hodnot vlastností u proměnných, abyste viděli, zda ukládají hodnoty, které očekáváte pro uložení, a tipy k datům jsou vhodným způsobem.

1. I když se stále pozastaví `for` smyčka v `Main` metodě, stiskněte klávesu **F11** (nebo zvolte možnost **ladit > krokovat** s), dokud nezastavíte `SendMessage` volání metody.

     Měli byste být na tomto řádku kódu:

     `SendMessage(name, a[i]);`

1. Stiskněte klávesu **F11** ještě jednou pro krokování do `SendMessage` metody.

     Žlutý ukazatel se přesune do `SendMessage` metody.

     ![Krokovat s vnořením kódu pomocí klávesy F11](../csharp/media/get-started-f11.png "F10 Step Into")

     Klávesa F11 je **Krok do** příkazu a aplikace pokračuje v jednom příkazu v jednom okamžiku. Klávesa F11 je dobrým způsobem, jak prostudovat tok spouštění v nejpodrobnějším podrobnostech. Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../../debugger/just-my-code.md)).

     Řekněme, že jste dokončili zkoumání `SendMessage` metody a chcete získat z metody, ale zůstat v ladicím programu. To můžete provést pomocí příkazu **Krok ven** .

1. Stiskněte **SHIFT**  +  **F11** (nebo **ladění > krokovat**).

     Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste být zpět ve `for` smyčce v `Main` metodě , pozastaveno při `SendMessage` volání metody. Další informace o různých způsobech procházení kódu najdete v tématu [Procházení kódu v ladicím programu.](../../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Navigace v kódu pomocí příkazu Run to Click

1. Stisknutím **klávesy F5** znovu přejdete na zarážku.

1. V editoru kódu se posuňte dolů a najeďte myší na metodu v metodě, dokud se na levé straně nezobrazí zelené tlačítko Run to Click Run to Click (Spustit a `Console.WriteLine` `SendMessage` kliknout).  ![](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") Popis tlačítka zobrazuje "Run execution to here" (Spustit provádění sem).

     ![Použití funkce Spustit do kliknutí](../csharp/media/get-started-run-to-click.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **Run to Click** (Spustit do kliknutí) je v systému [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] nové. (Pokud nevidíte zelené tlačítko se šipkou, pomocí **klávesy F11** v tomto příkladu přesuňte ladicí program na správné místo.)

2. Klikněte na **tlačítko Run to Click (Spustit do kliknutí)** Run to Click ![(Spustit do kliknutí) a klikněte na .](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Ladicí program přejde k `Console.WriteLine` metodě .

    Použití tohoto tlačítka se podobá nastavení dočasné zarážky. **Spuštění do kliknutí** je vhod, když se chcete rychle se dostat do viditelné oblasti kódu aplikace (můžete kliknout do libovolného otevřeného souboru).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Na panelu **nástrojů** ![ladění klikněte](../../debugger/media/dbg-tour-restart.png "RestartApp") na tlačítko Restart Restart App (Restartovat aplikaci) (**Ctrl**  +  **Shift**  +  **F5**).

Když **stisknete Restart (Restartovat),** ušetříte tím čas místo zastavení aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážce, ke které došlo spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili uvnitř `for` smyčky.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken Automatické hodnoty a Místní hodnoty

1. Podívejte se **na okno Automatické** funkce v dolní části editoru kódu.

    Pokud je zavřen, otevřete ho při pozastavení v ladicím programu výběrem možnosti  >  **Ladit automatické funkce**  >  **Windows.**

    V okně **Automatické** hodnoty se zobrazí proměnné a jejich aktuální hodnota. V **okně Automatické** hodnoty se zobrazí všechny proměnné použité na aktuálním řádku nebo na předchozím řádku (zkontrolujte chování specifické pro jazyk v dokumentaci).

1. Pak se podívejte na **okno Místní** hodnoty na kartě vedle okna **Automatické** hodnoty.

1. Rozbalte `letters` proměnnou a zobrazte prvky, které obsahuje.

     ![Kontrola proměnných v okně Místní hodnoty](../csharp/media/get-started-locals-window.png "Místní hodnoty – okno")

    V **okně** Místní hodnoty se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), to znamená aktuální kontext spuštění.

## <a name="set-a-watch"></a>Nastavení hodinek

1. V hlavním okně editoru kódu klikněte pravým tlačítkem na proměnnou a `name` zvolte Přidat watch **(Přidat hodinku).**

    V dolní části editoru kódu se otevře okno Watch **(Sledování).** V okně **Watch** (Sledování) můžete zadat proměnnou (nebo výraz), kterou chcete sledovat.

    Teď máte pro proměnnou nastavenou hodinku a při pohybu v ladicím programu můžete vidět její `name` změnu hodnoty. Na rozdíl od ostatních oken proměnných se v okně Watch vždy zobrazují proměnné, které sledujete (když jsou mimo rozsah, jsou zašedné). 

## <a name="examine-the-call-stack"></a>Prozkoumání zásobníku volání

1. Pozastavené ve smyčce klikněte na okno Zásobník volání, které je ve výchozím nastavení `for` otevřené v pravém dolním podokně. 

    Pokud je uzavřený, otevřete ho při pozastavení v ladicím programu výběrem možnosti **Ladit** zásobník volání  >    >  **systému** Windows.

2. Několikrát **klikněte na F11,** dokud v metodě neuvidíte pozastavení ladicího `SendMessage` programu. Podívejte se na **okno Zásobník volání.**

    ![Prozkoumání zásobníku volání](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    V **okně Zásobník** volání se zobrazuje pořadí, ve kterém se volají metody a funkce. Horní řádek zobrazuje aktuální funkci `SendMessage` (metodu v této aplikaci). Druhý řádek ukazuje, `SendMessage` že byl volán z `Main` metody a tak dále.

   > [!NOTE]
   > Okno **Zásobník volání** je podobné perspektivě ladění v některých prostředích ID, jako je Eclipse.

    Zásobník volání je dobrým způsobem, jak prozkoumat a pochopit tok provádění aplikace.

    Dvojitým kliknutím na řádek kódu se můžete podívat na zdrojový kód a tím se také změní aktuální obor prověřovaný ladicím programem. Tato akce neposoudí ladicí program.

    Můžete také použít nabídky po kliknutí pravým tlačítkem v okně Call Stack (Zásobník **volání)** a provést další věci. Můžete například vložit zarážky do zadaných funkcí, pomocí příkazu **Spustit** na kurzor přejít k ladicímu programu a prozkoumat zdrojový kód. Další informace najdete v tématu [Postupy: Prozkoumání zásobníku volání](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku provádění

1. Spusťte metodu tak, že dvakrát stisknete klávesu **F11.** `Console.WriteLine`

1. Když je ladicí program pozastavený ve volání metody, pomocí myši uchopte žlutou šipku (ukazatel provádění) vlevo a přesuňte žlutou šipku o jeden řádek nahoru `SendMessage` zpět na `Console.WriteLine` .

1. Stiskněte **klávesu F11**.

    Ladicí program znovu spustí `Console.WriteLine` metodu (uvidíte ji ve výstupu okna konzoly).

    Změnou toku provádění můžete například testovat různé cesty provádění kódu nebo znovu spustit kód bez restartování ladicího programu.

    > [!WARNING]
    > S touto funkcí často musíte být opatrní a v popisu se zobrazí upozornění. Může se zobrazit i další upozornění. Přesunutí ukazatele nemůže vrátit aplikaci do dřívějšího stavu aplikace.

1. Stisknutím **klávesy F5** pokračujte v provozu aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, procházet kód a kontrolovat proměnné. Možná budete chtít získat podrobnější pohled na funkce ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
