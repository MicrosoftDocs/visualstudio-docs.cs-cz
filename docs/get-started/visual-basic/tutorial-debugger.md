---
title: 'Kurz: ladění kódu Visual Basic'
description: Zjistěte, jak ke spuštění ladicího programu sady Visual Studio, krokovat kód a kontrolovat data.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eb7ac3dacf5d572a13eadf8a37b194962b2ef49
ms.sourcegitcommit: 4a4eed115525c6d34a1fbdf87b793893cd43b70d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "77001433"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Kurz: Naučte se ladit kód Visual Basic pomocí sady Visual Studio

Tento článek obsahuje představení funkcí v ladicím programu sady Visual Studio podrobného návodu. Pokud chcete zobrazit vyšší úroveň funkcí ladicího programu, podívejte [se na téma první pohled na ladicí program](../../debugger/debugger-feature-tour.md). Pokud jste *ladění aplikace*, obvykle to znamená, že spustíte aplikaci s připojeným ladícím nástrojem. Když toto provedete, ladicí program poskytuje mnoho způsobů, jak zjistit, co kód dělá, při spuštění. Můžete procházet kódem a podívejte se na hodnoty uložené v proměnné, můžete nastavit hodinky na proměnné zobrazíte, když se změní hodnoty, můžete prozkoumat cesta provedení kódu naleznete v tématu, jestli větev kódu je spuštěná, a tak dále. Pokud je to poprvé, kterou jste se pokusili ladění kódu, můžete chtít číst [ladění pro naprosté začátečníky](../../debugger/debugging-absolute-beginners.md) před provedením tohoto článku.

I když je ukázková aplikace Visual Basic, většina C#funkcí platí pro jazyky,, C++ F#, Python, JavaScript a další jazyky, které podporuje Visual Studio (F# nepodporuje funkci upravit a pokračovat. F#a nepodporuje jazyk JavaScript **automatické hodnoty** okno). Snímky obrazovky jsou v Visual Basic.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Spuštění ladicího programu a dosažení zarážky.
> * Další příkazy ke krokování kódu v ladicím programu
> * Kontrolovat proměnné v datových tipech a okno ladicího programu
> * Prozkoumat zásobník volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou aplikaci Visual Studio 2019 a úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou aplikaci Visual Studio 2017 a úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt konzolové aplikace .NET Core. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual Basic**a pak zvolte možnost **.NET Core**. V prostředním podokně vyberte **aplikace konzoly (.NET Core)** . Potom pojmenujte projekt *Get-Started-Debugging*.

     Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , vyberte odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** .

     Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

   Pokud okno Start není otevřeno, vyberte **soubor** > **Spustit okno**.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly (.NET Core)** a pak zvolte možnost **Další**.

   ![Volba šablony Visual Basic pro konzolovou aplikaci (.NET Core)](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **Konzolová aplikace (.NET Core)** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Pak v Instalační program pro Visual Studio zvolte úlohu **vývoje .NET Core pro různé platformy** .

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *příkaz Get-Started-Debugging* do pole **název projektu** . Pak zvolte **vytvořit**.

   Visual Studio otevře nový projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *programu program. vb*místo toho nahraďte veškerý výchozí kód následujícím kódem:

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

## <a name="start-the-debugger"></a>Spuštění ladicího programu!

1. Stiskněte klávesu **F5** (**ladění > Spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění.

     **F5** spustí aplikaci se ladicí program připojen k aplikaci zpracování, ale v tuto chvíli jsme neprovedli nic zvláštního prozkoumat kód. Proto pouze načítání aplikace a zobrazí výstup konzoly.

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

     V tomto kurzu vytvoříme podrobněji podíváme na tuto aplikaci pomocí ladicího programu a získejte funkce, podívejte se na ladicí program.

2. Ukončete ladicí program stisknutím tlačítka červené zastavení ![Zastavit ladění](../../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") (**SHIFT** + **F5**).

3. V okně konzoly stisknutím klávesy zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavte zarážku a spuštění ladicího programu

1. V `For` smyčku z `Main` fungovat, nastavte zarážku kliknutím na levém okraji následující řádek kódu:

    `name += letters(i)`

    Zarážka ![červeného kruhu se](../../debugger/media/dbg-breakpoint.png "Bod přerušení") zobrazí tam, kde jste nastavili zarážku.

    Zarážky jsou jednou ze základních a základních funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde jste nastavili zarážku.

    ![Nastavte a použijte zarážku](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Žlutá šipka označuje příkaz na které ladicí program pozastaví, což také pozastaví provádění aplikace na stejném místě (Tento příkaz nebyl dosud proveden).

     Pokud ještě není aplikace spuštěna, **F5** spustí ladicí program a k první zarážce se zastaví. V opačném případě **F5** bude pokračovat spuštěním aplikace až k další zarážce.

    Zarážky jsou užitečná funkce, když znáte řádek kódu nebo části kódu, který chcete prozkoumat podrobněji. Informace o různých typech zarážek, které lze nastavit, například podmíněné zarážky, naleznete v tématu [using zarážek](../../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Vyhledání kódu v ladicím programu pomocí příkazů kroku

Většinou, klávesové zkratky tady používáme, protože je dobrým způsobem, jak získat rychlé při spuštění aplikace v ladicím programu (ekvivalentní příkazy jako je například nabídka příkazy jsou uvedeny v závorkách).

1. Při pozastavení ve smyčce `For` v metodě `Main` stiskněte klávesu **F11** (nebo zvolte možnost **ladit > Krokovat s vnořením**), aby bylo možné přejít na `SendMessage` volání metody.

     Po stisknutí klávesy **F11** dvakrát byste měli být na tomto řádku kódu:

     `SendMessage(name, a(i))`

1. Stiskněte klávesu **F11** ještě jednou pro krokování do `SendMessage` metody.

     Žlutý ukazatel se přesune do metody `SendMessage`.

     ![Krokovat s vnořením kódu pomocí klávesy F11](../visual-basic/media/get-started-f11-vb.png "F10 Krokovat s vnořením")

     Je F11 **Krokovat s vnořením** příkazu a posune jeden příkaz spuštění aplikace v čase. F11 je dobrým způsobem, jak prozkoumat provádění toku v nejvíce podrobností. (K rychlejšímu přesunu kódu vám ukážeme i některé další možnosti.) Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../../debugger/just-my-code.md)).

     Řekněme, že jste dokončili zkoumání `SendMessage` metody a chcete získat z metody, ale zůstat v ladicím programu. Můžete provést pomocí **Krokovat s Vystoupením** příkazu.

1. Stisknutím klávesy **Shift** + **F11** (nebo **ladit > Krokovat s Vystoupením**).

     Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste se vrátit ve smyčce `For` v metodě `Main`, která je pozastavena při volání metody `SendMessage`.

1. Stiskněte klávesu **F11** , dokud se znovu nevrátíte do volání metody `SendMessage`.

1. Když jste pozastavili volání metody, stiskněte **F10** (nebo zvolte **ladění > krokovat**s) jednou.

     ![Pro krokování kódu použijte F10](../visual-basic/media/get-started-step-over-vb.png "F10 krok přes")

     Všimněte si, že ladicí program nekrokuje do metody `SendMessage`. **F10** přejde ladicí program bez krokování do funkce nebo metody v kódu vaší aplikace (kód stále provádí). Stisknutím klávesy **F10** ve volání metody `SendMessage` (namísto **klávesy F11**) přeskočíme na implementační kód pro `SendMessage` (což by mohlo být v současnosti nedotčeno). Další informace o různých způsobech, jak přesouvat kód, naleznete v tématu [Navigace v kódu v ladicím programu](../../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Vyhledání kódu pomocí běžet do kliknutí

1. V editoru kódu se posuňte dolů a najeďte myší na `Console.WriteLine`ovou zprávu ve zprávě `SendMessage`, dokud ![se na tlačítko](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") neotevře **zelené tlačítko spustit pro** kliknutí. V popisu tlačítka se zobrazí text spustit provádění na tomto místě.

     ![Použití funkce spustit pro kliknutí](../visual-basic/media/get-started-run-to-click-vb.png "Běžet do kliknutí")

   > [!NOTE]
   > **Běžet do kliknutí** je novinkou systémů tlačítko [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. (Pokud nevidíte zelenou šipku tlačítka, použijte klávesu **F11** v tomto příkladu, aby se ladicí program napředal na správné místo.)

2. Kliknutím na tlačítko **Spustit pro** klikněte na tlačítko ![Spustit](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Ladicí program přejde do metody `Console.WriteLine`.

    Pomocí tohoto tlačítka je podobné nastavení dočasné zarážky. **Běžet do kliknutí** je užitečné pro rychlé navigace v rámci viditelné oblasti kódu aplikace (můžete kliknout na jakékoli otevření souboru).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL** + **SHIFT** + **F5**).

Když stisknete klávesu **restartovat**, šetří čas a zastavuje se aplikace a restartování ladicího programu. Ladicí program pozastaví na první zarážce, kterou dosáhnete spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili ve smyčce `For`.

## <a name="inspect-variables-with-data-tips"></a>Kontrolovat proměnné s datových tipech

Funkce, které umožňují kontrolovat proměnné jsou jedním z nejužitečnějších funkce ladicího programu, a to různými způsoby. Při pokusu o ladění chyby se často, pokoušíte zjistit, zda jsou proměnné ukládání hodnot, které očekáváte, že ho, aby v určitou dobu.

1. Při pozastavení na příkazu `name += letters[i]`, najeďte myší na proměnnou `letters` a uvidíte, že je to výchozí hodnota, hodnota prvního prvku v poli `"f"c`.

1. Potom najeďte myší na proměnnou `name` a zobrazí se její aktuální hodnota, prázdný řetězec.

1. Několikrát stisknutím klávesy **F5** (nebo **ladění** > **pokračovat**) několikrát Iterujte pomocí `For` smyčky, opětovným pozastavením na zarážce a pokaždé, když se vrátíte na `name` proměnnou, a pokaždé, když chcete ověřit její hodnotu.

     ![Zobrazit Tip pro data](../visual-basic/media/get-started-data-tip-vb.png "Zobrazit Tip pro data")

     Hodnota proměnné se mění u každé iterace `For` smyčky, zobrazuje hodnoty `f`a pak `fr`, `fre`a tak dále.

     Často při ladění, chcete rychle zkontrolovat hodnoty vlastností pro proměnné, chcete-li zobrazit, jestli jsou jejich ukládání hodnoty, které očekáváte, že je pro uložení, a datových tipech jsou dobrým způsobem, jak to udělat.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrolovat proměnné s okna Automatické hodnoty a místní hodnoty

1. Podívejte se na **automatické hodnoty** okno v dolní části editoru kódu.

    Pokud se zavře, otevřete ho během pozastavení v ladicím programu výběrem **ladění** > **Windows** > **automatické hodnoty**.

    V **automatické hodnoty** okně se zobrazí proměnné a jejich aktuální hodnoty. **Automatické hodnoty** okně se zobrazí všechny proměnné používané v aktuálním řádkem nebo předchozí řádku (v dokumentaci pro konkrétní jazyk chování).

1. Dále, podívejte se na **lokální** okno na kartě vedle **automatické hodnoty** okna.

1. Rozbalte proměnnou `letters` pro zobrazení prvků, které obsahuje.

     ![Kontrola proměnných v okně místních hodnot](../visual-basic/media/get-started-locals-window-vb.png "Okno místních hodnot")

    **Lokální** v okně se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), to znamená, aktuální kontext spuštění.

## <a name="set-a-watch"></a>Nastavení sledování

1. V hlavním okně editoru kódu klikněte pravým tlačítkem myši na proměnnou `name` a vyberte možnost **Přidat kukátko**.

    **Watch** otevře se okno v dolní části editoru kódu. Můžete použít **Watch** okno zadat proměnné (nebo výraz), který chcete sledovat.

    Teď máte pro `name` proměnnou nastavenou kukátko a při procházení ladicího programu uvidíte její změnu hodnoty. Na rozdíl od jiných proměnných oknech **Watch** okno vždy zobrazuje proměnné, že se díváte (jsou sice zobrazené šedě, když mimo rozsah).

## <a name="examine-the-call-stack"></a>Prozkoumat zásobník volání

1. Během pozastavení v `For` opakovat, klikněte na tlačítko **zásobník volání** okna, která je ve výchozím nastavení, otevřete v pravém dolním podokně.

    Pokud se zavře, otevřete ho během pozastavení v ladicím programu výběrem **ladění** > **Windows** > **zásobník volání**.

2. Klikněte několikrát na klávesu **F11** , dokud se nezobrazí pozastavení ladicího programu v metodě `SendMessage`. Podívejte se na **zásobník volání** okna.

    ![Kontrola zásobníku volání](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    **Zásobník volání** okno zobrazuje pořadí, ve kterém jsou získávání volány metody a funkce. Na horní zobrazený řádek zobrazuje aktuální funkci ( `SendMessage` metody v této aplikaci). Druhý řádek ukazuje, že `SendMessage` byla volána `Main` metody a tak dále.

   > [!NOTE]
   > **Zásobník volání** okno je podobné ladění perspektivy v některých prostředí IDE, jako je Eclipse.

    Zásobník volání je dobrým způsobem, jak zkoumat a pochopit provádění toku aplikace.

    Dvojitým kliknutím na řádek kódu go, podívejte se na tento zdrojový kód a také změny v aktuálním oboru kontrolován ladicím programem. Tato akce nepřesouvejte vpřed ladicí program.

    Můžete také použít nabídek klikněte pravým tlačítkem **zásobník volání** okno a dělat jiné věci. Například vložení do určené funkce zarážky, ladicí program pomocí předem **spustit ke kurzoru**a zkontrolujte zdrojový kód. Další informace najdete v tématu [postupy: prozkoumání zásobník volání](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku provádění

1. Stisknutím klávesy **F11** dvakrát spusťte metodu `Console.WriteLine`.

1. Když je ladicí program pozastaven ve volání metody `SendMessage`, použijte myš k navýšení žluté šipky (ukazatel spuštění) na levé straně a přesuňte žlutou šipku o jeden řádek po návratu na `Console.WriteLine`.

1. Stisknutím klávesy **F11**.

    Znovu spustí ladicí program `Console.WriteLine` – metoda (vidíte to v okně výstup konzoly).

    Změnou provádění toku můžete provést kroky, jako je test cesty spuštění odlišný kód nebo znovu spustit kód bez restartování ladicího programu.

    > [!WARNING]
    > Často je potřeba pečlivě s touto funkcí a zobrazit upozornění v popisu. Příliš se může zobrazit další varování. Ukazatele nejde vrátit zpět aplikaci do předchozího stavu aplikace.

1. Stisknutím klávesy **F5** bude moct být spuštěná aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak spustit ladicí program, krokovat kód a můžete kontrolovat proměnné. Můžete chtít získat podrobný přehled funkcí ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
