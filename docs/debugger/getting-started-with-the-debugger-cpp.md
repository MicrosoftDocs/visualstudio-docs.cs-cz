---
title: 'Kurz: ladění C++ kódu'
description: Zjistěte, jak ke spuštění ladicího programu sady Visual Studio, krokovat kód a kontrolovat data.
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
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091805"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Kurz: Další informace k ladění kódu jazyka C++ pomocí sady Visual Studio

Tento článek obsahuje představení funkcí v ladicím programu sady Visual Studio podrobného návodu. Pokud chcete zobrazit vyšší úroveň funkcí ladicího programu, podívejte [se na téma první pohled na ladicí program](../debugger/debugger-feature-tour.md). Při *ladění aplikace*obvykle znamená, že máte spuštěnou aplikaci s připojeným ladicím programem. Když toto provedete, ladicí program poskytuje mnoho způsobů, jak zjistit, co kód dělá, při spuštění. Můžete procházet kódem a podívejte se na hodnoty uložené v proměnné, můžete nastavit hodinky na proměnné zobrazíte, když se změní hodnoty, můžete prozkoumat cesta provedení kódu naleznete v tématu, jestli větev kódu je spuštěná, a tak dále. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprosto začátečníky](../debugger/debugging-absolute-beginners.md) .

I C++když je ukázková aplikace, většina funkcí platí C#pro, Visual Basic, F#, Python, JavaScript a další jazyky, které podporuje Visual Studio (F# nepodporuje úpravy a pokračování. F#a jazyk JavaScript nepodporuje okno **Automatické** hodnoty. Snímky obrazovky jsou v C++.

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Spuštění ladicího programu a dosažení zarážky.
> * Další příkazy ke krokování kódu v ladicím programu
> * Kontrolovat proměnné v datových tipech a okno ladicího programu
> * Prozkoumat zásobník volání

## <a name="prerequisites"></a>Předpoklady

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou aplikaci Visual Studio 2019 a **vývoj C++ desktopových** aplikací.

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou aplikaci Visual Studio 2017 a **vývoj C++ desktopových** aplikací.

::: moniker-end

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **desktopový vývoj s C++**  úlohou a pak zvolte **Upravit**.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt C++ konzolové aplikace. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **vizuál C++**  a pak zvolte možnost **plocha systému Windows**. V prostředním podokně vyberte **Konzolová aplikace systému Windows**. Potom pojmenujte projekt *Get-Started-Debugging*.

     Pokud nevidíte šablonu projektu **Konzolová aplikace** , vyberte odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

4. Klikněte na tlačítko **OK**.

   Visual Studio otevře nový projekt.

::: moniker-end

::: moniker range="vs-2019"

1. Otevřete Visual Studio 2019.

   Pokud okno Start není otevřeno, vyberte **soubor** > **Spustit okno**.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Dále zvolte **C++** ze seznamu jazyk a v seznamu platforma zvolte možnost **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly** a klikněte na tlačítko **Další**.

   ![Zvolit C++ šablonu pro konzolovou aplikaci](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Pak v instalační program pro Visual Studio zvolte **vývoj desktopových aplikací C++ pomocí** úlohy.

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *příkaz Get-Started-Debugging* do pole **název projektu** . Pak zvolte **vytvořit**.

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *Get-Started-Debugging. cpp*nahraďte veškerý výchozí kód následujícím kódem:

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

## <a name="start-the-debugger"></a>Spuštění ladicího programu!

1. Stiskněte klávesu **F5** (**ladění > Spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění.

     **F5** spustí aplikaci s ladicím programem připojeným k procesu aplikace, ale nyní jsme ještě neudělali cokoli, co by bylo možné zkontrolovat kód. Proto pouze načítání aplikace a zobrazí výstup konzoly.

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

     V tomto kurzu vytvoříme podrobněji podíváme na tuto aplikaci pomocí ladicího programu a získejte funkce, podívejte se na ladicí program.

2. Ukončete ladicí program stisknutím tlačítka červené zastavení ![Zastavit ladění](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") (**SHIFT** + **F5**).

3. V okně konzoly stiskněte klávesu **a stisknutím** klávesy zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavte zarážku a spuštění ladicího programu

1. Ve `for` smyčce funkce `main` nastavte zarážku kliknutím na levý okraj následujícího řádku kódu:

    `name += letters[i];`

    Zarážka ![červeného kruhu se](../debugger/media/dbg-breakpoint.png "Zarážka") zobrazí tam, kde jste nastavili zarážku.

    Zarážky jsou jednou ze základních a základních funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde jste nastavili zarážku.

    ![Nastavte a použijte zarážku](../debugger/media/get-started-set-breakpoint-cpp.png)

    Žlutá šipka označuje příkaz na které ladicí program pozastaví, což také pozastaví provádění aplikace na stejném místě (Tento příkaz nebyl dosud proveden).

     Pokud aplikace ještě není spuštěná, spustí **F5** ladicí program a zastaví se na první zarážce. V opačném případě **F5** pokračuje v běhu aplikace na další zarážku.

    Zarážky jsou užitečná funkce, když znáte řádek kódu nebo části kódu, který chcete prozkoumat podrobněji. Informace o různých typech zarážek, které lze nastavit, například podmíněné zarážky, naleznete v tématu [using zarážek](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Vyhledání kódu v ladicím programu pomocí příkazů kroku

Většinou, klávesové zkratky tady používáme, protože je dobrým způsobem, jak získat rychlé při spuštění aplikace v ladicím programu (ekvivalentní příkazy jako je například nabídka příkazy jsou uvedeny v závorkách).

1. Při pozastavení ve smyčce `for` v metodě `main` stiskněte klávesu **F11** (nebo zvolte možnost **ladit > Krokovat s vnořením**), aby bylo možné přejít na `SendMessage` volání metody.

     Po stisknutí klávesy **F11** dvakrát byste měli být na tomto řádku kódu:

     `SendMessage(name, a[i]);`

1. Stiskněte klávesu **F11** ještě jednou pro krokování do `SendMessage` metody.

     Žlutý ukazatel se přesune do metody `SendMessage`.

     ![Krokovat s vnořením kódu pomocí klávesy F11](../debugger/media/get-started-f11-cpp.png "F10 Krokovat s vnořením")

     Klávesa F11 je **Krok do** příkazu a aplikace pokračuje v jednom příkazu v jednom okamžiku. F11 je dobrým způsobem, jak prozkoumat provádění toku v nejvíce podrobností. (K rychlejšímu přesunu kódu vám ukážeme i některé další možnosti.) Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../debugger/just-my-code.md)).

     Řekněme, že jste dokončili zkoumání `SendMessage` metody a chcete získat z metody, ale zůstat v ladicím programu. To můžete provést pomocí příkazu **Krok ven** .

1. Stiskněte **Shift** + **F11** (nebo **ladění > krokovat**).

     Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste se vrátit ve smyčce `for` v metodě `main`, která je pozastavena při volání metody `SendMessage`.

1. Několikrát stiskněte klávesu **F11** , dokud se znovu nevrátíte k volání metody `SendMessage`.

1. Když jste pozastavili volání metody, stiskněte **F10** (nebo zvolte **ladění > krokovat**s) jednou.

     ![Pro krokování kódu použijte F10](../debugger/media/get-started-step-over-cpp.png "F10 krok přes")

     Všimněte si, že ladicí program nekrokuje do metody `SendMessage`. **F10** posune ladicí program bez krokování do funkcí nebo metod v kódu aplikace (kód se pořád spustí). Stisknutím klávesy **F10** ve volání metody `SendMessage` (namísto **klávesy F11**) přeskočíme na implementační kód pro `SendMessage` (což by mohlo být v současnosti nedotčeno). Další informace o různých způsobech, jak přesouvat kód, naleznete v tématu [Navigace v kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Vyhledání kódu pomocí běžet do kliknutí

1. Stisknutím klávesy **F5** přejděte k zarážce.

1. V editoru kódu se posuňte dolů a najeďte myší na funkci `std::wcout` v metodě `SendMessage`, dokud se ![kliknutím](../debugger/media/dbg-tour-run-to-click.png "RunToClick") na tlačítko se zeleným tlačítkem **Spustit pro kliknutí** kliknete na tlačítko Zobrazit vlevo. V popisu tlačítka se zobrazí text spustit provádění na tomto místě.

     ![Použití funkce spustit pro kliknutí](../debugger/media/get-started-run-to-click-cpp.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **spustit do klikněte** je v [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]nového. (Pokud nevidíte zelenou šipku tlačítka, použijte klávesu **F11** v tomto příkladu, aby se ladicí program napředal na správné místo.)

2. Kliknutím na tlačítko **Spustit pro** klikněte na tlačítko ![Spustit](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Ladicí program přejde do funkce `std::wcout`.

    Pomocí tohoto tlačítka je podobné nastavení dočasné zarážky. **Možnost spustit pro** je užitečná pro rychlé seznámení v rámci viditelné oblasti kódu aplikace (můžete kliknout na libovolný otevřený soubor).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL** + **SHIFT** + **F5**).

Po stisknutí tlačítka **restartovat**ušetří čas oproti zastavování aplikace a restartování ladicího programu. Ladicí program pozastaví na první zarážce, kterou dosáhnete spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili ve smyčce `for`.

## <a name="inspect-variables-with-data-tips"></a>Kontrolovat proměnné s datových tipech

Funkce, které umožňují kontrolovat proměnné jsou jedním z nejužitečnějších funkce ladicího programu, a to různými způsoby. Při pokusu o ladění chyby se často, pokoušíte zjistit, zda jsou proměnné ukládání hodnot, které očekáváte, že ho, aby v určitou dobu.

1. Zatímco je pozastavený příkaz `name += letters[i]`, najeďte myší na proměnnou `letters` a uvidíte, že se jedná o výchozí hodnotu `size={10}`.

1. Rozbalením proměnné `letters` zobrazíte její vlastnosti, které zahrnují všechny prvky, které proměnná obsahuje.

1. Potom najeďte myší na proměnnou `name` a zobrazí se její aktuální hodnota, prázdný řetězec.

1. Několikrát stisknutím klávesy **F5** (nebo **ladění** > **pokračovat**) několikrát Iterujte pomocí `for` smyčky, opětovným pozastavením na zarážce a pokaždé, když se vrátíte na `name` proměnnou, a pokaždé, když chcete ověřit její hodnotu.

     ![Zobrazit Tip pro data](../debugger/media/get-started-data-tip-cpp.png "Zobrazit Tip pro data")

     Hodnota proměnné se mění u každé iterace `for` smyčky, zobrazuje hodnoty `f`a pak `fr`, `fre`a tak dále.

     Často při ladění, chcete rychle zkontrolovat hodnoty vlastností pro proměnné, chcete-li zobrazit, jestli jsou jejich ukládání hodnoty, které očekáváte, že je pro uložení, a datových tipech jsou dobrým způsobem, jak to udělat.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrolovat proměnné s okna Automatické hodnoty a místní hodnoty

1. Podívejte se na okno **Automatické** hodnoty v dolní části editoru kódu.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu výběrem možnosti **ladění** > **Windows** > **Automatické**hodnoty.

    V okně **Automatické** hodnoty vidíte proměnné a jejich aktuální hodnotu. Okno **Automatické** hodnoty zobrazuje všechny proměnné, které se používají na aktuálním řádku nebo na předchozím řádku (podívejte se na dokumentaci pro specifické chování jazyka).

1. Pak v okně **místní** hodnoty se podívejte na kartu vedle okna **Automatické** hodnoty.

1. Rozbalte proměnnou `letters` pro zobrazení prvků, které obsahuje.

     ![Kontrola proměnných v okně místních hodnot](../debugger/media/get-started-locals-window-cpp.png "Okno místních hodnot")

    V okně **místní** hodnoty se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), tj. aktuálním kontextem spuštění.

## <a name="set-a-watch"></a>Nastavení sledování

1. V hlavním okně editoru kódu klikněte pravým tlačítkem myši na proměnnou `name` a vyberte možnost **Přidat kukátko**.

    V dolní části editoru kódu se otevře okno **kukátko** . Okno **kukátka** můžete použít k určení proměnné (nebo výrazu), pro kterou chcete zachovat oči.

    Teď máte pro `name` proměnnou nastavenou kukátko a při procházení ladicího programu uvidíte její změnu hodnoty. Na rozdíl od ostatních oken proměnných se v okně **kukátka** vždy zobrazuje proměnné, které sledujete (v případě nedostatku rozsahu jsou šedé).

## <a name="examine-the-call-stack"></a>Prozkoumat zásobník volání

1. Při pozastavení ve smyčce `for` klikněte na okno **zásobník volání** , které je ve výchozím nastavení otevřené v pravém dolním podokně.

    Pokud je zavřena, otevřete ji v ladicím programu výběrem možnosti **ladění** > **Windows** > **zásobník volání**.

2. Klikněte několikrát na klávesu **F11** , dokud se nezobrazí pozastavení ladicího programu v metodě `SendMessage`. Podívejte se do okna **zásobník volání** .

    ![Kontrola zásobníku volání](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Okno **zásobník volání** zobrazuje pořadí, ve kterém jsou metody a funkce volány. V horním řádku se zobrazuje aktuální funkce (metoda `SendMessage` v této aplikaci). Druhý řádek ukazuje, že `SendMessage` bylo voláno z metody `main` atd.

   > [!NOTE]
   > Okno **zásobník volání** je podobné perspektivě ladění v některých prostředích, jako je například zatmění.

    Zásobník volání je dobrým způsobem, jak zkoumat a pochopit provádění toku aplikace.

    Dvojitým kliknutím na řádek kódu go, podívejte se na tento zdrojový kód a také změny v aktuálním oboru kontrolován ladicím programem. Tato akce nepřesouvejte vpřed ladicí program.

    Můžete také použít nabídky kliknutím pravým tlačítkem z okna **zásobník volání** k provedení dalších akcí. Můžete například vložit zarážky do určených funkcí, pokračovat v ladicím programu pomocí funkce **Run to Cursor**a přejít na zdrojový kód. Další informace naleznete v tématu [How to: Prohlédněte si zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku provádění

1. Stisknutím klávesy **F11** dvakrát spusťte funkci `std::wcout`.

1. Když je ladicí program pozastaven ve volání metody `SendMessage`, použijte myš k navýšení žluté šipky (ukazatel spuštění) na levé straně a přesuňte žlutou šipku o jeden řádek po návratu na `std::wcout`.

1. Stiskněte klávesu **F11**.

    Ladicí program znovu spustí funkci `std::wcout` (zobrazí se ve výstupu okna konzoly).

    Změnou provádění toku můžete provést kroky, jako je test cesty spuštění odlišný kód nebo znovu spustit kód bez restartování ladicího programu.

    > [!WARNING]
    > Často je potřeba pečlivě s touto funkcí a zobrazit upozornění v popisu. Příliš se může zobrazit další varování. Ukazatele nejde vrátit zpět aplikaci do předchozího stavu aplikace.

1. Stisknutím klávesy **F5** pokračujte v používání aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak spustit ladicí program, krokovat kód a můžete kontrolovat proměnné. Můžete chtít získat podrobný přehled funkcí ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)

