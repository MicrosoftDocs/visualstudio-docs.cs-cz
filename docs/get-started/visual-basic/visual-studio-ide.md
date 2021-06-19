---
title: Přehled pro Visual Basic vývojáře
description: Přečtěte si o Visual Studio k úpravám, ladění a sestavování kódu pomocí nástroje a pak publikujte aplikaci jako Visual Basic vývojáře.
ms.date: 03/02/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 486201d61f6bd2d149c9aea66efee1814ce667e7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386628"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Vítá vás integrované vývojové Visual Studio (IDE) | Visual Basic

Integrované Visual Studio *prostředí je* kreativní spouštěcí panel, který můžete použít k úpravám, ladění a sestavování kódu a k publikování aplikace. Integrované vývojové prostředí (IDE) je program s bohatými funkcemi, který lze použít pro mnoho aspektů vývoje softwaru. Kromě standardního editoru a ladicího programu, který poskytuje většina prostředí ID, Visual Studio zahrnuje kompilátory, nástroje pro dokončování kódu, grafické návrháře a mnoho dalších funkcí pro usnadnění procesu vývoje softwaru.

::: moniker range="vs-2017"

![Integrované vývojové Visual Studio (IDE)](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![Integrované vývojové Visual Studio 2019](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Tento obrázek ukazuje Visual Studio s otevřeným projektem a několika klíčovými okny nástrojů, které budete pravděpodobně používat:

- [Průzkumník řešení](../../ide/solutions-and-projects-in-visual-studio.md) (vpravo nahoře) umožňuje zobrazit, procházet a spravovat soubory kódu. **Průzkumník řešení** vám může pomoct s uspořádáním kódu seskupením souborů do [řešení a projektů](tutorial-projects-solutions.md).

- V [okně editoru](../../ide/writing-code-in-the-code-and-text-editor.md) (uprostřed), kde pravděpodobně strávíte většinu času, se zobrazí obsah souboru. Tady můžete upravovat kód nebo navrhovat uživatelské rozhraní, například okno s tlačítky a textová pole.

- V [okně Výstup](../../ide/reference/output-window.md) (dole uprostřed) se Visual Studio oznámení, jako jsou ladění a chybové zprávy, upozornění kompilátoru, stavové zprávy publikování a další. Každý zdroj zpráv má svou vlastní kartu.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (v pravém dolním rohu) umožňuje sledovat pracovní položky a sdílet kód s ostatními pomocí technologií pro řízení verzí, jako je [Git](https://git-scm.com/) [a Správa verzí Team Foundation (TFVC).](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)

## <a name="editions"></a>Edice

Visual Studio je k dispozici pro Windows a Mac. [Visual Studio pro Mac](/visualstudio/mac/) má mnoho stejných funkcí jako Visual Studio 2017 a je optimalizovaný pro vývoj aplikací pro více platforem a mobilních aplikací. Tento článek se zaměřuje na verzi Windows Visual Studio 2017.

Existují tři edice Visual Studio 2017: Community, Professional a Enterprise. Informace o tom, které funkce jsou podporované v jednotlivých edicích, najdete v tématu Porovnání prostředí [VISUAL STUDIO 2017.](https://visualstudio.microsoft.com/vs/compare/)

## <a name="popular-productivity-features"></a>Oblíbené funkce produktivity

Mezi oblíbené funkce v Visual Studio, které vám pomůžou být produktivnější při vývoji softwaru, patří:

- Squiggles and [Quick Actions](../../ide/quick-actions.md)

   Podtržení vlnovkou vás při psaní upozorní na chyby nebo potenciální problémy v kódu. Tato vizuální vodítka umožňují okamžitě opravit problémy, aniž byste čekali, až se chyba objeví během sestavování nebo při spuštění programu. Pokud najedete myší na podmyšlku, zobrazí se další informace o chybě. Na levém okraji se může objevit žárovka s akcemi, které se označuje jako Rychlé akce, které chybu opraví.

   ::: moniker range="vs-2017"

   ![Stříkáte v Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Stříkáte v Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refactoring](../../ide/refactoring-in-visual-studio.md)

   Refaktoring zahrnuje operace, jako je inteligentní přejmenování proměnných, extrahování jednoho nebo více řádků kódu do nové metody, změna pořadí parametrů metody a další.

   ::: moniker range="vs-2017"

   ![Nabídka refaktoringu v Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Nabídka refaktoringu v Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [Intellisense](../../ide/using-intellisense.md)

   IntelliSense je termín pro sadu funkcí, které zobrazují informace o kódu přímo v editoru a v některých případech za vás píšou malé části kódu. Je to jako mít základní dokumentaci přímo v editoru, což vám ušetří, abyste museli hledat informace o typech jinde. Funkce IntelliSense se liší podle jazyka. Další informace najdete v tématu [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense,](../../ide/visual-cpp-intellisense.md) [JavaScript IntelliSense](../../ide/javascript-intellisense.md)a [Visual Basic IntelliSense.](../../ide/visual-basic-specific-intellisense.md) Následující obrázek znázorňuje, jak IntelliSense zobrazuje seznam členů pro typ:

   ::: moniker range="vs-2017"

   ![Visual Studio seznamu členů](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio seznamu členů](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Vyhledávací pole

   Visual Studio se může občas zdát zahlcující s tolika nabídkami, možnostmi a vlastnostmi. Vyhledávací pole je skvělým způsobem, jak rychle najít to, co potřebujete v Visual Studio. Když začnete psát název něčeho, co hledáte, zobrazí Visual Studio výsledky, které vás převezou přesně tam, kde potřebujete. Pokud potřebujete do Visual Studio přidat funkce, například pro přidání podpory dalšího programovacího jazyka, vyhledávací pole poskytuje výsledky, které otevřou Instalační program pro Visual Studio pro instalaci úlohy nebo jednotlivé komponenty.

   > [!TIP]
   > Stiskněte **Ctrl** + **Q** jako zástupce vyhledávacího pole.

   ::: moniker range="vs-2017"

   ![Snadné spuštění vyhledávacího pole ve Visual Studio 2017](../media/quick-launch-nuget.png)

   Další informace najdete v tématu [Snadné spuštění](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Vyhledávací pole v Visual Studio 2019](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Upravovat a ladit v reálném čase společně s ostatními bez ohledu na to, jaký typ aplikace nebo programovací jazyk máte. Svůj projekt můžete okamžitě a bezpečně sdílet a podle potřeby také ladicí relace, instance terminálů, webové aplikace místního hostitele, hlasové hovory a další.

- [Hierarchie volání](../../ide/reference/call-hierarchy.md)

   V **okně Hierarchie** volání se zobrazují metody, které volají vybranou metodu. To může být užitečné, když uvažujete o změně nebo odebrání metody nebo když se snažíte najít chybu.

   ::: moniker range="vs-2017"

   ![Okno Hierarchie volání v Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Okno Hierarchie volání v Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vám pomůže najít odkazy na kód, změny kódu, propojené chyby, pracovní položky, recenze kódu a testy jednotek, a to vše bez opuštění editoru.

   ::: moniker range="vs-2017"

   ![CodeLens v Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens v Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Přejít k definici](../../ide/go-to-and-peek-definition.md)

   Funkce Přejít k definici vás přesouvá přímo do umístění, kde je definována funkce nebo typ.

   ::: moniker range="vs-2017"

   ![Přejít na definici v Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Přejít na definici v Visual Studio 2019](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Náhled definice](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Okno **Náhled definice** zobrazuje definici metody nebo typu, aniž by se ve skutečnosti otevřel samostatný soubor.

   ::: moniker range="vs-2017"

   ![Náhled definice v Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Náhled definice v Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Instalace integrovaného vývojového Visual Studio

V této části vytvoříte jednoduchý projekt, který vám umožní vyzkoušet si některé z věcí, které můžete s Visual Studio. Změníte barevný motiv, použijete [IntelliSense](../../ide/using-intellisense.md) jako pomůcku kódování a vyladíte aplikaci, abyste viděli hodnotu proměnné během provádění programu.

::: moniker range="vs-2017"

Pokud chcete začít, [stáhněte Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ho do svého systému. Modulární instalační program umožňuje vybrat a nainstalovat úlohy *,* což jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle [kroků pro vytvoření programu,](#create-a-program)nezapomeňte během instalace vybrat úlohu vývoj pro různé platformy v **.NET Core.**

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete začít, [stáhněte Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ho do svého systému. Modulární instalační program umožňuje vybrat a nainstalovat úlohy *,* což jsou skupiny funkcí potřebné pro programovací jazyk nebo platformu, které dáváte přednost. Pokud chcete postupovat podle [kroků pro vytvoření programu,](#create-a-program)nezapomeňte během instalace vybrat úlohu vývoj pro různé platformy v **.NET Core.**

::: moniker-end

![Úloha vývoje .NET Core pro různé platformy v Instalační program pro Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Když aplikaci Visual Studio poprvé, můžete se volitelně [](../../ide/signing-in-to-visual-studio.md) přihlásit pomocí svého pracovního účet Microsoft nebo školního účtu.

## <a name="customize-visual-studio"></a>Přizpůsobení Visual Studio

Uživatelské rozhraní můžete přizpůsobit Visual Studio, včetně změny výchozího barevného motivu.

### <a name="change-the-color-theme"></a>Změna barevného motivu

Změna na tmavý **motiv:**

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. V úvodním okně vyberte **Pokračovat bez kódu**.


    :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Snímek obrazovky s oknem Start Visual Studio 2019 se zvýrazněnou odkazem Pokračovat bez kódu":::

   Otevře se integrované vývojové prostředí (IDE).

::: moniker-end

2. Na řádku nabídek **zvolte** Nástroje  >  **Možnosti.** Otevře se **dialogové okno** Možnosti.

3. Na stránce **Obecné**  >  **možnosti** prostředí změňte výběr Motiv **barvy** na **Tmavý a** potom klikněte na **OK**.

   ![Změna barevného motivu na tmavý v Visual Studio](media/change-color-theme.png)

   Barevný motiv celého integrovaného vývojového prostředí (IDE) se změní na **Dark (Tmavý).**

   ::: moniker range="vs-2017"

   ![Visual Studio v tmavém motivu](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio v tmavém motivu](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Výběr nastavení prostředí

Dále nakonfigurujeme, Visual Studio používat nastavení prostředí přizpůsobená pro Visual Basic vývojáře.

1. Na řádku nabídek klikněte na **nástroje**  >  **importovat a exportovat nastavení**.

2. V **Průvodci importem a exportem nastavení** vyberte **Obnovit všechna nastavení** na první stránce a pak klikněte na **Další**.

3. Na stránce **Uložit aktuální nastavení** vyberte možnost Uložit aktuální nastavení, nebo ne, a poté klikněte na tlačítko **Další**. (Pokud jste nepřizpůsobili žádné nastavení, vyberte možnost **Ne, pouze resetovat nastavení a přepsat aktuální nastavení**.)

4. Na stránce **Výběr výchozí kolekce nastavení** zvolte **Visual Basic** a pak klikněte na **Dokončit**.

5. Na stránce **obnovení byla dokončena** klikněte na tlačítko **Zavřít**.

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

1. Na panelu nabídek aplikace Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**. (Případně stiskněte klávesu **CTRL** + **Posun** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Snímek obrazovky souboru > nový > výběr projektu z řádku nabídek sady Visual Studio 2019.":::

   Otevře se okno **vytvořit nový projekt** a zobrazí se několik *šablon* projektů. Šablona obsahuje základní soubory a nastavení, které jsou požadovány pro daný typ projektu.

1. Pokud chcete najít požadovanou šablonu, zadejte nebo zadejte do vyhledávacího pole **konzolu .NET Core** . Seznam šablon, které jsou k dispozici, se automaticky filtruje na základě klíčových slov, která jste zadali. Výsledky šablony můžete dál filtrovat volbou **Visual Basic** v rozevíracím seznamu **všechny jazyky** , **Windows** ze seznamu **všechny platformy** a z **konzoly** ze seznamu **všechny typy projektů** .

   Vyberte šablonu **Konzolová aplikace** a klikněte na tlačítko **Další**.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Snímek obrazovky okna vytvořit nový projekt v aplikaci Visual Studio 2019, kde můžete vybrat požadovanou šablonu.":::

1. V okně **Konfigurovat nový projekt** zadejte do pole **název projektu** **HelloWorld** a volitelně změňte umístění adresáře pro soubory projektu (výchozí národní prostředí je `C:\Users\<name>\source\repos` ) a pak klikněte na **Další**.

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Snímek obrazovky okna Konfigurovat nový projekt v aplikaci Visual Studio 2019, kde zadáte název projektu":::

1. V okně **Další informace** ověřte, že se v rozevírací nabídce **cílové** rozhraní zobrazí **.NET Core 3,1** a pak klikněte na **vytvořit**.

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Snímek obrazovky okna Další informace v aplikaci Visual Studio 2019, kde můžete vybrat požadovanou verzi rozhraní .NET Core.":::

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

4. Teď se podívejme na technologii IntelliSense. Pod řádkem, který říká `Console.WriteLine("Hello &quot; + username + &quot;!")` , zadejte následující fragment kódu:

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

## <a name="debug-code&quot;></a>Ladění kódu

Při psaní kódu ho musíte spustit a otestovat pro chyby. Ladicí systém sady Visual Studio umožňuje Krokovat s kódem v jednom okamžiku a při procházení proměnných kontrolovat proměnné. Můžete nastavit *zarážky* , které zastaví provádění kódu na určitém řádku. Můžete sledovat, jak se hodnota proměnné mění při spuštění kódu a dalších.

Pojďme nastavit zarážku, aby se zobrazila hodnota `username` proměnné, zatímco program je &quot;v letu&quot;.

1. Vyhledejte řádek kódu, který říká `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")` . Chcete-li nastavit zarážku na tomto řádku kódu, to znamená, aby program pozastavil provádění na tomto řádku, klikněte na levý levý okraj editoru. Můžete také kliknout kamkoli na řádek kódu a stisknout **F9**.

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
