---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: jillfra
author: jillre
manager: jillfra
ms.topic: include
ms.openlocfilehash: 973af983d0f07b0aceeedfc865280deea115f179
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632457"
---
*Integrované vývojové prostředí* sady Visual Studio je kreativní spouštěcí panel, který můžete použít k úpravám, ladění a vytváření kódu a pak k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatou funkcí, který se dá použít pro mnoho aspektů vývoje softwaru. Nad rámec a nad standardním editorem a ladicím programem, který využívá většina IDEs, Visual Studio obsahuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a mnoho dalších funkcí, které usnadňují proces vývoje softwaru.

::: moniker range="vs-2017"

![Integrované vývojové prostředí (IDE) sady Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![The rozhraní IDE sady Visual Studio 2019](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Tento obrázek ukazuje aplikaci Visual Studio s otevřeným projektem a několika okny s nástroji Key, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, navigovat a spravovat soubory kódu. **Průzkumník řešení** může přispět k uspořádání kódu seskupením souborů do [řešení a projektů](../tutorial-projects-solutions.md).

- [Okno editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), kde se pravděpodobně bude strávit většinou času, zobrazuje obsah souboru. Tady můžete upravit kód nebo navrhnout uživatelské rozhraní, jako je okno s tlačítky a textovými poli.

::: moniker range="vs-2017"

- [Okno výstup](../../ide/reference/output-window.md) (dole na střed) je místo, kde aplikace Visual Studio odesílá oznámení, jako jsou například ladění a chybové zprávy, upozornění kompilátoru, zprávy o stavu publikování a další. Každý zdroj zprávy má svou vlastní kartu.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (vpravo dole) umožňuje sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) a [Správa verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Enterprise

::: moniker range="vs-2017"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako sadu Visual Studio 2017 a je optimalizovaná pro vývoj aplikací pro různé platformy a mobilní aplikace. Tento článek se zaměřuje na verzi systému Windows sady Visual Studio 2017.

Existují tři edice sady Visual Studio 2017: komunita, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v článku [porovnání sady Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

::: moniker range="vs-2019"

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako sadu Visual Studio 2019 a je optimalizovaná pro vývoj aplikací pro různé platformy a mobilní aplikace. Tento článek se zaměřuje na verzi systému Windows sady Visual Studio 2019.

Existují tři edice sady Visual Studio 2019: komunita, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v tématu [porovnání sady Visual Studio](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

## <a name="popular-productivity-features"></a>Oblíbené funkce pro produktivitu

Některé z oblíbených funkcí v aplikaci Visual Studio, které vám pomůžou zvýšit produktivitu při vývoji softwaru, zahrnují:

- Vlnovky a [rychlé akce](../../ide/quick-actions.md)

   Vlnovky jsou podtržení vlnovkou, které upozorňují na chyby nebo potenciální problémy ve vašem kódu při psaní. Tato vizuální podoby vám umožní opravit problémy hned bez čekání na zjištění chyby během sestavení nebo při spuštění programu. Pokud najedete myší na vlnovku, zobrazí se další informace o chybě. Žárovka se může zobrazit také na levém okraji s akcemi, které jsou známé jako rychlé akce, a opravit tak chybu.

   ![Vlnovky v aplikaci Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Vyčištění kódu

   Kliknutím na tlačítko naformátujete kód a použijete všechny opravy kódu navrhované [nastavením stylu kódu](../../ide/reference/options-text-editor-csharp-formatting.md), [konvencemi editorconfig](../../ide/create-portable-custom-editor-options.md)a [analyzátory Roslyn](../../code-quality/roslyn-analyzers-overview.md). **Vyčištění kódu** pomáhá vyřešit problémy v kódu před tím, než se přejde na revizi kódu. (Aktuálně k dispozici pouze pro C# kód.)

   ![Tlačítko pro vyčištění kódu v aplikaci Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako je například inteligentní přejmenování proměnných, extrakce jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ![Refaktoring v sadě Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech zapisují malé bity kódu za vás. Vypadá to, že je v editoru vložená základní dokumentace, která vám ušetří informace o typu jinde. Funkce IntelliSense se liší podle jazyka. Další informace naleznete v tématu [ C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)a [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Následující obrázek ukazuje, jak IntelliSense zobrazuje seznam členů pro typ:

   ![Seznam členů sady Visual Studio](../media/intellisense-list-members.png)

- Vyhledávací pole

   Visual Studio se může zdát při velkém množství nabídek, možností a vlastností. Vyhledávací pole je skvělým způsobem, jak rychle najít, co potřebujete v aplikaci Visual Studio. Když začnete psát název hledaného textu, Visual Studio zobrazí seznam výsledků, které vám přesně přejdou, kde potřebujete. Pokud potřebujete přidat funkci do sady Visual Studio, například chcete-li přidat podporu pro další programovací jazyk, vyhledávací pole poskytuje výsledky, které otevřou Instalační program pro Visual Studio k instalaci úlohy nebo jednotlivé součásti.

   > [!TIP]
   > Stiskněte klávesu **Ctrl** +**Q** jako zástupce vyhledávacího pole.

   ::: moniker range="vs-2017"

   ![Rychlé spuštění vyhledávacího pole v aplikaci Visual Studio 2017](../media/quick-launch-nuget.png)

   Další informace najdete v tématu [Snadné spuštění](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Vyhledávací pole v aplikaci Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

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

1. Otevřete Visual Studio.

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt**.

   ![Soubor > Nový projekt na řádku nabídek](../media/file-new-project-menu.png)

   Dialogové okno **Nový projekt** ukazuje několik *šablon*projektů. Šablona obsahuje základní soubory a nastavení potřebná pro daný typ projektu.

1. Zvolte kategorii šablony **.NET Core** v kategorii **vizuál C#** a pak zvolte šablonu **aplikace konzoly (.NET Core)** . Do textového pole **název** zadejte **HelloWorld**a pak klikněte na tlačítko **OK** .

   ![Šablona aplikace .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Pokud nevidíte kategorii **.NET Core** , musíte nainstalovat **vývojovou úlohu .NET Core pro různé platformy** . Uděláte to tak, že kliknete na odkaz **otevřít instalační program pro Visual Studio** v levé dolní části dialogového okna **Nový projekt** . Po Instalační program pro Visual Studio se posuňte dolů a vyberte úlohu **vývoje .NET Core pro různé platformy** a pak vyberte **Upravit**.

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci "Hello World", která volá metodu <xref:System.Console.WriteLine?displayProperty=nameWithType> k zobrazení řetězcového literálu "Hello World!" v okně konzoly (programový výstup).

   Za chvíli by se měla zobrazit následující text:

   ![Visual Studio – sada IDE](../media/overview-ide-console-app.png)

   C# Kód vaší aplikace se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně barevný, aby označoval různé části kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které závorky se shodují s sebou, a čísla řádků vám pomůžou později vyhledat kód. Můžete zvolit malý, zabalené znaménko minus pro sbalení nebo rozbalení bloků kódu. Tato funkce osnovy kódu vám umožní skrýt kód, který nepotřebujete, a pomoct tak minimalizovat přehlednost na obrazovce. Soubory projektu jsou uvedeny na pravé straně okna s názvem **Průzkumník řešení**.

   ![Integrované vývojové prostředí sady Visual Studio s červenými poli](../media/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale teď se k ní přiblížíme.

1. Teď aplikaci spusťte. To lze provést výběrem možnosti **Spustit bez ladění** v nabídce **ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves Ctrl** +**F5**.

   ![Ladit > Spustit bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se zprávou **Hello World!** . Teď máte spuštěnou aplikaci.

   ![Okno konzoly](../media/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Přidejte následující C# kód před řádek, který říká `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazuje, **Jaké je vaše jméno?** v okně konzoly a pak počká, dokud uživatel nezadá text následovaný klávesou **ENTER** .

1. Změňte řádek, který říká `Console.WriteLine("Hello World!");` k následujícímu kódu:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu tak, že vyberete **ladění** > **Spustit bez ladění** nebo stisknutím klávesy **CTRL** +**F5**.

   Visual Studio aplikaci znovu sestaví a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte klávesu **ENTER**.

   ![Vstup okna konzoly](../media/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete Visual Studio.

   Otevře se okno Start s různými možnostmi klonování úložiště, otevřením posledního projektu nebo vytvořením značky nového projektu.

1. Vyberte **vytvořit nový projekt**.

   ![Úvodní okno sady Visual Studio – vytvořit nový projekt](../media/vs-2019/start-window-create-new-project.png)

   Otevře se okno **vytvořit nový projekt** a zobrazí se několik *šablon*projektů. Šablona obsahuje základní soubory a nastavení potřebná pro daný typ projektu.

1. Pokud chcete najít požadovanou šablonu, zadejte nebo zadejte do vyhledávacího pole **konzolu .NET Core** . Seznam šablon, které jsou k dispozici, se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dál filtrovat volbou **C#** z rozevíracího seznamu **jazyk** . Vyberte šablonu **aplikace konzoly (.NET Core)** a klikněte na tlačítko **Další**.

    ![Vytvoření nového projektu v aplikaci Visual Studio](../media/vs-2019/create-new-project.png)

1. V okně **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** a volitelně změňte umístění adresáře pro soubory projektu a pak zvolte **vytvořit**.

   ![Konfigurace nového projektu v aplikaci Visual Studio](../media/vs-2019/configure-new-project.png)

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci "Hello World", která volá metodu <xref:System.Console.WriteLine?displayProperty=nameWithType> k zobrazení řetězcového literálu "Hello World!" v okně konzoly (programový výstup).

   Za chvíli by se měla zobrazit následující text:

   ![Visual Studio – sada IDE](../media/vs-2019/overview-ide-console-app.png)

   C# Kód vaší aplikace se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně barevný, aby označoval různé části kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které závorky se shodují s sebou, a čísla řádků vám pomůžou později vyhledat kód. Můžete zvolit malý, zabalené znaménko minus pro sbalení nebo rozbalení bloků kódu. Tato funkce osnovy kódu vám umožní skrýt kód, který nepotřebujete, a pomoct tak minimalizovat přehlednost na obrazovce. Soubory projektu jsou uvedeny na pravé straně okna s názvem **Průzkumník řešení**.

   ![Integrované vývojové prostředí sady Visual Studio s červenými poli](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale teď se k ní přiblížíme.

1. Teď aplikaci spusťte. To lze provést výběrem možnosti **Spustit bez ladění** v nabídce **ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves Ctrl** +**F5**.

   ![Ladit > Spustit bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se zprávou **Hello World!** . Teď máte spuštěnou aplikaci.

   ![Okno konzoly](../media/vs-2019/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Přidejte následující C# kód před řádek, který říká `Console.WriteLine("Hello World!");`:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Tento kód zobrazuje, **Jaké je vaše jméno?** v okně konzoly a pak počká, dokud uživatel nezadá text následovaný klávesou **ENTER** .

1. Změňte řádek, který říká `Console.WriteLine("Hello World!");` k následujícímu kódu:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Spusťte aplikaci znovu tak, že vyberete **ladění** > **Spustit bez ladění** nebo stisknutím klávesy **CTRL** +**F5**.

   Visual Studio aplikaci znovu sestaví a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte klávesu **ENTER**.

   ![Okno konzoly](../media/vs-2019/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Použití refaktoringu a IntelliSense

Pojďme se podívat na několik způsobů, jak [refaktoring](../../ide/refactoring-in-visual-studio.md) , tak aby vám [IntelliSense](../../ide/using-intellisense.md) mohl efektivněji pomáhat s kódem.

Nejdřív přejmenujte `name` proměnnou:

1. Dvakrát klikněte na proměnnou `name` a vyberte ji.

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

4. Teď se podívejme na technologii IntelliSense. Pod řádkem, který říká `Console.WriteLine($"\nHello {username}!");`, zadejte `DateTime now = DateTime.`.

   Pole zobrazuje členy třídy <xref:System.DateTime>. Kromě toho popis aktuálně vybraného člena se zobrazí v samostatném poli.

   ![Členové seznamu IntelliSense v aplikaci Visual Studio](../media/intellisense-list-members.png)

5. Vyberte člena s názvem **nyní**, což je vlastnost třídy, dvakrát na ni klikněte nebo stiskněte klávesu **TAB**. Dokončete řádek kódu tak, že na konec přidáte středník.

6. Níže zadejte nebo vložte následující řádky kódu:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> se trochu liší od <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v tom, že po vytištění nepřidá ukončovací znak řádku. To znamená, že další část textu, která je odeslána do výstupu, bude vytištěna na stejném řádku. Svůj popis můžete zobrazit tak, že najedete myší na každou z těchto metod v kódu.

7. Dále znovu použijeme refaktoring, aby byl kód trochu výstižnější. V `DateTime now = DateTime.Now;` řádku klikněte na proměnnou `now`.

   Všimněte si, že na okraji na daném řádku se zobrazí trochu Screwdriver ikona.

8. Klikněte na ikonu Screwdriver a zjistěte, jaké návrhy nabízí Visual Studio. V tomto případě se zobrazuje [vložená dočasná](../../ide/reference/inline-temporary-variable.md) refaktoring proměnné pro odebrání řádku kódu beze změny celkového chování kódu:

   ![Refaktoring dočasné proměnné Refaktoring v aplikaci Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Klikněte na **vloženou dočasnou proměnnou** a refaktorujte kód.

::: moniker range="vs-2017"

10. Spusťte program znovu stisknutím klávesy **Ctrl** +**F5**. Výstup bude vypadat nějak takto:

    ![Okno konzoly s výstupem programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Spusťte program znovu stisknutím klávesy **Ctrl** +**F5**. Výstup bude vypadat nějak takto:

    ![Okno konzoly s výstupem programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Ladicí kód

Při psaní kódu ho musíte spustit a otestovat pro chyby. Ladicí systém sady Visual Studio umožňuje Krokovat s kódem v jednom okamžiku a při procházení proměnných kontrolovat proměnné. Můžete nastavit *zarážky* , které zastaví provádění kódu na určitém řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a dalších.

Pojďme nastavit zarážku, aby se zobrazila hodnota proměnné `username`, zatímco program je "v letu".

1. Vyhledejte řádek kódu, který říká `Console.WriteLine($"\nHello {username}!");`. Chcete-li nastavit zarážku na tomto řádku kódu, to znamená, aby program pozastavil provádění na tomto řádku, klikněte na levý levý okraj editoru. Můžete také kliknout kamkoli na řádek kódu a stisknout **F9**.

   V levém horním rohu se zobrazí červený kroužek a kód se zvýrazní červeně.

   ![Zarážka na řádku kódu v aplikaci Visual Studio](../media/breakpoint.png)

1. Spusťte ladění tak, že vyberete **ladění**  > **Spustit ladění** nebo stisknete klávesu **F5**.

1. Jakmile se zobrazí okno konzoly a požádá o vaše jméno, zadejte ho do pole a stiskněte klávesu **ENTER**.

   Fokus se vrátí do editoru kódu sady Visual Studio a řádek kódu se zarážkou se zvýrazní žlutě. To znamená, že se jedná o další řádek kódu, který bude program spouštět.

1. Pokud chcete zobrazit jeho hodnotu, najeďte myší na proměnnou `username`. Případně můžete kliknout pravým tlačítkem na `username` a výběrem **Přidat kukátko** přidat proměnnou do okna **kukátka** , kde můžete také zobrazit její hodnotu.

   ![Hodnota proměnné během ladění v aplikaci Visual Studio](../media/debugging-variable-value.png)

1. Pokud chcete nechat program běžet na dokončení, stiskněte znovu klávesu **F5** .

Další informace o ladění v aplikaci Visual Studio naleznete v tématu [prohlídka funkcí ladicího programu](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Přizpůsobení sady Visual Studio

Můžete přizpůsobit uživatelské rozhraní sady Visual Studio, včetně změny výchozího barevného motivu. Postup pro změnu na **tmavý** motiv:

1. Na panelu nabídek vyberte možnost **nástroje**  > **Možnosti** . otevře se dialogové okno **Možnosti** .

::: moniker range="vs-2017"

2. Na stránce **prostředí** > **Obecné** možnosti změňte výběr **barevného motivu** na **tmavý**a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí se změní na **tmavý**.

   ![Visual Studio v tmavém motivu](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **prostředí** > **Obecné** možnosti změňte výběr **barevného motivu** na **tmavý**a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí se změní na **tmavý**.

   ![Visual Studio v tmavém motivu](../media/vs-2019/dark-theme.png)

::: moniker-end

Další informace o dalších způsobech přizpůsobení rozhraní IDE naleznete v tématu [přizpůsobení sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).