---
ms.date: 06/29/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 452549030d77b90049b12716087544bdd1288a3f
ms.sourcegitcommit: 7393a37ce77c5b80312ce787baa060c91d41d959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2021
ms.locfileid: "113113662"
---
*Integrované vývojové prostředí* sady Visual Studio je kreativní spouštěcí panel, který můžete použít k úpravám, ladění a vytváření kódu a pak k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatou funkcí, který se dá použít pro mnoho aspektů vývoje softwaru. Nad rámec a nad standardním editorem a ladicím programem, který využívá většina IDEs, Visual Studio obsahuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a mnoho dalších funkcí, které usnadňují proces vývoje softwaru.

::: moniker range="vs-2017"

![Integrované vývojové prostředí (IDE) sady Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Snímek integrovaného vývojového prostředí (IDE) sady Visual Studio obsahující popisky, které označují, kde jsou umístěny klíčové funkce a funkce." lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

Tento obrázek ukazuje aplikaci Visual Studio s otevřeným projektem a několika okny s nástroji Key, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/use-solution-explorer.md) (vpravo nahoře) umožňuje zobrazit, navigovat a spravovat soubory kódu. **Průzkumník řešení** může přispět k uspořádání kódu seskupením souborů do [řešení a projektů](../../ide/use-solution-explorer.md).

- [Okno editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), kde se pravděpodobně bude strávit většinou času, zobrazuje obsah souboru. Tady můžete upravit kód nebo navrhnout uživatelské rozhraní, jako je okno s tlačítky a textovými poli.

::: moniker range="vs-2017"

- [Okno výstup](../../ide/reference/output-window.md) (dole na střed) je místo, kde aplikace Visual Studio odesílá oznámení, jako jsou například ladění a chybové zprávy, upozornění kompilátoru, zprávy o stavu publikování a další. Každý zdroj zprávy má svou vlastní kartu.

::: moniker-end

- [Změny Git](/visualstudio/version-control/) (vpravo dole) umožňují sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) a [GitHub](https://docs.github.com/github).

## <a name="editions"></a>Edice

::: moniker range="vs-2017"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako sadu Visual Studio 2017 a je optimalizovaná pro vývoj aplikací pro různé platformy a mobilní aplikace. Tento článek se zaměřuje na verzi systému Windows sady Visual Studio 2017.

Existují tři edice sady Visual Studio: komunita, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v článku [porovnání edice sady Visual Studio](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako sadu Visual Studio 2019 a je optimalizovaná pro vývoj aplikací pro různé platformy a mobilní aplikace. Tento článek se zaměřuje na verzi systému Windows sady Visual Studio 2019.

Existují tři edice sady Visual Studio 2019: komunita, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v článku [porovnání edice sady Visual Studio](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

## <a name="popular-productivity-features"></a>Oblíbené funkce pro produktivitu

Některé z oblíbených funkcí v aplikaci Visual Studio, které vám pomůžou zvýšit produktivitu při vývoji softwaru, zahrnují:

- Vlnovky a [rychlé akce](../../ide/quick-actions.md)

   Vlnovky jsou podtržení vlnovkou, které upozorňují na chyby nebo potenciální problémy ve vašem kódu při psaní. Tato vizuální podoby vám umožní opravit problémy hned bez čekání na zjištění chyby během sestavení nebo při spuštění programu. Pokud najedete myší na vlnovku, zobrazí se další informace o chybě. Žárovka se může zobrazit také na levém okraji s akcemi, které jsou známé jako rychlé akce, a opravit tak chybu.

   ![Vlnovky v aplikaci Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Vyčištění kódu

   Kliknutím na tlačítko naformátujete kód a použijete všechny opravy kódu navrhované [nastavením stylu kódu](../../ide/reference/options-text-editor-csharp-formatting.md), [konvencemi editorconfig](../../ide/create-portable-custom-editor-options.md)a [analyzátory Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Vyčištění kódu** pomáhá vyřešit problémy v kódu před tím, než se přejde na revizi kódu. (Aktuálně k dispozici pouze pro kód jazyka C#.)

   ![Tlačítko pro vyčištění kódu v aplikaci Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako je například inteligentní přejmenování proměnných, extrakce jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ![Refaktoring v sadě Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech zapisují malé bity kódu za vás. Vypadá to, že je v editoru vložená základní dokumentace, která vám ušetří informace o typu jinde. Funkce IntelliSense se liší podle jazyka. Další informace naleznete v tématu [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)a [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Následující obrázek ukazuje, jak IntelliSense zobrazuje seznam členů pro typ:

   ![Seznam členů sady Visual Studio](../media/intellisense-list-members.png)

- [Hledání v aplikaci Visual Studio](../../ide/visual-studio-search.md)

   Visual Studio se může zdát při velkém množství nabídek, možností a vlastností. Vyhledávání v rámci sady Visual Studio (**CTRL** + **Q**) představuje skvělý způsob, jak rychle najít funkce a kód rozhraní IDE na jednom místě.

   ::: moniker range="vs-2017"

   ![Rychlé spuštění vyhledávacího pole v aplikaci Visual Studio 2017](../media/quick-launch-nuget.png)

   Další informace najdete v tématu [Snadné spuštění](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Vyhledávací pole v aplikaci Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

    Tipy pro informace a produktivitu najdete v tématu [Jak používat Visual Studio Search](../../ide/visual-studio-search.md).

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Spoluupravujte a laďte s ostatními v reálném čase bez ohledu na typ aplikace nebo programovací jazyk. Můžete okamžitě a bezpečně sdílet svůj projekt a podle potřeby ladit relace, instance Terminálové služby, webové aplikace localhost, hlasové hovory a další.

- [Hierarchie volání](../../ide/reference/call-hierarchy.md)

   Okno **hierarchie volání** zobrazuje metody, které volají vybranou metodu. To může být užitečné v případě, že uvažujete o změně nebo odebrání metody nebo když se snažíte sledovat chybu.

   ![Okno hierarchie volání](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens pomáhá najít odkazy na váš kód, změny kódu, propojené chyby, pracovní položky, revize kódu a testování částí, aniž byste museli opustit Editor.

   ![CodeLens](../media/codelens-overview.png)

- [Přejít k definici](../../ide/go-to-and-peek-definition.md)

   Funkce přejít k definici přejde přímo do umístění, kde je definována funkce nebo typ.

   ![Přejít k definici](../media/go-to-definition-menu.png)

- [Náhled definice](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   V okně **Náhled definice** se zobrazí definice metody nebo typu bez skutečného otevření samostatného souboru.

   ![Náhled definice](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalace integrovaného vývojového prostředí sady Visual Studio

V této části vytvoříte jednoduchý projekt, abyste si vyzkoušeli některé z akcí, které můžete dělat se sadou Visual Studio. [IntelliSense](../../ide/using-intellisense.md) použijete jako pomůcku pro psaní kódu, laděním aplikace zobrazíte hodnotu proměnné během provádění programu a změníte barevný motiv.

::: moniker range="vs-2017"

Pokud chcete začít, [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat *úlohy*, které jsou skupiny funkcí, které jsou potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle kroků pro [vytvoření programu](#create-a-program), nezapomeňte při instalaci vybrat úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete začít, [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat *úlohy*, které jsou skupiny funkcí, které jsou potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle kroků pro [vytvoření programu](#create-a-program), nezapomeňte při instalaci vybrat úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end

![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Při prvním otevření sady Visual Studio se můžete volitelně [Přihlásit](../../ide/signing-in-to-visual-studio.md) pomocí účet Microsoft nebo svého pracovního nebo školního účtu.

## <a name="create-a-program"></a>Vytvoření programu

Pojďme se podrobně a vytvořit jednoduchý program.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

   ![Soubor > nový projekt na řádku nabídek](../media/file-new-project-menu.png)

   Dialogové okno **Nový projekt** ukazuje několik *šablon* projektů. Šablona obsahuje základní soubory a nastavení potřebná pro daný typ projektu.

1. Zvolte kategorii šablony **.NET Core** v jazyce **Visual C#** a pak zvolte šablonu **Konzolová aplikace (.NET Core)** . Do textového pole **název** zadejte **HelloWorld** a pak klikněte na tlačítko **OK** .

   ![Šablona aplikace .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Pokud nevidíte kategorii **.NET Core** , musíte nainstalovat **vývojovou úlohu .NET Core pro různé platformy** . Uděláte to tak, že kliknete na odkaz **otevřít instalační program pro Visual Studio** v levé dolní části dialogového okna **Nový projekt** . Po Instalační program pro Visual Studio se posuňte dolů a vyberte úlohu **vývoje .NET Core pro různé platformy** a pak vyberte **Upravit**.

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci "Hello World", která volá <xref:System.Console.WriteLine?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello World!" v okně konzoly (programový výstup).

   Za chvíli by se měla zobrazit následující text:

   ![Visual Studio – sada IDE](../media/overview-ide-console-app.png)

   Kód jazyka C# pro vaši aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text se automaticky obarizuje, aby indikuje různé části kódu, například klíčová slova a typy. Kromě toho malé svislé přerušované řádky v kódu označují, které složené závorky se navzájem shodují, a čísla řádků vám pomůžou vyhledat kód později. Pro sbalení nebo rozbalení bloků kódu můžete zvolit malé a krabicové znaménko minus. Tato funkce osnovy kódu umožňuje skrýt kód, který nepotřebujete, což pomáhá minimalizovat nepotřebné informace na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně s názvem **Průzkumník řešení**.

   ![Visual Studio IDE s červenými rámečky](../media/overview-ide-console-app-red-boxes.png)

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

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Snímek obrazovky s oknem Vytvořit nový projekt v Visual Studio 2019":::

   Otevře **se okno Vytvořit nový** projekt s několika šablonami *projektů.* Šablona obsahuje základní soubory a nastavení vyžadované pro daný typ projektu.

1. Pokud chcete najít šablonu, kterou chceme, zadejte nebo zadejte do vyhledávacího pole **konzolu .net** core. Seznam dostupných šablon se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dále filtrovat tak, že  v rozevíracím seznamu Všechny  jazyky zvolíte  **C#,** ze seznamu Všechny platformy vyberete **Windows** a ze seznamu Všechny typy projektů vyberete **Konzola.**

    Vyberte šablonu **Konzolová aplikace** a potom klikněte na **Další.**

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Snímek obrazovky okna Vytvořit nový projekt v Visual Studio 2019, kde vyberete požadovanou šablonu":::

1. V **okně Configure your new project** (Konfigurovat nový projekt) zadejte do pole Project **name** (Název projektu) text **HelloWorld,** volitelně změňte umístění adresáře pro soubory projektu (výchozí národní prostředí je ) a pak klikněte `C:\Users\<name>\source\repos` na Next **(Další).**

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Snímek obrazovky s oknem Konfigurovat nový projekt Visual Studio 2019, kde zadáte název projektu":::

1. V okně Další **informace** ověřte, že se v rozevírací  nabídce Cílová rozhraní zobrazuje **.NET Core 3.1,** a pak klikněte na **Vytvořit.**

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Snímek obrazovky s oknem Další informace v Visual Studio 2019, kde vyberete požadovanou verzi rozhraní .NET Core Framework":::

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci typu "Hello World", která volá metodu , která zobrazí řetězec literálu <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" v okně konzoly (výstup programu).

   Za chvíli by se mělo zobrazit něco podobného:

   ![Visual Studio – sada IDE](../media/vs-2019/overview-ide-console-app.png)

   Kód jazyka C# pro vaši aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text se automaticky obarizuje, aby indikuje různé části kódu, například klíčová slova a typy. Kromě toho malé svislé přerušované řádky v kódu označují, které složené závorky se navzájem shodují, a čísla řádků vám pomůžou vyhledat kód později. Pro sbalení nebo rozbalení bloků kódu můžete zvolit malé a krabicové znaménko minus. Tato funkce osnovy kódu umožňuje skrýt kód, který nepotřebujete, což pomáhá minimalizovat nepotřebné informace na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně s názvem **Průzkumník řešení**.

   ![Visual Studio IDE s červenými rámečky](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   K dispozici jsou i další nabídky a okna nástrojů, ale pojďme se teď pustit dál.

1. Teď spusťte aplikaci. Můžete to provést tak, že v  **nabídce Ladit** na řádku nabídek zvolíte Spustit bez ladění. Můžete také stisknout **Ctrl** + **F5**.

   ![Spuštění > ladění bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se **zprávou Hello World!**. Teď máte spuštěnou aplikaci.

   ![Snímek obrazovky Microsoft Visual Studio konzoly ladění s výstupem "Hello Word!" a stisknutím libovolné klávesy toto okno zavřete.](../media/vs-2019/overview-console-window.png)

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

8. Kliknutím na ikonudriveru zobrazíte návrhy, Visual Studio jsou k dispozici. V tomto případě se zobrazuje [vložená dočasná](../../ide/reference/inline-temporary-variable.md) refaktoring proměnné pro odebrání řádku kódu beze změny celkového chování kódu:

   ![Refaktoring dočasné proměnné Refaktoring v aplikaci Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Klikněte na **vloženou dočasnou proměnnou** a refaktorujte kód.

::: moniker range="vs-2017"

10. Spusťte program znovu stisknutím **klávesy CTRL** + **F5**. Výstup bude vypadat nějak takto:

    ! Snímek obrazovky okna konzoly cmd.exe zobrazující výzvu k zadání názvu, vstupu a výstupu Hello Georgette! Den roku: 151 '.] (.. /Media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Spusťte program znovu stisknutím **klávesy CTRL** + **F5**. Výstup bude vypadat nějak takto:

    ![Snímek obrazovky okna konzoly ladění Microsoft Visual Studio zobrazující výzvu k zadání názvu, vstupu a výstupu Georgette Hello! Den roku: 43 '.](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Ladění kódu

Při psaní kódu ho musíte spustit a otestovat pro chyby. Ladicí systém sady Visual Studio umožňuje Krokovat s kódem v jednom okamžiku a při procházení proměnných kontrolovat proměnné. Můžete nastavit *zarážky* , které zastaví provádění kódu na určitém řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a dalších.

Pojďme nastavit zarážku, aby se zobrazila hodnota `username` proměnné, zatímco program je &quot;v letu&quot;.

1. Vyhledejte řádek kódu, který říká `Console.WriteLine($&quot;\nHello {username}!");` . Chcete-li nastavit zarážku na tomto řádku kódu, to znamená, aby program pozastavil provádění na tomto řádku, klikněte na levý levý okraj editoru. Můžete také kliknout kamkoli na řádek kódu a stisknout **F9**.

   V levém horním rohu se zobrazí červený kroužek a kód se zvýrazní červeně.

   ![Zarážka na řádku kódu v aplikaci Visual Studio](../media/breakpoint.png)

1. Spusťte ladění tak, **že vyberete ladění**  >  **Spustit ladění** nebo stisknete klávesu **F5**.

1. Jakmile se zobrazí okno konzoly a požádá o vaše jméno, zadejte ho do pole a stiskněte klávesu **ENTER**.

   Fokus se vrátí do editoru kódu sady Visual Studio a řádek kódu se zarážkou se zvýrazní žlutě. To znamená, že se jedná o další řádek kódu, který bude program spouštět.

1. Pokud `username` chcete zobrazit jeho hodnotu, najeďte myší na proměnnou. Případně můžete kliknout pravým tlačítkem myši na `username` a vybrat možnost **Přidat kukátko** a přidat proměnnou do okna **kukátka** , kde můžete také zobrazit její hodnotu.

   ![Hodnota proměnné během ladění v aplikaci Visual Studio](../media/debugging-variable-value.png)

1. Pokud chcete nechat program běžet na dokončení, stiskněte znovu klávesu **F5** .

Další informace o ladění v aplikaci Visual Studio naleznete v tématu [prohlídka funkcí ladicího programu](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Přizpůsobení sady Visual Studio

Můžete přizpůsobit uživatelské rozhraní sady Visual Studio, včetně změny výchozího barevného motivu. Postup pro změnu na **tmavý** motiv:

1. V panelu nabídek   >  otevřete dialogové okno **Možnosti** výběrem **Možnosti** nástroje.

::: moniker range="vs-2017"

2. Na stránce  > **Obecné** možnosti prostředí změňte výběr **barevného motivu** na **tmavý** a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí se změní na **tmavý**.

   ![Visual Studio v tmavém motivu](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce  > **Obecné** možnosti prostředí změňte výběr **barevného motivu** na **tmavý** a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí se změní na **tmavý**.

   ![Visual Studio v tmavém motivu](../media/vs-2019/dark-theme.png)

::: moniker-end

Další informace o dalších způsobech přizpůsobení rozhraní IDE naleznete v tématu [přizpůsobení sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).