---
title: Ladění jazyka C++
description: Ladění nativního kódu pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b619b2b6c93da8be399b2fc35d81ffe226f408ad
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679405"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Úvodní příručka: Ladění pomocí jazyka C++ pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoho výkonných funkcí, které vám pomohou ladit aplikace. Toto téma poskytuje rychlý způsob, jak se naučit některé základní funkce.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** otevřete vyhledávací pole, zadejte **c++**, zvolte **Šablony**a pak zvolte Vytvořit nový **projekt konzolové aplikace**. V zobrazeném dialogovém okně zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** v části **Visual C++** zvolte **Plochu systému Windows**a potom v prostředním podokně zvolte Aplikace **konzoly systému Windows**. Potom zadejte název jako **MyDbgApp** a klepněte na tlačítko **OK**.
    ::: moniker-end

    Pokud šablonu projektu **aplikace konzoly systému Windows** nevidíte, přejděte na **nástrojové** > **nástroje a nástroje...**, který otevře Instalační službu sady Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte vývoj plochy s úlohami **C++** a pak zvolte **Změnit**.

    Visual Studio vytvoří projekt.

1. V souboru MyDbgApp.cpp nahraďte následující kód

    ```c++
    int main()
    {
        return 0;
    }
    ```

    s tímto kódem `#include "stdafx.h"`(neodstraňujte ):

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Nastavení zarážky

*Zarážka* je značka, která označuje, kde visual studio by měl pozastavit spuštěný kód, takže můžete podívat na hodnoty proměnných nebo chování paměti, nebo zda je či není větev kódu stále spuštěna. Jedná se o nejzákladnější funkci ladění.

1. Chcete-li nastavit zarážku, klepněte do `doWork` kanálu vlevo od volání funkce (nebo vyberte řádek kódu a stiskněte **klávesu F9**).

    ![Nastavení zarážky](../debugger/media/dbg-qs-set-breakpoint.png "Nastavení zarážky")

2. Nyní stiskněte **klávesu F5** (nebo zvolte **ladění > Spusťte ladění).**

    ![Zásah do zarážky](../debugger/media/dbg-qs-hit-breakpoint.png "Zásah do zarážky")

    Ladicí program pozastaví, kde nastavíte zarážku. Příkaz, kde je pozastaveno ladicí program a spuštění aplikace je označen žlutou šipkou. Řádek s `doWork` voláním funkce ještě nebyl proveden.

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurzi, nebo pokud máte mnoho zarážek, které často krokovat, použijte [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a ujistěte se, že váš kód je pozastavena pouze při splnění určité podmínky. Podmíněná zarážka šetří čas a může také usnadnit ladění problémů, které je obtížné reprodukovat.

    Při pokusu o ladění chyb souvisejících s pamětí v jazyce C++ můžete také použít zarážky ke kontrole hodnot adres (vyhledejte hodnotu NULL) a počty odkazů.

## <a name="navigate-code"></a>Navigace v kódu

Existují různé příkazy, které dávají pokyn ladicímu programu, aby pokračoval. Zobrazujeme užitečný příkaz navigace kódu, který je k dispozici od visual studia 2017.

Při pozastavení na zarážky, najeďte `c1.push_back(20)` nad příkaz, dokud se nezobrazí zelené tlačítko **Spustit kliknutím** ![Spustit na tlačítko A Klepněte](../debugger/media/dbg-tour-run-to-click.png "RunToClick") na tlačítko a pak stisknutím tlačítka Spustit **klikněte.**

![Spustit a kliknout](../debugger/media/dbg-qs-run-to-click.png "Spustit a kliknout")

Aplikace pokračuje v `doWork`provádění, volání a pozastavení na řádku kódu, kde jste klikli na tlačítko.

Běžné klávesové příkazy používané k prostolých kódů zahrnují **F10** a **F11**. Podrobnější pokyny naleznete v [tématu První pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Kontrola proměnných v datovém tipu

1. V aktuálním řádku kódu (označené žlutýukazatel spuštění), `c1` najeďte myší nad objektem a zobrazte datatip.

    ![Zobrazení datového tipu](../debugger/media/dbg-qs-data-tip.png "Zobrazení datového tipu")

    Tip data zobrazuje aktuální hodnotu `c1` proměnné a umožňuje zkontrolovat její vlastnosti. Při ladění, pokud se zobrazí hodnota, kterou neočekáváte, pravděpodobně máte chybu v předchozích nebo volajících řádcích kódu.

2. Rozbalte datový tip a podívejte se `c1` na aktuální hodnoty vlastností objektu.

3. Pokud chcete připnout datový tip, abyste mohli `c1` při spuštění kódu nadále vidět hodnotu, klikněte na malou ikonu špendlíku. (Připnutý datový tip můžete přesunout na vhodné místo.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud identifikujete změnu, kterou chcete otestovat v kódu uprostřed relace ladění, můžete to udělat také.

1. Klepněte na `c2.front()` druhou `c2.front()` instanci a změňte na `c2.back()`.

2. Stiskněte **klávesu F10** (nebo **Ladění > krok přes)** několikrát předem ladicí program a spustit upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue.gif "Upravit a pokračovat")

    **F10** předem ladicí program jeden příkaz najednou, ale kroky přes funkce namísto krokování do nich (kód, který přeskočíte stále provádí).

Další informace o používání omezení pro úpravy a pokračování a o funkcích naleznete v tématu [Úpravy a pokračování](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Možná budete chtít získat na vysoké úrovni podívat na ladicí prvky spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
