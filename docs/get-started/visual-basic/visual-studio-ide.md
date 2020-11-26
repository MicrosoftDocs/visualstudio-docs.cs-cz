---
title: Přehled Visual Basic vývojářů
description: Přečtěte si, jak pomocí sady Visual Studio upravovat, ladit a sestavovat kód a pak publikovat aplikace jako vývojář Visual Basic.
ms.date: 11/15/2018
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 990bff2832f290987ed29fd48b69f4d7a1a05bba
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189885"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Vítejte v integrovaném vývojovém prostředí sady Visual Studio | Visual Basic

*Integrované vývojové prostředí* sady Visual Studio je kreativní spouštěcí panel, který můžete použít k úpravám, ladění a vytváření kódu a pak k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatou funkcí, který se dá použít pro mnoho aspektů vývoje softwaru. Nad rámec a nad standardním editorem a ladicím programem, který využívá většina IDEs, Visual Studio obsahuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a mnoho dalších funkcí, které usnadňují proces vývoje softwaru.

::: moniker range="vs-2017"

![Integrované vývojové prostředí (IDE) sady Visual Studio](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![Integrované vývojové prostředí (IDE) sady Visual Studio 2019](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Tento obrázek ukazuje aplikaci Visual Studio s otevřeným projektem a několika okny s nástroji Key, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, navigovat a spravovat soubory kódu. **Průzkumník řešení** může přispět k uspořádání kódu seskupením souborů do [řešení a projektů](tutorial-projects-solutions.md).

- [Okno editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), kde se pravděpodobně bude strávit většinou času, zobrazuje obsah souboru. Tady můžete upravit kód nebo navrhnout uživatelské rozhraní, jako je okno s tlačítky a textovými poli.

- [Okno výstup](../../ide/reference/output-window.md) (dole na střed) je místo, kde aplikace Visual Studio odesílá oznámení, jako jsou například ladění a chybové zprávy, upozornění kompilátoru, zprávy o stavu publikování a další. Každý zdroj zprávy má svou vlastní kartu.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (vpravo dole) umožňuje sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) a [Správa verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true).

## <a name="editions"></a>Edice

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako sadu Visual Studio 2017 a je optimalizovaná pro vývoj aplikací pro různé platformy a mobilní aplikace. Tento článek se zaměřuje na verzi systému Windows sady Visual Studio 2017.

Existují tři edice sady Visual Studio 2017: komunita, Professional a Enterprise. Informace o tom, které funkce jsou v jednotlivých edicích podporované, najdete v článku [porovnání sady Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Oblíbené funkce pro produktivitu

Některé z oblíbených funkcí v aplikaci Visual Studio, které vám pomůžou zvýšit produktivitu při vývoji softwaru, zahrnují:

- Vlnovky a [rychlé akce](../../ide/quick-actions.md)

   Vlnovky jsou podtržení vlnovkou, které upozorňují na chyby nebo potenciální problémy ve vašem kódu při psaní. Tato vizuální podoby vám umožní opravit problémy hned bez čekání na zjištění chyby během sestavení nebo při spuštění programu. Pokud najedete myší na vlnovku, zobrazí se další informace o chybě. Žárovka se může zobrazit také na levém okraji s akcemi, které jsou známé jako rychlé akce, a opravit tak chybu.

   ::: moniker range="vs-2017"

   ![Vlnovky v aplikaci Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Vlnovky v aplikaci Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako je například inteligentní přejmenování proměnných, extrakce jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ::: moniker range="vs-2017"

   ![Nabídka refaktoringu v aplikaci Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Nabídka refaktoringu v aplikaci Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech zapisují malé bity kódu za vás. Vypadá to, že je v editoru vložená základní dokumentace, která vám ušetří informace o typu jinde. Funkce IntelliSense se liší podle jazyka. Další informace naleznete v tématu [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)a [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Následující obrázek ukazuje, jak IntelliSense zobrazuje seznam členů pro typ:

   ::: moniker range="vs-2017"

   ![Seznam členů sady Visual Studio](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Seznam členů sady Visual Studio](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Vyhledávací pole

   Visual Studio se může zdát při velkém množství nabídek, možností a vlastností. Vyhledávací pole je skvělým způsobem, jak rychle najít, co potřebujete v aplikaci Visual Studio. Když začnete psát název hledaného textu, Visual Studio zobrazí seznam výsledků, které vám přesně přejdou, kde potřebujete. Pokud potřebujete přidat funkci do sady Visual Studio, například chcete-li přidat podporu pro další programovací jazyk, vyhledávací pole poskytuje výsledky, které otevřou Instalační program pro Visual Studio k instalaci úlohy nebo jednotlivé součásti.

   > [!TIP]
   > Stiskněte klávesu **CTRL** + **Q** jako zástupce vyhledávacího pole.

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

   Okno **hierarchie volání** zobrazuje metody, které volají vybranou metodu. To může být užitečné v případě, že uvažujete o změně nebo odebrání metody nebo když se snažíte sledovat chybu.

   ::: moniker range="vs-2017"

   ![Okno hierarchie volání v aplikaci Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Okno hierarchie volání v aplikaci Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens pomáhá najít odkazy na váš kód, změny kódu, propojené chyby, pracovní položky, revize kódu a testování částí, aniž byste museli opustit Editor.

   ::: moniker range="vs-2017"

   ![CodeLens v aplikaci Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens v aplikaci Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Přejít k definici](../../ide/go-to-and-peek-definition.md)

   Funkce přejít k definici přejde přímo do umístění, kde je definována funkce nebo typ.

   ::: moniker range="vs-2017"

   ![Přejít k definici v aplikaci Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Přejít k definici v aplikaci Visual Studio 2019](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Náhled definice](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   V okně **Náhled definice** se zobrazí definice metody nebo typu bez skutečného otevření samostatného souboru.

   ::: moniker range="vs-2017"

   ![Náhled definice v aplikaci Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Náhled definice v aplikaci Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Instalace integrovaného vývojového prostředí sady Visual Studio

V této části vytvoříte jednoduchý projekt, abyste si vyzkoušeli některé z akcí, které můžete dělat se sadou Visual Studio. Změníte barevný motiv, použijete [IntelliSense](../../ide/using-intellisense.md) jako pomůcku pro psaní kódu a ladit aplikaci pro zobrazení hodnoty proměnné během provádění programu.

::: moniker range="vs-2017"

Pokud chcete začít, [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat *úlohy*, které jsou skupiny funkcí, které jsou potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle kroků pro [vytvoření programu](#create-a-program), nezapomeňte při instalaci vybrat úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete začít, [Stáhněte si Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ho do svého systému. Modulární instalační program umožňuje zvolit a nainstalovat *úlohy*, které jsou skupiny funkcí, které jsou potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle kroků pro [vytvoření programu](#create-a-program), nezapomeňte při instalaci vybrat úlohu **vývoje .NET Core pro různé platformy** .

::: moniker-end

![Úlohy vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Při prvním otevření sady Visual Studio se můžete volitelně [Přihlásit](../../ide/signing-in-to-visual-studio.md) pomocí účet Microsoft nebo svého pracovního nebo školního účtu.

## <a name="customize-visual-studio"></a>Přizpůsobení sady Visual Studio

Můžete přizpůsobit uživatelské rozhraní sady Visual Studio, včetně změny výchozího barevného motivu.

### <a name="change-the-color-theme"></a>Změna barevného motivu

Postup pro změnu na **tmavý** motiv:

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. V okně Start vyberte možnost **pokračovat bez kódu**.

   ![Okno Start v aplikaci Visual Studio 2019](media/vs-2019/continue-without-code.png)

   Otevře se rozhraní IDE.

::: moniker-end

2. V panelu nabídek **Tools**  >  otevřete dialogové okno **Možnosti** výběrem **Možnosti** nástroje.

3. Na stránce **Environment**  >  **Obecné** možnosti prostředí změňte výběr **barevného motivu** na **tmavý** a pak zvolte **OK**.

   ![Změnit barevný motiv na tmavý v aplikaci Visual Studio](media/change-color-theme.png)

   Barevný motiv pro celé vývojové prostředí se změní na **tmavý**.

   ::: moniker range="vs-2017"

   ![Visual Studio v tmavém motivu](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio v tmavém motivu](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Vybrat nastavení prostředí

Teď nakonfigurujeme Visual Studio tak, aby používalo nastavení prostředí, které je přizpůsobené Visual Basic vývojářům.

1. Na řádku nabídek klikněte na **nástroje**  >  **importovat a exportovat nastavení**.

2. V **Průvodci importem a exportem nastavení** vyberte **Obnovit všechna nastavení** na první stránce a pak zvolte **Další**.

3. Na stránce **Uložit aktuální nastavení** vyberte možnost pro uložení aktuálního nastavení, nebo ne, a poté klikněte na tlačítko **Další**. (Pokud jste nepřizpůsobili žádné nastavení, vyberte možnost **Ne, pouze resetovat nastavení a přepsat aktuální nastavení**.)

4. Na stránce **Výběr výchozí kolekce nastavení** zvolte **Visual Basic** a pak zvolte **Dokončit**.

5. Na stránce **obnovení dokončena** klikněte na tlačítko **Zavřít**.

Další informace o dalších způsobech přizpůsobení rozhraní IDE naleznete v tématu [přizpůsobení sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Vytvoření programu

Pojďme se podrobně a vytvořit jednoduchý program.

::: moniker range="vs-2017"

1. Na panelu nabídek aplikace Visual Studio vyberte **soubor** > **Nový projekt**.

   ![Soubor > nový projekt na řádku nabídek](media/file-new-project-menu.png)

   Dialogové okno **Nový projekt** ukazuje několik *šablon* projektů. Šablona obsahuje základní soubory a nastavení potřebná pro daný typ projektu.

1. Zvolte kategorii **.NET Core** v části **Visual Basic** a pak zvolte šablonu **Konzolová aplikace (.NET Core)** . Do textového pole **název** zadejte **HelloWorld** a pak klikněte na tlačítko **OK** .

   ![Šablona aplikace .NET Core](media/overview-npd.png)

   > [!NOTE]
   > Pokud nevidíte kategorii **.NET Core** , musíte nainstalovat **vývojovou úlohu .NET Core pro různé platformy** . Uděláte to tak, že kliknete na odkaz **otevřít instalační program pro Visual Studio** v levé dolní části dialogového okna **Nový projekt** . Po Instalační program pro Visual Studio se posuňte dolů a vyberte úlohu **vývoje .NET Core pro různé platformy** a pak vyberte **Upravit**.

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci "Hello World", která volá <xref:System.Console.WriteLine?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello World!" v okně konzoly (programový výstup).

   Za chvíli by se měla zobrazit následující text:

   ![Visual Studio – sada IDE](media/overview-ide-console-app.png)

   Kód Visual Basic pro aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně barevný, aby označoval různé části kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které závorky se shodují s sebou, a čísla řádků vám pomůžou později vyhledat kód. Můžete zvolit malý, zabalené znaménko minus pro sbalení nebo rozbalení bloků kódu. Tato funkce osnovy kódu vám umožní skrýt kód, který nepotřebujete, a pomoct tak minimalizovat přehlednost na obrazovce. Soubory projektu jsou uvedeny na pravé straně okna s názvem **Průzkumník řešení**.

   ![Integrované vývojové prostředí sady Visual Studio s červenými poli](media/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale teď se k ní přiblížíme.

1. Teď aplikaci spusťte. To lze provést výběrem možnosti **Spustit bez ladění** v nabídce **ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves CTRL** + **F5**.

   ![Ladit > spustit bez nabídky ladění](../media/overview-start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se zprávou **Hello World!**. Teď máte spuštěnou aplikaci.

   ![Okno konzoly](../media/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Přidejte následující kód Visual Basic před řádek, který říká `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Tento kód zobrazuje, **Jaké je vaše jméno?** v okně konzoly a pak počká, dokud uživatel nezadá text následovaný klávesou **ENTER** .

1. Změňte řádek, který říká `Console.WriteLine("Hello World!")` následujícímu kódu:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Spusťte aplikaci znovu stisknutím **klávesy CTRL** + **F5**.

   Visual Studio aplikaci znovu sestaví a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte klávesu **ENTER**.

   ![Vstup okna konzoly](../media/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

::: moniker range=">=vs-2019"

1. Na panelu nabídek aplikace Visual Studio vyberte **soubor** > **Nový projekt**.

   ![Soubor > nový projekt na řádku nabídek](media/vs-2019/file-new-project.png)

   Otevře se okno **vytvořit nový projekt** a zobrazí se několik *šablon* projektů. Šablona obsahuje základní soubory a nastavení potřebná pro daný typ projektu.

1. Pokud chcete najít požadovanou šablonu, zadejte nebo zadejte do vyhledávacího pole **konzolu .NET Core** . Seznam šablon, které jsou k dispozici, se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dál filtrovat volbou **Visual Basic** v rozevíracím seznamu **jazyk** .

1. Vyberte šablonu **aplikace konzoly (.NET Core)** a klikněte na tlačítko **Další**.

   ![Vytvoření nového projektu v aplikaci Visual Studio](media/vs-2019/create-new-project.png)

1. V okně **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** a volitelně změňte umístění adresáře pro soubory projektu a pak zvolte **vytvořit**.

   ![Konfigurace nového projektu v aplikaci Visual Studio](media/vs-2019/configure-new-project.png)

   Visual Studio vytvoří projekt. Jedná se o jednoduchou aplikaci "Hello World", která volá <xref:System.Console.WriteLine?displayProperty=nameWithType> metodu pro zobrazení řetězcového literálu "Hello World!" v okně konzoly (programový výstup).

   Za chvíli by se měla zobrazit následující text:

   ![Visual Studio – sada IDE](media/overview-ide-console-app.png)

   Kód Visual Basic pro aplikaci se zobrazí v okně editoru, které zabírá většinu místa. Všimněte si, že text je automaticky barevně barevný, aby označoval různé části kódu, jako jsou klíčová slova a typy. Kromě toho malé, svislé přerušované čáry v kódu označují, které závorky se shodují s sebou, a čísla řádků vám pomůžou později vyhledat kód. Můžete zvolit malý, zabalené znaménko minus pro sbalení nebo rozbalení bloků kódu. Tato funkce osnovy kódu vám umožní skrýt kód, který nepotřebujete, a pomoct tak minimalizovat přehlednost na obrazovce. Soubory projektu jsou uvedeny na pravé straně okna s názvem **Průzkumník řešení**.

   ![Integrované vývojové prostředí sady Visual Studio s červenými poli](media/overview-ide-console-app-red-boxes.png)

   K dispozici jsou další nabídky a okna nástrojů, ale teď se k ní přiblížíme.

1. Teď aplikaci spusťte. To lze provést výběrem možnosti **Spustit bez ladění** v nabídce **ladění** na řádku nabídek. Můžete také stisknout **kombinaci kláves CTRL** + **F5**.

   ![Ladit > spustit bez nabídky ladění](media/vs-2019/start-without-debugging.png)

   Visual Studio sestaví aplikaci a otevře se okno konzoly se zprávou **Hello World!**. Teď máte spuštěnou aplikaci.

   ![Snímek obrazovky okna konzoly znázorňující Hello Worldovou zprávu](../media/vs-2019/overview-console-window.png)

1. Okno konzoly zavřete stisknutím libovolné klávesy na klávesnici.

1. Pojďme do aplikace přidat nějaký další kód. Přidejte následující kód Visual Basic před řádek, který říká `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Tento kód zobrazuje, **Jaké je vaše jméno?** v okně konzoly a pak počká, dokud uživatel nezadá text následovaný klávesou **ENTER** .

1. Změňte řádek, který říká `Console.WriteLine("Hello World!")` následujícímu kódu:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Spusťte aplikaci znovu stisknutím **klávesy CTRL** + **F5**.

   Visual Studio aplikaci znovu sestaví a otevře se okno konzoly s výzvou k zadání vašeho jména.

1. Do okna konzoly zadejte své jméno a stiskněte klávesu **ENTER**.

   ![Snímek obrazovky okna konzoly s informacemi o tom, jaká je vaše otázka na jméno a odpověď aplikace](../media/vs-2019/overview-console-input.png)

1. Stisknutím libovolné klávesy zavřete okno konzoly a zastavte spuštěný program.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Použití refaktoringu a IntelliSense

Pojďme se podívat na několik způsobů, jak [refaktoring](../../ide/refactoring-in-visual-studio.md) , tak aby vám [IntelliSense](../../ide/using-intellisense.md) mohl efektivněji pomáhat s kódem.

Nejdřív přejmenujte `name` proměnnou:

1. Dvakrát klikněte na `name` proměnnou a vyberte ji.

2. Zadejte nový název proměnné, **uživatelské jméno**.

   Všimněte si, že kolem proměnné se zobrazí šedé pole a v okraji se zobrazí žárovka.

3. Výběrem ikony žárovky zobrazíte dostupné [rychlé akce](../../ide/quick-actions.md). Vyberte **přejmenovat název na uživatelské jméno**.

   ![Akce přejmenování v aplikaci Visual Studio](media/rename-quick-action.png)

   Proměnná je přejmenována v rámci projektu, což je v našem případě pouze dvou míst.

4. Teď se podívejme na technologii IntelliSense. Pod řádkem, který říká `Console.WriteLine("Hello " + username + "!")` , zadejte následující fragment kódu:

    ```vb
   Dim now = Date.
   ```

   Pole zobrazuje členy <xref:System.DateTime> třídy. Kromě toho popis aktuálně vybraného člena se zobrazí v samostatném poli.

   ![Členové seznamu IntelliSense v aplikaci Visual Studio](media/intellisense-list-members.png)

5. Vyberte člen s názvem **nyní**, který je vlastností třídy, dvojím kliknutím na něj nebo jeho výběrem pomocí šipek nahoru nebo dolů a stisknutím klávesy **TAB**.

6. Níže zadejte nebo vložte následující řádky kódu:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> se trochu liší <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> od v tom, že po vytištění nepřidá ukončovací znak řádku. To znamená, že další část textu, která je odeslána do výstupu, bude vytištěna na stejném řádku. Svůj popis můžete zobrazit tak, že najedete myší na každou z těchto metod v kódu.

7. Dále znovu použijeme refaktoring, aby byl kód trochu výstižnější. Klikněte na proměnnou na `now` řádku `Dim now = Date.Now` .

   Všimněte si, že na okraji na daném řádku se zobrazí trochu Screwdriver ikona.

8. Klikněte na ikonu Screwdriver a zjistěte, jaké návrhy nabízí Visual Studio. V tomto případě se zobrazuje [vložená dočasná](../../ide/reference/inline-temporary-variable.md) refaktoring proměnné pro odebrání řádku kódu beze změny celkového chování kódu:

   ![Refaktoring dočasné proměnné Refaktoring v aplikaci Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Klikněte na **vloženou dočasnou proměnnou** a refaktorujte kód.

::: moniker range="vs-2017"

10. Spusťte program znovu stisknutím **klávesy CTRL** + **F5**. Výstup bude vypadat nějak takto:

    ![Okno konzoly s výstupem programu](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Spusťte program znovu stisknutím **klávesy CTRL** + **F5**. Výstup bude vypadat nějak takto:

    ![Okno konzoly s výstupem programu](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Ladění kódu

Při psaní kódu ho musíte spustit a otestovat pro chyby. Ladicí systém sady Visual Studio umožňuje Krokovat s kódem v jednom okamžiku a při procházení proměnných kontrolovat proměnné. Můžete nastavit *zarážky* , které zastaví provádění kódu na určitém řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a dalších.

Pojďme nastavit zarážku, aby se zobrazila hodnota `username` proměnné, zatímco program je "v letu".

1. Vyhledejte řádek kódu, který říká `Console.WriteLine("Hello " + username + "!")` . Chcete-li nastavit zarážku na tomto řádku kódu, to znamená, aby program pozastavil provádění na tomto řádku, klikněte na levý levý okraj editoru. Můžete také kliknout kamkoli na řádek kódu a stisknout **F9**.

   V levém horním rohu se zobrazí červený kroužek a kód se zvýrazní červeně.

   ![Zarážka na řádku kódu v aplikaci Visual Studio](media/breakpoint.png)

1. Spusťte ladění tak, **že vyberete ladění**  >  **Spustit ladění** nebo stisknete klávesu **F5**.

1. Jakmile se zobrazí okno konzoly a požádá o vaše jméno, zadejte ho do pole a stiskněte klávesu **ENTER**.

   Fokus se vrátí do editoru kódu sady Visual Studio a řádek kódu se zarážkou se zvýrazní žlutě. To znamená, že se jedná o další řádek kódu, který bude program spouštět.

1. Pokud `username` chcete zobrazit jeho hodnotu, najeďte myší na proměnnou. Případně můžete kliknout pravým tlačítkem myši na `username` a vybrat možnost **Přidat kukátko** a přidat proměnnou do okna **kukátka** , kde můžete také zobrazit její hodnotu.

   ![Hodnota proměnné během ladění v aplikaci Visual Studio](media/debugging-variable-value.png)

1. Pokud chcete nechat program běžet na dokončení, stiskněte znovu klávesu **F5** .

Další informace o ladění v aplikaci Visual Studio naleznete v tématu [prohlídka funkcí ladicího programu](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Další kroky

Prozkoumejte Visual Studio dále pomocí jednoho z následujících úvodních článků:

> [!div class="nextstepaction"]
> [Naučte se používat editor kódu.](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Další informace o projektech a řešeních](tutorial-projects-solutions.md)

## <a name="see-also"></a>Viz také

- Objevte [Další funkce sady Visual Studio](../../ide/advanced-feature-overview.md)
- Navštívit [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/)
- Přečtěte si [blog sady Visual Studio](https://devblogs.microsoft.com/visualstudio/) .
