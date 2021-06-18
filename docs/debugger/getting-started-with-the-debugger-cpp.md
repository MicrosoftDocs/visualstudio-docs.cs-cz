---
title: 'Kurz: ladění kódu C++'
description: Přečtěte si o funkcích ladicího programu sady Visual Studio a o tom, jak spustit ladicí program, krokovat kód a kontrolovat data v aplikaci C++.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd02bbd2264720a5443807fb431b4dafa2a0a578
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306433"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Kurz: Naučte se ladit kód C++ pomocí sady Visual Studio

V tomto článku se seznámíte s funkcemi ladicího programu sady Visual Studio v podrobném podrobném návodu. Pokud chcete zobrazit vyšší úroveň funkcí ladicího programu, podívejte [se na téma první pohled na ladicí program](../debugger/debugger-feature-tour.md). Při *ladění aplikace* obvykle znamená, že máte spuštěnou aplikaci s připojeným ladicím programem. Když to uděláte, ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód při spuštění dělá. Můžete krokovat kód a prohlédnout si hodnoty uložené v proměnných, můžete nastavit hodinky pro proměnné, abyste viděli, kdy se hodnoty mění, můžete zkontrolovat cestu spuštění kódu, zjistit, zda je spuštěna větev kódu a tak dále. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprosto začátečníky](../debugger/debugging-absolute-beginners.md) .

I když je ukázková aplikace C++, většina funkcí je platná pro C#, Visual Basic, F #, Python, JavaScript a další jazyky, které podporuje Visual Studio (F # nepodporuje funkci upravit a pokračovat. F # a JavaScript nepodporují okno **Automatické** hodnoty). Snímky obrazovky jsou v jazyce C++.

V tomto kurzu:

> [!div class="checklist"]
> * Spusťte ladicí program a zarážky volání.
> * Přečtěte si příkazy pro krokování kódu v ladicím programu
> * Kontrola proměnných v tipech k datům a v oknech ladicího programu
> * Kontrola zásobníku volání

## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

Musíte mít nainstalovanou aplikaci Visual Studio 2019 a úlohu **vývoj desktopových aplikací v jazyce C++** .

::: moniker-end
::: moniker range="vs-2017"

Musíte mít nainstalovanou aplikaci Visual Studio 2017 a úlohu **vývoj desktopových aplikací v jazyce C++** .

::: moniker-end

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste ještě nenainstalovali Visual Studio 2022 Preview, nainstalujte ho zdarma na stránku [Visual studio 2022 Preview ke stažení](https://visualstudio.microsoft.com/vs/preview/vs2022) .

::: moniker-end

Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Spustí se instalační program pro Visual Studio. Zvolte **vývoj desktopových aplikací pomocí C++** a pak zvolte **Upravit**.

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt konzolové aplikace C++. Typ projektu se dodává se všemi soubory šablon, které budete potřebovat, než dokonce cokoli přidáte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio 2017.

2. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

3. V dialogovém okně **Nový projekt** v levém podokně rozbalte položku **Visual C++** a zvolte možnost **plocha systému Windows**. V prostředním podokně vyberte **Konzolová aplikace systému Windows**. Potom pojmenujte projekt *Get-Started-Debugging*.

     Pokud nevidíte šablonu projektu **Konzolová aplikace** , vyberte odkaz **otevřít instalační program pro Visual Studio** v levém podokně dialogového okna **Nový projekt** . Spustí se instalační program pro Visual Studio. Zvolte úlohu **vývoje .NET Core pro různé platformy** a pak zvolte **změnit**.

4. Klikněte na **OK**.

   Visual Studio otevře nový projekt.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete Visual Studio 2019.

   Pokud okno Start není otevřeno, klikněte **na tlačítko** > **Start okna**.

1. V okně Start vyberte možnost **vytvořit nový projekt**.

1. V okně **vytvořit nový projekt** zadejte do vyhledávacího pole nebo zadejte *Console* . Potom v seznamu jazyk vyberte **C++** a v seznamu platforma zvolte **Windows** . 

   Po použití filtrů jazyků a platforem zvolte šablonu **aplikace konzoly** a klikněte na tlačítko **Další**.

   ![Zvolit šablonu C++ pro konzolovou aplikaci](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Pokud nevidíte šablonu **konzolové aplikace** , můžete ji nainstalovat z okna **vytvořit nový projekt** . V části **nenajít, co hledáte?** klikněte na odkaz **instalovat další nástroje a funkce** . Pak v Instalační program pro Visual Studio zvolte **vývoj desktopových aplikací pomocí C++** .

1. V okně **Konfigurovat nový projekt** zadejte nebo zadejte *příkaz Get-Started-Debugging* do pole **název projektu** . Pak zvolte **vytvořit**.

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

1. Stiskněte klávesu **F5** (**ladění > spustit ladění**) nebo klikněte na tlačítko **Spustit** ladění ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění") na panelu nástrojů ladění.

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

2. Ukončete ladicí program stisknutím tlačítka červené zastavení ![Zastavit ladění](../debugger/media/dbg-tour-stop-debugging.png "Zastavit ladění") (**SHIFT**  +  **F5**).

3. V okně konzoly stiskněte klávesu **a stisknutím** klávesy zavřete okno konzoly.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Nastavit zarážku a spustit ladicí program

1. Ve `for` smyčce `main` funkce nastavte zarážku kliknutím na levý okraj následujícího řádku kódu:

    `name += letters[i];`

    Zarážka ![červeného kruhu se](../debugger/media/dbg-breakpoint.png "Bodu") zobrazí tam, kde jste nastavili zarážku.

    Zarážky jsou jednou ze základních a základních funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští.

2. Stiskněte klávesu **F5** nebo tlačítko **Spustit ladění** ![Spustit ladění](../debugger/media/dbg-tour-start-debugging.png "Spustit ladění"), spustí se aplikace a ladicí program se spustí na řádek kódu, kde jste nastavili zarážku.

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

     ![Krokovat s vnořením kódu pomocí klávesy F11](../debugger/media/get-started-f11-cpp.png "F10 Krokovat s vnořením")

     Klávesa F11 je **Krok do** příkazu a aplikace pokračuje v jednom příkazu v jednom okamžiku. Klávesa F11 je dobrým způsobem, jak prostudovat tok spouštění v nejpodrobnějším podrobnostech. (K rychlejšímu přesunu kódu vám ukážeme i některé další možnosti.) Ve výchozím nastavení přeskočí ladicí program neuživatelský kód (Pokud chcete více podrobností, přečtěte si téma [pouze můj kód](../debugger/just-my-code.md)).

     Řekněme, že jste dokončili zkoumání `SendMessage` metody a chcete získat z metody, ale zůstat v ladicím programu. To můžete provést pomocí příkazu **Krok ven** .

1. Stiskněte **SHIFT**  +  **F11** (nebo **ladění > krokovat**).

     Tento příkaz obnoví spuštění aplikace (a posune ladicí program), dokud se nevrátí aktuální metoda nebo funkce.

     Měli byste se vrátit do `for` smyčky v `main` metodě, pozastavena při `SendMessage` volání metody.

1. Několikrát stiskněte klávesu **F11** , dokud se znovu nevrátíte k `SendMessage` volání metody.

1. Když jste pozastavili volání metody, stiskněte **F10** (nebo zvolte **ladění > krokovat** s) jednou.

     ![Pro krokování kódu použijte F10](../debugger/media/get-started-step-over-cpp.png "F10 krok přes")

     Všimněte si, že ladicí program nekrokuje do `SendMessage` metody. **F10** posune ladicí program bez krokování do funkcí nebo metod v kódu aplikace (kód se pořád spustí). Stiskem klávesy **F10** ve `SendMessage` volání metody (místo **klávesy F11**) jsme přeskočili na implementační kód pro `SendMessage` (což možná není zajímatme hned teď). Další informace o různých způsobech, jak přesouvat kód, naleznete v tématu [Navigace v kódu v ladicím programu](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Procházení kódu pomocí rutiny Run to Click

1. Stisknutím klávesy **F5** přejděte k zarážce.

1. V editoru kódu se posuňte dolů a umístěte ukazatel myši na `std::wcout` funkci v `SendMessage` metodě, dokud na něj ![neklikne](../debugger/media/dbg-tour-run-to-click.png "RunToClick") tlačítko zelený **běh** na tlačítko, které se zobrazí vlevo. V popisu tlačítka se zobrazí text spustit provádění na tomto místě.

     ![Použití funkce spustit pro kliknutí](../debugger/media/get-started-run-to-click-cpp.png "Běžet do kliknutí")

   > [!NOTE]
   > Tlačítko **Spustit pro kliknutí** je v nástroji nového [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] . (Pokud nevidíte zelenou šipku tlačítka, použijte klávesu **F11** v tomto příkladu, aby se ladicí program napředal na správné místo.)

2. Kliknutím na tlačítko **Spustit pro** klikněte na tlačítko ![Spustit](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Ladicí program přejde do `std::wcout` funkce.

    Použití tohoto tlačítka je podobné nastavení dočasné zarážky. **Možnost spustit pro** je užitečná pro rychlé seznámení v rámci viditelné oblasti kódu aplikace (můžete kliknout na libovolný otevřený soubor).

## <a name="restart-your-app-quickly"></a>Rychlé restartování aplikace

Klikněte na tlačítko **restartovat** ![aplikaci](../debugger/media/dbg-tour-restart.png "RestartApp") na panelu nástrojů ladění (**CTRL**  +  **SHIFT**  +  **F5**).

Po stisknutí tlačítka **restartovat** ušetří čas oproti zastavování aplikace a restartování ladicího programu. Ladicí program se pozastaví na první zarážce, která je dosaženo spuštěním kódu.

Ladicí program se znovu zastaví na zarážce, kterou jste předtím nastavili uvnitř `for` smyčky.

## <a name="inspect-variables-with-data-tips"></a>Kontrola proměnných pomocí tipů k datům

Funkce, které umožňují kontrolu proměnných, jsou jedním z nejužitečnějších funkcí ladicího programu a existují různé způsoby, jak to provést. Pokud se při pokusu o ladění problému často pokusíte zjistit, zda proměnné ukládají hodnoty, které mají být v určitou dobu k dispozici.

1. Při pozastavení `name += letters[i]` příkazu, najeďte myší na `letters` proměnnou a uvidíte, že se jedná o výchozí hodnotu, `size={10}` .

1. Rozbalením `letters` proměnné zobrazíte její vlastnosti, které zahrnují všechny prvky, které proměnná obsahuje.

1. Potom najeďte myší na `name` proměnnou a uvidíte její aktuální hodnotu, prázdný řetězec.

1. Několikrát stiskněte klávesu **F5** (nebo pokračujte v **ladění**  >  ) několikrát k iterování několikrát přes smyčku a poklikáním `for` na zarážku, a pokaždé, když se podíváte na `name` proměnnou pokaždé, abyste zkontrolovali její hodnotu.

     ![Zobrazit Tip pro data](../debugger/media/get-started-data-tip-cpp.png "Zobrazit Tip pro data")

     Hodnota proměnné se mění v každé iteraci `for` smyčky, zobrazuje hodnoty `f` , potom `fr` , `fre` a tak dále.

     Při ladění budete často potřebovat rychlý způsob kontroly hodnot vlastností u proměnných, abyste viděli, zda ukládají hodnoty, které očekáváte pro uložení, a tipy k datům jsou vhodným způsobem.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Kontrola proměnných pomocí oken automatické hodnoty a místní hodnoty

1. Podívejte se na okno **Automatické** hodnoty v dolní části editoru kódu.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu, a to volbou **ladit**  >  **okna**  >  **Automatické** hodnoty.

    V okně **Automatické** hodnoty vidíte proměnné a jejich aktuální hodnotu. Okno **Automatické** hodnoty zobrazuje všechny proměnné, které se používají na aktuálním řádku nebo na předchozím řádku (podívejte se na dokumentaci pro specifické chování jazyka).

1. Pak v okně **místní** hodnoty se podívejte na kartu vedle okna **Automatické** hodnoty.

1. Rozbalte `letters` proměnnou pro zobrazení prvků, které obsahuje.

     ![Kontrola proměnných v okně místních hodnot](../debugger/media/get-started-locals-window-cpp.png "Okno místních hodnot")

    V okně **místní** hodnoty se zobrazí proměnné, které jsou v aktuálním [oboru](https://www.wikipedia.org/wiki/Scope_(computer_science)), tj. aktuálním kontextem spuštění.

## <a name="set-a-watch"></a>Nastavení kukátka

1. V hlavním okně editoru kódu klikněte pravým tlačítkem na `name` proměnnou a vyberte **Přidat kukátko**.

    V dolní části editoru kódu se otevře okno **kukátko** . Okno **kukátka** můžete použít k určení proměnné (nebo výrazu), pro kterou chcete zachovat oči.

    Teď máte pro proměnnou nastavenou kukátko `name` a při procházení ladicího programu můžete zobrazit jeho změnu hodnoty. Na rozdíl od ostatních oken proměnných se v okně **kukátka** vždy zobrazuje proměnné, které sledujete (v případě nedostatku rozsahu jsou šedé).

## <a name="examine-the-call-stack"></a>Kontrola zásobníku volání

1. Při pozastavení ve `for` smyčce klikněte na okno **zásobník volání** , které je ve výchozím nastavení otevřené v pravém dolním podokně.

    Pokud je zavřená, otevřete ji během pozastaveného ladicího programu výběrem možnosti **ladit**  >    >  **zásobník volání** systému Windows.

2. Klikněte několikrát na klávesu **F11** , dokud se nezobrazí pozastavení ladicího programu v `SendMessage` metodě. Podívejte se do okna **zásobník volání** .

    ![Kontrola zásobníku volání](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    Okno **zásobník volání** zobrazuje pořadí, ve kterém jsou metody a funkce volány. V horním řádku se zobrazuje aktuální funkce ( `SendMessage` metoda v této aplikaci). Druhý řádek ukazuje, který `SendMessage` byl volán z `main` metody a tak dále.

   > [!NOTE]
   > Okno **zásobník volání** je podobné perspektivě ladění v některých prostředích, jako je například zatmění.

    Zásobník volání je dobrým způsobem, jak prostudovat a pochopit tok spuštění aplikace.

    Dvakrát klikněte na řádek kódu, abyste se mohli podívat na zdrojový kód a zároveň změnit aktuální rozsah, který je kontrolován ladicím programem. Tato akce nepřejde do ladicího programu.

    Můžete také použít nabídky kliknutím pravým tlačítkem z okna **zásobník volání** k provedení dalších akcí. Můžete například vložit zarážky do určených funkcí, pokračovat v ladicím programu pomocí funkce **Run to Cursor** a přejít na zdrojový kód. Další informace naleznete v tématu [How to: Prohlédněte si zásobník volání](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Změna toku spuštění

1. Stiskněte klávesu **F11** dvakrát pro spuštění `std::wcout` funkce.

1. Když je ladicí program pozastaven ve `SendMessage` volání metody, použijte myš k navýšení žluté šipky (ukazatel spuštění) vlevo a přesuňte žlutou šipku o jeden řádek nahoru, zpět na `std::wcout` .

1. Stiskněte klávesu **F11**.

    Ladicí program znovu spustí `std::wcout` funkci (uvidíte ji ve výstupu okna konzoly).

    Změnou toku spuštění můžete provádět akce, jako je například testování různých cest spuštění kódu nebo opětovné spuštění kódu bez restartování ladicího programu.

    > [!WARNING]
    > Tuto funkci často potřebujete pečlivě a v popisu se zobrazí upozornění. Můžou se zobrazit i další upozornění. Přesunutí ukazatele nemůže vrátit aplikaci do dřívějšího stavu aplikace.

1. Stisknutím klávesy **F5** pokračujte v používání aplikace.

    Blahopřejeme k dokončení tohoto kurzu!

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak spustit ladicí program, krokovat kód a kontrolovat proměnné. Můžete chtít získat nejdůležitější pohled na funkce ladicího programu společně s odkazy na Další informace.

> [!div class="nextstepaction"]
> [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)

