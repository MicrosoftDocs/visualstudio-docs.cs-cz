---
title: 'Kurz: ladění kódu C++'
description: přečtěte si o funkcích ladicího programu Visual Studio a o tom, jak spustit ladicí program, krokovat kód a prozkoumat data v aplikaci C++.
ms.custom: debug-experiment,  vs-acquisition, get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5d3b4e277fc7ab2c97ccf72b7b1dd7898160c8d
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725557"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Kurz: Naučte se ladit kód C++ pomocí Visual Studio

v tomto článku se seznámíte s funkcemi ladicího programu Visual Studio v podrobném návodu. Pokud chcete zobrazit vyšší úroveň funkcí ladicího programu, podívejte [se na téma první pohled na ladicí program](../debugger/debugger-feature-tour.md). Při *ladění aplikace* obvykle znamená, že máte spuštěnou aplikaci s připojeným ladicím programem. Když to uděláte, ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód při spuštění dělá. Můžete krokovat kód a prohlédnout si hodnoty uložené v proměnných, můžete nastavit hodinky pro proměnné, abyste viděli, kdy se hodnoty mění, můžete zkontrolovat cestu spuštění kódu, zjistit, zda je spuštěna větev kódu a tak dále. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprosto začátečníky](../debugger/debugging-absolute-beginners.md) .

i když je ukázková aplikace C++, většina funkcí je platná pro C#, Visual Basic, F #, Python, JavaScript a další jazyky, které podporuje Visual Studio (F # nepodporuje funkci upravit a pokračovat. F # a JavaScript nepodporují okno **Automatické** hodnoty). Snímky obrazovky jsou v jazyce C++.

V tomto kurzu:

> [!div class="checklist"]
> * Spusťte ladicí program a zarážky volání.
> * Přečtěte si příkazy pro krokování kódu v ladicím programu
> * Kontrola proměnných v tipech k datům a v oknech ladicího programu
> * Kontrola zásobníku volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

musíte mít nainstalovanou Visual Studio 2019 a **desktopový vývoj s** využitím úlohy C++.

::: moniker-end
::: moniker range="vs-2017"

musíte mít nainstalovanou Visual Studio 2017 a **desktopový vývoj s** využitím úlohy C++.

::: moniker-end

::: moniker range="vs-2017"

pokud jste ještě nenainstalovali Visual Studio, pokračujte na stránku [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

pokud jste ještě nenainstalovali Visual Studio, pokračujte na stránku [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

pokud jste ještě nenainstalovali Visual Studio 2022 preview, můžete si ji nainstalovat zdarma na stránku [Visual Studio 2022 preview](https://visualstudio.microsoft.com/vs/preview/vs2022) .

::: moniker-end

pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, pokračujte v **nabídce nástroje**  >  **získat nástroje a funkce...**, které otevře Instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací pomocí C++** a pak zvolte **Upravit**.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt konzolové aplikace C++. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. v horním řádku nabídek vyberte **soubor** > **nový** > **Project**.

3. v dialogovém okně **nový Project** v levém podokně rozbalte položku **Visual C++** a pak zvolte možnost **Windows plocha**. v prostředním podokně vyberte **Windows konzolová aplikace**. Potom pojmenujte projekt *Get-Started-Debugging*.

     pokud nevidíte šablonu projektu **konzolová aplikace** , vyberte odkaz **otevřít Instalační program pro Visual Studio** v levém podokně dialogového okna **nový Project** . Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

4. Klikněte na **OK**.

   Visual Studio otevře nový projekt.

::: moniker-end

::: moniker range=">=vs-2019"

1. otevřete Visual Studio 2019.

   Pokud okno Start není otevřeno, klikněte **na tlačítko** > **Start okna**.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . dále v seznamu jazyk vyberte **C++** a v seznamu platforma zvolte **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly** a klikněte na tlačítko **Další**.

   ![Zvolit šablonu C++ pro konzolovou aplikaci](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . pak v Instalační program pro Visual Studio zvolte **vývoj desktopových aplikací pomocí C++** .

1. v okně **konfigurovat nový projekt** zadejte nebo zadejte *příkaz get-started-debugging* do pole **Project název** . Pak zvolte **vytvořit**.

   Visual Studio otevře nový projekt.

::: moniker-end

## <a name="create-the-application"></a>Vytvoření aplikace

1. V *Get-Started-Debugging. cpp* nahraďte veškerý výchozí kód následujícím kódem:

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

## <a name="start-the-debugger"></a>Spusťte ladicí program.

1. Stiskněte klávesu **F5** (**ladění > spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spuštění ladění") na panelu nástrojů ladění.

     **F5** spustí aplikaci s ladicím programem připojeným k procesu aplikace, ale nyní jsme ještě neudělali cokoli, co by bylo možné zkontrolovat kód. Takže se aplikace jenom načte a zobrazí se výstup z konzoly.

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

     V tomto kurzu se podíváme na tuto aplikaci s použitím ladicího programu a zjistíme, jak se podívat na funkce ladicího programu.

2. Ukončete ladicí program stisknutím tlačítka červené zastavení ![Zastavit ladění](../debugger/media/dbg-tour-stop-debugging.png "Zastavení ladění") (**SHIFT**  +  **F5**).

3. V okně konzoly stiskněte klávesu **a stisknutím** klávesy zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavit zarážku a spustit ladicí program

1. Ve `for` smyčce `main` funkce nastavte zarážku kliknutím na levý okraj následujícího řádku kódu:

    `name += letters[i];`

    Zarážka ![červeného kruhu se](../debugger/media/dbg-breakpoint.png "Zarážka") zobrazí tam, kde jste nastavili zarážku.

    Zarážky jsou jednou ze základních a základních funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spuštění ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde jste nastavili zarážku.

    ![Nastavení a volání zarážky](../debugger/media/get-started-set-breakpoint-cpp.png)

    Žlutá šipka představuje příkaz, na kterém je ladicí program pozastaven, což také pozastavuje spuštění aplikace ve stejném bodě (Tento příkaz ještě nebyl proveden).

     Pokud aplikace ještě není spuštěná, spustí **F5** ladicí program a zastaví se na první zarážce. V opačném případě **F5** pokračuje v běhu aplikace na další zarážku.

    Zarážky jsou užitečnou funkcí, když znáte řádek kódu nebo oddíl kódu, který chcete podrobně prošetřit. Informace o různých typech zarážek, které lze nastavit, například podmíněné zarážky, naleznete v tématu [using zarážek](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Procházení kódu v ladicím programu pomocí příkazů Step

Většinou používáme klávesové zkratky, protože je dobrým způsobem, jak rychle rychle spustit aplikaci v ladicím programu (ekvivalentní příkazy, jako jsou příkazy nabídky, se zobrazují v závorkách).

1. Při pozastavení ve `for` smyčce v `main` metodě stiskněte klávesu **F11** (nebo zvolte možnost **ladění > krokovat** s), aby bylo možné přejít k `SendMessage` volání metody.

     Po stisknutí klávesy **F11** dvakrát byste měli být na tomto řádku kódu:

     `SendMessage(name, a[i]);`

1. Stiskněte klávesu **F11** ještě jednou pro krokování do `SendMessage` metody.

     Žlutý ukazatel se přesune do `SendMessage` metody.

     ![Krokovat s vnořením kódu pomocí klávesy F11](../debugger/media/get-started-f11-cpp.png "F10 Step Into")

     Klávesa F11 je **Krok do** příkazu a aplikace pokračuje v jednom příkazu v jednom okamžiku. Klávesa F11 je dobrým způsobem, jak prostudovat tok spouštění v nejpodrobnějším podrobnostech. (K rychlejšímu přesunu kódu vám ukážeme i některé další možnosti.) Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../debugger/just-my-code.md)).

     Řekněme, že jste dokončili zkoumání `SendMessage` metody a chcete získat z metody, ale zůstat v ladicím programu. To můžete provést pomocí příkazu **Krok ven** .

1. Stiskněte **SHIFT**  +  **F11** (nebo **ladění > krokovat**).

     Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste se vrátit do `for` smyčky v `main` metodě, pozastavena při `SendMessage` volání metody.

1. Několikrát stiskněte klávesu **F11** , dokud se znovu nevrátíte k `SendMessage` volání metody.

1. Když jste pozastavili volání metody, stiskněte **F10** (nebo zvolte **ladění > krokovat** s) jednou.

     ![Pro krokování kódu použijte F10](../debugger/media/get-started-step-over-cpp.png "F10 Step Over")

     Všimněte si, že ladicí program nekrokuje do `SendMessage` metody. **F10** posune ladicí program bez krokování do funkcí nebo metod v kódu aplikace (kód se pořád spustí). Stiskem klávesy **F10** ve `SendMessage` volání metody (místo **klávesy F11**) jsme přeskočili na implementační kód pro `SendMessage` (což možná není zajímatme hned teď). Další informace o různých způsobech, jak přesouvat kód, naleznete v tématu [Navigace v kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Procházení kódu pomocí rutiny Run to Click

1. Stisknutím klávesy **F5** přejděte k zarážce.

1. V editoru kódu se posuňte dolů a umístěte ukazatel myši na `std::wcout` funkci v `SendMessage` metodě, dokud na něj ![neklikne](../debugger/media/dbg-tour-run-to-click.png "RunToClick") tlačítko zelený **běh** na tlačítko, které se zobrazí vlevo. V popisu tlačítka se zobrazí text spustit provádění na tomto místě.

     ![Použití funkce spustit pro kliknutí](../debugger/media/get-started-run-to-click-cpp.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **Run to Click** (Spustit do kliknutí) je v systému [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] nové. (Pokud nevidíte zelené tlačítko se šipkou, pomocí **klávesy F11** v tomto příkladu přesuňte ladicí program na správné místo.)

2. Klikněte na **tlačítko Run to Click (Spustit do kliknutí)** Run to Click ![(Spustit do kliknutí) a klikněte na .](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

    Ladicí program přejde do `std::wcout` funkce .

    Použití tohoto tlačítka se podobá nastavení dočasné zarážky. **Spuštění do kliknutí** je vhod, když se chcete rychle se dostat do viditelné oblasti kódu aplikace (můžete kliknout do libovolného otevřeného souboru).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Na panelu **nástrojů** ![ladění klikněte](../debugger/media/dbg-tour-restart.png "RestartApp") na tlačítko Restart Restart App (Restartovat aplikaci) (**Ctrl**  +  **Shift**  +  **F5**).

Když **stisknete Restart (Restartovat),** ušetříte tím čas místo zastavení aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážce, ke které došlo spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili uvnitř `for` smyčky.

## <a name="inspect-variables-with-data-tips"></a>Kontrola proměnných pomocí datových tipů

Funkce, které umožňují kontrolovat proměnné, jsou jednou z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to udělat. Často se při pokusu o ladění problému pokoušíte zjistit, jestli proměnné ukládají hodnoty, které očekáváte, že budou mít v konkrétním čase.

1. Při pozastavení příkazu `name += letters[i]` najeďte myší na proměnnou a zobrazí se výchozí `letters` hodnota `size={10}` .

1. Rozbalte `letters` proměnnou a zobrazte její vlastnosti, které zahrnují všechny prvky, které proměnná obsahuje.

1. Potom najeďte myší na proměnnou a zobrazí `name` se její aktuální hodnota – prázdný řetězec.

1. Několikrát **stiskněte klávesu F5** (nebo Pokračovat ladění), aby se několikrát iteroval smyčkou, znovu se pozasuoval na zarážce a při každém najetí myší na proměnnou   >   `for` `name` kontroloval její hodnotu.

     ![Zobrazení datového tipu](../debugger/media/get-started-data-tip-cpp.png "Zobrazení datového tipu")

     Hodnota proměnné se mění při každé iteraci smyčky a zobrazuje hodnoty `for` , pak , a tak `f` `fr` `fre` dále.

     Při ladění často potřebujete rychlý způsob, jak zkontrolovat hodnoty vlastností proměnných, abyste viděli, jestli ukládají hodnoty, které očekáváte, že budou uloženy, a datové tipy jsou dobrým způsobem, jak to udělat.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken Automatické hodnoty a Místní hodnoty

1. Podívejte se **na okno Automatické** funkce v dolní části editoru kódu.

    Pokud se zavře, otevřete ho při pozastavení v ladicím programu tak, že zvolíte  >  **Ladit a Windows**  >  **automaticky.**

    V okně **Automatické** hodnoty se zobrazí proměnné a jejich aktuální hodnota. V **okně Automatické** hodnoty se zobrazí všechny proměnné použité na aktuálním řádku nebo na předchozím řádku (zkontrolujte chování specifické pro jazyk v dokumentaci).

1. Pak se podívejte na **okno Místní** hodnoty na kartě vedle okna **Automatické** hodnoty.

1. Rozbalte `letters` proměnnou a zobrazte prvky, které obsahuje.

     ![Kontrola proměnných v okně Místní hodnoty](../debugger/media/get-started-locals-window-cpp.png "Místní hodnoty – okno")

    V **okně** Místní hodnoty se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), to znamená aktuální kontext spuštění.

## <a name="set-a-watch"></a>Nastavení hodinek

1. V hlavním okně editoru kódu klikněte pravým tlačítkem na proměnnou a `name` zvolte Přidat watch **(Přidat hodinku).**

    V dolní části editoru kódu se otevře okno Watch **(Sledování).** V okně **Watch** (Sledování) můžete zadat proměnnou (nebo výraz), kterou chcete sledovat.

    Teď máte pro proměnnou nastavenou hodinku a při pohybu v ladicím programu můžete vidět její `name` změnu hodnoty. Na rozdíl od ostatních oken proměnných se v okně Watch vždy zobrazují proměnné, které sledujete (když jsou mimo rozsah, jsou zašedné). 

## <a name="examine-the-call-stack"></a>Prozkoumání zásobníku volání

1. Pozastavené ve smyčce klikněte na okno Zásobník volání, které je ve výchozím nastavení `for` otevřené v pravém dolním podokně. 

    Pokud je uzavřený, otevřete ho při pozastavení v ladicím programu tak, že zvolíte Ladit  >  **Windows**  >  **zásobník volání**.

2. Několikrát **klikněte na F11,** dokud v metodě neuvidíte pozastavení ladicího `SendMessage` programu. Podívejte se na **okno Zásobník volání.**

    ![Prozkoumání zásobníku volání](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    V **okně Zásobník** volání se zobrazuje pořadí, ve kterém se volají metody a funkce. Horní řádek zobrazuje aktuální funkci `SendMessage` (metodu v této aplikaci). Druhý řádek ukazuje, `SendMessage` že byl volán z `main` metody a tak dále.

   > [!NOTE]
   > Okno **Zásobník volání** je podobné perspektivě ladění v některých prostředích ID, jako je Eclipse.

    Zásobník volání je dobrým způsobem, jak prozkoumat a pochopit tok provádění aplikace.

    Dvojitým kliknutím na řádek kódu se můžete podívat na zdrojový kód a tím se také změní aktuální obor prověřovaný ladicím programem. Tato akce neposoudí ladicí program.

    Můžete také použít nabídky po kliknutí pravým tlačítkem v okně Call Stack (Zásobník **volání)** a provést další věci. Můžete například vložit zarážky do zadaných funkcí, pomocí příkazu **Spustit** na kurzor přejít k ladicímu programu a prozkoumat zdrojový kód. Další informace najdete v tématu [Postupy: Prozkoumání zásobníku volání](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku provádění

1. Dvakrát **stiskněte klávesu F11,** aby se funkce `std::wcout` spouštěla.

1. Když je ladicí program pozastavený ve volání metody, pomocí myši uchopte žlutou šipku (ukazatel provádění) vlevo a přesuňte žlutou šipku o jeden řádek nahoru `SendMessage` zpět na `std::wcout` .

1. Stiskněte **klávesu F11**.

    Ladicí program znovu spustí funkci (uvidíte ji ve výstupu `std::wcout` okna konzoly).

    Změnou toku provádění můžete například testovat různé cesty provádění kódu nebo znovu spustit kód bez restartování ladicího programu.

    > [!WARNING]
    > S touto funkcí často musíte být opatrní a v popisu se zobrazí upozornění. Může se zobrazit i další upozornění. Přesunutí ukazatele nemůže vrátit aplikaci do dřívějšího stavu aplikace.

1. Stisknutím **klávesy F5** pokračujte v provozu aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, procházet kód a kontrolovat proměnné. Možná budete chtít získat podrobnější pohled na funkce ladicího programu spolu s odkazy na další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)

