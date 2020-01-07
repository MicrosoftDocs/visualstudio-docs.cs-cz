---
title: Přehled Visual Basic vývojářů
ms.date: 11/15/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5cf5f8d3660abcf941eb5cc429b8f190459d9c56
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596044"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Vítejte v integrovaném vývojovém prostředí sady Visual Studio | Visual Basic

Visual Studio *integrovaného vývojového prostředí* je creative odrazový, můžete použít k úpravám, ladit a sestavovat kód a pak publikujete aplikaci. Integrované vývojové prostředí (IDE) je plně funkční program, který lze použít pro mnoho aspektů vývoje softwaru. Kromě standardní editor a ladicího programu, že většina integrovanými vývojovými prostředími poskytnout, Visual Studio obsahuje kompilátory, nástroje dokončování kódu, grafičtí návrháři pro a mnoho dalších funkcí, které usnadňují proces vývoje softwaru.

::: moniker range="vs-2017"

![Prostředí IDE sady Visual Studio](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![integrované vývojové prostředí (IDE) sady Visual Studio 2019](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Tento obrázek ukazuje sady Visual Studio s otevřít projekt a několika okny nástrojů klíče, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, navigovat a spravovat soubory kódu. **Průzkumník řešení** pomáhá organizovat kód seskupením soubory do [řešení a projekty](tutorial-projects-solutions.md).

- [Okno editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (System center), kde budete pravděpodobně tráví většinu svého času zobrazí obsah souboru. Toto je, kde můžete upravit kódu nebo navrhnout uživatelské rozhraní, jako je například okno s tlačítka a textová pole.

- [Okno výstup](../../ide/reference/output-window.md) (dole uprostřed) je, kde sada Visual Studio odešle oznámení, jako jsou ladění a chybové zprávy, upozornění kompilátoru, publikování stavové zprávy a další. Každý zdroj zprávy má svůj vlastní kartu.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (vpravo dole) umožňuje sledování pracovních položek a sdílet s ostatními kód pomocí technologie pro řízení verze, například [Git](https://git-scm.com/) a [Team Foundation verze ovládacího prvku (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Edice

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako Visual Studio 2017 a je optimalizovaná pro vývoj multiplatformní a mobilní aplikace. Tento článek se týká Windows verze sady Visual Studio 2017.

Existují 3 edicích sady Visual Studio 2017: Community, Professional a Enterprise. V tématu [porovnání Visual Studio 2017 integrovanými vývojovými prostředími](https://visualstudio.microsoft.com/vs/compare/) Další informace o funkcích, které jsou podporované v každé edici.

## <a name="popular-productivity-features"></a>Oblíbené pro zvýšení produktivity

Mezi oblíbené funkce v sadě Visual Studio, které vám umožní být produktivnější při vývoji softwaru, patří:

- Podtržení vlnovkou a [rychlé akce](../../ide/quick-actions.md)

   Podtržení vlnovkou jsou podtržení vlnovkou, které vás upozorní na chyby nebo potenciální problémy v kódu při psaní. Tyto vizuální záchytné body umožňují opravit problémy okamžitě bez čekání na chyby mají být zjišťované, a během sestavování nebo při spuštění programu. Pokud najedete myší vlnovka, zobrazí se další informace o této chybě. Žárovky může také zobrazit na levém okraji s akcemi, známé jako rychlých akcí, chcete-li vyřešit chybu.

   ::: moniker range="vs-2017"

   ![Podtržení vlnovkou v sadě Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Podtržení vlnovkou v sadě Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako jsou inteligentní přejmenováním proměnné, extrahování jeden nebo více řádků kódu do nové metody, změna pořadí parametrů metod a dalších.

   ::: moniker range="vs-2017"

   ![Nabídka refaktoringu v aplikaci Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Nabídka refaktoringu v aplikaci Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   Technologie IntelliSense je termín pro sadu funkcí, která zobrazí informace o kódu přímo v editoru a v některých případech může zapisovat malé části kódu za vás. Je to jako mít základní dokumentaci vložené v editoru, což vám ušetří nebudou muset vyhledat informace o typu jinde. Funkce technologie IntelliSense se liší podle jazyka. Další informace najdete v tématu [jazyka C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [technologie IntelliSense jazyka JavaScript](../../ide/javascript-intellisense.md), a [jazyka Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Následující obrázek znázorňuje, jak technologie IntelliSense zobrazí seznam členů pro typ:

   ::: moniker range="vs-2017"

   ![Seznam členů sady Visual Studio](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Seznam členů sady Visual Studio](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Vyhledávací pole

   Visual Studio, může to působit příliš složitě čas od času s tolika nabídky, možnosti a vlastnosti. Vyhledávací pole je skvělým způsobem, jak rychle najít, co potřebujete v aplikaci Visual Studio. Když začnete psát název něco, co hledáte, Visual Studio obsahuje výsledky, které dostanete, přesně, kde potřebujete přejít. Pokud potřebujete přidat funkci do sady Visual Studio, například chcete-li přidat podporu pro další programovací jazyk, vyhledávací pole poskytuje výsledky, které otevřou Instalační program pro Visual Studio k instalaci úlohy nebo jednotlivé součásti.

   > [!TIP]
   > Stiskněte klávesu **Ctrl**+**Q** jako zástupce vyhledávacího pole.

   ::: moniker range="vs-2017"

   ![Rychlé spuštění vyhledávacího pole v aplikaci Visual Studio 2017](../media/quick-launch-nuget.png)

   Další informace najdete v tématu [Snadné spuštění](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Vyhledávací pole v aplikaci Visual Studio 2019](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Spoluupravujte a laďte s ostatními v reálném čase bez ohledu na typ aplikace nebo programovací jazyk. Můžete okamžitě a bezpečně sdílet svůj projekt a podle potřeby ladit relace, instance Terminálové služby, webové aplikace localhost, hlasové hovory a další.

- [Hierarchie volání](../../ide/reference/call-hierarchy.md)

   **Hierarchie volání** okno zobrazuje metody, které volají vybrané metody. To může být užitečné informace, pokud uvažujete o změně nebo odebrání metodu, nebo když se snažíte vysledování chybu.

   ::: moniker range="vs-2017"

   ![Okno hierarchie volání v aplikaci Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Okno hierarchie volání v aplikaci Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vám pomůže najít odkazy na kód, změny kódu, propojené chyby, pracovní položky, revize kódu a testy jednotek, to vše bez opuštění editoru.

   ::: moniker range="vs-2017"

   ![CodeLens v aplikaci Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens v aplikaci Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Přejít k definici](../../ide/go-to-and-peek-definition.md)

   Funkce Přejít k definici přejdete přímo do umístění, kde je funkce nebo typ definován.

   ::: moniker range="vs-2017"

   ![Přejít k definici v aplikaci Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Přejít k definici v aplikaci Visual Studio 2019](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Náhled definice](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **Definice operace Peek** okno zobrazuje definici metody nebo typ bez nutnosti otevřít ve skutečnosti samostatný soubor.

   ::: moniker range="vs-2017"

   ![Náhled definice v aplikaci Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Náhled definice v aplikaci Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Instalace sady Visual Studio IDE

V této části vytvoříte jednoduchý projekt, abyste si vyzkoušeli některé z akcí, které můžete dělat se sadou Visual Studio. Změníte barevný motiv, použijete [IntelliSense](../../ide/using-intellisense.md) jako pomůcku pro psaní kódu a ladit aplikaci pro zobrazení hodnoty proměnné během provádění programu.

::: moniker range="vs-2017"

Pokud chcete začít, [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ho do svého systému. Modulární instalačního programu umožňuje vybrat a nainstalovat *úlohy*, což jsou skupiny funkce potřebné pro programovací jazyk nebo platformu dáváte přednost. Postupovat podle kroků pro [vytvoření programu](#create-a-program), je nutné vybrat **vývoj pro různé platformy .NET Core** úloh během instalace.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete začít, [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ho do svého systému. Modulární instalačního programu umožňuje vybrat a nainstalovat *úlohy*, což jsou skupiny funkce potřebné pro programovací jazyk nebo platformu dáváte přednost. Postupovat podle kroků pro [vytvoření programu](#create-a-program), je nutné vybrat **vývoj pro různé platformy .NET Core** úloh během instalace.

::: moniker-end

![Úlohy pro vývoj pro různé platformy .NET core v instalační program sady Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Při prvním otevření sady Visual Studio se můžete volitelně [Přihlásit](../../ide/signing-in-to-visual-studio.md) pomocí účet Microsoft nebo svého pracovního nebo školního účtu.

## <a name="customize-visual-studio"></a>Přizpůsobení sady Visual Studio

Uživatelské rozhraní sady Visual Studio, včetně změn si můžete přizpůsobit výchozí barevný motiv.

### <a name="change-the-color-theme"></a>Změna barevného motivu

Chcete-li změnit na **tmavě** motivu:

::: moniker range="vs-2017"

1. Otevřít Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřít Visual Studio. V okně Start vyberte možnost **pokračovat bez kódu**.

   ![Okno Start v aplikaci Visual Studio 2019](media/vs-2019/continue-without-code.png)

   Otevře se rozhraní IDE.

::: moniker-end

2. V panelu nabídky zvolte **nástroje** > **možnosti** otevřít **možnosti** dialogového okna.

3. Na **prostředí** > **Obecné** stránka Možnosti, změna **barevný motiv** výběru **tmavě**a klikněte na tlačítko **OK**.

   ![Změnit barevný motiv na tmavý v aplikaci Visual Studio](media/change-color-theme.png)

   Barva motivu pro celý integrovaného vývojového prostředí se změní na **tmavě**.

   ::: moniker range="vs-2017"

   ![Visual Studio v tmavém motivu](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio v tmavém motivu](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Vybrat nastavení prostředí

Teď nakonfigurujeme Visual Studio tak, aby používalo nastavení prostředí, které je přizpůsobené Visual Basic vývojářům.

1. V panelu nabídky zvolte **nástroje** > **nastavení importu a exportu**.

2. V **Průvodci importem a exportem nastavení**vyberte **Obnovit všechna nastavení** na první stránce a pak zvolte **Další**.

3. Na stránce **Uložit aktuální nastavení** vyberte možnost pro uložení aktuálního nastavení, nebo ne, a poté klikněte na tlačítko **Další**. (Pokud jste nepřizpůsobili žádné nastavení, vyberte možnost **Ne, pouze resetovat nastavení a přepsat aktuální nastavení**.)

4. Na stránce **Výběr výchozí kolekce nastavení** zvolte **Visual Basic**a pak zvolte **Dokončit**.

5. Na stránce **obnovení dokončena** klikněte na tlačítko **Zavřít**.

Další informace o dalších způsobech mohli přizpůsobit integrovaného vývojového prostředí, najdete v článku [přizpůsobení sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Vytvoření programu

Pojďme začít a vytvořit jednoduchý program.

::: moniker range="vs-2017"

1. Na panelu nabídek aplikace Visual Studio vyberte **soubor** > **Nový projekt**.

   ![Soubor > Nový projekt v řádku nabídek](media/file-new-project-menu.png)

   **Nový projekt** dialogové okno zobrazí několik projektů *šablony*. Šablona obsahuje základní souborů a nastavení potřebných pro typ daného projektu.

1. Zvolte kategorii **.NET Core** v části **Visual Basic**a pak zvolte šablonu **Konzolová aplikace (.NET Core)** . V **název** textového pole, typ **HelloWorld**a pak vyberte **OK** tlačítko.

   ![Šablona aplikace .NET core](media/overview-npd.png)

   > [!NOTE]
   > Pokud se nezobrazí **.NET Core** kategorie, je nutné nainstalovat **vývoj pro různé platformy .NET Core** pracovního vytížení. Chcete-li to provést, zvolte **otevřít instalační program Visual Studio** odkaz v levé dolní části **nový projekt** dialogového okna. Jakmile se instalační program sady Visual Studio otevře, posuňte se dolů a vyberte **vývoj pro různé platformy .NET Core** úlohy a pak vyberte **změnit**.

   Visual Studio vytvoří projekt. To je jednoduchá aplikace "Hello World", která volá <xref:System.Console.WriteLine?displayProperty=nameWithType> metodu pro zobrazení řetězcový literál "Hello World!" v okně konzoly (výstup programu).

   Po chvíli, by měl vypadat přibližně takto:

   ![Visual Studio – sada IDE](media/overview-ide-console-app.png)

   Kód Visual Basic pro aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně zvýrazněné k označení různých částí kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které složené závorky odpovídat mezi sebou a čísla řádků vám pomohou vyhledat kód později. Můžete také malé, zabalený mínus bloky kódu rozbalíte nebo sbalíte. Tento kód funkce osnovy vám umožňuje skrýt kód, který už nebudete potřebovat, a usnadnit tak minimalizovat zbytečné soubory na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně **Průzkumníka řešení**.

   ![Visual Studio integrované vývojové prostředí s červená pole](media/overview-ide-console-app-red-boxes.png)

   K dispozici další nabídky a panely nástrojů, ale teď přejdeme teď.

1. Nyní spusťte aplikaci. To lze provést výběrem **spustit bez ladění** z **ladění** nabídky na řádku nabídek. Můžete také stisknout klávesu **Ctrl**+**F5**.

   ![Ladit > Spustit bez ladění nabídky](../media/overview-start-without-debugging.png)

   Visual Studio vytvoří aplikaci a otevře se okno konzoly se zprávou **Hello World!** . Nyní máte funkční aplikaci.

   ![Okno konzoly](../media/overview-console-window.png)

1. Zavřete okno konzoly stisknutím libovolné klávesy na klávesnici.

1. Přidejme do aplikace další kód. Přidejte následující kód Visual Basic před řádek, který říká `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Tento kód zobrazí **jak se jmenuješ?** v okně konzoly a potom počká, dokud uživatel zadá nějaký text, za nímž následuje **Enter** klíč.

1. Změňte řádek, který říká `Console.WriteLine("Hello World!")` v následujícím kódu:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Znovu spusťte aplikaci stisknutím **kombinace kláves Ctrl**+**F5**.

   Visual Studio znovu sestaví aplikaci a otevře se okno konzoly a vás vyzve k zadání název vaší.

1. Zadejte název v okně konzoly a stisknutím klávesy **Enter**.

   ![Vstup okno konzoly](../media/overview-console-input.png)

1. Stisknutím jakékoli klávesy zavřete okno konzoly a zastavit spuštěný program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Na panelu nabídek aplikace Visual Studio vyberte **soubor** > **Nový projekt**.

   ![Soubor > Nový projekt v řádku nabídek](media/vs-2019/file-new-project.png)

   Otevře se okno **vytvořit nový projekt** a zobrazí se několik *šablon*projektů. Šablona obsahuje základní souborů a nastavení potřebných pro typ daného projektu.

1. Pokud chcete najít požadovanou šablonu, zadejte nebo zadejte do vyhledávacího pole **konzolu .NET Core** . Seznam šablon, které jsou k dispozici, se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dál filtrovat volbou **Visual Basic** v rozevíracím seznamu **jazyk** .

1. Vyberte šablonu **aplikace konzoly (.NET Core)** a klikněte na tlačítko **Další**.

   ![Vytvoření nového projektu v aplikaci Visual Studio](media/vs-2019/create-new-project.png)

1. V okně **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** a volitelně změňte umístění adresáře pro soubory projektu a pak zvolte **vytvořit**.

   ![Konfigurace nového projektu v aplikaci Visual Studio](media/vs-2019/configure-new-project.png)

   Visual Studio vytvoří projekt. To je jednoduchá aplikace "Hello World", která volá <xref:System.Console.WriteLine?displayProperty=nameWithType> metodu pro zobrazení řetězcový literál "Hello World!" v okně konzoly (výstup programu).

   Po chvíli, by měl vypadat přibližně takto:

   ![Visual Studio – sada IDE](media/overview-ide-console-app.png)

   Kód Visual Basic pro aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně zvýrazněné k označení různých částí kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které složené závorky odpovídat mezi sebou a čísla řádků vám pomohou vyhledat kód později. Můžete také malé, zabalený mínus bloky kódu rozbalíte nebo sbalíte. Tento kód funkce osnovy vám umožňuje skrýt kód, který už nebudete potřebovat, a usnadnit tak minimalizovat zbytečné soubory na obrazovce. Soubory projektu jsou uvedeny na pravé straně v okně **Průzkumníka řešení**.

   ![Visual Studio integrované vývojové prostředí s červená pole](media/overview-ide-console-app-red-boxes.png)

   K dispozici další nabídky a panely nástrojů, ale teď přejdeme teď.

1. Nyní spusťte aplikaci. To lze provést výběrem **spustit bez ladění** z **ladění** nabídky na řádku nabídek. Můžete také stisknout klávesu **Ctrl**+**F5**.

   ![Ladit > Spustit bez ladění nabídky](media/vs-2019/start-without-debugging.png)

   Visual Studio vytvoří aplikaci a otevře se okno konzoly se zprávou **Hello World!** . Nyní máte funkční aplikaci.

   ![Okno konzoly](../media/vs-2019/overview-console-window.png)

1. Zavřete okno konzoly stisknutím libovolné klávesy na klávesnici.

1. Přidejme do aplikace další kód. Přidejte následující kód Visual Basic před řádek, který říká `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Tento kód zobrazí **jak se jmenuješ?** v okně konzoly a potom počká, dokud uživatel zadá nějaký text, za nímž následuje **Enter** klíč.

1. Změňte řádek, který říká `Console.WriteLine("Hello World!")` v následujícím kódu:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Znovu spusťte aplikaci stisknutím **kombinace kláves Ctrl**+**F5**.

   Visual Studio znovu sestaví aplikaci a otevře se okno konzoly a vás vyzve k zadání název vaší.

1. Zadejte název v okně konzoly a stisknutím klávesy **Enter**.

   ![Okno konzoly](../media/vs-2019/overview-console-input.png)

1. Stisknutím jakékoli klávesy zavřete okno konzoly a zastavit spuštěný program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Refaktoring a technologie IntelliSense

Podívejme se na několik způsobů, jak, který [refaktoring](../../ide/refactoring-in-visual-studio.md) a [IntelliSense](../../ide/using-intellisense.md) může pomoct kód efektivněji.

Nejprve přejmenujme `name` proměnné:

1. Dvakrát klikněte `name` proměnnou, která ho vyberte.

2. Zadejte nový název proměnné, **uživatelské jméno**.

   Všimněte si, že šedé pole se zobrazí kolem proměnnou a žárovky se zobrazí na okraji.

3. Vyberte ikonu žárovky k zobrazení dostupných [rychlé akce](../../ide/quick-actions.md). Vyberte **přejmenovat "název" na "username"** .

   ![Přejmenujte akci v sadě Visual Studio](media/rename-quick-action.png)

   Proměnná je přejmenovat v projektu, který v našem případě je pouze dvě místa.

4. Nyní Pojďme se podívat na IntelliSense. Pod řádkem, který říká `Console.WriteLine("Hello " + username + "!")`, zadejte následující fragment kódu:

    ```vb
   Dim now = Date.
   ```

   Pole zobrazuje jako objekty její členové <xref:System.DateTime> třídy. Popis aktuálně vybraného člena se navíc zobrazí v rámci samostatného pole.

   ![Seznam členů IntelliSense v sadě Visual Studio](media/intellisense-list-members.png)

5. Vyberte člen s názvem **nyní**, který je vlastností třídy, dvojím kliknutím na něj nebo jeho výběrem pomocí šipek nahoru nebo dolů a stisknutím klávesy **TAB**.

6. Níže zadejte nebo vložte následující řádky kódu:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> se mírně liší na <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> v tom, že po vytiskne nepřidá znakem ukončení řádku. To znamená, že další část textu, které je odesláno výstup vytiskne na stejném řádku. Myší nad každá z těchto metod v kódu zobrazíte jejich popis.

7. V dalším kroku použijeme refaktoring znovu provést trochu stručnější kód. Klikněte na proměnnou `now` v řádku `Dim now = Date.Now`.

   Všimněte si, že malou ikonu šroubovák se zobrazí na okraji na daném řádku.

8. Klikněte na ikonu šroubovák návrhy, které nabízí Visual Studio. V tomto případě se zobrazuje [vložená dočasná](../../ide/reference/inline-temporary-variable.md) refaktoring proměnné pro odebrání řádku kódu beze změny celkového chování kódu:

   ![Vložené dočasné proměnné refaktoring v sadě Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Klikněte na tlačítko **dočasná proměnná na řádku** Refaktorovat kód.

::: moniker range="vs-2017"

10. Spusťte program znovu stisknutím klávesy **Ctrl**+**F5**. Výstup bude vypadat přibližně takto:

    ![Okno konzoly s výstup programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Spusťte program znovu stisknutím klávesy **Ctrl**+**F5**. Výstup bude vypadat přibližně takto:

    ![Okno konzoly s výstup programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Ladění kódu

Při psaní kódu, musíte ji spustit a otestovat pro chyby. Ladění systému Visual Studio vám umožní krokovat kód jeden příkaz najednou a kontrolovat proměnné, co využijete. Můžete nastavit *zarážky* , který svém vyvolání zastaví provádění kódu na konkrétní řádek. Můžete sledovat, jak hodnota proměnné změny jako kód spustí a další.

Pojďme nastavit zarážku pro její hodnota `username` proměnné při "v cestě" program.

1. Vyhledejte řádek kódu, který říká `Console.WriteLine("Hello " + username + "!")`. Nastavit zarážku na tomto řádku kódu, to znamená, aby program pozastaví provádění na tomto řádku, klikněte v levém okraji editoru. Můžete také kliknout na libovolné místo na řádek kódu a stiskněte klávesu **F9**.

   V levém okraji se zobrazí červený kruh a kód se zvýrazní červeně.

   ![Zarážku na řádek kódu v sadě Visual Studio](media/breakpoint.png)

1. Spuštění ladění tak, že vyberete **ladění** > **spustit ladění** nebo stisknutím klávesy **F5**.

1. Když v okně konzoly se zobrazí a vyzve k zadání vaše jméno, zadejte jej a stiskněte klávesu **Enter**.

   Fokus se vrátí do editoru kódu sady Visual Studio a řádek kódu se zarážkou se zvýrazní žlutě. To znamená, že se jedná o další řádek kódu, který se spustí program.

1. Najeďte myší `username` proměnnou můžete zobrazit její hodnotu. Alternativně je můžete kliknout pravým tlačítkem na `username` a vyberte **Přidat kukátko** chcete přidat proměnnou **Watch** okno, kde můžete také zobrazit její hodnotu.

   ![Hodnota proměnné během ladění v sadě Visual Studio](media/debugging-variable-value.png)

1. Aby mohl program dokončen, stiskněte klávesu **F5** znovu.

Pokud chcete získat další informace o ladění v sadě Visual Studio, naleznete v tématu [prohlídka funkcí ladicího programu](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Další kroky

Prozkoumejte další Visual Studio na základě společně s některou z těchto úvodní články:

> [!div class="nextstepaction"]
> [Naučte se používat editor kódu.](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Seznamte se s projekty a řešení](tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také:

- Zjistit [další funkce sady Visual Studio](../../ide/advanced-feature-overview.md)
- Navštivte [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Čtení [blogu sady Visual Studio](https://devblogs.microsoft.com/visualstudio/)
