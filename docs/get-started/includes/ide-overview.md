---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jillfra
ms.topic: include
ms.openlocfilehash: c6e715602d0157f52109d7d0bedf25fbd25a23a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79082600"
---
*Integrované vývojové prostředí* sady Visual Studio je kreativní spouštěcí panel, který můžete použít k úpravám, ladění a sestavení kódu a následnému publikování aplikace. Integrované vývojové prostředí (IDE) je program bohatý na funkce, který lze použít pro mnoho aspektů vývoje softwaru. Kromě standardního editoru a ladicího programu, které poskytuje většina ide, sada Visual Studio obsahuje kompilátory, nástroje pro dokončení kódu, grafické návrháře a mnoho dalších funkcí, které usnadňují proces vývoje softwaru.

::: moniker range="vs-2017"

![IDE Visual Studia 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![IDE Visual Studia 2019](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Tento obrázek znázorňuje Visual Studio s otevřeným projektem a několika okny nástrojů klíčů, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, procházet a spravovat soubory kódu. **Průzkumník řešení** může pomoci uspořádat kód seskupením souborů do [řešení a projektů](../tutorial-projects-solutions.md).

- [Okno editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (uprostřed), kde pravděpodobně strávíte většinu svého času, zobrazuje obsah souboru. Toto je místo, kde můžete upravit kód nebo navrhnout uživatelské rozhraní, jako je například okno s tlačítky a textovými poli.

::: moniker range="vs-2017"

- [Okno Výstup](../../ide/reference/output-window.md) (dolní centrum) je místo, kde Visual Studio odesílá oznámení, jako je ladění a chybové zprávy, upozornění kompilátoru, zprávy o stavu publikování a další. Každý zdroj zprávy má vlastní kartu.

::: moniker-end

- [Průzkumník týmu](/azure/devops/user-guide/work-team-explorer?view=vsts) (vpravo dole) umožňuje sledovat pracovní položky a sdílet kód s ostatními pomocí technologií správy verzí, jako je [Git](https://git-scm.com/) a Team Foundation Version [Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Edice

::: moniker range="vs-2017"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako Visual Studio 2017 a je optimalizované pro vývoj aplikací napříč platformami a mobilními aplikacemi. Tento článek se zaměřuje na verzi Sady Visual Studio 2017 pro Windows.

Existují tři edice sady Visual Studio: Community, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v [tématu Porovnání edicí sady Visual Studio.](https://visualstudio.microsoft.com/vs/compare/)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako Visual Studio 2019 a je optimalizované pro vývoj aplikací napříč platformami a mobilními aplikacemi. Tento článek se zaměřuje na verzi Windows Visual Studia 2019.

Existují tři edice Visual Studia 2019: Komunita, Profesionál a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v [tématu Porovnání edicí sady Visual Studio.](https://visualstudio.microsoft.com/vs/compare/)

::: moniker-end

## <a name="popular-productivity-features"></a>Oblíbené funkce produktivity

Některé z oblíbených funkcí v sadě Visual Studio, které vám pomohou být produktivnější při vývoji softwaru, zahrnují:

- Klikyháky a [rychlé akce](../../ide/quick-actions.md)

   Vlnité vlnovky jsou podtržení vlnovkou, která vás při psaní upozorní na chyby nebo potenciální problémy v kódu. Tyto vizuální vodítka umožňují okamžitě opravit problémy bez čekání na chybu, která má být zjištěna během sestavení nebo při spuštění programu. Pokud najedete na vlnovku, zobrazí se další informace o chybě. Na levém okraji se může zobrazit také žárovka s akcemi, které se označují jako rychlé akce, které chybu opraví.

   ![Vlnité v sadě Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Vyčištění kódu

   Kliknutím na tlačítko naformátujte kód a použijte všechny opravy kódu navržené [nastavením stylu kódu](../../ide/reference/options-text-editor-csharp-formatting.md), [konvencemi .editorconfig](../../ide/create-portable-custom-editor-options.md)a [Roslyn analyzátory](../../code-quality/roslyn-analyzers-overview.md). **Vyčištění kódu** vám pomůže vyřešit problémy v kódu před tím, než přejde do kontroly kódu. (V současné době k dispozici pouze pro kód Jazyka C#.)

   ![Tlačítko Vyčištění kódu v sadě Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako je inteligentní přejmenování proměnných, extrahování jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ![Refaktoring v sadě Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech za vás píší malé kousky kódu. Je to jako mít základní dokumentaci veditoru v editoru, který vám ušetří od nutnosti hledat informace o typu jinde. Funkce Technologie IntelliSense se liší podle jazyka. Další informace naleznete v [tématech C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)a [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Následující obrázek znázorňuje, jak technologie IntelliSense zobrazuje seznam členů pro daný typ:

   ![Seznam členů sady Visual Studio](../media/intellisense-list-members.png)

- Vyhledávací pole

   Visual Studio může zdát ohromující občas s tolika nabídky, možnosti a vlastnosti. Vyhledávací pole je skvělý způsob, jak rychle najít to, co potřebujete v sadě Visual Studio. Když začnete psát název něčeho, co hledáte, Visual Studio zobrazí seznam výsledků, které vás přesně přemístí tam, kam potřebujete. Pokud potřebujete přidat funkce do sady Visual Studio, například pro přidání podpory pro další programovací jazyk, vyhledávací pole poskytuje výsledky, které otevřou Instalační služba sady Visual Studio pro instalaci pracovního vytížení nebo jednotlivé součásti.

   > [!TIP]
   > Stiskněte **ctrl**+**q** jako zástupce vyhledávacího pole.

   ::: moniker range="vs-2017"

   ![Vyhledávací pole Snadné spuštění ve Visual Studiu 2017](../media/quick-launch-nuget.png)

   Další informace naleznete v [tématu Snadné spuštění](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Vyhledávací pole ve Visual Studiu 2019](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Kolaborativně upravujte a laděte s ostatními v reálném čase bez ohledu na to, jaký typ aplikace nebo programovací jazyk. Můžete okamžitě a bezpečně sdílet svůj projekt a podle potřeby ladit relace, terminálové instance, webové aplikace localhost, hlasové hovory a další.

- [Hierarchie volání](../../ide/reference/call-hierarchy.md)

   Okno **Hierarchie volání** zobrazuje metody, které volají vybranou metodu. To může být užitečné informace, když uvažujete o změně nebo odebrání metody, nebo když se pokoušíte vystopovat chybu.

   ![Okno Hierarchie volání](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vám pomůže najít odkazy na váš kód, změny vašeho kódu, propojené chyby, pracovní položky, revize kódu a testy částí, to vše bez opuštění editoru.

   ![CodeLens](../media/codelens-overview.png)

- [Přejít na definici](../../ide/go-to-and-peek-definition.md)

   Funkce Přejít na definici vás přenese přímo do umístění, kde je definována funkce nebo typ.

   ![Přejít k definici](../media/go-to-definition-menu.png)

- [Náhled definice](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Okno **Definice náhledu** zobrazuje definici metody nebo typu bez skutečného otevření samostatného souboru.

   ![Náhled na definici](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalace ide sady Visual Studio

V této části vytvoříte jednoduchý projekt vyzkoušet některé z věcí, které můžete dělat s Visual Studio. Budete používat [IntelliSense](../../ide/using-intellisense.md) jako kódovací pomůcku, ladit aplikaci, abyste viděli hodnotu proměnné během provádění programu, a změňte barevný motiv.

::: moniker range="vs-2017"

Chcete-li začít, [stáhněte si Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ho do systému. Modulární instalační program umožňuje zvolit a nainstalovat úlohy , což jsou *skupiny*funkcí potřebných pro programovací jazyk nebo platformu, které dáváte přednost. Chcete-li postupovat podle kroků pro [vytvoření programu](#create-a-program), nezapomeňte během instalace vybrat vývojové zatížení **.NET Core napříč platformami.**

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li začít, [stáhněte si Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ho do systému. Modulární instalační program umožňuje zvolit a nainstalovat úlohy , což jsou *skupiny*funkcí potřebných pro programovací jazyk nebo platformu, které dáváte přednost. Chcete-li postupovat podle kroků pro [vytvoření programu](#create-a-program), nezapomeňte během instalace vybrat vývojové zatížení **.NET Core napříč platformami.**

::: moniker-end

![Úloha vývoje napříč platformami .NET Core v Instalační službě sady Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Při prvním spuštění sady Visual Studio se můžete volitelně [přihlásit](../../ide/signing-in-to-visual-studio.md) pomocí účtu Microsoft nebo pracovního nebo školního účtu.

## <a name="create-a-program"></a>Vytvoření programu

Pojďme se ponořit a vytvořit jednoduchý program.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

   ![Soubor > nový projekt na řádku nabídek](../media/file-new-project-menu.png)

   Dialogové okno **Nový projekt** zobrazuje několik *šablon*projektu . Šablona obsahuje základní soubory a nastavení potřebné pro daný typ projektu.

1. V části **Visual C#** zvolte kategorii šablony **.NET Core** a pak zvolte šablonu **Console App (.NET Core).** Do textového pole **Název** zadejte **HelloWorld**a pak vyberte tlačítko **OK.**

   ![Šablona aplikace .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Pokud nevidíte kategorii **.NET Core,** je třeba nainstalovat **zatížení vývoje napříč platformami .NET Core.** Chcete-li to provést, zvolte odkaz Otevřít instalační program **sady Visual Studio** v levém dolním rohu dialogového okna Nový **projekt.** Po otevření Instalační služby sady Visual Studio přejděte dolů a vyberte **vývojové úlohy .NET Core pro různé platformy** a pak vyberte **Změnit**.

   Visual Studio vytvoří projekt. Je to jednoduchá aplikace "Hello World", která volá metodu <xref:System.Console.WriteLine?displayProperty=nameWithType> pro zobrazení doslovného řetězce "Hello World!" v okně konzoly (výstup programu).

   Krátce, měli byste vidět něco jako následující:

   ![Visual Studio – sada IDE](../media/overview-ide-console-app.png)

   Kód Jazyka C# pro vaši aplikaci se zobrazí v okně editoru, který zabírá většinu místa. Všimněte si, že text je automaticky obarven a označuje různé části kódu, například klíčová slova a typy. Kromě toho malé, svislé přerušované čárky v kódu označují, které složená závorky se vzájemně shodují, a čísla řádků vám později pomohou najít kód. Můžete zvolit malé, krabicové znaménko mínus, které chcete sbalit nebo rozbalit bloky kódu. Tato funkce osnovy kódu umožňuje skrýt kód, který nepotřebujete, což pomáhá minimalizovat nepořádek na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně s názvem **Průzkumník řešení**.

   ![IDE visual studia s červenými rámečky](../media/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale pojďme se přesunout na teď.

1. Nyní spusťte aplikaci. To lze provést výběrem **možnosti Spustit bez ladění** z nabídky **Ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves Ctrl**+**F5**.

   ![Ladění > Spustit bez ladění nabídky](../media/overview-start-without-debugging.png)

   Visual Studio vytvoří aplikaci a otevře se okno konzoly se zprávou **Hello World!**. Nyní máte spuštěnou aplikaci!

   ![Okno konzoly](../media/overview-console-window.png)

1. Chcete-li zavřít okno konzoly, stiskněte libovolnou klávesu na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Před řádek, který říká: `Console.WriteLine("Hello World!");`

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazuje V okně konzoly **je vaše jméno** a poté počká, dokud uživatel nezadá nějaký text následovaný klávesou **Enter.**

1. Změňte řádek `Console.WriteLine("Hello World!");` s textem na následující kód:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu výběrem **ladění** > **Start bez ladění** nebo stisknutím **Ctrl**+**F5**.

   Visual Studio znovu vytvoří aplikaci a otevře se okno konzoly a zobrazí výzvu k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte **Enter**.

   ![Vstup okna konzoly](../media/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Zobrazí se okno start s různými možnostmi klonování repo, otevření nedávného projektu nebo vytvoření zcela nového projektu.

1. Zvolte **Vytvořit nový projekt**.

   ![Počáteční okno sady Visual Studio vytvoří nový projekt](../media/vs-2019/start-window-create-new-project.png)

   Otevře se okno **Vytvořit nový projekt** a zobrazí se několik *šablon*projektu . Šablona obsahuje základní soubory a nastavení potřebné pro daný typ projektu.

1. Chcete-li najít šablonu, kterou chceme, zadejte nebo zadejte do vyhledávacího pole **konzolu .net core.** Seznam dostupných šablon se automaticky filtruje na základě zadaných klíčových slov. Výsledky šablony můžete dále filtrovat výběrem **jazyka c#** z rozevíracího seznamu **Jazyk.** Vyberte šablonu **Konzola aplikace (.NET Core)** a pak zvolte **Další**.

    ![Vytvoření nového projektu v sadě Visual Studio](../media/vs-2019/create-new-project.png)

1. V okně **Konfigurovat nový projekt** zadejte **HelloWorld** do pole **Název projektu,** volitelně změňte umístění adresáře pro soubory projektu a pak zvolte **Vytvořit**.

   ![Konfigurace nového projektu v sadě Visual Studio](../media/vs-2019/configure-new-project.png)

   Visual Studio vytvoří projekt. Je to jednoduchá aplikace "Hello World", která volá metodu <xref:System.Console.WriteLine?displayProperty=nameWithType> pro zobrazení doslovného řetězce "Hello World!" v okně konzoly (výstup programu).

   Krátce, měli byste vidět něco jako následující:

   ![Visual Studio – sada IDE](../media/vs-2019/overview-ide-console-app.png)

   Kód Jazyka C# pro vaši aplikaci se zobrazí v okně editoru, který zabírá většinu místa. Všimněte si, že text je automaticky obarven a označuje různé části kódu, například klíčová slova a typy. Kromě toho malé, svislé přerušované čárky v kódu označují, které složená závorky se vzájemně shodují, a čísla řádků vám později pomohou najít kód. Můžete zvolit malé, krabicové znaménko mínus, které chcete sbalit nebo rozbalit bloky kódu. Tato funkce osnovy kódu umožňuje skrýt kód, který nepotřebujete, což pomáhá minimalizovat nepořádek na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně s názvem **Průzkumník řešení**.

   ![IDE visual studia s červenými rámečky](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale pojďme se přesunout na teď.

1. Nyní spusťte aplikaci. To lze provést výběrem **možnosti Spustit bez ladění** z nabídky **Ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves Ctrl**+**F5**.

   ![Ladění > Spustit bez ladění nabídky](../media/overview-start-without-debugging.png)

   Visual Studio vytvoří aplikaci a otevře se okno konzoly se zprávou **Hello World!**. Nyní máte spuštěnou aplikaci!

   ![Okno konzoly](../media/vs-2019/overview-console-window.png)

1. Chcete-li zavřít okno konzoly, stiskněte libovolnou klávesu na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Před řádek, který říká: `Console.WriteLine("Hello World!");`

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazuje V okně konzoly **je vaše jméno** a poté počká, dokud uživatel nezadá nějaký text následovaný klávesou **Enter.**

1. Změňte řádek `Console.WriteLine("Hello World!");` s textem na následující kód:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu výběrem **ladění** > **Start bez ladění** nebo stisknutím **Ctrl**+**F5**.

   Visual Studio znovu vytvoří aplikaci a otevře se okno konzoly a zobrazí výzvu k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte **Enter**.

   ![Okno konzoly](../media/vs-2019/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Použití refaktoringu a technologie IntelliSense

Podívejme se na několik způsobů, jak [refaktoring](../../ide/refactoring-in-visual-studio.md) a [IntelliSense](../../ide/using-intellisense.md) vám může pomoci kód efektivněji.

Nejprve přejmenujme proměnnou: `name`

1. Poklepejte `name` na proměnnou a vyberte ji.

2. Zadejte nový název proměnné, **uživatelské jméno**.

   Všimněte si, že se kolem proměnné zobrazí šedé pole a na okraji se zobrazí žárovka.

::: moniker range="vs-2017"

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce](../../ide/quick-actions.md). Vyberte **Přejmenovat 'jméno' na 'uživatelské jméno'**.

   ![Přejmenování akce v sadě Visual Studio](../media/rename-quick-action.png)

   Proměnná je přejmenována v rámci projektu, což je v našem případě pouze dvě místa.

   ![Animovaný gif zobrazující refaktoring přejmenování v sadě Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce](../../ide/quick-actions.md). Vyberte **Přejmenovat 'jméno' na 'uživatelské jméno'**.

   ![Přejmenování akce v sadě Visual Studio](../media/vs-2019/rename-quick-action.png)

   Proměnná je přejmenována v rámci projektu, což je v našem případě pouze dvě místa.

::: moniker-end

4. Nyní se podívejme na IntelliSense. Pod řádkem `Console.WriteLine($"\nHello {username}!");`, `DateTime now = DateTime.`který říká , zadejte .

   V poli se zobrazí <xref:System.DateTime> členové třídy. Kromě toho se popis aktuálně vybraného člena zobrazí v samostatném poli.

   ![Členové seznamu IntelliSense v sadě Visual Studio](../media/intellisense-list-members.png)

5. Vyberte člena s názvem **Nyní**, což je vlastnost třídy, poklepáním na něj nebo stisknutím **klávesy Tab**. Dokončete řádek kódu přidáním středníku na konec.

6. Pod tím zadejte nebo vložte následující řádky kódu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType>je trochu jiný <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v tom, že nepřidává řádek zakončení po vytištění. To znamená, že další text, který je odeslán do výstupu, se vytiskne na stejném řádku. Můžete najet nad každou z těchto metod v kódu zobrazíte jejich popis.

7. Dále použijeme refaktoring znovu, aby byl kód trochu výstižnější. Klikněte na `now` proměnnou `DateTime now = DateTime.Now;`v řádku .

   Všimněte si, že na okraji na tomto řádku se objeví malá ikona šroubováku.

8. Kliknutím na ikonu šroubováku zobrazíte, jaké návrhy má Visual Studio k dispozici. V tomto případě se zobrazuje [inline dočasné proměnné](../../ide/reference/inline-temporary-variable.md) refaktoring odebrat řádek kódu beze změny celkového chování kódu:

   ![Inline dočasné proměnné refaktoring v sadě Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Chcete-li kód refaktorovat, klepněte na položku **Inline temporary variable.**

::: moniker range="vs-2017"

10. Spusťte program znovu stisknutím **klávesctrl**+**F5**. Výstup vypadá asi takto:

    ![Okno konzoly s výstupem programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Spusťte program znovu stisknutím **klávesctrl**+**F5**. Výstup vypadá asi takto:

    ![Okno konzoly s výstupem programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Ladicí kód

Při psaní kódu je třeba jej spustit a otestovat na chyby. Systém ladění visual studia umožňuje krokovat kód po jednom příkazu a kontrolovat proměnné. Můžete nastavit *zarážky,* které zastaví provádění kódu na určitém řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a další.

Nastavíme zarážku tak, aby `username` se zoírá hodnota proměnné, zatímco je program "v letu".

1. Najděte řádek kódu, `Console.WriteLine($"\nHello {username}!");`který říká . Chcete-li nastavit zarážku na tomto řádku kódu, to znamená, aby program pozastavit provádění na tomto řádku, klepněte na zcela levý okraj editoru. Můžete také kliknout kamkoli v řádku kódu a pak stisknout **klávesu F9**.

   Na levém okraji se zobrazí červený kruh a kód je zvýrazněn červeně.

   ![Zarážka na řádku kódu v sadě Visual Studio](../media/breakpoint.png)

1. Ladění můžete spustit výběrem **možnosti Ladění** > **spouštět** ladění nebo stisknutím **klávesy F5**.

1. Když se zobrazí okno konzoly a zeptá se na vaše jméno, zadejte ho a stiskněte **Enter**.

   Fokus se vrátí do editoru kódu sady Visual Studio a řádek kódu s zarážkou je zvýrazněn žlutě. To znamená, že se jedná o další řádek kódu, který program spustí.

1. Najeďte myší `username` na proměnnou, abyste viděli její hodnotu. Případně můžete kliknout pravým `username` tlačítkem myši a vybrat **přidat hodinky** a přidat proměnnou do okna **Kukátko,** kde můžete také zobrazit její hodnotu.

   ![Hodnota proměnné během ladění v sadě Visual Studio](../media/debugging-variable-value.png)

1. Chcete-li, aby byl program spuštěn až do konce, stiskněte znovu **klávesu F5.**

Další podrobnosti o ladění v sadě Visual Studio najdete v [tématu prohlídka funkce ladicího programu](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Přizpůsobení sady Visual Studio

Uživatelské rozhraní sady Visual Studio můžete přizpůsobit, včetně změny výchozího barevného motivu. Změna na **tmavý** motiv:

1. Na řádku nabídek zvolte**Možnosti** **nástrojů,** > abyste otevřeli dialogové okno **Volby.**

::: moniker range="vs-2017"

2. Na stránce **Volby Obecné** **prostředí** > změňte výběr **motivu Barva** na **Tmavý**a pak zvolte **OK**.

   Barevný motiv pro celé ide se změní na **Tmavý**.

   ![Visual Studio v tmavém motivu](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **Volby Obecné** **prostředí** > změňte výběr **motivu Barva** na **Tmavý**a pak zvolte **OK**.

   Barevný motiv pro celé ide se změní na **Tmavý**.

   ![Visual Studio v tmavém motivu](../media/vs-2019/dark-theme.png)

::: moniker-end

Další informace o dalších způsobech přizpůsobení prostředí IDE najdete v [tématu Přizpůsobení sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).