---
title: Ladit spravovaný kód | Microsoft Docs
description: Ladění C# nebo Visual Basic pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: f790d30dc97d5549737c3c1cd003086477ce984f
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683008"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Rychlý Start: ladění pomocí jazyka C# nebo Visual Basic pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou s laděním aplikací. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

1. Otevřete Visual Studio a vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Pokud okno Start není otevřeno, klikněte **na tlačítko**  >  **Start okna**. V okně Start vyberte možnost **vytvořit nový projekt**.

    V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Potom v seznamu jazyk vyberte **C#** a pak v seznamu platforma zvolte **Windows** .

    Až použijete filtry jazyka a platformy, zvolte šablonu **Konzolová aplikace** pro .NET Core a pak zvolte **Další**.

    Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.

    Pokud nevidíte šablonu projektu **konzolové aplikace** pro .NET Core, přejděte do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual C#** zvolte **.NET Core** a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Core)**. Pak zadejte název jako **MyDbgApp** a klikněte na **OK**.

    Pokud nevidíte šablonu projektu **Konzolová aplikace (.NET Core)** , přejděte do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.
    ::: moniker-end

    Visual Studio vytvoří projekt.

1. V *program.cs* nebo *Module1. vb* nahraďte následující kód

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    tímto kódem:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > V Visual Basic se ujistěte, že je spouštěcí objekt nastavený na `Sub Main` (**vlastnosti > aplikace > spouštěcí objekt**).

## <a name="set-a-breakpoint"></a>Nastavení zarážky

*Zarážka* je značka, která označuje, kde má aplikace Visual Studio pozastavit běžící kód, abyste se mohli podívat na hodnoty proměnných nebo chování paměti nebo zda je nebo není větev kódu spouštěna. Je to nejzákladnější funkce ladění.

1. Chcete-li nastavit zarážku, klikněte na hřbet nalevo od `doWork` volání funkce (nebo vyberte řádek kódu a stiskněte **F9**).

    ![Nastavení zarážky](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Nastavení zarážky")

2. Nyní stiskněte klávesu **F5** (nebo zvolte **ladění > spustit ladění**).

    ![Stiskněte zarážku](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Stiskněte zarážku")

    Ladicí program pozastaví, kde jste nastavili zarážku. Příkaz, ve kterém je pozastavený ladicí program a spuštění aplikace, je označen žlutou šipkou. Řádek s `doWork` voláním funkce ještě nebyl proveden.

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurze, nebo pokud máte mnoho zarážek, které často procházíte, použijte [podmíněný bod přerušení](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a ujistěte se, že je váš kód pozastaven pouze v případě, že jsou splněny určité podmínky. Podmíněná zarážka může ušetřit čas a může také usnadnit ladění problémů, které je těžké rekládat.

## <a name="navigate-code"></a>Navigace v kódu

Existují různé příkazy k tomu, aby ladicí program mohl pokračovat. Zobrazujeme užitečný příkaz pro navigaci v kódu, který je k dispozici od začátku v aplikaci Visual Studio 2017.

Při pozastavení na zarážce umístěte ukazatel myši na příkaz, `c1.AddLast(20)` dokud se nezobrazí tlačítko ![Spustit](../debugger/media/dbg-tour-run-to-click.png "RunToClick") zeleným tlačítkem **Spustit pro kliknutí** , a pak stiskněte tlačítko **Spustit pro kliknutí** .

![Spustit kliknutím](../debugger/media/dbg-qs-run-to-click-csharp.png "Spustit kliknutím")

Aplikace pokračuje v provádění, volání `doWork` a pozastavení na řádku kódu, kde jste klikli na tlačítko.

Mezi běžné klávesové příkazy použité pro krokování kódu patří **F10** a **F11**. Podrobné pokyny najdete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-data-tip"></a>Kontrola proměnných v popisku dat

1. V aktuálním řádku kódu (označeného žlutým ukazatelem spuštění) umístěte ukazatel `c1` myši na objekt pomocí myši, aby se zobrazil Tip pro data.

    ![Zobrazit Tip pro data](../debugger/media/dbg-qs-data-tip-csharp.png "Zobrazit Tip pro data")

    Datový tip zobrazuje aktuální hodnotu `c1` proměnné a umožňuje zkontrolovat její vlastnosti. Pokud se při ladění zobrazí hodnota, kterou neočekáváte, pravděpodobně máte chybu v předchozím nebo volajícím řádku kódu.

2. Rozbalte tip data a podívejte se na aktuální hodnoty vlastností `c1` objektu.

3. Pokud chcete špičku dat připnout, abyste mohli i nadále vidět hodnotu `c1` při spouštění kódu, klikněte na ikonu malého kódu PIN. (Popis připnutých dat můžete přesunout do vhodného umístění.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud identifikujete změnu, kterou chcete testovat ve vašem kódu během relace ladění, můžete to udělat i vy.

1. Klikněte na druhou instanci `c2.First.Value` a změňte `c2.First.Value` na `c2.Last.Value` .

2. Stisknutím klávesy **F10** (nebo **ladění > Step over) několikrát zajděte** ladicí program a spusťte upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Upravit a pokračovat")

    **F10** posune ladicí program po jednom příkazu najednou, ale kroky nad funkcí místo do jejich krokování (kód, který přeskočíte, se pořád spustí).

Další informace o použití funkcí upravit a pokračovat a o omezeních funkcí najdete v tématu [Upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Můžete chtít získat nejdůležitější pohled na funkce ladicího programu společně s odkazy na Další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
