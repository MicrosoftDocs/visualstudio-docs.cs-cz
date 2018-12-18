---
title: Další informace k ladění vícevláknových aplikací
description: Ladění pomocí okna paralelní zásobníky a paralelní sledování v sadě Visual Studio
ms.custom: H1HackMay2017
ms.date: 11/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a6ded522a917dd7207da7731850303535e19fdb
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948982"
---
# <a name="get-started-debugging-multithreaded-applications"></a>Začínáme s laděním vícevláknových aplikací
Visual Studio poskytuje několik nástrojů a prvky uživatelského rozhraní si můžete usnadnit ladění aplikací s více vlákny. Tento kurz ukazuje, jak používat značky vlákna **paralelní zásobníky** okně **paralelní sledování** oken, podmíněné zarážky a filtr zarážek. Dokončení tohoto kurzu se můžete seznámit s funkcemi sady Visual Studio pro ladění aplikací s více vlákny.

| | |
|---------|---------|
| ![Ikona filmové kamery pro video](../install/media/video-icon.png "Sledovat video") | [Podívejte se na video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) vícevláknové ladění zobrazující podobný postup. |

Tyto dvě témata obsahují další informace o použití jiných vícevláknové ladění nástrojů:

- Použít **umístění ladění** nástrojů a **vlákna** okna, naleznete v tématu [návod: ladění aplikace s více vlákny](../debugger/how-to-use-the-threads-window.md).

- Příklad, který používá <xref:System.Threading.Tasks.Task> (spravovaný kód) a modulu runtime souběžnosti (C++), najdete v článku [návod: ladění paralelní aplikace](../debugger/walkthrough-debugging-a-parallel-application.md). Obecné ladění tipy, které se vztahují na typy nejvíce vícevláknové aplikace přečtěte si toto téma a tohoto objektu.
  
Nejprve musíte projekt aplikace s více vlákny. Následuje příklad.  
  
## <a name="create-a-multithreaded-app-project"></a>Vytvořte projekt aplikace s více podprocesy  
  
1.  Na **souboru** nabídce vyberte možnost **nový** > **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  Zvolte jazyk: **Visual C#** , **Visual C++**, nebo **jazyka Visual Basic**.  
  
3.  V části **Windows Desktop**, zvolte **konzolovou aplikaci**.  
  
4.  V **název** zadejte MyThreadWalkthroughApp.  
  
5.  Vyberte **OK**.  
  
     Zobrazí se nový projekt konzoly. Po vytvoření projektu se zobrazí zdrojový soubor. V závislosti na jazyku, kterou jste zvolili, může být názvem zdrojového souboru *Program.cs*, *MyThreadWalkthroughApp.cpp*, nebo *Module1.vb*.  
  
6.  Odstranit kód, který se zobrazí ve zdrojovém souboru a nahraďte ji metodou odpovídající ukázku kódu níže.

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
                "The instance method called by the worker thread has ended.");
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
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
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
                    "The instance method called by the worker thread has ended.")
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
  
7.  Na **souboru** nabídce vyberte možnost **Uložit vše**.  
  
## <a name="debug-the-multithreaded-app"></a>Ladění vícevláknových aplikací  
  
1. V editoru zdrojového kódu vyhledejte jednu z následujících fragmentů kódu: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Klikněte v levém hřbetu z `Thread.Sleep` nebo `this_thread::sleep_for` příkazu k vložení novou zarážku.  
  
    Na ovládací prvek červené kolečko označuje, že na tomto místě byla nastavena zarážka. 
  
2. Na **ladění** nabídce vyberte možnost **spustit ladění** (**F5**).  
  
    Visual Studio vytvoří řešení, aplikace spustí s připojeným ladícím nástrojem a poté se aplikace zastaví u zarážky.  
  
3. V editoru zdrojového kódu vyhledejte řádek, který obsahuje zarážku.
  
### <a name="ShowThreadsInSource"></a>Zjišťovat značky vlákna  

1.  Na panelu nástrojů ladění vyberte **zobrazit vlákna ve zdroji** tlačítko ![zobrazit vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Stisknutím klávesy **F11** jednou pro přechod na ladicí program jeden řádek kódu.
  
3.  Podívejte se na ovládací prvek na levé straně okna. Na tomto řádku se zobrazí *značky vlákna* ikonu ![značky vlákna](../debugger/media/dbg-thread-marker.png "ThreadMarker") , která připomíná dvě kroucená vlákna. Značky vlákna označuje, že je vlákno zastavené v tomto umístění.

    Značky vlákna mohou být částečně zakryty podle zarážku. 
  
4.  Ukazatel myši značky vlákna. DataTip nezobrazí číslo ID názvu a vlákna pro každé vlákno zastavené. V tomto případě název je pravděpodobně `<noname>`. 
  
5.  Vyberte značku vlákno zobrazíte dostupné možnosti v místní nabídce.
    
### <a name="ParallelStacks"></a>Zobrazit vlákna umístění

V **paralelní zásobníky** okně můžete přepínat mezi zobrazení vláken a (pro programování založené na úlohách) zobrazení úloh kde můžete zobrazit informace v zásobníku volání pro každé vlákno. V této aplikaci používáme zobrazení vláken.

1. Otevřít **paralelní zásobníky** okno výběrem **ladění** > **Windows** > **paralelní zásobníky**. By měl vypadat nějak takto. Přesné informace se budou lišit v závislosti na aktuální umístění každé vlákno, hardwaru a svůj oblíbený programovací jazyk.

    ![Paralelních zásobníků okno](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    V tomto příkladu vidíme zleva doprava tyto informace pro spravovaný kód:
    
    - Hlavní vlákno (levá strana) se zastavila na `Thread.Start`, kde je okamžik zastavení označená ikonou značky vlákna ![značky vlákna](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Zadaná dvě vlákna `ServerClass.InstanceMethod`, z nichž jeden je aktuální vlákno (žlutá šipka), zatímco jiné vlákno se zastavila v `Thread.Sleep`.
    - Nové vlákno (napravo) se také spouští ale se zastaví na `ThreadHelper.ThreadStart`.

2.  Klikněte pravým tlačítkem na položky v **paralelní zásobníky** okno zobrazte dostupné možnosti v místní nabídce.

    Můžete provádět různé akce z těchto nabídek klikněte pravým tlačítkem, ale pro účely tohoto kurzu vám ukážeme některé tyto podrobnosti v **paralelní sledování** okno (další oddíly).

    > [!NOTE]
    > Pokud chcete zobrazit na zobrazení seznamu s informace o každé vlákno, použijte **vlákna** okno místo toho. Zobrazit [návod: ladění aplikace s více vlákny](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Nastavení sledování u proměnné

1. Otevřít **paralelní sledování** okna tak, že vyberete **ladění** > **Windows** > **paralelní sledování**  >  **Paralelní sledování 1**.

2. Vyberte buňku, kde se zobrazují `<Add Watch>` text (nebo prázdný hlavičkové buňky ve sloupci 4) a zadejte `data`.

    V okně se zobrazí hodnoty pro proměnné data pro každé vlákno.

3. Vyberte buňku, kde se zobrazují `<Add Watch>` text (nebo prázdnou buňku v 5. sloupec) a zadejte `count`.

    Hodnoty `count` se zobrazí v okně proměnné pro každé vlákno. Pokud nevidíte ještě takovém množství informací, zkuste stisknutí **F11** několikrát k přechodu provádění vláken v ladicím programu.

    ![Paralelního kukátka](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Klikněte pravým tlačítkem na jednotlivé řádky v okně a zobrazí se dostupné možnosti.

### <a name="flag-and-unflag-threads"></a>Označení a odstranění označení vlákna  
Můžete označit příznakem vlákna a mějte přehled o důležitých vlákna ignorovat ostatní vlákna.  
  
1. V **paralelní sledování** okno, podržte stisknutou klávesu **Shift** klíče a výběr více řádků.

2. Klikněte pravým tlačítkem a vyberte **příznak**.

    Vybraných vláken jsou označeny. Teď můžete filtrovat, chcete-li zobrazit pouze vlákna s příznakem.
  
3.  V **paralelní sledování** okna, vyberte **zobrazit pouze s příznakem vlákna** tlačítko ![zobrazit vlákna s příznakem](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
    V seznamu se zobrazí pouze vlákna s příznakem.

    > [!TIP]
    > Po označena příznakem některá vlákna mohou klikněte pravým tlačítkem na řádek kódu v editoru kódu a zvolte **spustit vlákna s příznakem do pozice kurzoru**. Nezapomeňte vybrat, že kód, že všechna vlákna příznakem dosáhne. Visual Studio se pozastaví vláken na vybraný řádek kódu, usnadňují určit pořadí provedení [zmrazení a uvolnění vláken](#bkmk_freeze).

4.  Vyberte **zobrazit pouze s příznakem vlákna** tlačítko přepnete zpět do **zobrazit všechna vlákna** režimu.
    
5. Odstranění označení vlákna, kliknete pravým tlačítkem na jeden nebo více vlákna s příznakem v **paralelní sledování** okna a vyberte **Unflag**.

### <a name="bkmk_freeze"></a> Zablokovat a odblokovat vlákna provádění 

> [!TIP]
> Můžete zablokovat a odblokovat (pozastavení a obnovení) určit pořadí, ve kterém provádění vlákna pracovních vláken. To může pomoct vyřešit potíže se souběžností například zablokování a konflikty časování.
   
1.  V **paralelní sledování** okna se všechny řádky vybraný, klikněte pravým tlačítkem a vyberte **ukotvit**.

    V druhém sloupci se zobrazí ikona pozastavení pro každý řádek. Ikona pozastavení označuje, že vlákno je zmrazen.

2.  Zrušte výběr všech ostatních řádků tak, že vyberete pouze jeden řádek.

3.  Klikněte pravým tlačítkem na řádek a vyberte **uvolnit**.

    Ikona pozastavení zanikne na tento řádek, která udává, že vlákno je již zmrazen.

4.  Přepněte na editor kódu a stiskněte klávesu **F11**. Spouští pouze nezmrazený vlákno.

    Aplikace může také vytvořit instanci některá nová vlákna. Veškerá nová vlákna bez příznaku jsou a nejsou zmrazen.

### <a name="bkmk_follow_a_thread"></a> Postupujte podle jednoho vlákna s podmíněné zarážky

Může být užitečné sledovat provádění jedním vláknem v ladicím programu. Jednou z možností, které je zmrazení vlákna, které vás nezajímají. V některých případech budete muset postupovat podle jednoho vlákna bez zmrazení jiných vláken, například konkrétní chybu reprodukovat. Sledovat vlákna bez zmrazení ostatní vlákna, je třeba se vyvarovat rozdělení do kódu s výjimkou ve vlákně, které vás zajímají. Můžete to provést tak, že nastavíte [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Můžete nastavit zarážky v různých podmínkách, jako je například název vlákna nebo ID vlákna. To může být užitečné, je nastavit podmínku pro data, o kterém víte, že jsou jedinečné pro každé vlákno. Toto je běžný scénář ladění, ve které vás zajímají další některé konkrétní hodnoty dat než v žádné konkrétní vlákno.

1. Klikněte pravým tlačítkem na zarážku, kterou jste vytvořili dřív a vyberte **podmínky**.

2. V **nastavení zarážek** okno, zadejte `data == 5` podmíněného výrazu.

    ![Podmíněné zarážky](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Pokud vás zajímají další konkrétním vlákně, použijte název vlákna nebo ID vlákna pro podmínku. K tomu **nastavení zarážek** okně **filtr** místo **podmíněný výraz**a postupujte podle filtru tipy. Můžete chtít název vlákna v kódu aplikace, jak změnit ID vlákna po restartování ladicího programu.

3. Zavřít **nastavení zarážek** okna.

4. Vyberte restartování ![restartovat aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") tlačítko Restartovat ladicí relaci.

    Nechtě poškodíte do kódu ve vlákně, kde je hodnota proměnné data 5. V **paralelní sledování** okna, vyhledejte žlutá šipka označující aktuální kontext ladicího programu.

5. Teď můžete krokovat přes kód (**F10**) a krokování s vnořením do kódu (**F11**) a postupujte podle pokynů provádění jedno vlákno.

    Tak dlouho, dokud podmínka zarážky jsou jedinečné pro vlákno, a ladicí program nebude stiskněte tlačítko žádné zarážky na jiných vláknech (budete muset zakázat), můžete krokovat přes kódu a s vnořením do kódu bez přepnutí ostatní vlákna.

    > [!NOTE]
    > Při přechodu ladicí program se spustí všechna vlákna. Ladicí program však nebude proniknout do kódu v jiných vláknech, pokud jeden z jiných vláken narazí na zarážku. 
  
## <a name="see-also"></a>Viz také:  
[Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Postupy: Přepnutí na jiné vlákno během ladění](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
[Postupy: použití okna paralelní zásobníku](../debugger/using-the-parallel-stacks-window.md)  
[Postupy: Použití okna paralelního sledování](../debugger/how-to-use-the-parallel-watch-window.md)  
