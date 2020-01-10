---
title: ASP.NET Core ladění
description: Ladění ASP.NET Core pomocí ladicího programu sady Visual Studio
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847877"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>Rychlý Start: ladění ASP.NET Core pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou s laděním aplikací. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

1. Otevřít Visual Studio.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **ASP.NET**, zvolte **šablony**a pak zvolte **vytvořit novou ASP.NET Core webovou aplikaci**. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **vizuál C#** zvolte možnost **Web**a potom v prostředním podokně zvolte **ASP.NET Core webová aplikace**. Zadejte název jako **MyDbgApp** a klikněte na **OK**.

    V dialogovém okně, které se zobrazí, zvolte možnost **Webová aplikace** v prostředním podokně a pak klikněte na tlačítko **OK**.

    ![Zvolit webovou aplikaci](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    Pokud nevidíte šablonu projektu **ASP.NET Core webové aplikace** , přejděte do části **nástroje** > **získat nástroje a funkce...** , který otevře instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu a** pak zvolte **Upravit**.

    Visual Studio vytvoří projekt.

1. V Průzkumník řešení otevřete About.cshtml.cs (pod položkou stránky/o. cshtml) a nahraďte následující kód

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

*Zarážka* je značka, která označuje, kde má aplikace Visual Studio pozastavit běžící kód, abyste se mohli podívat na hodnoty proměnných nebo chování paměti nebo zda je nebo není větev kódu spouštěna. Je to nejzákladnější funkce ladění.

1. Chcete-li nastavit zarážku, klikněte na hřbet nalevo od funkce `doWork` (nebo vyberte řádek kódu a stiskněte **F9**).

    ![Nastavení zarážky](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Zarážka je nastavena nalevo od levé složené závorky (`{`).

1. Nyní stiskněte klávesu **F5** (nebo zvolte **ladění > Spustit ladění**).

1. Po načtení webové stránky klikněte na odkaz **o informace** v horní části webové stránky.

    Ladicí program pozastaví, kde jste nastavili zarážku. Příkaz, ve kterém je pozastavený ladicí program a spuštění aplikace, je označen žlutou šipkou. Čára s levou složenou závorkou (`{`) po deklaraci funkce `doWork` ještě není spuštěná.

    ![Stiskněte zarážku](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurze, nebo pokud máte mnoho zarážek, které často procházíte, použijte [podmíněný bod přerušení](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a ujistěte se, že je váš kód pozastaven pouze v případě, že jsou splněny určité podmínky. Tím ušetříte čas a může také usnadnit ladění problémů, které je těžké reprodukovány.

## <a name="navigate-code"></a>Navigace v kódu

Existují různé příkazy k tomu, aby ladicí program mohl pokračovat. Zobrazujeme užitečný příkaz pro navigaci v kódu, který je k dispozici od začátku v aplikaci Visual Studio 2017.

Při pozastavení na zarážce umístěte ukazatel myši na příkaz `return c2`, dokud se nezobrazí zelené tlačítko **Spustit pro kliknutí** ![spustit, aby se zobrazilo](../debugger/media/dbg-tour-run-to-click.png), a potom stiskněte tlačítko **Spustit pro kliknutí** .

![Spustit kliknutím](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikace pokračuje v provádění a pozastaví na řádku kódu, kde jste klikli na tlačítko.

Mezi běžné klávesové příkazy použité pro krokování kódu patří **F10** a **F11**. Podrobné pokyny najdete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Kontrola proměnných v DataTip

1. V aktuálním řádku kódu (označeného žlutým ukazatelem spuštění) umístěte ukazatel myši na objekt `c2` s myší a zobrazí se DataTip.

    ![Zobrazit DataTip](../debugger/media/dbg-qs-data-tip-aspnet.png)

    DataTip zobrazí aktuální hodnotu proměnné `c2` a umožňuje zkontrolovat její vlastnosti. Pokud se při ladění zobrazí hodnota, kterou neočekáváte, pravděpodobně máte chybu v předchozím nebo volajícím řádku kódu.

2. Rozbalte DataTip a podívejte se na aktuální hodnoty vlastností objektu `c2`.

3. Pokud chcete DataTip připnout, abyste mohli i nadále zobrazovat hodnotu `c2` při spouštění kódu, klikněte na ikonu malého kódu PIN. (Připnuté DataTip můžete přesunout do pohodlného umístění.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud identifikujete změnu, kterou chcete testovat ve vašem kódu během relace ladění, můžete to udělat i vy.

1. V metodě `OnGet` klikněte na druhou instanci `result.First.Value` a změňte `result.First.Value` na `result.Last.Value`.

1. Stisknutím klávesy **F10** (nebo **ladění > Step over) několikrát zajděte**ladicí program a spusťte upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "Upravit a pokračovat")

    **F10** posune ladicí program po jednom příkazu najednou, ale kroky nad funkcí místo do jejich krokování (kód, který přeskočíte, se pořád spustí).

Další informace o použití funkcí upravit a pokračovat a o omezeních funkcí najdete v tématu [Upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak spustit ladicí program, krokovat kód a můžete kontrolovat proměnné. Můžete chtít získat podrobný přehled funkcí ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
