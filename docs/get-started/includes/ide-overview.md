---
ms.date: 07/01/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 007327dc525f515523f98323bc95e133209e1531
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113280082"
---
Integrované Visual Studio *je* kreativní spouštěcí panel, který můžete použít k úpravám, ladění a sestavování kódu a k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatými funkcemi, který lze použít pro mnoho aspektů vývoje softwaru. Kromě standardního editoru a ladicího programu, který poskytuje většina prostředí SCE, Visual Studio zahrnuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a mnoho dalších funkcí pro usnadnění procesu vývoje softwaru.

::: moniker range="vs-2017"

![Integrované vývojové Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Snímek obrazovky s Visual Studio IDE, který obsahuje popisky, které označují, kde jsou umístěné klíčové funkce" lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

Tento obrázek ukazuje Visual Studio s otevřeným projektem a několika okny klíčových nástrojů, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/use-solution-explorer.md) (vpravo nahoře) umožňuje zobrazit, procházet a spravovat soubory kódu. **Průzkumník řešení** vám může pomoct s uspořádáním kódu seskupením souborů do [řešení a projektů](../../ide/solutions-and-projects-in-visual-studio.md).

- V [okně editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (uprostřed), kde pravděpodobně strávíte většinu času, se zobrazí obsah souboru. Tady můžete upravovat kód nebo navrhovat uživatelské rozhraní, například okno s tlačítky a textová pole.

::: moniker range="vs-2017"

- V [okně Výstup](../../ide/reference/output-window.md) (dole uprostřed) posílá Visual Studio oznámení, jako jsou ladění a chybové zprávy, upozornění kompilátoru, stavové zprávy publikování a další. Každý zdroj zpráv má svou vlastní kartu.

::: moniker-end

- [Změny Gitu](/visualstudio/version-control/) (vpravo dole) umožňují sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) [a GitHub](https://docs.github.com/github).

## <a name="editions"></a>Edice

::: moniker range="vs-2017"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako Visual Studio 2017 a je optimalizovaný pro vývoj aplikací pro více platforem a mobilních aplikací. Tento článek se zaměřuje na Windows verzi Visual Studio 2017.

Existují tři edice Visual Studio: Community, Professional a Enterprise. Informace [o podporovaných Visual Studio jednotlivých edicích](https://visualstudio.microsoft.com/vs/compare/) najdete v tématu Porovnání edicí.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má řadu stejných funkcí jako Visual Studio 2019 a je optimalizovaný pro vývoj aplikací pro více platforem a mobilních aplikací. Tento článek se zaměřuje na Windows verzi Visual Studio 2019.

Existují tři edice Visual Studio 2019: Community, Professional a Enterprise. Informace [o podporovaných Visual Studio jednotlivých edicích](https://visualstudio.microsoft.com/vs/compare/) najdete v tématu Porovnání edicí.

::: moniker-end

## <a name="popular-productivity-features"></a>Oblíbené funkce produktivity

Mezi oblíbené funkce v Visual Studio, které vám pomůžou být produktivnější při vývoji softwaru, patří:

- Squiggles and [Quick Actions](../../ide/quick-actions.md)

   Podtržení vlnovkou vás při psaní upozorní na chyby nebo potenciální problémy v kódu. Tato vizuální vodítka umožňují okamžitě opravit problémy, aniž byste čekali, až se chyba objeví během sestavování nebo při spuštění programu. Pokud najedete myší na podmyšlku, zobrazí se další informace o chybě. Na levém okraji se může objevit žárovka s akcemi, které se označuje jako Rychlé akce, které chybu opraví.

   ![Stříkáte v Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Vyčištění kódu

   Kliknutím na tlačítko naformátovat kód a aplikovat všechny opravy kódu navrhované nastavením stylu [kódu,](../../ide/reference/options-text-editor-csharp-formatting.md) [konvencemi .editorconfig](../../ide/create-portable-custom-editor-options.md)a analyzátory [Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Vyčištění kódu** vám pomůže vyřešit problémy v kódu před tím, než přejde ke revize kódu. (Aktuálně je k dispozici pouze pro kód jazyka C#.)

   ![Tlačítko Vyčištění kódu v Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako je inteligentní přejmenování proměnných, extrahování jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ![Refaktoring v sadě Visual Studio](../media/refactoring-menu.png)

- [Intellisense](../../ide/using-intellisense.md)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech za vás píšou malé části kódu. Je to jako mít základní dokumentaci přímo v editoru, což vám ušetří, abyste museli hledat informace o typech jinde. Funkce IntelliSense se liší podle jazyka. Další informace najdete v tématu [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense,](../../ide/visual-cpp-intellisense.md) [JavaScript IntelliSense](../../ide/javascript-intellisense.md)a [Visual Basic IntelliSense.](../../ide/visual-basic-specific-intellisense.md) Následující obrázek znázorňuje, jak IntelliSense zobrazuje seznam členů pro typ:

   ![Visual Studio Seznam členů](../media/intellisense-list-members.png)

- [Visual Studio hledání](../../ide/visual-studio-search.md)

   Visual Studio se může občas zdát zahlcující s tolika nabídkami, možnostmi a vlastnostmi. Visual Studio vyhledávání (**Ctrl** Q ) je skvělý způsob, jak rychle najít funkce a kód integrovaného vývojového prostředí na jednom + místě.

   ::: moniker range="vs-2017"

   ![Snadné spuštění vyhledávacího pole ve Visual Studio 2017](../media/quick-launch-nuget.png)

   Další informace najdete v tématu [Snadné spuštění](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Vyhledávací pole v Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

    Informace a tipy pro zvýšení produktivity najdete v [tématu Jak používat Visual Studio vyhledávání.](../../ide/visual-studio-search.md)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Upravovat a ladit v reálném čase společně s ostatními bez ohledu na to, jaký typ aplikace nebo programovací jazyk máte. Svůj projekt můžete okamžitě a bezpečně sdílet a podle potřeby také ladicí relace, instance terminálů, webové aplikace místního hostitele, hlasové hovory a další.

- [Hierarchie volání](../../ide/reference/call-hierarchy.md)

   V **okně Hierarchie** volání se zobrazují metody, které volají vybranou metodu. To může být užitečné, když uvažujete o změně nebo odebrání metody nebo když se snažíte najít chybu.

   ![Okno Hierarchie volání](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vám pomůže najít odkazy na kód, změny kódu, propojené chyby, pracovní položky, recenze kódu a testy jednotek, a to vše bez opuštění editoru.

   ![CodeLens](../media/codelens-overview.png)

- [Přejít k definici](../../ide/go-to-and-peek-definition.md)

   Funkce Přejít k definici vás přesouvá přímo do umístění, kde je definována funkce nebo typ.

   ![Přejít k definici](../media/go-to-definition-menu.png)

- [Náhled definice](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Okno **Náhled definice** zobrazuje definici metody nebo typu, aniž by se ve skutečnosti otevřel samostatný soubor.

   ![Náhled do definice](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalace integrovaného vývojového Visual Studio (IDE)

V této části vytvoříte jednoduchý projekt, který vám umožní vyzkoušet si některé z věcí, které můžete s Visual Studio. [IntelliSense](../../ide/using-intellisense.md) použijete jako pomůcku pro kódování, budete ladit aplikaci, abyste viděli hodnotu proměnné během provádění programu, a změníte barevný motiv.

::: moniker range="vs-2017"

Pokud chcete začít, [stáhněte Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat úlohy *,* což jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle [kroků pro vytvoření programu,](#create-a-program)nezapomeňte během instalace vybrat úlohu vývoj pro různé platformy v **.NET Core.**

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete začít, [stáhněte Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat úlohy *,* což jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle [kroků pro vytvoření programu,](#create-a-program)nezapomeňte během instalace vybrat úlohu vývoj pro různé platformy v **.NET Core.**

::: moniker-end

![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Když aplikaci Visual Studio poprvé, můžete se volitelně [](../../ide/signing-in-to-visual-studio.md) přihlásit pomocí svého pracovního účet Microsoft nebo školního účtu.

## <a name="create-a-program"></a>Vytvoření programu

Pojďme se ponořit do jednoduchého programu.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. V řádku nabídek  zvolte Soubor > **Nový** > **Project**.

   ![Soubor > Nový Project řádku nabídek](../media/file-new-project-menu.png)

   Dialogové **okno Project** obsahuje několik šablon *projektů*. Šablona obsahuje základní soubory a nastavení potřebné pro daný typ projektu.

1. V části Visual **C#** zvolte kategorii šablony **.NET Core** a pak zvolte šablonu **Konzolová aplikace (.NET Core).** Do **textového** pole Název zadejte **HelloWorld** a pak vyberte **tlačítko OK.**

   ![Šablona aplikace .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Pokud nevidíte kategorii **.NET Core,** musíte nainstalovat úlohu vývoj pro **různé platformy v .NET Core.** Chcete-li to provést, **Instalační program pro Visual Studio** v levém dolním rohu dialogového okna **Nový** Project. Po Instalační program pro Visual Studio se posuňte dolů, vyberte úlohu vývoj pro **různé platformy v .NET Core** a pak vyberte **Upravit.**

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci typu "Hello World", která volá metodu , která zobrazí řetězec literálu <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" v okně konzoly (výstup programu).

   Za chvíli by se mělo zobrazit něco podobného:

   ![Visual Studio – sada IDE](../media/overview-ide-console-app.png)

   Kód jazyka C# pro vaši aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text se automaticky obarizuje, aby indikuje různé části kódu, například klíčová slova a typy. Kromě toho malé svislé přerušované řádky v kódu označují, které složené závorky se navzájem shodují, a čísla řádků vám pomůžou vyhledat kód později. Pro sbalení nebo rozbalení bloků kódu můžete zvolit malé a krabicové znaménko minus. Tato funkce osnovy kódu umožňuje skrýt kód, který nepotřebujete, což pomáhá minimalizovat nepotřebné informace na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně s názvem **Průzkumník řešení**.

   ![Visual Studio Integrované vývojové prostředí s červenými rámečky](../media/overview-ide-console-app-red-boxes.png)

   K dispozici jsou i další nabídky a okna nástrojů, ale pojďme se teď pustit dál.

1. Teď spusťte aplikaci. Můžete to provést tak, že v  **nabídce Ladit** na řádku nabídek zvolíte Spustit bez ladění. Můžete také stisknout **Ctrl** + **F5**.

   ![Spuštění > ladění bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se **zprávou Hello World!**. Teď máte spuštěnou aplikaci.

   ![Snímek obrazovky cmd.exe konzoly s výstupem "Hello Word!" a pokračujte stisknutím libovolné klávesy.](../media/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Přidejme do aplikace další kód. Před řádek s kódem přidejte následující kód jazyka `Console.WriteLine("Hello World!");` C#:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazí v okně konzoly what is your name? (Jaké je vaše **jméno?)** a potom počká, dokud uživatel nezadá nějaký text následovaný **klávesou Enter.**

1. Změňte řádek, který `Console.WriteLine("Hello World!");` říká , na následující kód:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu tak, že **vyberete** > **Spustit ladění bez ladění** nebo **stisknete Ctrl** + **F5**.

   Visual Studio aplikaci znovu sestavíte a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. V okně konzoly zadejte své jméno a stiskněte **Enter.**

   ![Vstup okna konzoly](../media/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Zobrazí se úvodní okno s různými možnostmi pro klonování, otevření nedávného projektu nebo vytvoření zcela nového projektu.

1. Zvolte **Create a new project (Vytvořit nový projekt).**

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Snímek obrazovky okna Vytvořit nový projekt v Visual Studio 2019":::

   Otevře **se okno Vytvořit nový** projekt s několika šablonami *projektů.* Šablona obsahuje základní soubory a nastavení vyžadované pro daný typ projektu.

1. Pokud chcete najít šablonu, kterou chceme, zadejte nebo zadejte do vyhledávacího pole **konzolu .net** core. Seznam dostupných šablon se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dále filtrovat tak, že  v rozevíracím seznamu Všechny jazyky zvolíte **C#,** ze seznamu Všechny platformy vyberete **Windows** a ze seznamu Všechny typy projektů vyberete  **Konzola.** 

    Vyberte šablonu **Konzolová aplikace** a potom klikněte na **Další.**

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Snímek obrazovky okna Vytvořit nový projekt v Visual Studio 2019, kde vyberete požadovanou šablonu":::

1. V **okně Configure your new project** (Konfigurovat nový projekt) zadejte do pole Project name (Název **souboru)** text **HelloWorld,** volitelně změňte umístění adresáře pro soubory projektu (výchozí národní prostředí je ) a pak klikněte `C:\Users\<name>\source\repos` na Next **(Další).**

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Snímek obrazovky s oknem Konfigurovat nový projekt Visual Studio 2019, kde zadáte název projektu":::

1. V okně Další **informace** ověřte, že se v rozevírací  nabídce Cílová rozhraní zobrazuje **.NET Core 3.1,** a pak klikněte na **Vytvořit.**

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Snímek obrazovky s oknem Další informace v Visual Studio 2019, kde vyberete požadovanou verzi rozhraní .NET Core Framework":::

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci typu "Hello World", která volá metodu , která zobrazí řetězec literálu <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" v okně konzoly (výstup programu).

   Za chvíli by se mělo zobrazit něco podobného:

   ![Visual Studio – sada IDE](../media/vs-2019/overview-ide-console-app.png)

   Kód jazyka C# pro vaši aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text se automaticky obarizuje, aby indikuje různé části kódu, například klíčová slova a typy. Kromě toho malé svislé přerušované řádky v kódu označují, které složené závorky se navzájem shodují, a čísla řádků vám pomůžou vyhledat kód později. Pro sbalení nebo rozbalení bloků kódu můžete zvolit malé a krabicové znaménko minus. Tato funkce osnovy kódu umožňuje skrýt kód, který nepotřebujete, což pomáhá minimalizovat nepotřebné informace na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně s názvem **Průzkumník řešení**.

   ![Visual Studio Integrované vývojové prostředí s červenými rámečky](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   K dispozici jsou i další nabídky a okna nástrojů, ale pojďme se teď pustit dál.

1. Teď spusťte aplikaci. Můžete to provést tak, že v  **nabídce Ladit** na řádku nabídek zvolíte Spustit bez ladění. Můžete také stisknout **Ctrl** + **F5**.

   ![Spuštění > ladění bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se **zprávou Hello World!**. Teď máte spuštěnou aplikaci.

   ![Snímek obrazovky Microsoft Visual Studio konzoly ladění zobrazující výstup "Hello Word!" a stisknutím libovolné klávesy toto okno zavřete.](../media/vs-2019/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Přidejme do aplikace další kód. Před řádek s kódem přidejte následující kód jazyka `Console.WriteLine("Hello World!");` C#:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazí v okně konzoly what is your name? (Jaké je vaše **jméno?)** a potom počká, dokud uživatel nezadá nějaký text následovaný **klávesou Enter.**

1. Změňte řádek, který `Console.WriteLine("Hello World!");` říká , na následující kód:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu tak, že **vyberete** > **Spustit ladění bez ladění** nebo **stisknete Ctrl** + **F5**.

   Visual Studio aplikaci znovu sestavíte a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. V okně konzoly zadejte své jméno a stiskněte **Enter.**

   ![Snímek obrazovky Microsoft Visual Studio konzoly ladění zobrazující výzvu k zadání názvu, vstupu a výstupu Hello Natte!](../media/vs-2019/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Použití refaktoringu a IntelliSense

Podívejme se na několik způsobů, jak vám [refaktoring](../../ide/refactoring-in-visual-studio.md) a [IntelliSense](../../ide/using-intellisense.md) můžou pomoct s efektivnějším kódem.

Nejprve přejmenujte proměnnou `name` :

1. Poklikejte `name` na proměnnou a vyberte ji.

2. Zadejte nový název proměnné, uživatelské **jméno**.

   Všimněte si, že kolem proměnné se zobrazí šedé pole a na okraji se zobrazí žárovka.

::: moniker range="vs-2017"

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce.](../../ide/quick-actions.md) Vyberte **Přejmenovat 'name' na 'uživatelské jméno'.**

   ![Akce Přejmenovat v Visual Studio](../media/rename-quick-action.png)

   Proměnná se přejmenuje napříč projektem, což jsou v našem případě jenom dvě místa.

   ![Animovaný gif znázorňující refaktoring přejmenování v Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce.](../../ide/quick-actions.md) Vyberte **Přejmenovat 'name' na 'uživatelské jméno'.**

   ![Akce Přejmenovat v Visual Studio](../media/vs-2019/rename-quick-action.png)

   Proměnná se přejmenuje napříč projektem, což jsou v našem případě jenom dvě místa.

::: moniker-end

4. Teď se podívejme na IntelliSense. Pod řádek s `Console.WriteLine($"\nHello {username}!");` textem zadejte `DateTime now = DateTime.` .

   V poli se zobrazí členy <xref:System.DateTime> třídy . Kromě toho se popis aktuálně vybraného členu zobrazí v samostatném poli.

   ![Seznam členů IntelliSense v Visual Studio](../media/intellisense-list-members.png)

5. Poklikáním nebo stisknutím klávesy Tab vyberte člen s názvem **Now**(Nyní), což je vlastnost **třídy**. Dokončete řádek kódu přidáním středníku na konec.

6. Pod to zadejte nebo vložte následující řádky kódu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> je trochu jiná než v tom, že po vytištění nepřidá <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ukončovací znak řádku. To znamená, že další část textu, která se odesílá do výstupu, se vytiskne na stejném řádku. Pokud chcete zobrazit jejich popis, najeďte myší na každou z těchto metod v kódu.

7. V dalším kroku znovu použijeme refaktoring, aby byl kód trochu stručnější. Klikněte na proměnnou `now` na řádku `DateTime now = DateTime.Now;` .

   Všimněte si, že na okraji na tomto řádku se zobrazuje malá ikona vyšichovačky.

8. Kliknutím na ikonudriveru zobrazíte návrhy, Visual Studio jsou k dispozici. V tomto případě se zobrazuje [](../../ide/reference/inline-temporary-variable.md) refaktoring vložené dočasné proměnné pro odebrání řádku kódu beze změny celkového chování kódu:

   ![Refaktoring v vložené dočasné proměnné v Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Pokud **chcete kód refaktorovat,** klikněte na dočasnou proměnnou Inline (Vložený).

::: moniker range="vs-2017"

10. Znovu spusťte program stisknutím **klávesy Ctrl** + **F5.** Výstup vypadá nějak takhle:

    ! Snímek obrazovky cmd.exe konzoly nástroje zobrazující výzvu k zadání názvu, vstupu a výstupu "Hello Přivítáme! Den v roce: 151'.] (.. /media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Znovu spusťte program stisknutím **klávesy Ctrl** + **F5.** Výstup vypadá nějak takhle:

    ![Snímek obrazovky Microsoft Visual Studio konzoly ladění zobrazující výzvu k zadání názvu, vstupu a výstupu "Hello Přivítáme! Den v roce: 43'](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Ladění kódu

Když píšete kód, musíte ho spustit a otestovat, jestli ne. Visual Studio systému ladění umožňuje krokovat kód po jednom příkazu a kontrolovat proměnné tak, jak jdete. Můžete nastavit *zarážky,* které zastaví provádění kódu na konkrétním řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a další.

Nastavte zarážku, abyste viděli hodnotu `username` proměnné, zatímco program &quot;letí&quot;.

1. Vyhledejte řádek kódu s kódem `Console.WriteLine($&quot;\nHello {username}!");` . Pokud chcete nastavit zarážku na tomto řádku kódu, to znamená, že pokud chcete program pozastavit provádění na tomto řádku, klikněte na levý okraj editoru. Můžete také kliknout kamkoli na řádek kódu a pak stisknout **klávesu F9**.

   V levém okraji se zobrazí červený kruh a kód je zvýrazněný červeně.

   ![Zarážka na řádku kódu v Visual Studio](../media/breakpoint.png)

1. Spusťte ladění výběrem **možnosti**  >  **Ladit a spustit ladění** nebo stisknutím **klávesy F5.**

1. Když se zobrazí okno konzoly a vyzve vás k zadání vašeho jména, zadejte ho a stiskněte **Enter.**

   Fokus se vrátí do Visual Studio kódu a řádek kódu se zarážkou je zvýrazněný žlutou barvou. To znamená, že se jedná o další řádek kódu, který program spustí.

1. Najeďte myší na `username` proměnnou a zobrazte její hodnotu. Případně můžete kliknout pravým tlačítkem a vybrat Přidat hodinku a přidat proměnnou do okna Watch `username` (Hodinka),  kde můžete také zobrazit její hodnotu. 

   ![Hodnota proměnné během ladění v Visual Studio](../media/debugging-variable-value.png)

1. Pokud chcete program nechat běžet do konce, znovu **stiskněte klávesu F5.**

Další podrobnosti o ladění v nástroji Visual Studio v tématu [Prohlídka funkcí ladicího programu.](../../debugger/debugger-feature-tour.md)

## <a name="customize-visual-studio"></a>Přizpůsobení Visual Studio

Uživatelské rozhraní můžete přizpůsobit Visual Studio, včetně změny výchozího barevného motivu. Změna na tmavý **motiv:**

1. Na řádku nabídek **zvolte** Nástroje  >  **Možnosti.** Otevře se **dialogové okno** Možnosti.

::: moniker range="vs-2017"

2. Na stránce **Obecné** > **možnosti** prostředí změňte výběr **Motiv barvy** na Tmavý **a** pak zvolte **OK**.

   Barevný motiv celého integrovaného vývojového prostředí (IDE) se změní na **Dark (Tmavý).**

   ![Visual Studio v tmavém motivu](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **Obecné** > **možnosti** prostředí změňte výběr **Motiv barvy** na Tmavý **a** pak zvolte **OK**.

   Barevný motiv celého integrovaného vývojového prostředí (IDE) se změní na **Dark (Tmavý).**

   ![Visual Studio v tmavém motivu](../media/vs-2019/dark-theme.png)

::: moniker-end

Další informace o dalších způsobech přizpůsobení integrovaného vývojového prostředí najdete v tématu [Přizpůsobení Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).