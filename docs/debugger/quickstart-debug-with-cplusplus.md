---
title: Ladit C++
description: Ladění nativního kódu pomocí ladicího programu sady Visual Studio
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8735ecd409eca2801b42b11bd3928a00e5191bf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840896"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Rychlý Start: ladění pomocí jazyka C++ pomocí ladicího programu sady Visual Studio

Ladicí program sady Visual Studio poskytuje mnoho výkonných funkcí, které vám pomůžou s laděním aplikací. Toto téma nabízí rychlý způsob, jak se naučit některé základní funkce.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **C++**, zvolte **šablony** a pak zvolte **vytvořit nový projekt konzolové aplikace**. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual C++** zvolte možnost **plocha systému Windows** a potom v prostředním podokně zvolte možnost **Konzolová aplikace systému Windows**. Pak zadejte název jako **MyDbgApp** a klikněte na **OK**.
    ::: moniker-end

    Pokud nevidíte šablonu projektu **Konzolová aplikace systému Windows** , přejděte do části **nástroje**  >  **získat nástroje a funkce...**, čímž otevřete instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací pomocí C++** a pak zvolte **Upravit**.

    Visual Studio vytvoří projekt.

1. V MyDbgApp. cpp nahraďte následující kód.

    ```c++
    int main()
    {
        return 0;
    }
    ```

    s tímto kódem (neodstraňujte `#include "stdafx.h"` ):

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

*Zarážka* je značka, která označuje, kde má aplikace Visual Studio pozastavit běžící kód, abyste se mohli podívat na hodnoty proměnných nebo chování paměti nebo zda je nebo není větev kódu spouštěna. Je to nejzákladnější funkce ladění.

1. Chcete-li nastavit zarážku, klikněte na hřbet nalevo od `doWork` volání funkce (nebo vyberte řádek kódu a stiskněte **F9**).

    ![Nastavení zarážky](../debugger/media/dbg-qs-set-breakpoint.png "Nastavení zarážky")

2. Nyní stiskněte klávesu **F5** (nebo zvolte **ladění > spustit ladění**).

    ![Stiskněte zarážku](../debugger/media/dbg-qs-hit-breakpoint.png "Stiskněte zarážku")

    Ladicí program pozastaví, kde jste nastavili zarážku. Příkaz, ve kterém je pozastavený ladicí program a spuštění aplikace, je označen žlutou šipkou. Řádek s `doWork` voláním funkce nebyl dosud proveden.

    > [!TIP]
    > Pokud máte zarážku ve smyčce nebo rekurze, nebo pokud máte mnoho zarážek, které často procházíte, použijte [podmíněný bod přerušení](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a ujistěte se, že je váš kód pozastaven pouze v případě, že jsou splněny určité podmínky. Podmíněná zarážka šetří čas a může také usnadnit ladění problémů, které je těžké rekládat.

    Při pokusu o ladění chyb souvisejících s pamětí v jazyce C++ můžete také použít zarážky pro kontrolu hodnot adres (hledání hodnoty NULL) a počty odkazů.

## <a name="navigate-code"></a>Navigace v kódu

Existují různé příkazy k tomu, aby ladicí program mohl pokračovat. Zobrazujeme užitečný příkaz pro navigaci v kódu, který je k dispozici od začátku v aplikaci Visual Studio 2017.

Při pozastavení na zarážce umístěte ukazatel myši na příkaz, `c1.push_back(20)` dokud se nezobrazí tlačítko ![Spustit](../debugger/media/dbg-tour-run-to-click.png "RunToClick") zeleným tlačítkem **Spustit pro kliknutí** , a pak stiskněte tlačítko **Spustit pro kliknutí** .

![Spustit kliknutím](../debugger/media/dbg-qs-run-to-click.png "Spustit kliknutím")

Aplikace pokračuje v provádění, volání `doWork` a pozastavení na řádku kódu, kde jste klikli na tlačítko.

Mezi běžné klávesové příkazy použité pro krokování kódu patří **F10** a **F11**. Podrobné pokyny najdete v tématu [první pohled na ladicí program](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Kontrola proměnných v DataTip

1. V aktuálním řádku kódu (označeného žlutým ukazatelem spuštění) umístěte ukazatel `c1` myši na objekt pomocí myši, aby se zobrazila DataTip.

    ![Zobrazit DataTip](../debugger/media/dbg-qs-data-tip.png "Zobrazit DataTip")

    DataTip zobrazí aktuální hodnotu `c1` proměnné a umožní vám zkontrolovat její vlastnosti. Pokud se při ladění zobrazí hodnota, kterou neočekáváte, pravděpodobně máte chybu v předchozím nebo volajícím řádku kódu.

2. Rozbalte DataTip a podívejte se na aktuální hodnoty vlastností `c1` objektu.

3. Pokud chcete DataTip připnout, abyste mohli i nadále vidět hodnotu `c1` při spouštění kódu, klikněte na ikonu malého kódu PIN. (Připnuté DataTip můžete přesunout do pohodlného umístění.)

## <a name="edit-code-and-continue-debugging"></a>Úprava kódu a pokračování ladění

Pokud identifikujete změnu, kterou chcete testovat ve vašem kódu během relace ladění, můžete to udělat i vy.

1. Klikněte na druhou instanci `c2.front()` a změňte `c2.front()` na `c2.back()` .

2. Stisknutím klávesy **F10** (nebo **ladění > Step over) několikrát zajděte** ladicí program a spusťte upravený kód.

    ![Upravit a pokračovat](../debugger/media/dbg-qs-edit-and-continue.gif "Upravit a pokračovat")

    **F10** posune ladicí program po jednom příkazu najednou, ale kroky nad funkcí místo do jejich krokování (kód, který přeskočíte, se pořád spustí).

Další informace o použití funkcí upravit a pokračovat a o omezeních funkcí najdete v tématu [Upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Můžete chtít získat nejdůležitější pohled na funkce ladicího programu společně s odkazy na Další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
