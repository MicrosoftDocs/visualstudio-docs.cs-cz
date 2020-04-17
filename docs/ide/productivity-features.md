---
title: Tipy pro vyšší produktivitu
ms.date: 2/21/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 620ad93c03e1a1b260ee14cb27093403f27648d7
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544299"
---
# <a name="productivity-tips-for-visual-studio"></a>Tipy pro produktivitu pro Visual Studio

Tento článek popisuje tipy pro funkce sady Visual Studio, které vám pomohou psát, procházet a ladit kód rychleji a efektivněji.

Informace o užitečných klávesových zkratkách naleznete v [tématu Pracovní zkratky](../ide/productivity-shortcuts.md). Úplný seznam klávesových zkratek příkazů naleznete [v tématu Výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Psaní kódu

Rychlejší psaní kódu pomocí následujících funkcí.

- **Používejte příkazy pohodlí**. Visual Studio obsahuje různé příkazy, které vám pomohou rychleji provádět běžné úlohy úprav. Můžete například zvolit příkaz, který snadno duplikuje řádek kódu, aniž byste jej museli kopírovat, přemístit kurzor a pak jej vložit. Zvolte **Upravit** > **duplicitní nebo** stiskněte **Ctrl**+**E**,**V**. Výběr textu můžete také rychle rozbalit nebo**Alt**+**-** zostřit tak, že zvolíte **Upravit** > **rozšířený** > **rozbalovací výběr** nebo **Upravit** > **rozšířený** > výběr**smlouvy**nebo stisknete **Shift**+**Alt** + **=** . **Shift**+

- **Použijte technologie IntelliSense**. Při zadávání kódu do editoru se zobrazí informace technologie IntelliSense, například Seznam členů, Informace o parametrech, Rychlé informace, Nápověda k podpisu a Kompletní word. Tyto funkce podporují přibližné shody textu; Seznamy výsledků pro členy seznamu například obsahují nejen položky začínající znaky, které jste zadali, ale také položky, které obsahují kombinaci znaků kdekoli v jejich názvech. Další informace naleznete [v tématu Use IntelliSense](../ide/using-intellisense.md).

- **Při zadávání kódu změňte automatické vkládání možností technologie IntelliSense**. Přepnutím technologie IntelliSense do režimu návrhů můžete určit, že možnosti technologie IntelliSense budou vloženy pouze v případě, že je explicitně vyberete.

     Chcete-li povolit režim návrhů, zvolte klávesy **Ctrl**+**Alt**+**Mezerník** nebo na řádku nabídek zvolte **Upravit** > **režim dokončení**technologie**IntelliSense** > .

- **Použijte fragmenty kódu**. Můžete použít předdefinované úryvky nebo vytvořit vlastní úryvky.

     Chcete-li vložit výstřižek, zvolte na řádku nabídek možnost **Upravit** > výstřižk**intelliSense** > **Vložit výstřižk** nebo **Prostorovat**do souboru nebo otevřete místní nabídku v souboru a zvolte **Výstřižk** > **Vložit výstřižk** nebo **Prostorovat s**. Další informace naleznete v [tématu Fragmenty kódu](../ide/code-snippets.md).

- **Oprava vřádík chyb kódu**. Rychlé akce umožňují snadno refaktorovat, generovat nebo jinak upravovat kód pomocí jediné akce. Tyto akce lze použít pomocí ![ikony](media/screwdriver-icon.png) šroubováku ![šroubovák nebo ikony ikony](media/light-bulb-icon.png) žárovky nebo stisknutím **kláves Alt**+**Enter** nebo **Ctrl**+**.** když je kurzor na příslušném řádku kódu. Další informace najdete v [tématu Rychlé akce.](quick-actions.md)

- **Zobrazení a úprava definice prvku kódu**. Můžete rychle zobrazit a upravit modul, ve kterém je definován prvek kódu, například člen, proměnná nebo místní.

    Chcete-li otevřít definici v rozbalovacím okně, zvýrazněte prvek a pak zvolte klávesy **Alt**+**F12** nebo otevřete místní nabídku prvku a pak zvolte **Peek Definition**. Chcete-li otevřít definici v samostatném okně kódu, otevřete místní nabídku prvku a pak zvolte **Přejít na definici**.

- **Používejte ukázkové aplikace**. Vývoj aplikací můžete urychlit stažením a instalací ukázkových aplikací ze [služby Microsoft Developer Network](https://code.msdn.microsoft.com/). Můžete se také naučit konkrétní technologie nebo programovací koncept stažením a zkoumání ukázkový balíček pro tuto oblast.

## <a name="navigate-within-your-code"></a>Navigace v kódu

Můžete použít různé techniky najít a přesunout do konkrétních míst v kódu rychleji.

- **Řádky kódu záložky**. Záložky můžete použít k rychlému přechodu na určité řádky kódu v souboru.

    Chcete-li nastavit záložku, zvolte na řádku nabídek **možnost Upravit** > **záložky** > **.** V okně **Záložky** můžete zobrazit všechny záložky pro řešení. Další informace naleznete v tématu [Nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md).

- **Vyhledejte definice symbolů v souboru**. V rámci řešení můžete vyhledat definice symbolů a názvy souborů, ale výsledky hledání neobsahují obory názvů ani místní proměnné.

   Chcete-li získat přístup k této funkci, zvolte na řádku nabídek **možnost Upravit** > **přechod na**.

- **Prohlédněte si celkovou strukturu kódu**. V **Průzkumníku řešení**můžete vyhledávat a procházet třídy a jejich typy a členy ve vašich projektech. Můžete také vyhledávat symboly, zobrazit hierarchii volání metody, najít odkazy na symboly a provádět další úkoly. Pokud v **Průzkumníku řešení**zvolíte prvek kódu , přidružený soubor se otevře na kartě **Náhled** a kurzor se přesune na prvek v souboru. Další informace naleznete [v tématu Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md).

## <a name="find-items-faster"></a>Rychlejší hledání položek

V prostředí IDE můžete kromě filtrování obsahu oken nástrojů vyhledávat příkazy, soubory a možnosti a zobrazit pouze relevantní informace pro aktuální úkol.

- **Filtrujte obsah oken nástrojů**. Můžete prohledávat v obsahu mnoha oken nástrojů, například **panelu nástrojů**, okna **Vlastnosti** a **Průzkumníka řešení**, ale zobrazit pouze položky, jejichž názvy obsahují zadané znaky.

- **Zobrazí pouze chyby, které chcete adresovat**. Pokud na panelu nástrojů **Seznam chyb** zvolíte tlačítko **Filtr,** můžete snížit počet chyb, které se zobrazí v okně **Seznam chyb.** V souborech, které jsou otevřené v editoru, lze zobrazit pouze chyby v aktuálním souboru nebo pouze chyby v aktuálním projektu. Můžete také hledat v okně **Seznam chyb** a najít konkrétní chyby.

- **Hledání dialogových oken, příkazů nabídek, možností a dalších možností**. Do vyhledávacího pole zadejte klíčová slova nebo fráze pro položky, které se pokoušíte najít. Pokud zadáte **nový projekt,** zobrazí se například následující možnosti :

   ::: moniker range="vs-2017"

   ![Výsledky snadného spuštění pro "nový projekt"](../ide/media/productivity_quicklaunch.png)

   **Panel Snadné spuštění** zobrazuje odkazy na vytvoření nového projektu, přidání nové položky do projektu a mimo jiné na stránku **Projekty a řešení** v dialogovém okně **Možnosti.** Výsledky hledání mohou také obsahovat soubory projektu a okna nástrojů.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Výsledky hledání pro 'nový projekt'](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Stisknutím **klávesy Ctrl**+**Q** přejděte přímo do vyhledávacího pole.

## <a name="debug-code"></a>Ladicí kód

Ladění může spotřebovat spoustu času, ale následující tipy vám mohou pomoci urychlit proces.

- **Otestujte stejnou stránku, aplikaci nebo web v různých prohlížečích**. Při ladění kódu můžete snadno přepínat mezi nainstalovanými webovými prohlížeči, včetně [Page Inspector (Visual Studio),](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209)aniž byste museli **otevírat** dialogové okno Procházet pomocí. Pomocí seznamu **Ladění cíle,** který je na panelu nástrojů **Standardní** vedle tlačítka **Spustit ladění,** můžete rychle ověřit, který prohlížeč používáte při ladění nebo zobrazení stránek.

    ![Výběr možností ladění webového prohlížeče](../ide/media/webbrowserdropdowntoolbar.png)

- **Nastavte dočasné zarážky**. Můžete vytvořit dočasnou zarážku v aktuálním řádku kódu a spustit ladicí program současně. Když stisknete tento řádek kódu, ladicí program přejde do režimu přerušení. Další informace naleznete [v tématu Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

    Chcete-li tuto funkci použít, zvolte klávesy **Ctrl**+**F10** nebo otevřete místní nabídku pro řádek kódu, na kterém chcete přerušit, a pak zvolte **Spustit kurzor**.

- **Přesuňte bod spuštění během ladění**. Aktuální bod spuštění můžete přesunout do jiné části kódu a potom restartovat ladění od tohoto bodu. Tato technika je užitečná, pokud chcete ladit část kódu bez nutnosti znovu vytvořit všechny kroky, které jsou nutné k dosažení tohoto oddílu. Další informace naleznete [v tématu Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

     Chcete-li přesunout bod spuštění, přetáhněte žlutou šipku do umístění, kde chcete nastavit další příkaz ve stejném zdrojovém souboru, a pak zvolte klávesu **F5,** chcete-li pokračovat v ladění.

- **Zachyťte informace o hodnotě proměnných**. DataTip můžete přidat do proměnné v kódu a připnout, abyste měli přístup k poslední známé hodnotě proměnné po dokončení ladění. Další informace naleznete [v tématu Zobrazení datových hodnot v tipech na data](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Chcete-li přidat DataTip, ladicí program musí být v režimu přerušení. Umístěte kurzor na proměnnou a pak zvolte tlačítko pin na DataTip, který se zobrazí. Při zastavení ladění se ve zdrojovém souboru vedle řádku kódu, který obsahuje proměnnou, zobrazí modrá ikona špendlíku. Pokud ukážete na modrý špendlík, zobrazí se hodnota proměnné z poslední relace ladění.

- **Zrušte zaškrtnutí okna Okamžité**. Obsah [okna Okamžité](../ide/reference/immediate-window.md) můžete vymazat v době návrhu zadáním `>cls` nebo zadáním nebo`>Edit.ClearAll`

     Další informace o dalších příkazech naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

## <a name="access-visual-studio-tools"></a>Aplikace Access Visual Studio

Pokud jej připnete do nabídky Start nebo na hlavní panel, můžete rychle přistupovat k příkazovému řádku pro vývojáře nebo k jinému nástroji sady Visual Studio.

::: moniker range="vs-2017"

1. V Průzkumníkovi Windows přejděte na *%ProgramData%\Microsoft\Windows\Nabídka Start\Programy\Visual Studio 2017\Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. V Průzkumníkovi Windows přejděte na *%ProgramData%\Microsoft\Windows\Nabídka Start\Programy\Visual Studio 2019\Visual Studio Tools*.

::: moniker-end

2. Klikněte pravým tlačítkem myši nebo otevřete místní nabídku **pro příkazový řádek vývojáře**a pak zvolte **Připnout na úvodní obrazovku** nebo **Připnout na hlavní panel**.

## <a name="manage-files-toolbars-and-windows"></a>Správa souborů, panelů nástrojů a oken

V každém okamžiku můžete pracovat ve více souborech kódu a při vývoji aplikace se pohybovat mezi několika okny nástrojů. Uspořádat můžete pomocí následujících tipů:

- **Udržujte soubory, které často používáte, viditelné v editoru**. Soubory můžete dobře připnout na levou stranu karty, aby zůstaly viditelné bez ohledu na to, kolik souborů je v editoru otevřeno.

   Pokud chcete připnout soubor, zvolte kartu souboru a pak zvolte tlačítko **Přepnout stav pinu.**

- **Přesuňte dokumenty a okna na jiné monitory**. Pokud při vývoji aplikací používáte více než jeden monitor, můžete snadněji pracovat s částmi aplikace přesunutím souborů otevřených v editoru na jiný monitor. Okna nástrojů, například okna ladicího programu, můžete také přesunout na jiný dokument dokovací stanice monitorů a karet a okna nástrojů společně a vytvořit tak "rafty". Další informace naleznete [v tématu Přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Soubory můžete také snadněji spravovat vytvořením jiné instance **Průzkumníka řešení** a jejím přesunutím na jiný monitor. Chcete-li vytvořit další instanci **Průzkumníka řešení**, otevřete v **Průzkumníku řešení**místní nabídku a zvolte **Nové zobrazení Průzkumníka řešení**.

- **Přizpůsobte písma, která se zobrazí v sadě Visual Studio**. Můžete změnit plochu písma, velikost a barvu, která se používá pro text v ide. Můžete například přizpůsobit barvu určitých prvků kódu v editoru a plochu písma v oknech nástrojů nebo v celém rozhraní IDE. Další informace naleznete v [tématu Postup: Změna písem a barev](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) a [Postup: Změna písem a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také

- [Příspěvek na blogu s tipy a triky visual studia](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Postup: Přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Návod: Vytvoření jednoduché aplikace](../get-started/csharp/tutorial-wpf.md)
- [Rady a tipy k usnadnění přístupu](../ide/reference/accessibility-tips-and-tricks.md)
