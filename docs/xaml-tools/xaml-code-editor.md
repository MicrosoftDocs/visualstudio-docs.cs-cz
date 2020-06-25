---
title: Editor kódu XAML
ms.date: 06/16/2020
ms.topic: conceptual
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d789ac099e6d0bba7a44f0d6efd7a19beec54c19
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290445"
---
# <a name="xaml-code-editor"></a>Editor kódu XAML

Editor kódu XAML v [integrovaném vývojovém prostředí sady Visual Studio](../get-started/visual-studio-ide.md) obsahuje všechny nástroje, které potřebujete k vytváření aplikací WPF a UWP pro platformu Windows a pro [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). Tento článek popisuje jak roli, tak jak editor kódu hraje při vývoji aplikací založených na jazyce XAML a funkcí, které jsou jedinečné pro Editor kódu XAML v aplikaci Visual Studio 2019.

Začněte tím, že se podíváme na integrované vývojové prostředí (IDE) s otevřeným projektem WPF. Následující obrázek ukazuje několik klíčových nástrojů IDE, které použijete spolu s editorem kódu XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="Integrované vývojové prostředí (IDE) sady Visual Studio 2019 s otevřeným projektem WPF v jazyce XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

V levém dolním rohu image se budou používat klíčové nástroje IDE:

- Okno **[editoru kódu XAML](#xaml-code-editor-ui)** &mdash; předmět tohoto článku, &mdash; kde můžete vytvořit a upravit kód.
- Okno **[Návrhář XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** , kde NAVRHNETE uživatelské rozhraní.
- Okno ukotvit **[panelu nástrojů](../ide/reference/toolbox.md)** , kde můžete přidat ovládací prvky do uživatelského rozhraní.
- Tlačítko **[ladit](../debugger/debugger-feature-tour.md)** , kde spustíte kód a budete ho ladit. <br>(Můžete také upravit kód v reálném čase při ladění pomocí programu [XAML Hot reloading](xaml-hot-reload.md).)
- Okno **[Průzkumník řešení](../ide/solutions-and-projects-in-visual-studio.md)** , kde můžete spravovat soubory, projekty a řešení.
- Okno **[vlastnosti](../ide/reference/properties-window.md)** , ve kterém změníte vzhled uživatelského rozhraní a jak fungují ovládací prvky uživatelského rozhraní.

Chcete-li pokračovat, Podívejme se na Další informace o editoru kódu XAML.

## <a name="xaml-code-editor-ui"></a>Uživatelské rozhraní editoru kódu XAML

Zatímco okno Editor kódu pro aplikace XAML sdílí některé prvky uživatelského rozhraní (uživatelské rozhraní), které se také zobrazí na našem standardním integrovaném vývojovém prostředí (IDE), obsahuje také několik jedinečných funkcí, které usnadňují vývoj aplikací XAML.

Tady je pohled na samotné okno editoru kódu XAML.

![Okno editoru kódu XAML v aplikaci Visual Studio](media/xaml-code-editor-window.png "Snímek obrazovky s oknem editoru kódu XAML v aplikaci Visual Studio 2019")

Potom se podíváme na funkce každého prvku uživatelského rozhraní v editoru kódu.

### <a name="first-row"></a>První řádek

V prvním řádku v horní části okna kódu XAML je na levé straně karta **Návrh** , tlačítko **odkládací podokna** , karta **XAML** a **místní tlačítko XAML** .

![První ze dvou horních řádků okna editoru kódu v jazyce XAML v aplikaci Visual Studio s levou stranou prvního řádku, který je zvýrazněný](media/xaml-code-editor-top-row-left.png "Snímek obrazovky prvního ze dvou horních řádků okna editoru kódu v jazyce XAML v aplikaci Visual Studio 2019, ve kterém jsou prvky uživatelského rozhraní vlevo zvýrazněny")

Jak fungují:

- Karta **Návrh** změní fokus z editoru kódu XAML na Návrhář XAML.
- Tlačítko **odkládacích panelů** obrátí umístění Návrhář XAML a editoru kódu XAML v integrovaném vývojovém prostředí (IDE).
- Karta **XAML** změní fokus zpátky na Editor kódu XAML.
- Tlačítko pro **místní XAML** vytvoří samostatné okno editoru kódu XAML, které je mimo rozhraní IDE.

Při dalším stisknutí pravého tlačítka se zobrazí **svislé tlačítko rozdělení** , tlačítko **horizontálního rozdělení** a tlačítko **sbalit podokna** .

![První ze dvou horních řádků okna editoru kódu v jazyce XAML v aplikaci Visual Studio s pravou stranou prvního řádku, který je zvýrazněn](media/xaml-code-editor-top-row-right.png "Snímek obrazovky prvního ze dvou horních řádků okna editoru kódu v jazyce XAML v aplikaci Visual Studio 2019, ve kterém jsou prvky uživatelského rozhraní na pravé straně zvýrazněny")

Jak fungují:

- Tlačítko **Svislé rozdělení** změní umístění Návrhář XAML a editoru kódu XAML v integrovaném vývojovém prostředí z vodorovného zarovnání na svislé zarovnání.
- Tlačítko **horizontálního rozdělení** změní umístění Návrhář XAML a editoru kódu XAML v rozhraní IDE ze svislého zarovnání na vodorovné zarovnání.
- Tlačítko **sbalit podokno** umožňuje sbalit, co je v dolním podokně, bez ohledu na to, jestli je to Editor kódu nebo Návrhář. (Chcete-li obnovit dolní podokno, znovu vyberte stejné tlačítko, které se nyní nazývá tlačítko **Rozbalit podokno** .)

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Druhý řádek

Ve druhém řádku v horní části okna kódu XAML existují dva rozevírací seznamy okna. Nicméně pokud zobrazíte popisy pro tyto prvky uživatelského rozhraní, budou dále identifikovány jako "element: Window" a "member: Window".

![Druhý ze dvou horních řádků okna editoru kódu XAML v aplikaci Visual Studio, kde jsou zobrazeny rozevírací seznamy obou oken](media/xaml-code-editor-top-row-windows.png "Snímek obrazovky druhé ze dvou horních řádků okna editoru kódu v jazyce XAML v aplikaci Visual Studio 2019, ve kterém jsou zobrazeny obě rozevírací seznamy okna")

Rozevírací seznamy okna mají různé funkce, a to následujícím způsobem:

- **Element: okno** na levé straně vám pomůže zobrazit a přejít na stejné nebo nadřazené prvky.

  Konkrétně ukazuje zobrazení typu osnova, které odhalí strukturu značek kódu. Když vyberete ze seznamu, fokus v editoru kódu se bude přitahovat na řádek kódu, který obsahuje vybraný prvek.

    ![Element: rozevírací seznam okna v aplikaci Visual Studio](media/xaml-element-window-dropdown.png "Snímek obrazovky elementu: rozevírací seznam okna v aplikaci Visual Studio 2019")

- **Člen: okno** na pravé straně vám pomůže zobrazit atributy nebo podřízené prvky a přejít na ně.

    Konkrétně zobrazuje seznam vlastností v kódu. Když vyberete ze seznamu, fokus v editoru kódu se přichytí k řádku kódu, který obsahuje vlastnost, kterou jste vybrali.

    ![Rozevírací seznam člen: okno v aplikaci Visual Studio](media/xaml-member-window-dropdown.png "Snímek obrazovky s rozevíracím seznamem člena: okno v aplikaci Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Prostřední podokno, Editor kódu

Prostřední podokno je část Code (kód) editoru kódu XAML. Obsahuje většinu funkcí, které najdete v [editoru kódu IDE](../get-started/tutorial-editor.md). Podíváme se na některé z univerzálních funkcí IDE, které vám pomůžou s vývojem kódu XAML. Také zvýrazníme funkce jedinečného na XAML v integrovaném vývojovém prostředí (IDE).

![Editor kódu XAML, pouze prostřední podokno, v aplikaci Visual Studio](media/xaml-code-editor-middle.png "Snímek obrazovky editoru kódu XAML, pouze prostřední podokno, v aplikaci Visual Studio 2019")

#### <a name="quick-actions"></a>Rychlé akce

[Rychlé akce](../ide/quick-actions.md) můžete použít k refaktorování, generování nebo jiným úpravám kódu jedinou akcí.

Například jedna užitečná úloha, kterou můžete provést pomocí rychlých akcí, je **odebrat nepotřebné použití** z kódu jazyka C# na kartě **MainWindow.XAML.cs** .

Zde je uveden postup:

1. Najeďte myší na příkaz using, zvolte ikonu žárovky a v rozevíracím seznamu zvolte **odebrat nepotřebné** direktivy using.

    ![Editor IDE s možností "odebrat nepotřebné použití" z nabídky rychlé akce](media/xaml-code-editor-remove-usings.png "Snímek obrazovky s možností odebrat nepotřebné použití v editoru IDE z nabídky rychlé akce")

1. Vyberte, zda chcete opravit všechny výskyty v **dokumentu**, **projektu**nebo **řešení**.
1. Zobrazte dialogové okno **Náhled** a pak zvolte **použít**.

K této funkci můžete získat přístup také z panelu nabídek. Pokud to chcete udělat, vyberte **Upravit**  >  **IntelliSense**  >  **Odebrat a seřadit pomocí**.

Další informace o použití nastavení naleznete na stránce [řazení pomocí](../ide/reference/sort-usings.md) . Další informace o technologii IntelliSense naleznete na stránce [IntelliSense v aplikaci Visual Studio](../ide/using-intellisense.md) . Další informace o některých typických způsobech, jak vývojáři používají rychlé akce, najdete na stránce [běžné rychlé akce](../ide/common-quick-actions.md) .

#### <a name="change-tracking"></a>Sledování změn

Barva levého okraje umožňuje sledovat změny, které jste provedli v souboru. Tady je postup, jak se barvy vztahují k akcím, které provádíte:

- Změny, které jste provedli od otevření souboru, ale nebyly uloženy, jsou označeny **žlutým** pruhem na levém okraji (známé jako okraj výběru).

    ![Editor kódu – upravit se žlutým pruhem](media/code-editor-edit-yellow.png "Snímek obrazovky editoru kódu se změnou označenou žlutým pruhem na okraji výběru")

- Po uložení změn (ale před zavřením souboru) se pruh změní na **zelený**.

    ![Editor kódu – upravit se zelenou čárou](media/code-editor-edit-green.png "Snímek obrazovky editoru kódu se změnou označenou zeleným pruhem na okraji výběru")

Chcete-li tuto funkci vypnout a zapnout, změňte možnost **sledovat změny** v nastavení **textový editor** (Editor**Tools**  >  **možností**nástroje  >  **textový editor**).

Další informace o sledování změn &mdash; pro zahrnutí vlnovek (označované také jako "vlnovky"), které se zobrazují v části řetězce kódu, &mdash; naleznete v části **[editory funkcí](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** v tématu [funkce editoru kódu sady Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md) .

#### <a name="right-click-context-menu"></a>Místní nabídka kliknutím pravým tlačítkem myši

Při úpravách kódu v editoru kódu XAML je k dispozici několik funkcí, ke kterým lze přistupovat pomocí místní nabídky kliknutím pravým tlačítkem myši. Většina těchto funkcí je všeobecně dostupná v integrovaném vývojovém prostředí sady Visual Studio, zatímco některé jsou specifické pro použití editoru kódu společně s oknem návrhu.

![Místní nabídka editoru kódu XAML v aplikaci Visual Studio, která je pravým tlačítkem myši](media/xaml-code-editor-right-click-menu.png "Snímek obrazovky s kontextovou nabídkou editoru kódu XAML v aplikaci Visual Studio 2019 kliknutím pravým tlačítkem myši")

V tomto článku jsou jednotlivé funkce a jejich užitečnost:

- **Zobrazit kód** – otevře okno kód programovacího jazyka, který je obvykle umístěn vedle výchozího zobrazení, které obsahuje okno návrh a Editor kódu XAML.
- **Návrhář zobrazení** – otevře výchozí zobrazení, které obsahuje okno návrh a Editor kódu XAML. (Pokud jste již ve výchozím zobrazení, neprovede akci.)
- **Rychlé akce a refaktoring – refaktoring** , vygeneruje nebo jinak upraví kód jedinou akcí. Když najedete myší na kód, zobrazí se ikona žárovky, když je k dispozici rychlá akce nebo refaktoring. <br>Viz také: [rychlé akce](../ide/quick-actions.md) a [refaktoring kódu](../ide/refactoring-in-visual-studio.md).
- **Přejmenovat...** -Přejmenuje pouze obory názvů. Pokud nemáte obor názvů pro přejmenování, obdržíte chybovou zprávu s oznámením, že se dají přejmenovat jenom předpony oboru názvů.
- **Odebrání a řazení oborů názvů** – odebere nepoužívané obory názvů a potom seřadí tyto obory názvů, které zůstanou.
- **Náhled definice** – zobrazí definici typu bez nutnosti opustit aktuální polohu v editoru. <br>Viz také: [Náhled definice](../ide/go-to-and-peek-definition.md#peek-definition) a [zobrazení a úprava kódu pomocí náhledu definice](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Přejít k definici** – přejde ke zdroji typu nebo členu a otevře výsledek na nové kartě. <br>Viz také: [Přejít k definici](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Uzavřít do...** – Použijte obklopit s fragmenty kódu, které jsou přidány kolem vybraného bloku kódu. <br>Viz také: [fragmenty rozšíření a obklopení pomocí fragmentů kódu](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Vložit fragment** – vloží fragment kódu do umístění kurzoru.
- **Vyjmout** – s vysvětlením
- **Kopie** – bez jakýchkoli vysvětlení
- **Vložení** – s vysvětlením
- **Osnova** – rozbalí a sbalí oddíly kódu. <br>Viz také: [sbalení](../ide/outlining.md).
- **Správa zdrojového** kódu – zobrazení historie příspěvků kódu do Open Source úložiště

### <a name="middle-pane-scroll-bar"></a>Prostřední panel, posuvník

Posuvník může probírat více než procházet kód. Můžete ji také použít k otevření jiného podokna editoru kódu. A můžete použít posuvník, který vám umožní zvýšit efektivitu kódu přidáním poznámek nebo pomocí různých režimů zobrazení.

#### <a name="split-the-code-window"></a>Rozdělit okno kódu

Na posuvníku v editoru kódu existuje tlačítko **rozdělení** v pravém horním rohu. Když si ho vyberete, můžete otevřít jiný podokno editoru kódu. To je užitečné, protože pracují nezávisle na sobě, takže je můžete použít pro práci s kódem v různých umístěních.

![Editor kódu XAML, pouze prostřední podokno, v aplikaci Visual Studio](media/code-editor-split-window-button.png "Snímek obrazovky editoru kódu XAML, pouze prostřední podokno, v aplikaci Visual Studio 2019")

Další informace o tom, jak rozdělit okno editoru, naleznete na stránce [Správa oken editoru](../ide/how-to-manage-editor-windows.md) .

#### <a name="use-annotations-or-map-mode"></a>Použití poznámek nebo režimu mapování

Můžete také změnit způsob, jakým posuvník vypadá a jaké další funkce obsahuje. Mnoho lidí například chce do posuvníku zahrnout *poznámky* , které poskytují vizuální pomůcky, jako jsou například změny kódu, zarážky, záložky, chyby a pozice blikajícího kurzoru.

Ostatní oceňují pomocí *režimu mapy*, který v posuvníku zobrazuje řádky kódu v miniaturním pruhu. Vývojáři, kteří mají velký kód v souboru, mohou najít, že se tento režim mapy bude sledovat na řádky kódu efektivněji, než je výchozí posuvník.

Další informace o tom, jak změnit výchozí nastavení posuvníku, najdete v tématu přizpůsobení stránky [s posuvníkem](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) .

## <a name="xaml-specific-features"></a>Funkce specifické pro XAML

Většina následujících funkcí je v integrovaném vývojovém prostředí sady Visual Studio všeobecně dostupná, ale k některým z nich přidávají dimenze, které usnadňují kódování pro vývojáře v jazyce XAML.

### <a name="xaml-code-snippets"></a>Fragmenty kódu XAML

Fragmenty kódu jsou malé bloky opakovaně použitelného kódu, který lze vložit do v souboru kódu pomocí příkazu místní nabídky klikněte pravým tlačítkem myši **Vložit fragment** nebo kombinaci klávesových zkratek (**CTRL** + **K**, **CTRL** + **X**). Vylepšili jsme [technologii IntelliSense](../ide/using-intellisense.md) tak, aby podporovala zobrazování fragmentů XAML, které fungují jak pro předdefinované fragmenty kódu, tak i pro všechny vlastní fragmenty kódu, které přidáte ručně. Některé předem připravené fragmenty kódu XAML zahrnují `#region` , `Column definition` ,, `Row definition` `Setter` a `Tag` .

![Editor kódu XAML s možnostmi #region zobrazenými v IntelliSense](media/xaml-code-snippets.png "Snímek obrazovky editoru kódu XAML s možnostmi #region zobrazenými v IntelliSense")

Další informace naleznete na stránkách [fragmenty kódu](../ide/code-snippets.md) a [fragmenty kódu jazyka C#](../ide/visual-csharp-code-snippets.md) .

### <a name="xaml-region-support"></a>Podpora #region XAML

Od sady Visual Studio 2015 jsme provedli #region podporu pro vývojáře v jazyce XAML v prostředí WPF a UWP a v poslední době i v [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). V aplikaci Visual Studio 2019 budeme nadále provádět přírůstková vylepšení #region podporu. Například ve [verzi 16,4](/visualstudio/releases/2019/release-notes-v16.4/) a novější #region možnosti se zobrazí při zahájení psaní `<!` .

![Editor kódu XAML s možnostmi #region zobrazenými v IntelliSense](media/code-editor-xaml-region.png "Snímek obrazovky editoru kódu XAML s možnostmi #region zobrazenými v IntelliSense")

Oblasti můžete použít, pokud chcete seskupit části kódu, které chcete také rozbalit nebo sbalit.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Další informace o oblastech naleznete na stránce [#region (Referenční dokumentace jazyka C#)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) . Další informace o rozbalení a sbalení oddílů kódu najdete na stránce s [přehledem](../ide/outlining.md) .

### <a name="xaml-comments"></a>Komentáře XAML

Vývojáři často dávají přednost dokumentu kódu pomocí komentářů. Komentáře můžete přidat do kódu jazyka XAML, který je na kartě **MainWindow. XAML** následujícími způsoby:

- Zadejte `<!--` před komentář a přidejte ho `-->` za komentář.
- Zadejte `<!` a pak vyberte `!--` ze seznamu možností.

  ![Editor kódu XAML – dialogové okno klikněte pravým tlačítkem myši na přidat komentáře.](media/xaml-code-editor-comments.png "Snímek obrazovky místní nabídky kliknutím pravým tlačítkem myši k přidání komentářů v editoru kódu XAML")

- Vyberte kód, který chcete uzavřít s komentářem a pak zvolte tlačítko **Komentář** z panelu nástrojů v integrovaném vývojovém prostředí (IDE). Chcete-li akci vrátit zpět, klikněte na tlačítko zrušit **Komentář** .

  ![Tlačítko komentář a tlačítko odkomentovat na panelu nástrojů IDE](media/comment-undo-comment-buttons.png "Snímek obrazovky s tlačítkem komentáře a tlačítkem zrušit komentář na panelu nástrojů IDE")

- Vyberte kód, který chcete obklopit s komentářem, a potom stiskněte klávesu **CTRL** + **K**, **CTRL** + **C**. Chcete-li odkomentovat vybraný kód, stiskněte klávesy **CTRL** + **K**, **CTRL** + **U**.

Další informace o tom, jak používat komentáře v kódu jazyka C#, který je na kartě **MainWindow.XAML.cs** , najdete na stránce s [poznámkami k dokumentaci](/dotnet/csharp/language-reference/language-specification/documentation-comments/) .

### <a name="xaml-lightbulbs"></a>Lightbulbs XAML

Žárovky ikony, které se zobrazují v kódu jazyka XAML, jsou součástí [rychlých akcí](../ide/quick-actions.md) , které lze použít k refaktorování, generování nebo jiným úpravám kódu.

Tady je několik příkladů, jak můžou využít prostředí kódování XAML:

- **Odstraňte nepotřebné obory názvů**. V editoru kódu XAML se v DIMM textu zobrazují nadbytečné obory názvů. Pokud ukazatel myši najedete na nepotřebné použití, zobrazí se žárovky. Když v rozevíracím seznamu zvolíte možnost **odebrat nepotřebné obory názvů** , zobrazí se náhled, který můžete odebrat.

  ![Možnost odebrat nepotřebné obory názvů editoru kódu XAML z rychlých akcí žárovky](media/xaml-code-editor-dimmed-namespaces-preview.png "Snímek obrazovky s možností odebrat nepotřebné obory názvů editoru kódu XAML, která se zobrazí pomocí žárovkyu rychlé akce")

- **Přejmenujte obor názvů**. Tato funkce, která je dostupná v místní nabídce po kliknutí pravým tlačítkem myši po zvýraznění oboru názvů, usnadňuje změnu více instancí nastavení najednou. K této funkci můžete získat přístup také pomocí panelu nabídek, **úpravou**  >  **refaktoru**  >  **přejmenování**nebo stisknutím **kombinace kláves CTRL** + **r**a následným **Ctrl**stisknutím klávesy CTRL + **r** .

  ![Možnost Přejmenovat Editor kódu XAML z místní nabídky kliknutím pravým tlačítkem myši](media/code-editor-rename-namespace.png "Snímek obrazovky s možností přejmenovat obor názvů editoru kódu XAML, která se zobrazí pomocí místní nabídky klikněte pravým tlačítkem myši")

  Další informace naleznete na stránce [přejmenování symbolu kódu pro refaktoring](../ide/reference/rename.md) .

### <a name="conditional-xaml-for-uwp"></a>Podmíněný kód XAML pro UWP

Podmíněný kód XAML poskytuje způsob, jak použít metodu [ApiInformation. IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) v kódu XAML. To vám umožní nastavit vlastnosti a vytvořit instance objektů v kódu na základě přítomnosti rozhraní API, aniž byste museli použít kód na pozadí.

Další informace naleznete na stránce [podmíněného XAML](/windows/uwp/debug-test-perf/conditional-xaml/) a v části [hostitel ovládacího prvku XAML pro UWP na stránce aplikace klasické pracovní plochy (XAML)](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>Vizualizér struktury XAML

Funkce Vizualizér struktury v editoru kódu zobrazuje vodicí čáry struktury, které označují odpovídající otevřené a uzavřené prvky značek ve vašem kódu. Tyto svislé čáry usnadňují zjištění, kde začínají a končí logické bloky.

Další informace naleznete na stránce [navigace s kódem](../ide/navigating-code.md) .

### <a name="intellicode-for-xaml"></a>IntelliCode pro XAML

Při přidání značky jazyka XAML do kódu obvykle začíná levá lomená závorka `<` . Při psaní této lomené závorky se zobrazí nabídka IntelliCode, která obsahuje několik oblíbených značek jazyka XAML. Vyberte ten, který chcete rychle přidat do kódu.

Výběry IntelliCode můžete rozpoznat, protože se zobrazují v horní části seznamu a jsou označených hvězdičkou.

![Seznam IntelliCode pro textový Editor XAML](media/xaml-intellicode-selection.png "Snímek obrazovky seznamu IntelliCode pro editor textu XAML")

Další informace najdete na stránce s [přehledem IntelliCode](/visualstudio/intellicode/overview/) .

### <a name="settings"></a>Nastavení

Další informace o *všech* nastaveních v INTEGROVANÉm vývojovém prostředí sady Visual Studio naleznete v tématu [funkce stránky Editor kódu](../ide/writing-code-in-the-code-and-text-editor.md) .

## <a name="xaml-optional-settings"></a>Volitelná nastavení XAML

Můžete použít dialogové okno [Možnosti](../ide/reference/options-dialog-box-visual-studio.md) ke změně výchozího nastavení editoru kódu XAML. Chcete-li zobrazit nastavení, klikněte na tlačítko **nástroje**  >  **Možnosti**  >  **textový editor**  >  **XAML**.

![Seznam možností pro textový Editor XAML](media/xaml-tools-options.png "Snímek obrazovky se seznamem možností pro editor textu XAML")

> [!NOTE]
> Pro přístup k dialogovému oknu možnosti můžete také použít klávesové zkratky. Tady je postup: stisknutím klávesy **CTRL** + **Q** prohledejte IDE, zadejte **Možnosti**a pak stiskněte **ENTER**. Potom stisknutím klávesy **CTRL** + **E** prohledáte dialogové okno Možnosti, zadáte **textový editor**, stisknete **ENTER**, zadáte **kód XAML**a stisknete klávesu **ENTER**.
>  
> Další informace o klávesových zkratkách naleznete na stránce [tipy pro zástupce pro Visual Studio](../ide/productivity-shortcuts.md#code-editor) .

### <a name="universal-text-editor-options"></a>Možnosti univerzálního textového editoru

V dialogovém okně [Možnosti](../ide/reference/options-text-editor-xaml-formatting.md) pro jazyk XAML jsou následující první tři položky univerzální pro všechny programovací jazyky, které podporuje integrované vývojové prostředí (IDE) sady Visual Studio. Pokud chcete získat další informace o těchto možnostech a jejich použití, přejděte na propojené informace v následující tabulce.

|Název  |Další informace  |
|---------|---------|
|Obecné  | [Dialogové okno Možnosti: textový editor > všechny jazyky](../ide/reference/options-text-editor-all-languages.md) |
|Posuvníky | [Možnosti, textový editor, všechny jazyky, posuvníky](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Karty  |  [Možnosti, Textový editor, Všechny jazyky, Tabulátory](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Možnosti textového editoru specifické pro jazyk XAML

Následující tabulka uvádí nastavení v dialogovém okně [Možnosti](../ide/reference/options-text-editor-xaml-formatting.md) , které může zlepšit možnosti úprav při vývoji aplikací založených na jazyce XAML. Další informace o těchto možnostech a jejich použití najdete v propojených informacích.

|Název  |Další informace  |
|---------|---------|
|Formátování | [Možnosti, Textový editor, XAML, Formátování](../ide/reference/options-text-editor-xaml-formatting.md) |
|Různé |  [Možnosti, textový editor, XAML, různé](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> Nastavení **názvu metody obslužné rutiny události velkými písmeny** v části **různé** je užitečné hlavně pro vývojáře XAML. Toto nastavení je ve výchozím nastavení *vypnuté* , protože je nového, ale doporučujeme, abyste ho nastavili na *zapnuto* pro podporu správného používání velkých a malých písmen v kódu.

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak upravit kód v reálném čase, když spouštíte svou aplikaci v režimu ladění, naleznete na stránce [XAML Hot Loading](xaml-hot-reload.md) .

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu sady Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML v aplikacích pro UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML v aplikacích Xamarin. Forms](/xamarin/xamarin-forms/xaml/)
- [Vývoj mobilních aplikací Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 for Mac – prohlídka integrovaného vývojového prostředí (Mac)](/visualstudio/mac/ide-tour/)
