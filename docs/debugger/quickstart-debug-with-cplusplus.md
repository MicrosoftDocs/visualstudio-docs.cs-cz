---
title: Ladění jazyka C++
description: Ladění nativního kódu pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 036774134f705d95fbc526a9e6a336ac43005820
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639773"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Rychlý úvod: Ladění v C++ pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoha výkonným funkcím, které vám pomůžou ladit vaše aplikace. Toto téma poskytuje rychlý způsob, jak Seznamte se s některými základními funkcemi.

## <a name="create-a-new-project"></a>Vytvoření nového projektu 

1. V sadě Visual Studio, zvolte **soubor > Nový projekt**.

2. V části **Visual C++**, zvolte **Windows Desktop**a potom v prostředním podokně vyberte **Konzolová aplikace Windows**.

    Pokud se nezobrazí **Konzolová aplikace Windows** šablony projektu, klikněte na tlačítko **otevřít instalační program Visual Studio** odkaz v levém podokně **nový projekt** dialogové okno. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací pomocí C++** úloh, klikněte na tlačítko **změnit**.

3. Zadejte název, například **MyDbgApp** a klikněte na tlačítko **OK**.

    Visual Studio vytvoří projekt.

4. V MyDbgApp.cpp nahraďte následujícím kódem

    ```c++
    int main()
    {
        return 0;
    }
    ```

    s tímto kódem (neodebírejte `#include "stdafx.h"`):

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

A *zarážku* je značku, která určuje, kde by měl Visual Studio pozastavit spuštěného kódu, se můžete podívat na hodnoty proměnných nebo chování paměti nebo zda je získávání běhových větve kódu. Je nejzákladnější funkce ladění.

1. Nastavit zarážku, klikněte na ovládací prvek vlevo od `doWork` volání funkce (nebo vyberte řádek kódu a stiskněte klávesu **F9**).

    ![Nastavit zarážku](../debugger/media/dbg-qs-set-breakpoint.png "nastavte zarážku")

2. Nyní stiskněte **F5** (nebo zvolte **ladit > Spustit ladění**).

    ![Na zarážku,](../debugger/media/dbg-qs-hit-breakpoint.png "na zarážku")

    Ladicí program pozastaví, kde nastavit zarážku. Příkaz, kde je pozastaven spuštění ladicího programu a aplikace je označen žlutou šipkou. Řádek s `doWork` ještě neprovedlo volání funkce.

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurzi, nebo pokud máte mnoho zarážky, které často projdete, použijte [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) abyste měli jistotu, že váš kód je pozastavený, pouze v případě, že jsou splněny konkrétní podmínky. Podmíněné zarážky šetří čas a můžete také usnadňují ladění problémů, které je těžké reprodukovat.

    Při pokusu o ladění chyby související s pamětí v jazyce C++, zarážky můžete použít také ke kontrole hodnoty adres (vyhledejte NULL) a odkazovat na počty. 

## <a name="navigate-code"></a>Vyhledání kódu

Existují různé příkazy dáte pokyn, aby ladicí program pokračovat. Ukážeme příkaz navigace užitečné kód, který je nového v sadě Visual Studio 2017.

Během pozastavení na zarážce, najeďte myší příkaz `c1.push_back(20)` až do zelené **běžet do kliknutí** tlačítko ![běžet do kliknutí](../debugger/media/dbg-tour-run-to-click.png "RunToClick") se zobrazí a potom stiskněte klávesu **Běžet do kliknutí** tlačítko.

![Běžet do kliknutí](../debugger/media/dbg-qs-run-to-click.png "běžet do kliknutí")

Aplikace pokračuje v provádění, volání `doWork`a pozastaví na řádek kódu, které jste klepnuli na tlačítku.

Běžné klávesové příkazy používá k procházejte kódem po krocích zahrnují **F10** a **F11**. Další podrobné pokyny najdete v tématu [Průvodce pro začátečníky](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Kontrolovat proměnné v datovém tipu

1. Na aktuálním řádku kódu (označená žlutou provádění ukazatel), najeďte myší `c1` objektu pomocí myši a zobrazit datatip.

    ![Zobrazit datatip](../debugger/media/dbg-qs-data-tip.png "zobrazit datatip")

    Datatip se dozvíte, aktuální hodnota `c1` proměnné a umožňuje vám umožní zkontrolovat její vlastnosti. Při ladění, pokud se zobrazí hodnotu, kterou nečekáte, pravděpodobně chyby v předchozích nebo volání řádků kódu. 

2. Rozbalení datového tipu se podívat na aktuální hodnoty vlastností `c1` objektu.

3. Pokud chcete oblast připnout datatip tak, aby se může nadále zobrazovat hodnota `c1` když je kód spuštěn, kliknutím na ikonu Připnutí malé. (Definovaného datového tipu můžete přesunout do vhodného umístění.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud zjistíte změnu, kterou chcete testovat ve vašem kódu, zatímco uprostřed relaci ladění, vám pomůžou, příliš.

1. Klikněte na druhou instanci `c2.front()` a změňte `c2.front()` k `c2.back()`.

2. Stisknutím klávesy **F10** (nebo **ladit > Krokovat s přeskočením**) několikrát k přechodu ladicí program a spusťte upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue.gif "upravit a pokračovat")

    **F10** přejde ladicí program jeden příkaz v době, ale postup přes funkce místo krokování do nich (kód, který můžete přeskočit, stále provádí).

Další informace o používání edit-and-continue a na omezení funkcí najdete v tématu [upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak spustit ladicí program, krokovat kód a můžete kontrolovat proměnné. Můžete chtít získat podrobný přehled funkcí ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [Prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md)
