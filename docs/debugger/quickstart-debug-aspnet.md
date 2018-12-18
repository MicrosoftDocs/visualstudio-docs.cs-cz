---
title: Ladění technologie ASP.NET
description: Ladění technologie ASP.NET pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636984"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Rychlý úvod: Ladění technologie ASP.NET v ladicím programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoha výkonným funkcím, které vám pomůžou ladit vaše aplikace. Toto téma poskytuje rychlý způsob, jak Seznamte se s některými základními funkcemi.

## <a name="create-a-new-project"></a>Vytvoření nového projektu 

1. V sadě Visual Studio, zvolte **soubor > Nový projekt**.

1. V části **Visual C#**, zvolte **webové**a potom v prostředním podokně vyberte **webové aplikace ASP.NET Core**.

1. Zadejte název, například **MyDbgApp** a klikněte na tlačítko **OK**.

1. V dialogovém okně, které se zobrazí, zvolte **webovou aplikaci** v prostředním podokně a pak klikněte na tlačítko **OK**.

     Pokud se nezobrazí **webovou aplikaci** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte **vývoj pro ASP.NET a web** úloh, klikněte na tlačítko **změnit**.

    ![Vyberte webovou aplikaci](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio vytvoří projekt.

1. V Průzkumníku řešení otevřete About.cshtml.cs (v rámci Pages/About.cshtml) a nahraďte následující kód

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

A *zarážku* je značku, která určuje, kde by měl Visual Studio pozastavit spuštěného kódu, se můžete podívat na hodnoty proměnných nebo chování paměti nebo zda je získávání běhových větve kódu. Je nejzákladnější funkce ladění.

1. Nastavit zarážku, klikněte na ovládací prvek vlevo od `doWork` – funkce (nebo vyberte řádek kódu a stiskněte klávesu **F9**).

    ![Nastavení zarážky](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Zarážka je nastavena na levé straně levou složenou závorku (`{`).

1. Nyní stiskněte **F5** (nebo zvolte **ladit > Spustit ladění**).

1. Po načtení webové stránky, klikněte na tlačítko **o** odkazu v horní části webové stránky.

    Ladicí program pozastaví, kde nastavit zarážku. Příkaz, kde je pozastaven spuštění ladicího programu a aplikace je označen žlutou šipkou. Řádek s levou složenou závorku (`{`) po `doWork` ještě neprovedlo deklarace funkce.

    ![Na zarážku](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurzi, nebo pokud máte mnoho zarážky, které často projdete, použijte [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) abyste měli jistotu, že váš kód je pozastavený, pouze v případě, že jsou splněny konkrétní podmínky. To šetří čas a můžete také usnadňují ladění problémů, které je těžké reprodukovat.

## <a name="navigate-code"></a>Vyhledání kódu

Existují různé příkazy dáte pokyn, aby ladicí program pokračovat. Ukážeme příkaz navigace užitečné kód, který je nového v sadě Visual Studio 2017.

Během pozastavení na zarážce, najeďte myší příkaz `return c2` až do zelené **běžet do kliknutí** tlačítko ![běžet do kliknutí](../debugger/media/dbg-tour-run-to-click.png) se zobrazí a potom stiskněte klávesu **běžet do kliknutí** tlačítko.

![Běžet do kliknutí](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Aplikace pokračuje v provádění kódu a pozastaví na řádek kódu, které jste klepnuli na tlačítku.

Běžné klávesové příkazy používá k procházejte kódem po krocích zahrnují **F10** a **F11**. Další podrobné pokyny najdete v tématu [Průvodce pro začátečníky](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Kontrolovat proměnné v datovém tipu

1. Na aktuálním řádku kódu (označená žlutou provádění ukazatel), najeďte myší `c2` objektu pomocí myši a zobrazit datatip.

    ![Zobrazit datatip](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Datatip se dozvíte, aktuální hodnota `c2` proměnné a umožňuje vám umožní zkontrolovat její vlastnosti. Při ladění, pokud se zobrazí hodnotu, kterou nečekáte, pravděpodobně chyby v předchozích nebo volání řádků kódu. 

2. Rozbalení datového tipu se podívat na aktuální hodnoty vlastností `c2` objektu.

3. Pokud chcete oblast připnout datatip tak, aby se může nadále zobrazovat hodnota `c2` když je kód spuštěn, kliknutím na ikonu Připnutí malé. (Definovaného datového tipu můžete přesunout do vhodného umístění.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud zjistíte změnu, kterou chcete testovat ve vašem kódu, zatímco uprostřed relaci ladění, vám pomůžou, příliš.

1. V `OnGet` metoda, klikněte na druhou instanci `result.First.Value` a změňte `result.First.Value` k `result.Last.Value`.

1. Stisknutím klávesy **F10** (nebo **ladit > Krokovat s přeskočením**) několikrát k přechodu ladicí program a spusťte upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "upravit a pokračovat")

    **F10** přejde ladicí program jeden příkaz v době, ale postup přes funkce místo krokování do nich (kód, který můžete přeskočit, stále provádí).

Další informace o používání edit-and-continue a na omezení funkcí najdete v tématu [upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak spustit ladicí program, krokovat kód a můžete kontrolovat proměnné. Můžete chtít získat podrobný přehled funkcí ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [Prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md)
