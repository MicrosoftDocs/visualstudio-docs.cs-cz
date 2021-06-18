---
title: 'Kurz: Ladění Visual Basic kódu'
description: Seznamte se s funkcemi Visual Studio ladicího programu a zjistěte, jak spustit ladicí program, procházet kód a kontrolovat data v Visual Basic aplikaci.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/03/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- VB
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42dd3c6b7301162e239bc87764056fdda2d08413
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308412"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Kurz: Naučte se ladit Visual Basic kódu pomocí Visual Studio

Tento článek představuje funkce ladicího Visual Studio v podrobném návodu. Pokud chcete zobrazit funkce ladicího programu na vyšší úrovni, podívejte se nejprve na [ladicí program.](../../debugger/debugger-feature-tour.md) Při ladění *aplikace obvykle znamená,* že aplikaci používáte s připojeným ladicím programem. Když to použijete, ladicí program poskytuje mnoho způsobů, jak zobrazit, co váš kód dělá, zatímco běží. Můžete si projít kód a podívat se na hodnoty uložené v proměnných, nastavit u proměnných sledujete, abyste viděli, kdy se hodnoty mění, můžete prozkoumat cestu provádění kódu, zjistit, jestli je spuštěná větev kódu atd. Pokud jste se pokusili ladit kód poprvé, možná si [](../../debugger/debugging-absolute-beginners.md) budete chtít před tímto článkem přečíst ladění pro absolutní začátečníky.

I když je ukázková aplikace Visual Basic, většina funkcí se vztahuje na C#, C++, F#, Python, JavaScript a další jazyky podporované jazykem Visual Studio (jazyk F# nepodporuje příkaz Edit-and-continue. Jazyk F# a JavaScript nepodporují **okno Automatické** zápisy. Snímky obrazovky jsou v Visual Basic.

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

3. V dialogovém **okně Nový** projekt v levém podokně rozbalte **Visual Basic** a pak zvolte **.NET Core**. V prostředním podokně zvolte **Konzolová aplikace (.NET Core).** Pak projekt *pojmechte get-started-debugging*.

     Pokud šablonu projektu Konzolová aplikace **(.NET Core)** nevidíte, zvolte odkaz Otevřít **Instalační program pro Visual Studio** v levém podokně dialogového okna **Nový** projekt.

     Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoj pro různé platformy** v .NET Core a pak zvolte **Upravit.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Pokud úvodní okno není otevřené, zvolte **Úvodní** > **okno souboru**.

1. V úvodním okně zvolte **Vytvořit nový projekt.**

1. V **okně Vytvořit nový projekt** zadejte nebo zadejte *do* vyhledávacího pole konzolu. Dále zvolte **Visual Basic** v seznamu Jazyk a pak **v** seznamu Platforma zvolte Windows. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Konzolová aplikace** pro .NET Core a pak zvolte **Další.**

   ![Zvolte šablonu Visual Basic pro konzolovou aplikaci.](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Pokud šablonu Konzolová **aplikace nevidíte,** můžete ji nainstalovat z **okna Vytvořit nový** projekt. Ve zprávě **Nehledá se, co hledáte?** zvolte odkaz Instalovat **další** nástroje a funkce. Potom v části Instalační program pro Visual Studio úlohu **Vývoj pro různé platformy v .NET Core.**

1. V **okně Configure your new project** (Konfigurace nového projektu) zadejte nebo do pole Project name **(Název projektu)** zadejte nebo zadejte *get-started-debugging.* Pak zvolte **Další.**

1. Zvolte doporučené cílové rozhraní (.NET Core 3.1) nebo .NET 5 a pak zvolte **Vytvořit.**

   Visual Studio nový projekt otevřete.
   
::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *souboru Program.vb* nahraďte veškerý výchozí kód následujícím kódem:

    ```vb
    Imports System

    Class ArrayExample
        Public Shared Sub Main()
            Dim letters As Char() = {"f"c, "r"c, "e"c, "d"c, " "c, "s"c, "m"c, "i"c, "t"c, "h"c}
            Dim name As String = ""
            Dim a As Integer() = New Integer(9) {}

            For i As Integer = 0 To letters.Length - 1
                name += letters(i)
                a(i) = i + 1
                SendMessage(name, a(i))
            Next

            Console.ReadKey()
        End Sub

        Private Shared Sub SendMessage(ByVal name As String, ByVal msg As Integer)
            Console.WriteLine("Hello, " & name & "! Count to " & msg)
        End Sub
    End Class
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

1. Ve `For` smyčce funkce nastavte zarážku kliknutím na `Main` levý okraj následujícího řádku kódu:

    `name += letters(i)`

    Zarážka s ![červeným kruhem](../../debugger/media/dbg-breakpoint.png "Bodu") se zobrazí tam, kde nastavíte zarážku.

    Zarážky jsou jednou z nejzákladnějších a nejzákladnějších funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte **klávesu F5** nebo **tlačítko** Spustit ladění Spustit ladění ![,](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění")spustí se aplikace a ladicí program se spustí na řádku kódu, kde nastavíte zarážku.

    ![Nastavení a přístup k zarážce](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Žlutá šipka představuje příkaz, na kterém se ladicí program pozastavil, což také pozastaví provádění aplikace ve stejném bodě (tento příkaz se ještě nespouštěl).

     Pokud aplikace ještě není spuštěná, **F5** spustí ladicí program a zastaví se na první zarážce. V opačném **případě bude F5** pokračovat ve spouštění aplikace až k další zarážce.

    Zarážky jsou užitečnou funkcí, pokud znáte řádek kódu nebo část kódu, kterou chcete podrobně prozkoumat. Informace o různých typech zarážek, které můžete nastavit, například podmíněné zarážky, najdete v tématu [Použití zarážek](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Procházení kódu v ladicím programu pomocí příkazů kroku

Většinou tady používáme klávesové zkratky, protože je to dobrý způsob, jak rychle spustit aplikaci v ladicím programu (ekvivalentní příkazy, jako jsou příkazy nabídky, se zobrazují v závorkách).

1. Při pozastavení ve smyčce v metodě stiskněte `For` `Main` klávesu **F11** (nebo dvakrát > **Krokovat** s krokem do ), abyste se posunuli `SendMessage` na volání metody.

     Po stisknutí **klávesy F11** dvakrát byste měli být na tomto řádku kódu:

     `SendMessage(name, a(i))`

1. Dalším **stisknutím klávesy F11** zakrokte do `SendMessage` metody .

     Žlutý ukazatel přejde do `SendMessage` metody .

     ![Použití klávesy F11 ke kroku do kódu](../visual-basic/media/get-started-f11-vb.png "F10 Krokovat s vnořením")

     F11 je příkaz **Step Into (Krokovat** s krokem do) a postupuje provádění aplikace po jednom příkazu. F11 je dobrý způsob, jak podrobněji prozkoumat tok provádění. (Pokud chcete kódem urychlit, ukážeme vám také některé další možnosti.) Ve výchozím nastavení ladicí program přeskočí kód bez uživatele (pokud chcete další podrobnosti, podívejte se [na Pouze můj kód](../../debugger/just-my-code.md)).

     Řekněme, že jste skončili s prozkoumáním metody a chcete se z metody dostat, ale `SendMessage` zůstat v ladicím programu. Můžete to provést pomocí příkazu **Krok ven.**

1. Stiskněte **Klávesu Shift**  +  **F11** (nebo > Krok **ven**).

     Tento příkaz pokračuje v provádění aplikace (a pokračuje v ladicím programu), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste být zpět ve `For` smyčce v `Main` metodě , pozastaveno při `SendMessage` volání metody.

1. Několikrát **stiskněte klávesu F11,** dokud se znovu nevrátíte `SendMessage` k volání metody.

1. Při pozastavení při volání metody stiskněte **klávesu F10** (nebo jednou **> Krok přes**).

     ![Použití klávesy F10 ke kroku přes kód](../visual-basic/media/get-started-step-over-vb.png "F10 krok přes")

     Všimněte si, že ladicí program tentokrát nepřidá krok do `SendMessage` metody . **F10** posune ladicí program bez krokování s funkcemi nebo metodami v kódu aplikace (kód se stále provádí). Stisknutím **klávesy F10** při volání metody `SendMessage` (místo **F11)** jsme přeskočili kód implementace pro (který nás možná zrovna `SendMessage` nezajímá). Další informace o různých způsobech procházení kódu najdete v tématu [Procházení kódu v ladicím programu.](../../debugger/navigating-through-code-with-the-debugger.md)

## <a name="navigate-code-using-run-to-click"></a>Navigace v kódu pomocí příkazu Run to Click

1. Stisknutím **klávesy F5** znovu přejdete na zarážku.

1. V editoru kódu se posuňte dolů a najeďte myší na metodu v metodě, dokud se na levé straně nezobrazí zelené tlačítko Run to Click Run to Click (Spustit a `Console.WriteLine` `SendMessage` kliknout).  ![](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") Popis tlačítka zobrazuje "Run execution to here" (Spustit provádění sem).

     ![Použití funkce Spustit do kliknutí](../visual-basic/media/get-started-run-to-click-vb.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **Run to Click** (Spustit do kliknutí) je v systému [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)] nové. (Pokud nevidíte zelenou šipku tlačítka, použijte klávesu **F11** v tomto příkladu, aby se ladicí program napředal na správné místo.)

2. Kliknutím na tlačítko **Spustit pro** klikněte na tlačítko ![Spustit](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Ladicí program přejde do `Console.WriteLine` metody.

    Použití tohoto tlačítka je podobné nastavení dočasné zarážky. **Možnost spustit pro** je užitečná pro rychlé seznámení v rámci viditelné oblasti kódu aplikace (můžete kliknout na libovolný otevřený soubor).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**).

Po stisknutí tlačítka **restartovat** ušetří čas oproti zastavování aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážce, která je dosaženo spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili uvnitř `For` smyčky.

## <a name="inspect-variables-with-data-tips"></a>Kontrola proměnných pomocí tipů k datům

Funkce, které umožňují kontrolu proměnných, jsou jedním z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to provést. Pokud se při pokusu o ladění problému často pokusíte zjistit, zda proměnné ukládají hodnoty, které mají být v určitou dobu k dispozici.

1. Při pozastavení `name += letters[i]` příkazu, najeďte myší na `letters` proměnnou a vidíte její výchozí hodnotu, hodnotu prvního prvku v poli `"f"c` .

1. Potom najeďte myší na `name` proměnnou a uvidíte její aktuální hodnotu, prázdný řetězec.

1. Několikrát stiskněte klávesu **F5** (nebo pokračujte v **ladění**  >  ) několikrát k iterování několikrát přes smyčku a poklikáním `For` na zarážku, a pokaždé, když se podíváte na `name` proměnnou pokaždé, abyste zkontrolovali její hodnotu.

     ![Zobrazit Tip pro data](../visual-basic/media/get-started-data-tip-vb.png "Zobrazit Tip pro data")

     Hodnota proměnné se mění v každé iteraci `For` smyčky, zobrazuje hodnoty `f` , potom `fr` , `fre` a tak dále.

     Při ladění budete často potřebovat rychlý způsob kontroly hodnot vlastností u proměnných, abyste viděli, zda ukládají hodnoty, které očekáváte pro uložení, a tipy k datům jsou vhodným způsobem.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken automatické hodnoty a místní hodnoty

1. Podívejte se na okno **Automatické** hodnoty v dolní části editoru kódu.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu, a to volbou **ladit**  >  **okna**  >  **Automatické** hodnoty.

    V okně **Automatické** hodnoty vidíte proměnné a jejich aktuální hodnotu. Okno **Automatické** hodnoty zobrazuje všechny proměnné, které se používají na aktuálním řádku nebo na předchozím řádku (podívejte se na dokumentaci pro specifické chování jazyka).

1. Pak v okně **místní** hodnoty se podívejte na kartu vedle okna **Automatické** hodnoty.

1. Rozbalte `letters` proměnnou pro zobrazení prvků, které obsahuje.

     ![Kontrola proměnných v okně místních hodnot](../visual-basic/media/get-started-locals-window-vb.png "Okno místních hodnot")

    V okně **místní** hodnoty se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), tj. aktuálním kontextem spuštění.

## <a name="set-a-watch"></a>Nastavení kukátka

1. V hlavním okně editoru kódu klikněte pravým tlačítkem na `name` proměnnou a vyberte **Přidat kukátko**.

    V dolní části editoru kódu se otevře okno **kukátko** . Okno **kukátka** můžete použít k určení proměnné (nebo výrazu), pro kterou chcete zachovat oči.

    Teď máte pro proměnnou nastavenou kukátko `name` a při procházení ladicího programu můžete zobrazit jeho změnu hodnoty. Na rozdíl od ostatních oken proměnných se v okně **kukátka** vždy zobrazuje proměnné, které sledujete (v případě nedostatku rozsahu jsou šedé).

## <a name="examine-the-call-stack"></a>Kontrola zásobníku volání

1. Při pozastavení ve `For` smyčce klikněte na okno **zásobník volání** , které je ve výchozím nastavení otevřené v pravém dolním podokně.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu výběrem možnosti **ladit**  >    >  **zásobník volání** systému Windows.

2. Klikněte několikrát na klávesu **F11** , dokud se nezobrazí pozastavení ladicího programu v `SendMessage` metodě. Podívejte se do okna **zásobník volání** .

    ![Kontrola zásobníku volání](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

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
