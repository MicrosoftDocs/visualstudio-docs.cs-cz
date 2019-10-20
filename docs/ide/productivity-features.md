---
title: Tipy pro vyšší produktivitu
ms.date: 2/21/2019
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0ac256d9878df45404dc62f1080e12bb6e7f002
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666778"
---
# <a name="productivity-tips-for-visual-studio"></a>Tipy pro produktivitu pro Visual Studio

V tomto článku jsou popsány tipy pro funkce sady Visual Studio, které vám pomůžou rychleji a efektivně psát, Procházet a ladit kód.

Informace o užitečných klávesových zkratkách najdete v tématu věnovaném [zástupcům produktivity](../ide/productivity-shortcuts.md). Úplný seznam klávesových zkratek najdete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Napsat kód

Vytvářejte kód rychleji pomocí následujících funkcí.

- **Používejte praktické příkazy**. Visual Studio obsahuje různé příkazy, které vám pomůžou rychleji provádět běžné úlohy úprav. Můžete například zvolit příkaz pro snadné duplikování řádku kódu bez nutnosti jeho zkopírování, přemístění kurzoru a vložení. Zvolte možnost **upravit**  > **Duplikovat** nebo stiskněte klávesu **CTRL** +**E**,**V**. Výběr textu můžete také rychle rozšířit nebo zúžit výběrem možnosti **upravit**  > **Upřesnit**  > **rozšířit výběr** nebo **upravit**  > **pokročilý** **Výběr kontraktu** >  nebo stisknutím klávesy  **Shift** 1**alt** 3 **5** nebo **SHIFT** 7**ALT** 9 **1**.

- **Použijte technologii IntelliSense**. Při zadávání kódu v editoru se zobrazí informace IntelliSense, jako jsou například členové seznamu, informace o parametrech, rychlé informace, signatura podpisu a hotové slovo. Tyto funkce podporují přibližnou shodu textu; například seznam výsledků pro seznam členů zahrnuje nejen položky, které začínají znaky, které jste zadali, ale také záznamy, které obsahují kombinaci znaků kdekoli v jejich jménu. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md).

- **Umožňuje změnit automatické vkládání možností IntelliSense při zadávání kódu**. Přepnutím technologie IntelliSense na režim návrhu můžete určit, zda jsou možnosti technologie IntelliSense vloženy pouze v případě, že je zvolíte explicitně.

     Chcete-li povolit režim návrhu, **stiskněte klávesu Ctrl** +**ALT** + klávesy**MEZERNÍK** nebo na panelu nabídek vyberte možnost **Upravit**  > **IntelliSense**  > **Přepnout režim dokončení**.

- **Použijte fragmenty kódu**. Můžete použít předdefinované fragmenty nebo vytvořit vlastní fragmenty kódu.

     Chcete-li vložit fragment, v panelu nabídek vyberte možnost **upravit**  > **IntelliSense**  > **Vložit fragment** nebo **obklopit pomocí**nebo otevřete místní nabídku souboru a vyberte možnost **fragment kódu**  > **Vložit fragment kódu** nebo  **Obklopit s**. Další informace naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).

- **Opravte chyby kódu jako vložené**. Rychlé akce umožňují snadno Refaktorovat, generovat nebo jinak upravovat kód jedinou akcí. Tyto akce lze použít pomocí ikony ![Screwdriver Screwdriver ](media/screwdriver-icon.png) nebo ikony ![Light žárovky ](media/light-bulb-icon.png) ikonu nebo stisknutím kombinace **kláves Alt** +**Enter** nebo **CTRL** + **.** Když je kurzor na příslušném řádku kódu. Další informace najdete v tématu [rychlé akce](quick-actions.md) .

- **Zobrazit a upravit definici prvku kódu**. Můžete rychle zobrazit a upravit modul, ve kterém je definován prvek kódu, jako je například člen, proměnná nebo místní,.

    Chcete-li otevřít definici v překryvném okně, zvýrazněte prvek a zvolte klávesu **Alt** +**F12** nebo otevřete místní nabídku pro prvek a pak zvolte možnost **Náhled definice**. Chcete-li otevřít definici v samostatném okně kódu, otevřete místní nabídku pro prvek a zvolte možnost **Přejít k definici**.

- **Použijte ukázkové aplikace**. Vývoj aplikací můžete urychlit stažením a instalací ukázkových aplikací ze [sítě Microsoft Developer Network](https://code.msdn.microsoft.com/). Můžete si také přečíst konkrétní technologii nebo programovací koncept stažením a prozkoumáním ukázkové sady pro tuto oblast.

## <a name="navigate-within-your-code"></a>Navigace v kódu

Můžete použít různé techniky k rychlejšímu vyhledání a přesunu do konkrétních umístění v kódu.

- **Záložek řádků kódu** Pomocí záložek můžete rychle přejít na konkrétní řádky kódu v souboru.

    Chcete-li nastavit záložku, na panelu nabídek vyberte možnost **upravit**  > **záložky**  > **Přepnout záložku**. Všechny záložky pro řešení můžete zobrazit v okně **záložky** . Další informace naleznete v tématu [Nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md).

- **Hledání definic symbolů v souboru**. Můžete hledat v rámci řešení a vyhledat definice symbolů a názvy souborů, ale výsledky hledání neobsahují obory názvů nebo místní proměnné.

   Chcete-li získat přístup k této funkci, v řádku nabídek vyberte možnost **upravit**  > **přejděte na**.

- **Projděte si celkovou strukturu kódu**. V **Průzkumník řešení**můžete vyhledávat a procházet třídy a jejich typy a členy v projektech. Můžete také vyhledat symboly, zobrazit hierarchii volání metody, najít odkazy na symboly a provádět další úkoly. Pokud zvolíte prvek kódu v **Průzkumník řešení**, otevře se přidružený soubor na kartě **Preview** a kurzor se přesune do prvku v souboru. Další informace naleznete v tématu [zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md).

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

   Stisknutím **kombinace kláves Ctrl** +**Q** můžete přejít přímo do vyhledávacího pole.

## <a name="debug-code"></a>Ladicí kód

Ladění může spotřebovat spoustu času, ale následující tipy vám pomůžou tento proces urychlit.

- **Otestujte stejnou stránku, aplikaci nebo web v různých prohlížečích**. Při ladění kódu můžete snadno přepínat mezi nainstalovanými webovými prohlížeči, včetně nástroje [Page Inspector (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), aniž byste museli otevřít dialogové okno **Procházet s** . Můžete použít seznam **cílů ladění** , který je na **standardním** panelu nástrojů vedle tlačítka **Spustit ladění** , a rychle ověřit, který prohlížeč používáte při ladění nebo prohlížení stránek.

    ![Vybrat možnosti ladění webového prohlížeče](../ide/media/webbrowserdropdowntoolbar.png)

- **Nastavte dočasné zarážky**. Můžete vytvořit dočasnou zarážku v aktuálním řádku kódu a spustit ladicí program současně. Po dosažení tohoto řádku kódu ladicí program přejde do režimu přerušení. Další informace najdete v tématu [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

    Chcete-li použít tuto funkci, zvolte klávesy **Ctrl** +**F10** nebo otevřete místní nabídku pro řádek kódu, na kterém chcete přerušit, a pak zvolte možnost **Spustit ke kurzoru**.

- **Přesunout bod spuštění během ladění**. Aktuální bod spuštění můžete přesunout do jiné části kódu a pak z tohoto bodu znovu spustit ladění. Tato technika je užitečná, pokud chcete ladit část kódu bez nutnosti znovu vytvořit všechny kroky, které jsou požadovány pro dosažení této části. Další informace najdete v tématu [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

     Chcete-li přesunout bod provádění, přetáhněte žlutou šipku na místo, kde chcete nastavit další příkaz ve stejném zdrojovém souboru, a pak stiskněte klávesu **F5** pro pokračování v ladění.

- **Zachytit informace o hodnotě pro proměnné**. Můžete přidat DataTip do proměnné v kódu a připnout ji tak, abyste měli přístup k poslední známé hodnotě pro proměnnou po dokončení ladění. Další informace najdete v tématu [zobrazení hodnot dat v tipech k datům](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Chcete-li přidat DataTip, musí být ladicí program v režimu pozastavení. Umístěte kurzor na proměnnou a pak zvolte tlačítko Připnout na DataTip, které se zobrazí. Při zastavení ladění se ve zdrojovém souboru vedle řádku kódu, který obsahuje proměnnou, zobrazí ikona modrého kódu PIN. Pokud navedete ukazatel na modrý kód PIN, zobrazí se hodnota proměnné z poslední relace ladění.

- **Vymažte okno Immediate**. Obsah [okamžitého okna](../ide/reference/immediate-window.md) můžete vymazat v době návrhu zadáním `>cls` nebo `>Edit.ClearAll`

     Další informace o dalších příkazech naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

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

- **Soubory, které často používáte, se budou zobrazovat v editoru**. Soubory můžete připnout na levou stranu na kartě, aby zůstaly viditelné bez ohledu na to, kolik souborů je v editoru otevřené.

   Chcete-li připnout soubor, zvolte kartu soubor a poté klikněte na tlačítko **Přepnout stav pinu** .

- **Přesuňte dokumenty a okna do jiných monitorů**. Pokud používáte více než jedno monitorování při vývoji aplikací, můžete snadněji pracovat na částech aplikace tím, že přesunete soubory, které jsou otevřeny v editoru, na jiný monitor. Můžete také přesunout okna nástrojů, jako je například okna ladicího programu, na jiný monitor a umístit kartu dokumentů a nástrojů společně a vytvořit "vory". Další informace naleznete v tématu [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Soubory můžete spravovat i snadněji tím, že vytvoříte jinou instanci **Průzkumník řešení** a přesunete ji do jiného monitoru. Chcete-li vytvořit jinou instanci **Průzkumník řešení**, otevřete místní nabídku v **Průzkumník řešení**a zvolte možnost **zobrazení nového Průzkumník řešení**.

- **Přizpůsobení písem, která se zobrazí v aplikaci Visual Studio**. U textu v integrovaném vývojovém prostředí můžete změnit řez písma, jeho velikost a barvu. Například můžete přizpůsobit barvu konkrétních prvků kódu v editoru a řez písma v oknech nástrojů nebo v celém rozhraní IDE. Další informace najdete v tématu [Postup: Změna písma a barev](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) a [Postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také:

- [Příspěvek na blogu tipy a triky pro Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Návod: Vytvoření jednoduché aplikace](../get-started/csharp/tutorial-wpf.md)
- [Tipy a triky pro usnadnění](../ide/reference/accessibility-tips-and-tricks.md)
