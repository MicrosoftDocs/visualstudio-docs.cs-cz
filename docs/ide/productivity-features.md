---
title: Průvodce produktivitou
ms.date: 4/29/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa4a768f8ebd8b39918fa3ba51d4eb9b3f773151
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89219761"
---
# <a name="productivity-guide-for-visual-studio"></a>Průvodce produktivitou pro Visual Studio

Pokud chcete ušetřit čas při psaní kódu, jste na správném místě. Tato příručka produktivity obsahuje tipy, které vám pomůžou začít se sadou Visual Studio, psát kód, ladit kód, zpracovávat chyby a používat klávesové zkratky &mdash; na jedné stránce.

Informace o užitečných klávesových zkratkách najdete v tématu věnovaném [zástupcům produktivity](../ide/productivity-shortcuts.md). Úplný seznam klávesových zkratek najdete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>Začínáme

Šetřete čas prozkoumá prostřednictvím nabídek, a to tak, že rychle vyhledáte cokoli, co potřebujete, včetně příkazů, nastavení, dokumentace a možností instalace. V sadě Visual Studio najdete klávesové zkratky pro příkazy v rámci výsledků hledání, abyste je mohli snadno nepamatují. 

- **Kód v seznamu úkolů**. Pokud nemáte dostatek požadavků k dokončení části kódu, použijte Seznam úkolů ke sledování komentářů kódu, které používají tokeny, jako jsou `TODO` a `HACK` , nebo vlastní tokeny, a ke správě zástupců, které vás přejímají přímo na předdefinované umístění v kódu. Další informace najdete v tématu [použití seznam úkolů](../ide/using-the-task-list.md).

- **Použijte zástupce Průzkumník řešení**. Pokud s Visual Studiem začínáte, budou tyto klávesové zkratky užitečné a ušetříte si čas, kdy budete mít k dispaměti nový základ kódu. Úplný seznam klávesových zkratek naleznete v tématu [výchozí klávesové zkratky v aplikaci Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Identifikujte a přizpůsobení klávesových zkratek v aplikaci Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**. Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Klávesovou zkratku můžete kdykoli najít a změnit v dialogovém okně Možnosti.

- **Zajištění přístupnější dostupnosti sady Visual Studio**. Visual Studio obsahuje integrované funkce pro usnadnění přístupu, které jsou kompatibilní s čtečkami obrazovky a dalšími technologiemi usnadnění. Úplný seznam dostupných funkcí najdete v tématu [tipy a triky pro usnadnění pro sadu Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) . 

- **Projděte si životní cyklus produktu Visual Studio a údržba**. Informace o tom, jak získat aktualizace pro sadu Visual Studio, možnosti podpory pro zákazníky v edicích Enterprise a Professional, podporu pro starší verze sady Visual Studio a součásti, na které se nezabývá údržba sady Visual Studio, najdete v tématu [životní cyklus a údržba produktu Visual Studio](https://docs.microsoft.com/visualstudio/releases/2019/servicing). 

- **Nainstalujte a spravujte balíčky NuGet v aplikaci Visual Studio**. Uživatelské rozhraní Správce balíčků NuGet v aplikaci Visual Studio ve Windows umožňuje snadno nainstalovat, odinstalovat a aktualizovat balíčky NuGet v projektech a řešeních. Další informace najdete v tématu [instalace a Správa balíčků v aplikaci Visual Studio pomocí Správce balíčků NuGet](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Psaní kódu

Vytvářejte kód rychleji pomocí následujících funkcí.

- **Používejte praktické příkazy**. Visual Studio obsahuje různé příkazy, které vám pomůžou rychleji provádět běžné úlohy úprav. Můžete například zvolit příkaz pro snadné duplikování řádku kódu bez nutnosti jeho zkopírování, přemístění kurzoru a vložení. Zvolte možnost **Upravit**  >  **Duplikovat** nebo stiskněte klávesu **CTRL** + **E**,**V**. Můžete také rychle rozbalit nebo Sbalit výběr textu výběrem možnosti **Upravit**  >  **Rozšířené**  >  **rozbalení výběru** nebo **Upravit**  >  **pokročilý**  >  **Výběr smlouvy**nebo stisknutím klávesy **SHIFT** + **ALT** + **=** nebo **SHIFT** + **ALT** + **-** .

- **Použijte technologii IntelliSense**. Při zadávání kódu v editoru se zobrazí informace IntelliSense, jako jsou například členové seznamu, informace o parametrech, rychlé informace, signatura podpisu a hotové slovo. Tyto funkce podporují přibližnou shodu textu; například seznam výsledků pro seznam členů zahrnuje nejen položky, které začínají znaky, které jste zadali, ale také záznamy, které obsahují kombinaci znaků kdekoli v jejich jménu. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md).

- **Umožňuje změnit automatické vkládání možností IntelliSense při zadávání kódu**. Přepnutím technologie IntelliSense na režim návrhu můžete určit, zda jsou možnosti technologie IntelliSense vloženy pouze v případě, že je zvolíte explicitně.

     Chcete-li povolit režim návrhu, **stiskněte klávesy CTRL** + **ALT +** + **MEZERNÍK** nebo na panelu nabídek vyberte možnost **Upravit**  >  **IntelliSense**  >  **režim dokončení přepínání**technologie IntelliSense.

- **Použijte fragmenty kódu**. Můžete použít předdefinované fragmenty nebo vytvořit vlastní fragmenty kódu.

     Chcete-li vložit fragment kódu, v panelu nabídek vyberte možnost **Upravit**  >  **IntelliSense**  >  **Vložit fragment** nebo **obklopit pomocí**nebo otevřete místní nabídku v souboru a vyberte možnost **fragment**  >  **Vložit fragment** nebo **obklopit pomocí**. Další informace naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).

- **Opravte chyby kódu jako vložené**. Rychlé akce umožňují snadno Refaktorovat, generovat nebo jinak upravovat kód jedinou akcí. Tyto akce lze použít pomocí ikony ikony Screwdriver Screwdriver nebo ikony žárovky žárovky nebo ![ ](media/screwdriver-icon.png) stisknutím klávesy ![ ](media/light-bulb-icon.png) **ALT** + **ENTER** nebo **CTRL** + **.** Když je kurzor na příslušném řádku kódu. Další informace najdete v tématu [rychlé akce](quick-actions.md) .

- **Zobrazit a upravit definici prvku kódu**. Můžete rychle zobrazit a upravit modul, ve kterém je definován prvek kódu, jako je například člen, proměnná nebo místní,.

    Chcete-li otevřít definici v překryvném okně, zvýrazněte prvek a zvolte klávesy **ALT** + **F12** nebo otevřete místní nabídku pro prvek a pak zvolte možnost **Náhled definice**. Chcete-li otevřít definici v samostatném okně kódu, otevřete místní nabídku pro prvek a zvolte možnost **Přejít k definici**.

- **Použijte ukázkové aplikace**. Vývoj aplikací můžete urychlit stažením a instalací ukázkových aplikací ze [sítě Microsoft Developer Network](https://code.msdn.microsoft.com/). Můžete si také přečíst konkrétní technologii nebo programovací koncept stažením a prozkoumáním ukázkové sady pro tuto oblast.

- **Změna formátování složených závorek s formátováním/novými řádky** Pomocí stránky možnosti **formátování**  můžete nastavit možnosti formátování kódu v editoru kódu, včetně nových řádků. Další informace o tom, jak používat toto nastavení v jazyce C#, naleznete v [dialogovém okně Možnosti: textový Editor > C# > stylu kódu > formátování](../ide/reference/options-text-editor-csharp-formatting.md). Jazyk C++ naleznete [v tématu Nastavení předvoleb kódování jazyka c++ v sadě Visual Studio](https://docs.microsoft.com/cpp/ide/how-to-set-preferences). Pro Python si přečtěte téma [formátování kódu Pythonu](../python/formatting-python-code.md).

- **Změňte odsazení pomocí tabulátorů**. Použijte vlastní nastavení editoru, které je přizpůsobené každému základu kódu, k vykonání konzistentních stylů kódování pro více vývojářů pracujících na stejném projektu napříč různými editory a architekturou IDEs. Zajistěte, aby celý tým měl stejné jazykové konvence, konvence pojmenování a pravidla formátování. Vzhledem k tomu, že jsou tato vlastní nastavení přenosné a cestovaná s vaším kódem, můžete vymáhat styly kódování i mimo sadu Visual Studio. Další informace najdete v tématu [Možnosti, textový editor, všechny jazyky, karty](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Navigace v rámci kódu a integrovaného vývojového prostředí

Můžete použít různé techniky k rychlejšímu vyhledání a přesunu do konkrétních umístění v kódu. Můžete také změnit rozložení oken aplikace Visual Studio podle vašich požadavků. 

- **Záložek řádků kódu** Pomocí záložek můžete rychle přejít na konkrétní řádky kódu v souboru.

    Chcete-li nastavit záložku, vyberte na panelu nabídek možnost **Upravit**  >  **záložky**  >  **Přepnout záložku**. Všechny záložky pro řešení můžete zobrazit v okně **záložky** . Další informace naleznete v tématu [Nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md).

- **Hledání definic symbolů v souboru**. Můžete hledat v rámci řešení a vyhledat definice symbolů a názvy souborů, ale výsledky hledání neobsahují obory názvů nebo místní proměnné.

   Přístup k této funkci získáte tak, že v řádku nabídek kliknete na možnost **Upravit**  >  **Navigovat na**.

- **Projděte si celkovou strukturu kódu**. V **Průzkumník řešení**můžete vyhledávat a procházet třídy a jejich typy a členy v projektech. Můžete také vyhledat symboly, zobrazit hierarchii volání metody, najít odkazy na symboly a provádět další úkoly. Pokud zvolíte prvek kódu v **Průzkumník řešení**, otevře se přidružený soubor na kartě **Preview** a kurzor se přesune do prvku v souboru. Další informace naleznete v tématu [zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md).

- **Přejděte na umístění v souboru s režimem mapy**. V režimu mapy se na posuvníku zobrazují řádky kódu v miniaturách. Další informace o tomto režimu zobrazení naleznete v tématu [How to: Customize a Scroll posuvník](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- **Pochopení struktury kódu pomocí mapy kódu**. Mapy kódu vám mohou pomoci vizualizovat závislosti napříč vaším kódem a vidět, jak se vejde dohromady bez čtení souborů a řádků kódu. Další informace najdete v tématu [Mapování závislostí pomocí map kódu](../modeling/map-dependencies-across-your-solutions.md).

- **Podívejte se na často používané soubory s úpravou a přechodem k poslednímu souboru**. Pomocí příkazů přejít na v aplikaci Visual Studio můžete provádět cílené hledání kódu, abyste mohli rychle najít zadané položky. Podrobné pokyny najdete v tématu [vyhledání kódu pomocí příkazu Přejít na](../ide/go-to.md).

- **Přesuňte [okno Vlastnosti](../ide/reference/properties-window.md) na pravou stranu**. Pokud hledáte podrobnější rozložení okna, můžete okno Vlastnosti v aplikaci Visual Studio přesunout stisknutím klávesy **F4**.

## <a name="find-items-faster"></a>Rychlejší hledání položek

Můžete hledat v integrovaném vývojovém prostředí (IDE) pro příkazy, soubory a možnosti, kromě filtrování obsahu oken nástrojů, aby se zobrazily pouze relevantní informace pro aktuální úkol.

- **Filtrování obsahu oken nástrojů** Můžete hledat v obsahu mnoha oken nástrojů, jako je například **Sada nástrojů**, okno **vlastnosti** a **Průzkumník řešení**, ale zobrazit pouze položky, jejichž názvy obsahují znaky, které zadáte.

- **Zobrazí jenom chyby, které chcete adresovat**. Pokud zvolíte tlačítko **Filtr** na panelu nástrojů **Seznam chyb** , můžete snížit počet chyb, které se zobrazí v okně **Seznam chyb** . Můžete zobrazit pouze chyby v souborech, které jsou otevřeny v editoru, pouze chyby v aktuálním souboru nebo pouze chyby v aktuálním projektu. Můžete také vyhledat konkrétní chyby v okně **Seznam chyb** .

- **Najděte dialogová okna, příkazy nabídky, možnosti a další**. Do vyhledávacího pole zadejte klíčová slova nebo fráze pro položky, které se pokoušíte najít. Například následující možnosti se zobrazí, pokud zadáte **Nový projekt**:

   ::: moniker range="vs-2017"

   ![Výsledky snadného spuštění pro nový projekt](../ide/media/productivity_quicklaunch.png)

   **Rychlé spuštění** zobrazuje odkazy na vytvoření nového projektu, pro přidání nové položky do projektu a na stránku **projekty a řešení** v dialogovém okně **Možnosti** mimo jiné. Výsledky hledání mohou také zahrnovat soubory projektu a okna nástrojů.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Výsledky hledání pro nový projekt](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Stiskněte klávesu **CTRL** + **Q** pro přechod přímo do vyhledávacího pole.

## <a name="debug-code"></a>Ladění kódu

Ladění může spotřebovat spoustu času, ale následující tipy vám pomůžou tento proces urychlit.

- **Použijte nástroje ladicího programu sady Visual Studio**. Když v kontextu aplikace Visual Studio *ladíte aplikaci*, obvykle to znamená, že aplikaci spouštíte v režimu ladicího programu. Ladicí program poskytuje mnoho způsobů, jak zjistit, co váš kód provádí při spuštění. V tématu [první pohled na ladicí program sady Visual Studio](../debugger/debugger-feature-tour.md) , který vám pomůže začít. 

- **Otestujte stejnou stránku, aplikaci nebo web v různých prohlížečích**. Při ladění kódu můžete snadno přepínat mezi nainstalovanými webovými prohlížeči, včetně nástroje [Page Inspector (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), aniž byste museli otevřít dialogové okno **Procházet s** . Můžete použít seznam **cílů ladění** , který je na **standardním** panelu nástrojů vedle tlačítka **Spustit ladění** , a rychle ověřit, který prohlížeč používáte při ladění nebo prohlížení stránek.

    ![Vybrat možnosti ladění webového prohlížeče](../ide/media/webbrowserdropdowntoolbar.png)

- **Nastavte dočasné zarážky**. Můžete vytvořit dočasnou zarážku v aktuálním řádku kódu a spustit ladicí program současně. Po dosažení tohoto řádku kódu ladicí program přejde do režimu přerušení. Další informace najdete v tématu [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

    Chcete-li použít tuto funkci, zvolte klávesy **CTRL** + **F10** nebo otevřete místní nabídku pro řádek kódu, na kterém chcete přerušit, a pak zvolte možnost **Spustit ke kurzoru**.

- **Přesunout bod spuštění během ladění**. Aktuální bod spuštění můžete přesunout do jiné části kódu a pak z tohoto bodu znovu spustit ladění. Tato technika je užitečná, pokud chcete ladit část kódu bez nutnosti znovu vytvořit všechny kroky, které jsou požadovány pro dosažení této části. Další informace najdete v tématu [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

     Chcete-li přesunout bod provádění, přetáhněte žlutou šipku na místo, kde chcete nastavit další příkaz ve stejném zdrojovém souboru, a pak stiskněte klávesu **F5** pro pokračování v ladění.

- **Zachytit informace o hodnotě pro proměnné**. Můžete přidat DataTip do proměnné v kódu a připnout ji tak, abyste měli přístup k poslední známé hodnotě pro proměnnou po dokončení ladění. Další informace najdete v tématu [zobrazení hodnot dat v tipech k datům](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Chcete-li přidat DataTip, musí být ladicí program v režimu pozastavení. Umístěte kurzor na proměnnou a pak zvolte tlačítko Připnout na DataTip, které se zobrazí. Při zastavení ladění se ve zdrojovém souboru vedle řádku kódu, který obsahuje proměnnou, zobrazí ikona modrého kódu PIN. Pokud navedete ukazatel na modrý kód PIN, zobrazí se hodnota proměnné z poslední relace ladění.

- **Vymažte okno Immediate**. Obsah [okamžitého okna](../ide/reference/immediate-window.md) můžete vymazat v době návrhu zadáním `>cls` nebo `>Edit.ClearAll`

     Další informace o dalších příkazech naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- **[Najděte změny kódu a další historii pomocí CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)**. CodeLens vám umožňuje soustředit se na práci, zatímco zjistíte, co se stalo s vaším kódem, &mdash; aniž byste museli opustit Editor. Můžete najít odkazy na část kódu, změny kódu, propojené chyby, pracovní položky, revize kódu a testování částí.

- **Použijte Live Share k ladění v reálném čase s ostatními**. Rozšíření Live Share vám umožňuje upravovat a ladit v reálném čase společně s ostatními bez ohledu na to, jaké programovací jazyky používáte nebo jaké typy aplikací vytváříte. Další informace najdete v tématu [co je Visual Studio Live Share?](https://docs.microsoft.com/visualstudio/liveshare/)

- **Použijte interaktivní okno k psaní a testování malého kódu**. Visual Studio poskytuje interaktivní okno pro čtení a vyhodnocení-tisk-smyčky (REPL), které umožňuje zadat libovolný kód a zobrazit okamžité výsledky. Tento způsob psaní kódu pomáhá naučit a experimentovat s rozhraními API a knihovnami a interaktivně vyvíjet pracovní kód pro zahrnutí do vašich projektů. Informace o Pythonu najdete v tématu [práce s interaktivním oknem Pythonu](../python/python-interactive-repl-in-visual-studio.md). Funkce interaktivního okna je také k dispozici pro jazyk C#. 

## <a name="access-visual-studio-tools"></a>Přístup k nástrojům sady Visual Studio

Můžete rychle získat přístup k Developer Command Prompt nebo k jinému nástroji sady Visual Studio, pokud ho připnete v nabídce Start nebo na hlavním panelu.

::: moniker range="vs-2017"

1. V Průzkumníku Windows přejděte do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual studia 2017 \ Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. V Průzkumníku Windows přejděte do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual studia 2019 \ Visual Studio Tools*.

::: moniker-end

2. Klikněte pravým tlačítkem nebo otevřete kontextovou nabídku pro **Developer Command Prompt**a pak zvolte připnout pro **začátek** nebo **Připnout na hlavní panel**.

## <a name="manage-files-toolbars-and-windows"></a>Správa souborů, panelů nástrojů a oken

V jednom okamžiku můžete pracovat v několika souborech kódu a při vývoji aplikace se pohybovat mezi několika okny nástrojů. Pomocí následujících tipů můžete dál organizovat:

- **Soubory, které často používáte, se budou zobrazovat v editoru**. Soubory můžete připnout na levou stranu karty, aby zůstaly viditelné bez ohledu na to, kolik souborů je v editoru otevřené.

   Chcete-li připnout soubor, zvolte kartu soubor a poté klikněte na tlačítko **Přepnout stav pinu** .

- **Přesuňte dokumenty a okna do jiných monitorů**. Pokud používáte více než jedno monitorování při vývoji aplikací, můžete snadněji pracovat na částech aplikace tím, že přesunete soubory, které jsou otevřeny v editoru, na jiný monitor. Můžete také přesunout okna nástrojů, jako je například okna ladicího programu, na jiný monitor a umístit kartu dokumentů a nástrojů společně a vytvořit "vory". Další informace naleznete v tématu [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Soubory můžete spravovat i snadněji tím, že vytvoříte jinou instanci **Průzkumník řešení** a přesunete ji do jiného monitoru. Chcete-li vytvořit jinou instanci **Průzkumník řešení**, otevřete místní nabídku v **Průzkumník řešení**a zvolte možnost **zobrazení nového Průzkumník řešení**.

- **Přizpůsobení písem, která se zobrazí v aplikaci Visual Studio**. U textu v integrovaném vývojovém prostředí můžete změnit řez písma, jeho velikost a barvu. Například můžete přizpůsobit barvu konkrétních prvků kódu v editoru a řez písma v oknech nástrojů nebo v celém rozhraní IDE. Další informace najdete v tématu [Postup: Změna písma a barev](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) a [Postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také

- [Příspěvek na blogu tipy a triky pro Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Návod: Vytvoření jednoduché aplikace](../get-started/csharp/tutorial-wpf.md)
- [Rady a tipy k usnadnění přístupu](../ide/reference/accessibility-tips-and-tricks.md)
