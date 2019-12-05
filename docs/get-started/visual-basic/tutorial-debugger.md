---
title: 'Kurz: ladění kódu Visual Basic'
description: Zjistěte, jak ke spuštění ladicího programu sady Visual Studio, krokovat kód a kontrolovat data.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b38089a088186a30ebd13cae68d19ac23235bf9
ms.sourcegitcommit: 697f2ab875fd789685811687387e9e8e471a38c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74829976"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Kurz: Naučte se ladit kód Visual Basic pomocí sady Visual Studio

Tento článek obsahuje představení funkcí v ladicím programu sady Visual Studio podrobného návodu. Pokud chcete zobrazit vyšší úroveň funkcí ladicího programu, podívejte [se na téma první pohled na ladicí program](../../debugger/debugger-feature-tour.md). Pokud jste *ladění aplikace*, obvykle to znamená, že spustíte aplikaci s připojeným ladícím nástrojem. Když toto provedete, ladicí program poskytuje mnoho způsobů, jak zjistit, co kód dělá, při spuštění. Můžete procházet kódem a podívejte se na hodnoty uložené v proměnné, můžete nastavit hodinky na proměnné zobrazíte, když se změní hodnoty, můžete prozkoumat cesta provedení kódu naleznete v tématu, jestli větev kódu je spuštěná, a tak dále. Pokud je to poprvé, kterou jste se pokusili ladění kódu, můžete chtít číst [ladění pro naprosté začátečníky](../../debugger/debugging-absolute-beginners.md) před provedením tohoto článku.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Spuštění ladicího programu a dosažení zarážky.
> * Další příkazy ke krokování kódu v ladicím programu
> * Kontrolovat proměnné v datových tipech a okno ladicího programu
> * Prozkoumat zásobník volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou aplikaci Visual Studio 2019 a úlohu **vývoj desktopových aplikací .NET** .

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou sadu Visual Studio 2017 a **vývoj desktopových aplikací .NET** pracovního vytížení.

::: moniker-end

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** úloh, klikněte na tlačítko **změnit**.

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřít Visual Studio.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **Visual Basic**, zvolte **šablony**a pak zvolte buď **vytvořit novou konzolovou aplikaci (.NET Core) projekt** , nebo **vytvořte nový projekt Konzolová aplikace (.NET Framework)** . V dialogovém okně, které se zobrazí, zadejte název, jako je například **Get-Started**, a pak zvolte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual Basic**zvolte **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** . Pak zadejte název, jako je například **Get-Started-Debugging** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Framework)** , přejděte do části **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací .NET** úloh, klikněte na tlačítko **změnit**.

    Visual Studio vytvoří projekt.

1. V *Module1. vb*nahraďte veškerý výchozí kód.

    ```vb
    Module Module1

        Sub Main()
        End Sub

    End Module
    ```

    s tímto kódem:

    ```vb
    Imports System
    Imports System.Collections.Generic

    Public Class Shape

      ' A few example members
        Public Property X As Integer
            Get
                Return X
            End Get
            Set
            End Set
        End Property

        Public Property Y As Integer
            Get
                Return Y
            End Get
            Set
            End Set
        End Property

        Public Property Height As Integer
            Get
                Return Height
            End Get
            Set
            End Set
        End Property

        Public Property Width As Integer
            Get
                Return Width
            End Get
            Set
            End Set
        End Property

        ' Virtual method
        Public Overridable Sub Draw()
            Console.WriteLine("Performing base class drawing tasks")
        End Sub
    End Class

    Public Class Circle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a circle...
            Console.WriteLine("Drawing a circle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Rectangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Triangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a triangle...
            Console.WriteLine("Drawing a trangle")
            MyBase.Draw()
        End Sub
    End Class

    Module Module1

        Sub Main(ByVal args() As String)

            Dim shapes = New List(Of Shape) From
            {
                New Rectangle,
                New Triangle,
                New Circle
            }

            For Each shape In shapes
                shape.Draw()
            Next
            ' Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.")
            Console.ReadKey()

        End Sub

    End Module

    ' Output:
    '    Drawing a rectangle
    '    Performing base class drawing tasks
    '    Drawing a triangle
    '    Performing base class drawing tasks
    '    Drawing a circle
    '    Performing base class drawing tasks
    ```

## <a name="start-the-debugger"></a>Spuštění ladicího programu!

1. Stiskněte klávesu **F5** (**ladění > Spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění.

     **F5** spustí aplikaci se ladicí program připojen k aplikaci zpracování, ale v tuto chvíli jsme neprovedli nic zvláštního prozkoumat kód. Proto pouze načítání aplikace a zobrazí výstup konzoly.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     V tomto kurzu vytvoříme podrobněji podíváme na tuto aplikaci pomocí ladicího programu a získejte funkce, podívejte se na ladicí program.

2. Ukončete ladicí program stisknutím tlačítka červené zastavení ![Zastavit ladění](../../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") .

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavte zarážku a spuštění ladicího programu

1. V `For Each` smyčku z `Main` fungovat, nastavte zarážku kliknutím na levém okraji následující řádek kódu:

    `shape.Draw()`

    Se zobrazí červený kruh, kde nastavit zarážku.

    ![Nastavení zarážky](../visual-basic/media/get-started-set-breakpoint-vb.png)

    Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../../debugger/media/dbg-tour-start-debugging.png "Spustit ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde jste nastavili zarážku.

    ![Stiskněte zarážku](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    Žlutá šipka označuje příkaz na které ladicí program pozastaví, což také pozastaví provádění aplikace na stejném místě (Tento příkaz nebyl dosud proveden).

     Pokud ještě není aplikace spuštěna, **F5** spustí ladicí program a k první zarážce se zastaví. V opačném případě **F5** bude pokračovat spuštěním aplikace až k další zarážce.

    Zarážky jsou užitečná funkce, když znáte řádek kódu nebo části kódu, který chcete prozkoumat podrobněji.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Vyhledání kódu v ladicím programu pomocí příkazů kroku

Většinou, klávesové zkratky tady používáme, protože je dobrým způsobem, jak získat rychlé při spuštění aplikace v ladicím programu (ekvivalentní příkazy jako je například nabídka příkazy jsou uvedeny v závorkách).

1. Během pozastavení v `shape.Draw` volání metody `Main` funkci, stiskněte klávesu **F11** (nebo zvolte **ladění > Krokovat s vnořením**) pro přechod do kódu pro `Rectangle` třídy.

     ![Krokovat s vnořením kódu pomocí klávesy F11](../visual-basic/media/get-started-f11-vb.png "F11 Krokovat s vnořením")

     Je F11 **Krokovat s vnořením** příkazu a posune jeden příkaz spuštění aplikace v čase. F11 je dobrým způsobem, jak prozkoumat provádění toku v nejvíce podrobností. (K rychlejšímu přesunu kódu vám ukážeme i některé další možnosti.) Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../../debugger/just-my-code.md)).

2. Stisknutím klávesy **F10** (nebo zvolte **ladit > Krokovat s přeskočením**) několikrát, dokud ladicí program se zastaví na `MyBase.Draw` volání metody a poté stiskněte klávesu **F10** ještě jednou.

     ![Pro krokování kódu použijte F10](../visual-basic/media/get-started-step-over-vb.png "F10 krok přes")

     Všimněte si, že tento čas, který ladicí program Nekrokovat s vnořením do `Draw` metody základní třídy (`Shape`). **F10** přejde ladicí program bez krokování do funkce nebo metody v kódu vaší aplikace (kód stále provádí). Stisknutím klávesy **F10** ve volání metody `MyBase.Draw` (namísto **klávesy F11**) přeskočíme na implementační kód pro `MyBase.Draw` (což by mohlo být v současnosti nedotčeno).

## <a name="navigate-code-using-run-to-click"></a>Vyhledání kódu pomocí běžet do kliknutí

1. V editoru kódu se posuňte dolů a najeďte myší na `Console.WriteLine`ovou metodu ve třídě `Triangle`, dokud se na tlačítko, které se zobrazí na levé straně, ![klikne](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") na tlačítko zeleného **spuštění** , které se spustí. V popisu tlačítka se zobrazí text spustit provádění na tomto místě.

     ![Použití funkce spustit pro kliknutí](../visual-basic/media/get-started-run-to-click-vb.png "Běžet do kliknutí")

   > [!NOTE]
   > **Běžet do kliknutí** je novinkou systémů tlačítko [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Pokud nevidíte tlačítko zelenou šipku, použijte **F11** v tomto příkladu místo toho k přechodu na správném místě ladicí program.

2. Kliknutím na tlačítko **Spustit pro** klikněte na tlačítko ![Spustit](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Pomocí tohoto tlačítka je podobné nastavení dočasné zarážky. **Běžet do kliknutí** je užitečné pro rychlé navigace v rámci viditelné oblasti kódu aplikace (můžete kliknout na jakékoli otevření souboru).

    Ladicí program přejde `Console.WriteLine` implementace metody pro `Triangle` třídy. (Pokud ladicí program nejprve pozastaví na zarážce, kterou jste nastavili dříve, pomocí **příkazu spustit znovu spusťte** ladicí program na `Console.WriteLine`.)

    Během pozastavení, si všimnete překlep! Je zadáno chybně výstupu "Kreslení trangle". Jsme tady ho můžou opravit při spuštění aplikace v ladicím programu.

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

1. Klikněte na tlačítko do "Kreslení trangle" a zadejte opravu, změna "trangle" na "trojúhelník".

1. Stisknutím klávesy **F11** jednou a můžete zobrazit znovu přejde ladicí program.

    > [!NOTE]
    > V závislosti na tom, jaký typ kódu upravit v ladicím programu může se zobrazit zpráva upozornění. V některých případech kód potřeba překompilovat, než budete moct pokračovat.

## <a name="step-out"></a>Krokovat s Vystoupením

Řekněme, že skončíte zkoumání `Draw` metodu `Triangle` třídy a chcete využít funkce ale zůstávají v ladicím programu. Můžete provést pomocí **Krokovat s Vystoupením** příkazu.

1. Stisknutím klávesy **Shift** + **F11** (nebo **ladit > Krokovat s Vystoupením**).

     Tento příkaz pokračuje v provádění aplikace (a přejde ladicí program) až do aktuálního funkce vrátí.

     Měli byste se vrátit `For Each` smyčky v `Main` – metoda. Pokud ne, stiskněte klávesu **Shift** + **F11** ještě jednou.

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL** + **SHIFT** + **F5**).

Když stisknete klávesu **restartovat**, šetří čas a zastavuje se aplikace a restartování ladicího programu. Ladicí program pozastaví na první zarážce, kterou dosáhnete spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, nastavíte na `shape.Draw()` metody.

## <a name="inspect-variables-with-data-tips"></a>Kontrolovat proměnné s datových tipech

Funkce, které umožňují kontrolovat proměnné jsou jedním z nejužitečnějších funkce ladicího programu, a to různými způsoby. Při pokusu o ladění chyby se často, pokoušíte zjistit, zda jsou proměnné ukládání hodnot, které očekáváte, že ho, aby v určitou dobu.

1. Zatímco je pozastavená metoda `shape.Draw()`, najeďte myší na objekt `shapes` a zobrazí se jeho výchozí hodnota vlastnosti `Count`.

1. Rozbalením objektu `shapes` zobrazíte všechny jeho vlastnosti, jako je například první index `[0]`pole, který má hodnotu `Rectangle`.

     ![Zobrazit Tip pro data](../visual-basic/media/get-started-data-tip-vb.png "Zobrazit Tip pro data")

    Můžete dále rozbalovat objekty pro zobrazení jejich vlastností, jako je například vlastnost `Height` obdélníku.

    Často při ladění, chcete rychle zkontrolovat hodnoty vlastností pro objekty a datové tipy jsou dobrým způsobem, jak to udělat.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrolovat proměnné s okna Automatické hodnoty a místní hodnoty

1. Podívejte se na **automatické hodnoty** okno v dolní části editoru kódu.

     ![Kontrola proměnných v okně Automatické hodnoty](../visual-basic/media/get-started-autos-window-vb.png "Okno Automatické hodnoty")

    V **automatické hodnoty** okně se zobrazí proměnné a jejich aktuální hodnoty. **Automatické hodnoty** okně se zobrazí všechny proměnné používané v aktuálním řádkem nebo předchozí řádku (v dokumentaci pro konkrétní jazyk chování).

2. Dále, podívejte se na **lokální** okno na kartě vedle **automatické hodnoty** okna.

    **Lokální** v okně se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), to znamená, aktuální kontext spuštění.

## <a name="set-a-watch"></a>Nastavení sledování

1. V okně editoru hlavní kód, klikněte pravým tlačítkem myši `shapes` objektu a zvolte **Přidat kukátko**.

    **Watch** otevře se okno v dolní části editoru kódu. Můžete použít **Watch** okno zadat proměnné (nebo výraz), který chcete sledovat.

    Teď máte nastavit na sledování `shapes` objekt kde můžete zobrazit její hodnotu změnit při procházení ladicí program. Na rozdíl od jiných proměnných oknech **Watch** okno vždy zobrazuje proměnné, že se díváte (jsou sice zobrazené šedě, když mimo rozsah).

## <a name="examine-the-call-stack"></a>Prozkoumat zásobník volání

1. Během pozastavení v `For Each` opakovat, klikněte na tlačítko **zásobník volání** okna, která je ve výchozím nastavení, otevřete v pravém dolním podokně.

2. Klikněte na tlačítko **F11** několikrát, dokud se nezobrazí pozastavení v ladicím programu `MyBase.Draw` metodu `Rectangle` třídy v editoru kódu. Podívejte se na **zásobník volání** okna.

    ![Kontrola zásobníku volání](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    **Zásobník volání** okno zobrazuje pořadí, ve kterém jsou získávání volány metody a funkce. Na horní zobrazený řádek zobrazuje aktuální funkci ( `Rectangle.Draw` metody v této aplikaci). Druhý řádek ukazuje, že `Rectangle.Draw` byla volána `Main` funkce a tak dále.

   > [!NOTE]
   > **Zásobník volání** okno je podobné ladění perspektivy v některých prostředí IDE, jako je Eclipse.

    Zásobník volání je dobrým způsobem, jak zkoumat a pochopit provádění toku aplikace.

    Dvojitým kliknutím na řádek kódu go, podívejte se na tento zdrojový kód a také změny v aktuálním oboru kontrolován ladicím programem. Tato akce nepřesouvejte vpřed ladicí program.

    Můžete také použít nabídek klikněte pravým tlačítkem **zásobník volání** okno a dělat jiné věci. Například vložení do určené funkce zarážky, ladicí program pomocí předem **spustit ke kurzoru**a zkontrolujte zdrojový kód. Další informace najdete v tématu [postupy: prozkoumání zásobník volání](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku provádění

1. Ladicí program byl pozastaven ve volání metody `MyBase.Draw` `Rectangle` třídy, pomocí myši umístěte žlutou šipku (ukazatel spuštění) na levé straně a přesuňte žlutou šipku po jednom řádku na volání metody `Console.WriteLine`.

1. Stisknutím klávesy **F11**.

    Ladicí program znovu spustí metodu `Console.WriteLine` (ve výstupu okna konzoly se zobrazí duplicitní výstup).

    Změnou provádění toku můžete provést kroky, jako je test cesty spuštění odlišný kód nebo znovu spustit kód bez restartování ladicího programu.

    > [!WARNING]
    > Často je potřeba pečlivě s touto funkcí a zobrazit upozornění v popisu. Příliš se může zobrazit další varování. Ukazatele nejde vrátit zpět aplikaci do předchozího stavu aplikace.

1. Stisknutím klávesy **F5** bude moct být spuštěná aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak spustit ladicí program, krokovat kód a můžete kontrolovat proměnné. Můžete chtít získat podrobný přehled funkcí ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
