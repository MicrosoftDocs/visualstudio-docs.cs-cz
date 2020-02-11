---
title: Naučte se ladit vícevláknové aplikace
description: Ladění pomocí paralelních zásobníků a oken paralelního kukátka v sadě Visual Studio
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e21d5174c9a909e9ad8031dfb7585abc52a7e78
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091792"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Začínáme s laděním vícevláknových aplikací (C#, Visual Basic, C++)

Visual Studio poskytuje několik nástrojů a prvků uživatelského rozhraní, které vám pomůžou ladit aplikace s více vlákny. V tomto kurzu se dozvíte, jak používat značky vláken, okno **paralelní zásobníky** , okno **paralelního sledování** , podmíněné zarážky a filtrovat zarážky. Po dokončení tohoto kurzu se seznámíte s funkcemi sady Visual Studio pro ladění aplikací s více vlákny.

Tato dvě témata obsahují další informace o použití jiných nástrojů pro Multithreading s více vlákny:

- Chcete-li použít panel nástrojů **umístění ladění** a okno **vlákna** , přečtěte si [Návod: ladění aplikace s více vlákny](../debugger/how-to-use-the-threads-window.md).

- Ukázku, která používá <xref:System.Threading.Tasks.Task> (spravovaný kód) a Concurrency Runtime (C++), naleznete v tématu [Návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md). Pro Obecné tipy pro ladění, které platí pro více typů aplikací s více vlákny, si přečtěte toto téma i tento článek.

Nejdříve budete potřebovat aplikační projekt s více vlákny. Následuje příklad.

## <a name="create-a-multithreaded-app-project"></a>Vytvoření vícevláknového projektu aplikace

1. Otevřete Visual Studio a vytvořte nový projekt.

   ::: moniker range=">=vs-2019"

   Pokud okno Start není otevřeno, vyberte **soubor** > **Spustit okno**.

   V okně Start vyberte možnost **vytvořit nový projekt**.

   V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále v seznamu **C#** jazyk **C++** vyberte, nebo **Visual Basic** a v seznamu platforma zvolte možnost **Windows** . 

   Po použití filtrů jazyků a platforem zvolte **Konzolová aplikace (.NET Core)** nebo, pro C++šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

   > [!NOTE]
   > Pokud nevidíte správnou šablonu, přejděte na **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **Desktop C++**  a zvolte možnost **Upravit**.

   V okně **Konfigurovat nový projekt** zadejte nebo zadejte *MyThreadWalkthroughApp* do pole **název projektu** . Pak zvolte **vytvořit**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** vyberte následující:

   - V případě C# aplikace v části **vizuál C#** zvolte **Windows Desktop**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
   - V případě aplikace Visual Basic vyberte v části **Visual Basic**možnost **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
   - V případě C++ aplikace v části **vizuál C++** zvolte **plocha Windows**, a pak zvolte **Konzolová aplikace Windows**.

   Pokud se nezobrazuje **Konzolová aplikace (.NET Core)** nebo, pro C++šablonu projektu **Konzolová aplikace** , přejděte do části **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte možnost vývoj **desktopových** aplikací pro .NET nebo **Desktop C++**  a zvolte možnost **Upravit**.

   Pak zadejte název jako *MyThreadWalkthroughApp* a klikněte na **OK**.

   Vyberte **OK**.
   ::: moniker-end

   Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor. V závislosti na zvoleném jazyce se může zdrojový soubor jmenovat *program.cs*, *MyThreadWalkthroughApp. cpp*nebo *Module1. vb*.

1. Odstraňte kód, který se zobrazí ve zdrojovém souboru, a nahraďte ho příslušným ukázkovým kódem uvedeným níže.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended. " + data);
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended. " + data)
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. V nabídce **soubor** vyberte **Uložit vše**.

1. (Jenom Visual Basic) V Průzkumník řešení (pravé podokno) klikněte pravým tlačítkem myši na uzel projektu a vyberte **vlastnosti**. Na kartě **aplikace** změňte **spouštěcí objekt** na **jednoduché**.

## <a name="debug-the-multithreaded-app"></a>Ladění vícevláknové aplikace

1. V editoru zdrojového kódu vyhledejte jeden z následujících fragmentů kódu:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Kliknutím levým na levé straně `Thread.Sleep` nebo příkazu `std::this_thread::sleep_for` vložte novou zarážku.

    Červený kroužek na hřbetu indikuje, že je v tomto umístění nastavená zarážka.

2. V nabídce **ladění** vyberte **Spustit ladění** (**F5**).

    Visual Studio sestaví řešení, aplikace se spustí s připojeným ladicím programem a pak se aplikace zastaví na zarážce.

3. V editoru zdrojového kódu vyhledejte řádek, který obsahuje zarážku.

### <a name="ShowThreadsInSource"></a>Zjistit značku vlákna  

1. Na panelu nástrojů ladění vyberte tlačítko **Zobrazit vlákna ve zdroji** ![Zobrazit vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Stiskněte klávesu **F11** jednou pro posunutí ladicího programu o jeden řádek kódu.

3. Podívejte se na ovládací prvek na levé straně okna. Na tomto řádku uvidíte ![značku vlákna](../debugger/media/dbg-thread-marker.png "ThreadMarker") *ikony vlákna, která se* podobá dvěma vytvořeným vláknům. Značky vlákna označuje, že je vlákno zastavené v tomto umístění.

    Značka vlákna může být částečně skryta zarážkou.

4. Ukazatel myši značky vlákna. Zobrazí se DataTip s informacemi o názvu a čísle ID vlákna pro každé zastavené vlákno. V tomto případě je název pravděpodobně `<noname>`.

5. Vyberte značku vlákna, abyste viděli dostupné možnosti v místní nabídce.

### <a name="ParallelStacks"></a>Zobrazit umístění vláken

V okně **paralelní zásobníky** můžete přepínat mezi zobrazením vlákna a (pro programování na základě úloh) zobrazení úkolů a můžete zobrazit informace o zásobníku volání pro každé vlákno. V této aplikaci můžeme použít zobrazení vláken.

1. Otevřete okno **paralelní zásobníky** tak, že vyberete možnost **ladění** > **Windows** > **paralelní zásobníky**. Měl by se zobrazit něco podobného jako následující. Přesné informace se budou lišit v závislosti na aktuálním umístění každého vlákna, hardwaru a programovacího jazyka.

    ![Okno paralelní zásobníky](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    V tomto příkladu uvidíme tyto informace pro spravovaný kód zleva doprava:

    - Hlavní vlákno (levá strana) bylo zastaveno na `Thread.Start`, kde je bod zastavení označen ![značkou](../debugger/media/dbg-thread-marker.png "ThreadMarker")ikony vlákna.
    - Dvě vlákna zadaly `ServerClass.InstanceMethod`, jeden z nich je aktuální vlákno (žlutá šipka), zatímco druhé vlákno bylo zastaveno v `Thread.Sleep`.
    - Spouští se také nové vlákno (na pravé straně), ale při `ThreadHelper.ThreadStart`se zastavilo.

2. Kliknutím pravým tlačítkem myši na položky v okně **paralelní zásobníky** zobrazíte dostupné možnosti v místní nabídce.

    Z těchto nabídek, které kliknete pravým tlačítkem, můžete provádět různé akce, ale v tomto kurzu se zobrazí více z těchto podrobností v okně **paralelní kukátko** (další části).

    > [!NOTE]
    > Chcete-li zobrazit seznam s informacemi o každém vlákně, použijte místo toho okno **vlákna** . Viz [Návod: ladění aplikace s více vlákny](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Nastavení kukátka pro proměnnou

1. Otevřete okno **paralelní sledování** tak, že vyberete možnost **ladění** > **Windows** > **paralelní sledování** > **paralelní sledování 1**.

2. Vyberte buňku, kde se zobrazuje text `<Add Watch>` (nebo prázdná buňka záhlaví ve sloupci 4) a zadejte `data`.

    Hodnoty pro datovou proměnnou pro každé vlákno se zobrazí v okně.

3. Vyberte buňku, kde se zobrazuje text `<Add Watch>` (nebo prázdná buňka záhlaví ve sloupci 5 @) a zadejte `count`.

    Hodnoty proměnné `count` pro každé vlákno se zobrazí v okně. Pokud ještě tyto informace nevidíte, zkuste stisknout klávesu **F11** několikrát, abyste mohli pokračovat v provádění vláken v ladicím programu.

    ![Okno paralelního sledování](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Kliknutím pravým tlačítkem myši na jeden z řádků v okně zobrazíte dostupné možnosti.

### <a name="flag-and-unflag-threads"></a>Označení a odstranění označení vlákna
Můžete označit vlákna pro udržení přehledu o důležitých vláknech a ignorovat další vlákna.

1. V okně **paralelní kukátko** podržte klávesu **SHIFT** a vyberte více řádků.

2. Klikněte pravým tlačítkem a vyberte **příznak**.

    Všechna vybraná vlákna jsou označena příznakem. Nyní můžete filtrovat, aby se zobrazila pouze vlákna označená příznakem.

3. V okně **paralelní sledování** zaškrtněte tlačítko **Zobrazit pouze vlákna označená příznakem** ![Zobrazit](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")vlákna.

    V seznamu se zobrazí pouze vlákna s příznakem.

    > [!TIP]
    > Po označení některých vláken můžete kliknout pravým tlačítkem myši na řádek kódu v editoru kódu a vybrat možnost **Spustit vlákna s příznakem na kurzor**. Ujistěte se, že jste zvolili kód, který bude mít všechna vlákna s příznakem. Visual Studio pozastaví vlákna na vybraném řádku kódu, což usnadňuje řízení pořadí spouštění pomocí [zmrazení a odmrazování vláken](#bkmk_freeze).

4. Zaškrtněte tlačítko **Zobrazit pouze vlákna označená příznakem** a přepněte zpět na **zobrazení všech režimů vláken** .

5. Chcete-li zrušit označení vláken, klikněte pravým tlačítkem myši na jedno nebo více vláken označených příznakem v okně **paralelní kukátko** a vyberte možnost zrušit **příznak**.

### <a name="bkmk_freeze"></a>Zablokovat a uvolnit provádění vlákna

> [!TIP]
> Můžete ukotvit a odblokovat (pozastavit a obnovit) vlákna a řídit tak pořadí, ve kterém vlákna provádějí práci. To vám může pomáhat vyřešit problémy souběžnosti, jako jsou zablokování a konflikty časování.

1. V okně **paralelní kukátko** vyberte všechny vybrané řádky, klikněte pravým tlačítkem myši a vyberte **ukotvit**.

    Ve druhém sloupci se pro každý řádek zobrazí ikona pozastavení. Ikona pozastavit označuje, že je vlákno zmrazeno.

2. Zrušte výběr všech ostatních řádků výběrem pouze jednoho řádku.

3. Klikněte pravým tlačítkem na řádek a vyberte možnost **uvolnit**.

    Ikona pozastavit se na tomto řádku neprojeví, což značí, že vlákno již není zmrazeno.

4. Přepněte do editoru kódu a stiskněte klávesu **F11**. Spouští se pouze nezmrazené vlákno.

    Aplikace může také vytvořit instanci některých nových vláken. Všechna nová vlákna nejsou označena příznakem a nejsou zmrazena.

### <a name="bkmk_follow_a_thread"></a>Sledování jednoho vlákna s podmíněnými zarážkami

Může být užitečné postupovat při provádění jednoho vlákna v ladicím programu. Jedním ze způsobů, jak to udělat, je zmrazení vláken, která vás zajímají. V některých scénářích může být nutné postupovat podle jednoho vlákna bez zmrazení jiných vláken, například pro reprodukování konkrétní chyby. Chcete-li postupovat podle vlákna bez zmrazení jiných vláken, musíte se vyhnout přerušení kódu s výjimkou vlákna, které vás zajímá. To můžete provést nastavením [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Můžete nastavit zarážky pro různé podmínky, například název vlákna nebo ID vlákna. Může být užitečné nastavit podmínku pro data, která znáte, je jedinečná pro každé vlákno. Toto je běžný scénář pro ladění, ve kterém máte více zajímat určitou konkrétní datovou hodnotu než v jakémkoli konkrétním vlákně.

1. Klikněte pravým tlačítkem na zarážku, kterou jste předtím vytvořili, a vyberte **podmínky**.

2. V okně **Nastavení zarážky** zadejte `data == 5` pro podmíněný výraz.

    ![Podmíněná zarážka](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Pokud máte více zajímat konkrétní vlákno, použijte pro podmínku název vlákna nebo ID vlákna. Pokud to chcete provést v okně **Nastavení zarážky** , vyberte **Filtr** místo **podmíněného výrazu**a postupujte podle tipů pro filtry. Můžete chtít pojmenovat vlákna v kódu aplikace, protože ID vláken se mění po restartování ladicího programu.

3. Zavřete okno **Nastavení zarážky** .

4. Kliknutím na tlačítko restartovat ![restart aplikace](../debugger/media/dbg-tour-restart.png "RestartApp") restartujte relaci ladění.

    Dojde k rozdělení do kódu ve vlákně, kde je hodnota datové proměnné 5. V okně **paralelní kukátko** vyhledejte žlutou šipku označující aktuální kontext ladicího programu.

5. Nyní můžete krokovat kód (**F10**) a krokovat kód (**F11**) a postupovat podle spuštění jednoho vlákna.

    Pokud je podmínka zarážky pro vlákno jedinečná a ladicí program nedosáhl žádné jiné zarážky v jiných vláknech (možná je budete muset zakázat), můžete krokovat kód a krokovat kód bez přepínání do jiných vláken.

    > [!NOTE]
    > Při přechodu do ladicího programu se spustí všechna vlákna. Ladicí program se však nebude přerušit do kódu v jiných vláknech, pokud jedno z ostatních vláken narazí na zarážku.

## <a name="see-also"></a>Viz také

- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Postupy: použití okna paralelního zásobníku](../debugger/using-the-parallel-stacks-window.md)
- [Postupy: Použití okna paralelního sledování](../debugger/how-to-use-the-parallel-watch-window.md)