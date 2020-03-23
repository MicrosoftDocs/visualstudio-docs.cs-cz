---
title: Ladění ASP.NET jádra
description: Ladění ASP.NET jádra pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bbe3d23301f0853626a930855acf4b595c6a2923
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75847877"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Úvodní příručka: Ladění ASP.NET jádra pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoho výkonných funkcí, které vám pomohou ladit aplikace. Toto téma poskytuje rychlý způsob, jak se naučit některé základní funkce.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

1. Otevřete sadu Visual Studio.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** chcete-li otevřít vyhledávací pole, zadejte **asp.net**, zvolte **Šablony**a pak zvolte Vytvořit novou ASP.NET **základní webovou aplikaci**. V zobrazeném dialogovém okně zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** v části **Visual C#** zvolte **Web**a potom v prostředním podokně zvolte ASP.NET **Základní webová aplikace**. Zadejte název jako **MyDbgApp** a klepněte na **tlačítko OK**.

    V zobrazeném dialogovém okně zvolte v prostředním podokně **webovou aplikaci** a klepněte na tlačítko **OK**.

    ![Výběr webové aplikace](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Pokud šablonu projektu **základní webové aplikace ASP.NET** nevidíte, přejděte na **nástrojové** > **nástroje a nástroje...**, který otevře Instalační službu sady Visual Studio. Zvolte **úlohu ASP.NET a vývoje webu a** pak zvolte **Změnit**.

    Visual Studio vytvoří projekt.

1. V Průzkumníku řešení otevřete About.cshtml.cs (v části Stránky/About.cshtml) a nahraďte následující kód

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    s tímto kódem:

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Nastavení zarážky

*Zarážka* je značka, která označuje, kde visual studio by měl pozastavit spuštěný kód, takže můžete podívat na hodnoty proměnných nebo chování paměti, nebo zda je či není větev kódu stále spuštěna. Jedná se o nejzákladnější funkci ladění.

1. Chcete-li nastavit zarážku, klepněte do `doWork` kanálu vlevo od funkce (nebo vyberte řádek kódu a stiskněte **klávesu F9**).

    ![Nastavení zarážky](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Zarážka je nastavena vlevo`{`od otevírací závorky ( ).

1. Nyní stiskněte **klávesu F5** (nebo zvolte **ladění > Spusťte ladění).**

1. Po načtení webové stránky klikněte v horní části webové stránky na odkaz **Informace.**

    Ladicí program pozastaví, kde nastavíte zarážku. Příkaz, kde je pozastaveno ladicí program a spuštění aplikace je označen žlutou šipkou. Řádek s otevírací závorkou (`{`) po deklaraci `doWork` funkce ještě nebyl proveden.

    ![Zásah do zarážky](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurzi, nebo pokud máte mnoho zarážek, které často krokovat, použijte [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a ujistěte se, že váš kód je pozastavena pouze při splnění určité podmínky. To šetří čas a může také usnadnit ladění problémů, které jsou obtížné reprodukovat.

## <a name="navigate-code"></a>Navigace v kódu

Existují různé příkazy, které dávají pokyn ladicímu programu, aby pokračoval. Zobrazujeme užitečný příkaz navigace kódu, který je k dispozici od visual studia 2017.

Při pozastavení na zarážky, najeďte `return c2` nad příkaz, dokud ![se](../debugger/media/dbg-tour-run-to-click.png) nezobrazí zelené tlačítko **Spustit kliknutím** Spustit na tlačítko A Klepněte na tlačítko a pak stisknutím tlačítka **Spustit klikněte.**

![Spustit a kliknout](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikace pokračuje v provádění a pozastaví se na řádku kódu, kde jste klikli na tlačítko.

Běžné klávesové příkazy používané k prostolých kódů zahrnují **F10** a **F11**. Podrobnější pokyny naleznete v [tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Kontrola proměnných v datovém tipu

1. V aktuálním řádku kódu (označené žlutýukazatel spuštění), `c2` najeďte myší nad objektem a zobrazte datatip.

    ![Zobrazení datového tipu](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Tip data zobrazuje aktuální hodnotu `c2` proměnné a umožňuje zkontrolovat její vlastnosti. Při ladění, pokud se zobrazí hodnota, kterou neočekáváte, pravděpodobně máte chybu v předchozích nebo volajících řádcích kódu.

2. Rozbalte datový tip a podívejte se `c2` na aktuální hodnoty vlastností objektu.

3. Pokud chcete připnout datový tip, abyste mohli `c2` při spuštění kódu nadále vidět hodnotu, klikněte na malou ikonu špendlíku. (Připnutý datový tip můžete přesunout na vhodné místo.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud identifikujete změnu, kterou chcete otestovat v kódu uprostřed relace ladění, můžete to udělat také.

1. V `OnGet` metodě klepněte na `result.First.Value` druhou `result.First.Value` `result.Last.Value`instanci a změňte na .

1. Stiskněte **klávesu F10** (nebo **Ladění > krok přes)** několikrát předem ladicí program a spustit upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Upravit a pokračovat")

    **F10** předem ladicí program jeden příkaz najednou, ale kroky přes funkce namísto krokování do nich (kód, který přeskočíte stále provádí).

Další informace o používání omezení pro úpravy a pokračování a o funkcích naleznete v tématu [Úpravy a pokračování](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Možná budete chtít získat na vysoké úrovni podívat na ladicí prvky spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
