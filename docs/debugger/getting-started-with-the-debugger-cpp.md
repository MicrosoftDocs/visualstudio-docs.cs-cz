---
title: 'Kurz: Ladění kódu Jazyka C++'
description: Zjistěte, jak spustit ladicí program sady Visual Studio, krokovat kód a kontrolovat data.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b1a031a6c4e4e823a1fcc12aba228750aee27e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77091805"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Kurz: Naučte se ladit kód Jazyka C++ pomocí sady Visual Studio

Tento článek představuje funkce ladicího programu sady Visual Studio v podrobném návodu. Pokud chcete zobrazení ladicího programu na vyšší úrovni, [přečtěte si část První pohled na ladicí program](../debugger/debugger-feature-tour.md). Při *ladění aplikace*, obvykle znamená, že spouštějíte aplikaci s připojeným ladicím programem. Když toto uděláte, ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód dělá při jeho spuštění. Můžete krokovat kód a podívat se na hodnoty uložené v proměnných, můžete nastavit hodinky na proměnné, abyste viděli, kdy se hodnoty změní, můžete zkontrolovat cestu spuštění kódu, zjistit, zda je spuštěna větev kódu a tak dále. Pokud je to poprvé, co jste se pokusili ladit kód, můžete si přečíst [ladění pro absolutní začátečníky](../debugger/debugging-absolute-beginners.md) před procházením tohoto článku.

Přestože ukázková aplikace je C++, většina funkcí je použitelná pro C#, Visual Basic, F#, Python, JavaScript a další jazyky podporované Visual Studio (F# nepodporuje úpravy a pokračovat. F# a JavaScript nepodporují okno **Autos).** Snímky obrazovky jsou v jazyce C++.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Spusťte ladicí program a stisknete zarážky.
> * Naučte se příkazy pro krokovat kód v ladicím programu
> * Kontrola proměnných v datových tipech a oknech ladicího programu
> * Zkontrolujte zásobník volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou Visual Studio 2019 a vývoj plochy s úlohami **C++.**

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou Visual Studio 2017 a vývoj plochy s úlohami **C++.**

::: moniker-end

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte vývoj plochy s úlohami **C++** a pak zvolte **Změnit**.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt aplikace konzoly C++. Typ projektu je dodáván se všemi soubory šablon, které budete potřebovat, ještě předtím, než něco přidáte!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte **visual c++** a pak zvolte **Plochu Windows**. V prostředním podokně zvolte **Aplikace konzoly systému Windows**. Potom pojmenujte projekt *get-started-ladění*.

     Pokud šablonu projektu **konzolové aplikace** nevidíte, zvolte odkaz Otevřít instalační program **sady Visual Studio** v levém podokně dialogového okna Nový **projekt.** Spustí se instalační program pro Visual Studio. Zvolte **úlohu vývoje napříč platformami .NET Core** a pak zvolte **Změnit**.

4. Klikněte na tlačítko **OK**.

   Visual Studio otevře nový projekt.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

   Pokud úvodní okno není otevřené, zvolte Počáteční okno **souboru** > **Start Window**.

1. V počátečním okně zvolte **Vytvořit nový projekt**.

1. V okně **Vytvořit nový projekt** zadejte nebo zadejte *konzolu* do vyhledávacího pole. Dále zvolte **C++** ze seznamu Jazyk a pak zvolte **Windows** ze seznamu Platform. 

   Po použití filtrů jazyka a platformy zvolte šablonu **Konzolové aplikace** a pak zvolte **Další**.

   ![Výběr šablony Jazyka C++ pro konzolovou aplikaci](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Pokud šablonu **konzolové aplikace** nevidíte, můžete ji nainstalovat z okna **Vytvořit nový projekt.** Ve zprávě **Install more tools and features** **Nenajít to, co hledáte?** Potom v Instalační službě Visual Studia zvolte vývoj plochy s úlohami **jazyka C++.**

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte do pole Název **projektu** *přečtou a začínáme.* Potom zvolte **Vytvořit**.

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *souboru začínáme s laděním.cpp*nahraďte veškerý výchozí kód následujícím kódem:

    ```cpp
    #include <string>
    #include <vector>
    #include <iostream>

    void SendMessage(const std::wstring& name, int msg)
    {
        std::wcout << L"Hello, " << name << L"! Count to " << msg << std::endl;
    }

    int main()
    {
        std::vector<wchar_t> letters = { L'f', L'r', L'e', L'd', L' ', L's', L'm', L'i', L't', L'h' };
        std::wstring name = L"";
        std::vector<int> a(10);
        std::wstring key = L"";

        for (int i = 0; i < letters.size(); i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        std::wcin >> key;
        return 0;
    }
    ```

## <a name="start-the-debugger"></a>Spusťte ladicí program!

1. Stiskněte **klávesu F5** (**Ladění > Spustit ladění)** nebo tlačítko Spustit **ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů Ladění.

     **F5** spustí aplikaci s ladicím programem připojeným k procesu aplikace, ale právě teď jsme neudělali nic zvláštního, abychom prozkoumali kód. Takže aplikace se načte a uvidíte výstup konzoly.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     V tomto kurzu se blíže podíváme na tuto aplikaci pomocí ladicího programu a podíváme se na funkce ladicího programu.

2. Zastavte ladicí program stisknutím červeného tlačítka ![Stop Debugging](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") **(Shift** + **F5).**

3. V okně konzoly stiskněte klávesu a **Enter** zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavení zarážky a spuštění ladicího programu

1. Ve `for` smyčce `main` funkce nastavte zarážku klepnutím na levý okraj následujícího řádku kódu:

    `name += letters[i];`

    Tam, kde nastavíte zarážku, se zobrazí ![zarážka](../debugger/media/dbg-breakpoint.png "Zarážka") červeného kruhu.

    Zarážky jsou jedním z nejzákladnějších a základní funkce spolehlivé ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte **klávesu F5** nebo tlačítko **Start Ladění** Spustit ![ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde nastavíte zarážku.

    ![Nastavení a dosažení zarážky](../debugger/media/get-started-set-breakpoint-cpp.png)

    Žlutá šipka představuje příkaz, na kterém ladicí program pozastaven, který také pozastaví spuštění aplikace ve stejném bodě (tento příkaz ještě nebyl proveden).

     Pokud aplikace ještě není spuštěna, **F5** spustí ladicí program a zastaví se na první zarážky. V opačném případě **F5** pokračuje ve spuštění aplikace na další zarážku.

    Zarážky jsou užitečnou funkcí, pokud znáte řádek kódu nebo část kódu, kterou chcete podrobně prozkoumat. Informace o různých typech zarážek, které můžete nastavit, například podmíněné zarážky, naleznete [v tématu Použití zarážek](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigace v kódu v ladicím programu pomocí příkazů kroku

Většinou zde používáme klávesové zkratky, protože je to dobrý způsob, jak rychle spustit aplikaci v ladicím programu (ekvivalentní příkazy, jako jsou příkazy nabídky, jsou zobrazeny v závorce).

1. Při pozastavení ve `for` smyčce `main` v metodě stiskněte **klávesu F11** (nebo zvolte `SendMessage` ladění > krok **do**) dvakrát, abyste přešli na volání metody.

     Po stlačení **F11** dvakrát, měli byste být na tomto řádku kódu:

     `SendMessage(name, a[i]);`

1. Stisknutím **klávesy F11** ještě `SendMessage` jednou vstoupíte do metody.

     Žlutý ukazatel přepne `SendMessage` do metody.

     ![Použití F11 k kroku do kódu](../debugger/media/get-started-f11-cpp.png "F10 krok do")

     F11 je **krok do** příkazu a zálohy spuštění aplikace jeden příkaz najednou. F11 je dobrý způsob, jak prozkoumat tok provádění v nejpodrobněji. (Chcete-li se pohybovat rychleji prostřednictvím kódu, ukážeme vám také některé další možnosti.) Ve výchozím nastavení ladicí program přeskočí kód uživatele (pokud chcete další podrobnosti, přečtěte [si část Pouze můj kód).](../debugger/just-my-code.md)

     Řekněme, že jste hotovi `SendMessage` zkoumání metody a chcete se dostat z metody, ale zůstat v ladicím programu. Můžete to provést pomocí příkazu **Krok ven.**

1. Stiskněte **klávesu Shift** + **F11** (nebo **Ladění > krok ven).**

     Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste být `for` zpět ve `main` smyčce v `SendMessage` metodě, pozastaveno při volání metody.

1. Několikrát stiskněte `SendMessage` **klávesu F11,** dokud se znovu nevrátíte k volání metody.

1. Při pozastavení při volání metody stiskněte **f10** (nebo zvolte **Ladění > krok přes)** jednou.

     ![Použití kódu F10 k krokovacímu kroku](../debugger/media/get-started-step-over-cpp.png "F10 krok přes")

     Všimněte si, že tentokrát ladicí `SendMessage` program není krok do metody. **F10** posune ladicí program bez krokování do funkcí nebo metod v kódu aplikace (kód se stále spustí). Stisknutím **klávesy F10** při volání `SendMessage` metody (namísto **F11**) `SendMessage` jsme přeskočili kód implementace pro (což možná nemáme zájem právě teď). Další informace o různých způsobech procházení kódu najdete [v tématu Navigace v kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Přechod kódu pomocí příkazu Spustit ke kliknutí

1. Stisknutím **klávesy F5** přejděte na zarážku.

1. V editoru kódu přejděte dolů `std::wcout` a najeďte na funkci v `SendMessage` metodě, dokud se vlevo nezobrazí zelené tlačítko **Spustit** na tlačítko Spustit na tlačítko ![Klikněte.](../debugger/media/dbg-tour-run-to-click.png "RunToClick") Popis pro tlačítko zobrazuje "Spustit spuštění sem".

     ![Použití funkce Spustit pro kliknutí](../debugger/media/get-started-run-to-click-cpp.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **Spustit pro klepnutí** je v souboru [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]novinku. (Pokud zelené tlačítko se šipkou nevidíte, použijte v tomto příkladu **klávesu F11** a umístěte ladicí program na správné místo.)

2. Klepněte na tlačítko **Spustit a klepnout** ![na tlačítko](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Ladicí program přepočtou na `std::wcout` funkci.

    Použití tohoto tlačítka je podobné nastavení dočasné zarážky. **Spustit na tlačítko** je užitečné pro rychlé obcíní v rámci viditelné oblasti kódu aplikace (můžete kliknout v libovolném otevřeném souboru).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klepněte na tlačítko **Restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "Restartovat aplikaci") na panelu nástrojů Ladění **(Ctrl** + **Shift** + **F5).**

Po stisknutí tlačítka **Restart**ušetří tečas oproti zastavení aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážku, která je přístupná spuštěním kódu.

Ladicí program se znovu zastaví na zarážky, kterou jste dříve nastavili `for` uvnitř smyčky.

## <a name="inspect-variables-with-data-tips"></a>Kontrola proměnných pomocí datových špiček

Funkce, které umožňují kontrolovat proměnné, jsou jednou z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to udělat. Často při pokusu o ladění problému se pokoušíte zjistit, zda proměnné ukládají hodnoty, které očekáváte, že budou mít v určitém čase.

1. Při pozastavení příkazu `name += letters[i]` najeďte `letters` na proměnnou a uvidíte, `size={10}`že je to výchozí hodnota .

1. Rozbalte `letters` proměnnou, abyste viděli její vlastnosti, které zahrnují všechny prvky, které proměnná obsahuje.

1. Dále najeďte `name` na proměnnou a uvidíte její aktuální hodnotu, prázdný řetězec.

1. Stiskněte **klávesu F5** (nebo **Ladění** > **pokračovat**) několikrát `for` opakovat několikrát prostřednictvím smyčky, pozastavení znovu na `name` zarážky a najetím nad proměnnou pokaždé zkontrolovat jeho hodnotu.

     ![Zobrazení tipu na data](../debugger/media/get-started-data-tip-cpp.png "Zobrazení tipu na data")

     Hodnota proměnné se mění s každou `for` iterací `f`smyčky `fr`a `fre`zobrazuje hodnoty , then , then a tak dále.

     Často při ladění, chcete rychlý způsob, jak zkontrolovat hodnoty vlastností na proměnné, chcete-li zjistit, zda jsou ukládání hodnot, které očekáváte, že k uložení a data tipy jsou dobrý způsob, jak to udělat.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken Autos a Locals

1. Podívejte se na okno **Autos** v dolní části editoru kódu.

    Pokud je zavřená, otevřete ji, když je pozastavena v ladicím programu, a to výběrem **možnosti Ladění** > **automatických užitků****systému Windows** > .

    V okně **Autos** se zobrazí proměnné a jejich aktuální hodnota. Okno **Autos** zobrazuje všechny proměnné použité na aktuálním řádku nebo na předchozím řádku (Kontrola dokumentace pro chování specifické pro jazyk).

1. Dále se podívejte do okna **Locals** na kartě vedle okna **Autos.**

1. Rozbalte `letters` proměnnou a zobrazte prvky, které obsahuje.

     ![Kontrola proměnných v okně Locals](../debugger/media/get-started-locals-window-cpp.png "Místní okno")

    Místní **Locals** okno zobrazuje proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), to znamená aktuální kontext spuštění.

## <a name="set-a-watch"></a>Nastavení hodinek

1. V okně hlavního editoru kódu `name` klikněte pravým tlačítkem myši na proměnnou a zvolte **Přidat hodinky**.

    V dolní části editoru kódu se otevře okno **Kukátko.** Okno **Kukátko** můžete použít k určení proměnné (nebo výrazu), na kterou chcete dávat pozor.

    Nyní máte hodinky nastavit `name` na proměnnou a můžete vidět jeho změnu hodnoty při procházení ladicího programu. Na rozdíl od ostatních proměnných oken okno **kukátko** vždy zobrazuje proměnné, které sledujete (jsou šedě, když mimo rozsah).

## <a name="examine-the-call-stack"></a>Zkontrolujte zásobník volání

1. Při pozastavení ve `for` smyčce klikněte na okno **Zásobník volání,** které je ve výchozím nastavení otevřeno v pravém dolním podokně.

    Pokud je zavřená, otevřete ji, když se pozastavuje v ladicím programu, a to výběrem **možnosti Ladění** > **zásobníku volání systému****Windows** > .

2. Několikrát klikněte na **F11,** dokud se `SendMessage` v metodě nezobrazí pozastavení ladicího programu. Podívejte se na okno **Zásobník volání.**

    ![Zkontrolujte zásobník volání](../debugger/media/get-started-call-stack-cpp.png "ZkoumatCallStack")

    Okno **Zásobník volání** zobrazuje pořadí, ve kterém jsou volány metody a funkce. Horní řádek zobrazuje aktuální funkci `SendMessage` (metodu v této aplikaci). Druhý řádek ukazuje, že `SendMessage` `main` byl volán z metody a tak dále.

   > [!NOTE]
   > Okno **Zásobník volání** je podobné perspektivě ladění v některých IDE, jako je Eclipse.

    Zásobník volání je dobrý způsob, jak prozkoumat a pochopit tok spuštění aplikace.

    Můžete poklepat na řádek kódu jít podívat na tento zdrojový kód a že také změní aktuální obor kontrolovány ladicí program. Tato akce není předem ladicí program.

    Můžete také použít nabídky po kliknutí pravým tlačítkem myši z okna **Zásobník volání** k jiným věcem. Můžete například vložit zarážky do zadaných funkcí, předem ladicí program pomocí **Spustit kurzor**a přejít zkontrolovat zdrojový kód. Další informace naleznete v [tématu How to: Examine the Call Stack](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku spuštění

1. Dvakrát stiskněte **klávesu F11,** abyste ji spusťte. `std::wcout`

1. S ladicí program pozastaven `SendMessage` ve volání metody, pomocí myši uchopit žlutou šipku (ukazatel spuštění) na `std::wcout`levé straně a přesuňte žlutou šipku nahoru jeden řádek, zpět na .

1. Stiskněte **klávesu F11**.

    Ladicí program znovu `std::wcout` spustí funkci (vidíte to ve výstupu okna konzoly).

    Změnou toku spuštění můžete dělat věci, jako je testování různých cest spuštění kódu nebo znovu spustit kód bez restartování ladicího programu.

    > [!WARNING]
    > Často je třeba být opatrní s touto funkcí a zobrazí se upozornění v popisku. Můžete vidět i další varování. Přesunutí ukazatele nemůže vrátit aplikaci do dřívějšího stavu aplikace.

1. Dalším stisknutím **klávesy F5** pokračujte v spouštění aplikace.

    Gratulujeme k dokončení tohoto výukového programu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Možná budete chtít získat na vysoké úrovni podívat na ladicí prvky spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)

