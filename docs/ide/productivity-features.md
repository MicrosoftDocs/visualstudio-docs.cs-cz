---
title: Tipy pro vyšší produktivitu
ms.date: 2/21/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd85565ee573015737ab815258914bec89ab9369
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596980"
---
# <a name="productivity-tips-for-visual-studio"></a>Tipy pro vyšší produktivitu sady Visual Studio

V tomto článku jsou popsány tipy pro funkce sady Visual Studio, které vám pomůžou rychleji a efektivně psát, Procházet a ladit kód.

Informace o užitečných klávesových zkratkách najdete v tématu věnovaném [zástupcům produktivity](../ide/productivity-shortcuts.md). Úplný seznam klávesových zkratek najdete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="write-code"></a>Psaní kódu

Napište kód rychleji s využitím následující funkce.

- **Pomocí příkazů pohodlí**. Visual Studio obsahuje různé příkazy můžete provádět běžné úlohy úprav rychleji. Můžete například zvolit příkaz pro snadné duplikování řádku kódu bez nutnosti jeho zkopírování, přemístění kurzoru a vložení. Zvolte **upravit** > **duplicitní** nebo stiskněte klávesu **Ctrl**+**E**,**V**. Výběr textu můžete také rychle rozbalit nebo zúžit výběrem možnosti **upravit** > **Upřesnit** > **rozšířit výběr** nebo **upravit** > **pokročilý** **výběr kontraktu** > nebo stisknutím klávesy **SHIFT**+**ALT**+ **=** nebo **SHIFT**+**ALT**+ **-** .

- **Použijte technologii IntelliSense**. Při zadávání kódu v editoru, zobrazí se informace technologie IntelliSense, jako je například seznam členů, informace o parametrech, rychlé informace, pomoc při podpisu a dokončit slovo. Tyto funkce podporují fuzzy vyhledávání textu. například seznam výsledků pro seznam členů obsahuje nejen pouze položky, které začínají znaky, zda jste zadali, ale také záznamy, které obsahují kombinaci znaků kdekoli v jejich názvy. Další informace najdete v tématu [použití IntelliSense](../ide/using-intellisense.md).

- **Změna automatického vkládání technologie možnosti technologie IntelliSense při vkládání kódu**. Přepnutím technologie IntelliSense do režimu návrhu, můžete určit, aby možnosti technologie IntelliSense byly vloženy pouze po jejich explicitním výběru.

     Povolení režimu návrhu, zvolte **Ctrl**+**Alt**+**MEZERNÍK** klíče, nebo na panelu nabídek zvolte **upravit**  >  **IntelliSense** > **přepnout režim dokončení**.

- **Používání fragmentů kódu**. Můžete použít předdefinované fragmenty kódu nebo vytvořit vlastní fragmenty kódu.

     Chcete-li vložit fragment kódu na řádku nabídek zvolte **upravit** > **IntelliSense** > **Vložit fragment** nebo **obklopit fragmentem**, nebo v souboru otevřete místní nabídku a zvolte **fragment** > **Vložit fragment** nebo **obklopit fragmentem**. Další informace najdete v tématu [fragmenty kódu](../ide/code-snippets.md).

- **Oprava chyby vložený kód**. Rychlé akce vám umožní snadno Refaktorujte, generovat nebo jinak upravit kód pomocí jedné akce. Tyto akce lze aplikovat pomocí šroubovák ![šroubovák ikonu](media/screwdriver-icon.png) nebo žárovky ![ikonou žárovky](media/light-bulb-icon.png) ikony, nebo stisknutím klávesy **Alt** +  **Zadejte** nebo **Ctrl**+ **.** Když je ukazatel myši na příslušný řádek kódu. Zobrazit [rychlé akce](quick-actions.md) Další informace.

- **Zobrazit a upravit definici prvku kódu**. Můžete rychle zobrazit a upravit modul, ve kterém je definován prvek kódu, jako je například člen, proměnná nebo místní.

    Chcete-li otevřít definici v překryvném okně, zvýrazněte element a klikněte na tlačítko **Alt**+**F12** klíče, nebo otevřete místní nabídku pro prvek a pak zvolte **operace Peek Definice**. Pro otevření definice v samostatném okně s kódem, otevřete místní nabídku pro prvek a klikněte na tlačítko **přejít k definici**.

- **Použití ukázkových aplikací**. Můžete urychlit vývoj aplikací stažením a instalací ukázkové aplikace od [Microsoft Developer Network](https://code.msdn.microsoft.com/). Určitou technologii nebo programovací koncept můžete také naučit stáhnutím a Prozkoumáním balíčku ukázek pro tuto oblast.

## <a name="navigate-within-your-code"></a>Navigace v kódu

Různé techniky slouží k vyhledání a přesunutí na konkrétní místo v kódu rychleji.

- **Záložka pro řádky kódu**. Pomocí záložek lze rychle přejít na konkrétní řádky kódu v souboru.

    Chcete-li nastavit záložky, na panelu nabídek, zvolte **upravit** > **záložky** > **Přepnout záložku**. Můžete zobrazit všechny záložky řešení v **záložky** okna. Další informace najdete v tématu [nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md).

- **Vyhledání definice symbolů v souboru**. V rámci řešení lze vyhledat definice symbolů a názvy souborů, ale výsledky hledání neobsahují obory názvů ani místní proměnné.

   Chcete-li použít tuto funkci na řádku nabídek zvolte **upravit** > **přejít na**.

- **Projděte celkovou strukturu kódu**. V **Průzkumníka řešení**, můžete vyhledat a procházet třídy a jejich typy a členy v projektech. Můžete také hledat symboly, zobrazit hierarchii volání metod, najít odkazy na symboly a provádět další úlohy. Pokud se rozhodnete prvek kódu v **Průzkumníka řešení**, související soubor se otevře v **ve verzi Preview** kartu a kurzor se přesune k prvku v souboru. Další informace najdete v tématu [zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md).

## <a name="find-items-faster"></a>Hledání položek rychleji

Můžete hledat v prostředí IDE pro příkazy, soubory a možnosti, kromě filtrování obsahu okna nástrojů, chcete-li zobrazit pouze relevantní informace pro aktuální úlohu.

- **Filtrujte obsah okna nástrojů**. Můžete vyhledávat v obsahu mnoha nástrojových oken, například **nástrojů**, **vlastnosti** okně a **Průzkumníka řešení**, ale zobrazit jenom položky, jejichž názvy obsahovat znaky, které zadáte.

- **Zobrazit pouze chyby, které chcete na adresu**. Pokud se rozhodnete **filtr** tlačítko **seznam chyb** nástrojů, můžete snížit počet chyb, které se zobrazují v **seznam chyb** okno. Můžete zobrazit pouze chyby v souborech, které jsou otevřeny v editoru, pouze chyby v aktuálním souboru, nebo pouze chyby v aktuálním projektu. Můžete také hledat v rámci **seznam chyb** okno najít konkrétní chyby.

- **Najděte dialogová okna, příkazy nabídky, možnosti a další**. Do vyhledávacího pole zadejte klíčová slova nebo fráze pro položky, které se pokoušíte najít. Například následující možnosti se zobrazí, pokud zadáte **Nový projekt**:

   ::: moniker range="vs-2017"

   ![Rychlé spuštění výsledky pro "nový projekt.](../ide/media/productivity_quicklaunch.png)

   **Rychlé spuštění** zobrazuje odkazy na vytvoření nového projektu, pro přidání nové položky do projektu a na stránku **projekty a řešení** v dialogovém okně **Možnosti** mimo jiné. Výsledky hledání mohou také zahrnovat soubory projektu a okna nástrojů.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Výsledky hledání pro nový projekt](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Stisknutím **kombinace kláves Ctrl**+**Q** můžete přejít přímo do vyhledávacího pole.

## <a name="debug-code"></a>Ladění kódu

Ladění může spotřebovat spoustu času, ale následující tipy vám pomůžou zrychlit proces.

- **Testování stejnou stránku, aplikaci nebo web v různých prohlížečích**. Při ladění kódu můžete snadno přepínat mezi nainstalovanými webovými prohlížeči, včetně [nástroj Page Inspector (Visual Studio)](https://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), aniž byste museli otevřít **procházet s** dialogové okno. Můžete použít **cíl ladění** seznam, který se nachází na **standardní** nástrojů vedle položky **spustit ladění** tlačítko pro rychlé kontrole aktuálně používaného ladění webového prohlížeče nebo zobrazení stránek.

    ![Vyberte možnosti ladění webového prohlížeče](../ide/media/webbrowserdropdowntoolbar.png)

- **Nastavení dočasných zarážek**. Můžete vytvořit dočasnou zarážku na aktuálním řádku kódu a zároveň spustit ladicí program. Při dosažení tohoto řádku přejde ladicí program do režimu přerušení. Další informace najdete v tématu [Navigovat prostřednictvím kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).

    Chcete-li tuto funkci použít, zvolte **Ctrl**+**F10** klíče, nebo otevřete místní nabídku pro řádek kódu, na kterém chcete přerušit a klikněte na tlačítko **provést do pozice kurzoru** .

- **Přesuňte bod provádění během ladění**. Můžete přesunout do jiné části kódu aktuální bod provádění a pak znovu spusťte ladění od tohoto okamžiku. Tato technika je užitečná, pokud chcete ladit sekci kódu bez nutnosti provádět všechny kroky, které jsou potřeba k dosažení této části. Další informace najdete v tématu [Navigovat prostřednictvím kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).

     Přesunout bod spuštění, přetáhněte žlutou šipku do umístění, ve které chcete nastavit další příkaz ve stejném zdrojovém souboru a klikněte na tlačítko **F5** klíč pro pokračování v ladění.

- **Zachycení informací o hodnotách proměnných**. Můžete přidat DataTip proměnné ve vašem kódu a připnout ho tak, aby po dokončení ladění můžete přistupovat k poslední známé hodnotě proměnné. Další informace najdete v tématu [zobrazení hodnot dat v datových tipech](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Pro přidání DataTip musí být ladicí program v režimu pozastavení. Umístěte kurzor na proměnnou a pak klikněte na tlačítko připnout na, které se zobrazí. Při zastavení ladění, zobrazí se ikona s modrým ve zdrojovém souboru vedle řádku kódu, který obsahuje proměnné. Pokud přejděte myší na modrý špendlík se zobrazí hodnota proměnné z poslední relace ladění.

- **Vymazání příkazového podokna**. Můžete vymazat obsah [podokna](../ide/reference/immediate-window.md) v době návrhu zadáním `>cls` nebo `>Edit.ClearAll`

     Další informace o dalších příkazech najdete v tématu [aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

## <a name="access-visual-studio-tools"></a>Přístup k nástrojům Visual Studio

Můžete rychle získat Developer Command Prompt nebo jiného nástroje Visual Studio, jej můžete připnout do nabídky Start nebo na hlavním panelu.

::: moniker range="vs-2017"

1. V Průzkumníku Windows přejděte do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual studia 2017 \ Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. V Průzkumníku Windows přejděte do *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual studia 2019 \ Visual Studio Tools*.

::: moniker-end

2. Klikněte pravým tlačítkem myši nebo otevřete kontextovou nabídku pro **Developer Command Prompt**a klikněte na tlačítko **připnout na Start** nebo **připnout na hlavní panel**.

## <a name="manage-files-toolbars-and-windows"></a>Správa souborů, panelů nástrojů a windows

V jednu chvíli můžete být práce ve více souborech s kódem a budete přecházet mezi několika okny nástrojů při vývoji aplikace. Pomocí následujících tipů můžete dál organizovat:

- **Soubory, které často používají ve viditelném stavu v editoru**. Dobře, takže zůstávají viditelné bez ohledu na to, kolik souborů je otevřen v editoru můžete připnout soubory k levé straně karty.

   Pokud chcete připnout soubor, zvolte kartu Soubor a klikněte na tlačítko **změnit stav Připnutí** tlačítko.

- **Přesuňte dokumenty a okna do jiných monitorů**. Pokud používáte více než jeden monitor při vývoji aplikací, můžete pracovat na částech aplikace snadněji přesunutím souborů, které jsou otevřeny v editoru na jiný monitor. Můžete také přesunout ukotvení okna nástrojů, jako je například okna ladicího programu na jinou kartu a sledování dokumentů a nástrojů systému windows dohromady a vytvoří "řady." Další informace najdete v tématu [přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Můžete také spravovat soubory snadněji tak, že vytvoříte jiná instance **Průzkumníka řešení** a jeho přesunutím na jiný monitor. K vytvoření další instance okna **Průzkumníka řešení**, otevřete místní nabídku v **Průzkumníka řešení**a klikněte na tlačítko **nové zobrazení Průzkumníka řešení**.

- **Přizpůsobte písmo zobrazené v sadě Visual Studio**. Můžete změnit vzhled písma, velikost a barvu, která se používá pro text v integrovaném vývojovém prostředí. Například lze upravit barvu konkrétních prvků kódu v editoru a řez písma v oknech nástrojů nebo v celém rozhraní IDE. Další informace najdete v tématu [postupy: Změna písma a barev](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) a [postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také:

- [Příspěvek na blogu tipy a triky pro Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Návod: Vytvoření jednoduché aplikace](../get-started/csharp/tutorial-wpf.md)
- [A tipy k přístupnosti](../ide/reference/accessibility-tips-and-tricks.md)
