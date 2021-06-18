---
ms.date: 05/28/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 128a09500aaa326fad717efcade9040496452963
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112362465"
---
Integrované Visual Studio *prostředí je* kreativní spouštěcí panel, který můžete použít k úpravám, ladění a sestavování kódu a k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatými funkcemi, který lze použít pro mnoho aspektů vývoje softwaru. Kromě standardního editoru a ladicího programu, který poskytuje většina prostředí ID, Visual Studio zahrnuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a mnoho dalších funkcí pro usnadnění procesu vývoje softwaru.

::: moniker range="vs-2017"

![Integrované vývojové Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Snímek obrazovky s Visual Studio IDE, který obsahuje popisky, které označují, kde jsou umístěné klíčové funkce" lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

Tento obrázek ukazuje Visual Studio s otevřeným projektem a několika klíčovými okny nástrojů, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, procházet a spravovat soubory kódu. **Průzkumník řešení** vám může pomoct s uspořádáním kódu seskupením souborů do [řešení a projektů](../tutorial-projects-solutions.md).

- V [okně editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (uprostřed), kde pravděpodobně strávíte většinu času, se zobrazí obsah souboru. Tady můžete upravovat kód nebo navrhovat uživatelské rozhraní, například okno s tlačítky a textová pole.

::: moniker range="vs-2017"

- V [okně Výstup](../../ide/reference/output-window.md) (dole uprostřed) se Visual Studio oznámení, jako jsou ladění a chybové zprávy, upozornění kompilátoru, stavové zprávy publikování a další. Každý zdroj zpráv má svou vlastní kartu.

::: moniker-end

- [Změny Gitu](/visualstudio/version-control/) (vpravo dole) umožňují sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) a [GitHub](https://docs.github.com/github).

## <a name="editions"></a>Edice

::: moniker range="vs-2017"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako Visual Studio 2017 a je optimalizovaný pro vývoj aplikací pro více platforem a mobilních aplikací. Tento článek se zaměřuje na verzi Windows Visual Studio 2017.

Existují tři edice Visual Studio: Community, Professional a Enterprise. Informace [o podporovaných Visual Studio jednotlivých edicích](https://visualstudio.microsoft.com/vs/compare/) najdete v tématu Porovnání jednotlivých edicí.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má řadu stejných funkcí jako Visual Studio 2019 a je optimalizovaný pro vývoj aplikací pro více platforem a mobilních aplikací. Tento článek se zaměřuje na verzi Windows Visual Studio 2019.

Existují tři edice Visual Studio 2019: Community, Professional a Enterprise. Informace [o podporovaných Visual Studio jednotlivých edicích](https://visualstudio.microsoft.com/vs/compare/) najdete v tématu Porovnání jednotlivých edicí.

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

   ![Visual Studio seznamu členů](../media/intellisense-list-members.png)

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

## <a name="install-the-visual-studio-ide"></a>Instalace integrovaného vývojového Visual Studio

V této části vytvoříte jednoduchý projekt, který vám umožní vyzkoušet si některé z věcí, které můžete s Visual Studio. [IntelliSense](../../ide/using-intellisense.md) použijete jako pomůcku pro kódování, budete ladit aplikaci, abyste viděli hodnotu proměnné během provádění programu, a změníte barevný motiv.

::: moniker range="vs-2017"

Pokud chcete začít, [stáhněte Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat úlohy *,* což jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle [kroků pro vytvoření programu,](#create-a-program)nezapomeňte během instalace vybrat úlohu vývoj pro různé platformy v **.NET Core.**

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete začít, [stáhněte Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat úlohy *,* což jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle [kroků pro vytvoření programu,](#create-a-program)nezapomeňte během instalace vybrat úlohu vývoj pro různé platformy v **.NET Core.**

::: moniker-end

![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Když aplikaci Visual Studio poprvé, můžete se volitelně [](../../ide/signing-in-to-visual-studio.md) přihlásit pomocí svého pracovního účet Microsoft nebo školního účtu.

## <a name="create-a-program"></a>Vytvoření programu

Pojďme se ponořit do jednoduchého programu.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. Na řádku nabídek zvolte File New Project **(Soubor** > **nový** > **projekt).**

   ![Soubor > řádku nabídek Nový projekt](../media/file-new-project-menu.png)

   V **dialogovém okně** Nový projekt se zobrazuje několik šablon *projektů.* Šablona obsahuje základní soubory a nastavení potřebné pro daný typ projektu.

1. V části Visual **C#** zvolte kategorii šablony **.NET Core** a pak zvolte šablonu **Konzolová aplikace (.NET Core).** Do **textového** pole Název zadejte **HelloWorld** a pak vyberte **tlačítko OK.**

   ![Šablona aplikace .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Pokud nevidíte kategorii **.NET Core,** musíte nainstalovat úlohu vývoj pro **různé platformy v .NET Core.** Pokud to chcete udělat, **zvolte Instalační program pro Visual Studio** v levém dolním rohu **dialogového** okna Nový projekt. Po Instalační program pro Visual Studio se posuňte dolů, vyberte úlohu vývoj pro **různé platformy v .NET Core** a pak vyberte **Upravit.**

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci typu "Hello World", která volá metodu , která zobrazí řetězec literálu <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" v okně konzoly (výstup programu).

   Za chvíli by se mělo zobrazit něco podobného:

   ![Visual Studio – sada IDE](../media/overview-ide-console-app.png)

   Kód jazyka C# pro vaši aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně barevný, aby označoval různé části kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které závorky se shodují s sebou, a čísla řádků vám pomůžou později vyhledat kód. Můžete zvolit malý, zabalené znaménko minus pro sbalení nebo rozbalení bloků kódu. Tato funkce osnovy kódu vám umožní skrýt kód, který nepotřebujete, a pomoct tak minimalizovat přehlednost na obrazovce. Soubory projektu jsou uvedeny na pravé straně okna s názvem **Průzkumník řešení**.

   ![Integrované vývojové prostředí sady Visual Studio s červenými poli](../media/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale teď se k ní přiblížíme.

1. Teď aplikaci spusťte. To lze provést výběrem možnosti **Spustit bez ladění** v nabídce **ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves CTRL** + **F5**.

   ![Ladit > spustit bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se zprávou **Hello World!**. Teď máte spuštěnou aplikaci.

   ![Snímek obrazovky okna konzoly cmd.exe zobrazující výstup Hello Word! a pokračujte stisknutím libovolné klávesy.](../media/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Přidejte následující kód jazyka C# před řádek, který říká `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazuje, **Jaké je vaše jméno?** v okně konzoly a pak počká, dokud uživatel nezadá text následovaný klávesou **ENTER** .

1. Změňte řádek, který říká `Console.WriteLine("Hello World!");` následujícímu kódu:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu tak, že vyberete **ladit** > **Spustit bez ladění** nebo stisknete **klávesu CTRL** + **F5**.

   Visual Studio aplikaci znovu sestaví a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte klávesu **ENTER**.

   ![Vstup okna konzoly](../media/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Otevře se okno Start s různými možnostmi klonování úložiště, otevřením posledního projektu nebo vytvořením značky nového projektu.

1. Vyberte **vytvořit nový projekt**.

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Snímek obrazovky okna vytvořit nový projekt v aplikaci Visual Studio 2019":::

   Otevře se okno **vytvořit nový projekt** a zobrazí se několik *šablon* projektů. Šablona obsahuje základní soubory a nastavení, které jsou požadovány pro daný typ projektu.

1. Pokud chcete najít požadovanou šablonu, zadejte nebo zadejte do vyhledávacího pole **konzolu .NET Core** . Seznam šablon, které jsou k dispozici, se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dále filtrovat volbou **C#** z rozevíracího seznamu **všechny jazyky** , **Windows** ze seznamu **všechny platformy** a **konzoly** ze seznamu **všechny typy projektů** .

    Vyberte šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Snímek obrazovky okna vytvořit nový projekt v aplikaci Visual Studio 2019, kde můžete vybrat požadovanou šablonu.":::

1. V okně **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** a volitelně změňte umístění adresáře pro soubory projektu (výchozí národní prostředí je `C:\Users\<name>\source\repos` ) a pak klikněte na **Další**.

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Snímek obrazovky okna Konfigurovat nový projekt v aplikaci Visual Studio 2019, kde zadáte název projektu":::

1. V okně **Další informace** ověřte, že se v rozevírací nabídce **cílové** rozhraní zobrazí **.NET Core 3,1** a pak klikněte na **vytvořit**.

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Snímek obrazovky okna Další informace v aplikaci Visual Studio 2019, kde můžete vybrat požadovanou verzi rozhraní .NET Core.":::

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci "Hello World", která volá <xref:System.Console.WriteLine?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello World!" v okně konzoly (programový výstup).

   Za chvíli by se měla zobrazit následující text:

   ![Visual Studio – sada IDE](../media/vs-2019/overview-ide-console-app.png)

   Kód jazyka C# pro vaši aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně barevný, aby označoval různé části kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které závorky se shodují s sebou, a čísla řádků vám pomůžou později vyhledat kód. Můžete zvolit malý, zabalené znaménko minus pro sbalení nebo rozbalení bloků kódu. Tato funkce osnovy kódu vám umožní skrýt kód, který nepotřebujete, a pomoct tak minimalizovat přehlednost na obrazovce. Soubory projektu jsou uvedeny na pravé straně okna s názvem **Průzkumník řešení**.

   ![Integrované vývojové prostředí sady Visual Studio s červenými poli](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale teď se k ní přiblížíme.

1. Teď aplikaci spusťte. To lze provést výběrem možnosti **Spustit bez ladění** v nabídce **ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves CTRL** + **F5**.

   ![Ladit > spustit bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se zprávou **Hello World!**. Teď máte spuštěnou aplikaci.

   ![Snímek obrazovky okna konzoly ladění Microsoft Visual Studio, ve kterém se zobrazuje výstup "Hello Word!" a stisknutím libovolné klávesy zavřete toto okno.](../media/vs-2019/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Přidejte následující kód jazyka C# před řádek, který říká `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazuje, **Jaké je vaše jméno?** v okně konzoly a pak počká, dokud uživatel nezadá text následovaný klávesou **ENTER** .

1. Změňte řádek, který říká `Console.WriteLine("Hello World!");` následujícímu kódu:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu tak, že vyberete **ladit** > **Spustit bez ladění** nebo stisknete **klávesu CTRL** + **F5**.

   Visual Studio aplikaci znovu sestaví a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte klávesu **ENTER**.

   ![Snímek obrazovky okna konzoly ladění Microsoft Visual Studio, kde se zobrazí výzva k zadání názvu, vstupu a výstupu "Hello! Georgette!".](../media/vs-2019/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Použití refaktoringu a IntelliSense

Pojďme se podívat na několik způsobů, jak [refaktoring](../../ide/refactoring-in-visual-studio.md) , tak aby vám [IntelliSense](../../ide/using-intellisense.md) mohl efektivněji pomáhat s kódem.

Nejdřív přejmenujte `name` proměnnou:

1. Dvakrát klikněte na `name` proměnnou a vyberte ji.

2. Zadejte nový název proměnné, **uživatelské jméno**.

   Všimněte si, že kolem proměnné se zobrazí šedé pole a v okraji se zobrazí žárovka.

::: moniker range="vs-2017"

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce](../../ide/quick-actions.md). Vyberte **přejmenovat název na uživatelské jméno**.

   ![Akce přejmenování v aplikaci Visual Studio](../media/rename-quick-action.png)

   Proměnná je přejmenována v rámci projektu, což je v našem případě pouze dvou míst.

   ![Animovaný obrázek GIF znázorňující refaktorování přejmenování v aplikaci Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce](../../ide/quick-actions.md). Vyberte **přejmenovat název na uživatelské jméno**.

   ![Akce přejmenování v aplikaci Visual Studio](../media/vs-2019/rename-quick-action.png)

   Proměnná je přejmenována v rámci projektu, což je v našem případě pouze dvou míst.

::: moniker-end

4. Teď se podívejme na technologii IntelliSense. Pod řádek, který říká `Console.WriteLine($"\nHello {username}!");` , zadejte `DateTime now = DateTime.` .

   Pole zobrazuje členy <xref:System.DateTime> třídy. Kromě toho popis aktuálně vybraného člena se zobrazí v samostatném poli.

   ![Členové seznamu IntelliSense v aplikaci Visual Studio](../media/intellisense-list-members.png)

5. Vyberte člena s názvem **nyní**, což je vlastnost třídy, dvakrát na ni klikněte nebo stiskněte klávesu **TAB**. Dokončete řádek kódu tak, že na konec přidáte středník.

6. Níže zadejte nebo vložte následující řádky kódu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> se trochu liší <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> od v tom, že po vytištění nepřidá ukončovací znak řádku. To znamená, že další část textu, která je odeslána do výstupu, bude vytištěna na stejném řádku. Svůj popis můžete zobrazit tak, že najedete myší na každou z těchto metod v kódu.

7. Dále znovu použijeme refaktoring, aby byl kód trochu výstižnější. Klikněte na proměnnou na `now` řádku `DateTime now = DateTime.Now;` .

   Všimněte si, že na okraji na daném řádku se zobrazí trochu Screwdriver ikona.

8. Klikněte na ikonu Screwdriver a zjistěte, jaké návrhy nabízí Visual Studio. V tomto případě se zobrazuje [](../../ide/reference/inline-temporary-variable.md) refaktoring vložené dočasné proměnné pro odebrání řádku kódu beze změny celkového chování kódu:

   ![Refaktoring vnoěných dočasných proměnných v Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Pokud **chcete kód refaktorovat,** klikněte na dočasnou proměnnou Inline (Vložený).

::: moniker range="vs-2017"

10. Znovu spusťte program stisknutím **klávesy Ctrl** + **F5.** Výstup vypadá nějak takhle:

    ! Snímek obrazovky cmd.exe konzoly nástroje zobrazující výzvu k zadání názvu, vstupu a výstupu "Hello Přivítáme! Den v roce: 151'.] (.. /media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Znovu spusťte program stisknutím **klávesy Ctrl** + **F5.** Výstup vypadá nějak takhle:

    ![Snímek obrazovky Microsoft Visual Studio konzoly ladění zobrazující výzvu k zadání názvu, vstupu a výstupu "Hello Natte! Den v roce: 43'](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Ladění kódu

Když píšete kód, musíte ho spustit a otestovat, jestli ne. Visual Studio systému ladění umožňuje krokovat kód po jednom příkazu a kontrolovat proměnné, jak chcete. Můžete nastavit *zarážky,* které zastaví provádění kódu na konkrétním řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a další.

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