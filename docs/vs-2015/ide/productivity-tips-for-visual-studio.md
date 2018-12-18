---
title: Tipy pro vyšší produktivitu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: db89bda465d1a4fc4da1b3066858b270ce50c5bb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051027"
---
# <a name="productivity-tips-for-visual-studio"></a>Tipy pro vyšší produktivitu v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí těchto tipů můžete rychleji a efektivněji psaní, navigace a ladění kódu v sadě Visual Studio. Další informace o běžných klávesových zkratkách naleznete v tématu [tipy a triky](../ide/tips-and-tricks-for-visual-studio.md). Úplný seznam najdete v tématu [určení a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) a [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Toto téma obsahuje následující oddíly:

 [Přístup k Visual Studio Tools](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Psaní kódu](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Navigace v kódu](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Rychlejší vyhledávání položek](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Ladění kódu](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Správa souborů, panelů nástrojů a Windows](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

##  <a name="BKMK_Access"></a> Přístup k Visual Studio Tools
 Developer Command Prompt nebo jiného nástroje můžete přistupovat mnohem snazší v případě, že jej můžete připnout na úvodní obrazovce nebo na hlavním panelu.

1.  Na obrazovce Start zadejte `Visual Studio Tools`a potom stiskněte klávesu Enter.

2.  V **Průzkumníka souborů**, otevřete místní nabídku pro položku, kterou požadujete:

    -   Upozornění sestavení

    -   Správce Laditelného balíku

    -   Developer Command Prompt for VS2013

    -   Microsoft Feedback Client 2013

    -   VS2013 ARM Cross Tools Command Prompt

    -   VS2013 x64 Cross Tools Command Prompt

    -   VS2013 x64 Native Tools Command Prompt

    -   VS2013 x86 Native Tools Command Prompt

3.  Zvolte **připnout na Start** nebo **připnout na hlavní panel**.

##  <a name="BKMK_Writing"></a> Psaní kódu
 Napište kód rychleji s využitím následující funkce.

-   **Použití ukázkových aplikací**. Stažením a instalací ukázkové aplikace z Galerie kódu na webu MSDN můžete urychlit vývoj aplikací. Určitou technologii nebo programovací koncept můžete také naučit stáhnutím a Prozkoumáním balíčku ukázek pro tuto oblast.

-   **Použijte technologii IntelliSense**. Při zadávání kódu v editoru, zobrazí se informace technologie IntelliSense, jako je například seznam členů, informace o parametrech, rychlé informace, pomoc při podpisu a dokončit slovo. Tyto funkce podporují fuzzy vyhledávání textu. například seznam výsledků pro seznam členů obsahuje nejen pouze položky, které začínají znaky, zda jste zadali, ale také záznamy, které obsahují kombinaci znaků kdekoli v jejich názvy. Další informace najdete v tématu [pomocí technologie IntelliSense](../ide/using-intellisense.md).

-   **Změna automatického vkládání technologie možnosti technologie IntelliSense při vkládání kódu**. Přepnutím technologie IntelliSense do režimu návrhu, můžete určit, aby možnosti technologie IntelliSense byly vloženy pouze po jejich explicitním výběru.

     Povolení režimu návrhu, zvolte klávesy Ctrl + Alt + mezerník klíče, nebo na panelu nabídek zvolte **upravit**, **IntelliSense**, **přepnout režim dokončení**.

-   **Používání fragmentů kódu**. Můžete použít předdefinované fragmenty kódu nebo vytvořit vlastní fragmenty kódu.

     Chcete-li vložit fragment kódu na řádku nabídek zvolte **upravit**, **IntelliSense**, **Vložit fragment** nebo v souboru otevřete místní nabídku a zvolte **Vložit fragment** . Další informace najdete v tématu [fragmenty kódu](../ide/code-snippets.md).

-   **Oprava chyby vložený kód**. Inteligentní značky se objeví jako modrá nebo červená pole pod řádkem kódu. Možnosti inteligentních značek lze zobrazit najetím myší na jednu z polí nebo umístěním kurzoru do řádku kódu a výběrem Ctrl +. (tečka).

     Modrá pole navrhují způsoby, jak opravit chyby ve vašem kódu.

     Obrázek 1: Inteligentní značky chyb

     ![Chyba inteligentních značek návrhy](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     Červená pole doporučují způsoby, jak kód Refaktorovat.

     Obrázek 2: Inteligentní značky refaktoringu

     ![Refaktorujte inteligentních značek návrhy](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

-   **Zobrazit a upravit definici prvku kódu**. Můžete rychle zobrazit a upravit modul, ve kterém je definován prvek kódu, jako je například člen, proměnná nebo místní.

     Chcete-li otevřít definici v překryvném okně, zvýrazněte element a pak zvolte klávesy Alt + F12 nebo otevřete místní nabídku pro prvek a klikněte na tlačítko **definice operace Peek**. Pro otevření definice v samostatném okně s kódem, otevřete místní nabídku pro prvek a klikněte na tlačítko **přejít k definici**.

##  <a name="BKMK_Navigating"></a> Navigace v kódu
 Různé techniky slouží k vyhledání a přesunutí na konkrétní místo v kódu rychleji.

-   **Záložka pro řádky kódu**. Pomocí záložek lze rychle přejít na konkrétní řádky kódu v souboru.

     Chcete-li nastavit záložky, na panelu nabídek, zvolte **upravit**, **záložky**, **Přepnout záložku**. Můžete zobrazit všechny záložky řešení v **záložky** okna. Další informace najdete v tématu [nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md).

-   **Vyhledání definice symbolů v souboru**. V rámci řešení lze vyhledat definice symbolů a názvy souborů, ale výsledky hledání neobsahují obory názvů ani místní proměnné.

     Chcete-li použít tuto funkci na řádku nabídek zvolte **upravit**, **přejít na**.

-   **Projděte celkovou strukturu kódu**. V **Průzkumníka řešení**, můžete vyhledat a procházet třídy a jejich typy a členy v projektech. Můžete také hledat symboly, zobrazit hierarchii volání metod, najít odkazy na symboly a provádět další úlohy. Pokud se rozhodnete prvek kódu v **Průzkumníka řešení**, související soubor se otevře v **ve verzi Preview** kartu a kurzor se přesune k prvku v souboru. Další informace najdete v tématu [zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md).

##  <a name="BKMK_Finding"></a> Rychlejší vyhledávání položek
 Můžete hledat v prostředí IDE pro příkazy, soubory a možnosti, kromě filtrování obsahu okna nástrojů, chcete-li zobrazit pouze relevantní informace pro aktuální úlohu.

-   **Filtrujte obsah okna nástrojů**. Můžete vyhledávat v obsahu mnoha nástrojových oken, například **nástrojů**, **vlastnosti** okně a **Průzkumníka řešení**, ale zobrazit jenom položky, jejichž názvy obsahovat znaky, které zadáte.

-   **Zobrazit pouze chyby, které chcete na adresu**. Pokud se rozhodnete **filtr** tlačítko **seznam chyb** nástrojů, můžete snížit počet chyb, které se zobrazují v **seznam chyb** okno. Můžete zobrazit pouze chyby v souborech, které jsou otevřeny v editoru, pouze chyby v aktuálním souboru, nebo pouze chyby v aktuálním projektu. Můžete také hledat v rámci okna Seznam chyb pro určité chyby.

-   **Vyhledejte dialogová okna, příkazy nabídky a možnosti**. V [dialogové okno Snadné spuštění, prostředí, možnosti](../ide/reference/quick-launch-environment-options-dialog-box.md) zadejte klíčová slova nebo fráze pro položky, které se snažíte najít. Například se zobrazí následující možnosti, pokud zadáte `new project`:

     Obrázek 3: Seznam výsledků rychlého spuštění pro `new project`

     ![Rychlé spuštění výsledky pro "projekt"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     **Snadné spuštění** zobrazuje odkazy na **nový projekt** dialogovém okně **přidat novou položku** dialogové okno a stránku projekty a řešení **možnosti** dialogového okna pole, mimo jiné. Rychlé výsledky spuštění můžete také obsahovat soubory projektů a okna nástrojů.

##  <a name="BKMK_Debugging"></a> Ladění kódu
 Ladění může spotřebovat spoustu času, ale následující tipy vám pomůžou zrychlit proces.

-   **Testování stejnou stránku, aplikaci nebo web v různých prohlížečích**. Při ladění kódu můžete snadno přepínat mezi nainstalovanými webovými prohlížeči, včetně [nástroj Page Inspector (Visual Studio)](http://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209), aniž byste museli otevřít **procházet s** dialogové okno. Můžete použít **cíl ladění** seznam, který se nachází na **standardní** nástrojů vedle položky **spustit ladění** tlačítko pro rychlé kontrole aktuálně používaného ladění webového prohlížeče nebo zobrazení stránek.

     ![Vyberte možnosti ladění webového prohlížeče](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

-   **Nastavení dočasných zarážek**. Můžete vytvořit dočasnou zarážku na aktuálním řádku kódu a zároveň spustit ladicí program. Při dosažení tohoto řádku přejde ladicí program do režimu přerušení. Další informace najdete v tématu [procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).

     Chcete-li tuto funkci použít, zvolte klávesy Ctrl + F10 nebo otevřením místní nabídku pro řádek kódu, na kterém chcete přerušit a klikněte na tlačítko **provést do pozice kurzoru**.

-   **Přesuňte bod provádění během ladění**. Můžete přesunout do jiné části kódu aktuální bod provádění a pak znovu spusťte ladění od tohoto okamžiku. Tato technika je užitečná, pokud chcete ladit sekci kódu bez nutnosti provádět všechny kroky, které jsou potřeba k dosažení této části. Další informace najdete v tématu [procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).

     Přesunout bod spuštění, přetáhněte žlutou šipku do umístění, ve které chcete nastavit další příkaz ve stejném zdrojovém souboru a pak zvolte klávesu F5 pro pokračování v ladění.

-   **Zachycení informací o hodnotách proměnných**. Můžete přidat DataTip proměnné ve vašem kódu a připnout ho tak, aby po dokončení ladění můžete přistupovat k poslední známé hodnotě proměnné. Další informace najdete v tématu [zobrazení hodnot dat v datových tipech](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Pro přidání DataTip musí být ladicí program v režimu pozastavení. Umístěte kurzor na proměnnou a pak klikněte na tlačítko připnout na, které se zobrazí. Při zastavení ladění, zobrazí se ikona s modrým ve zdrojovém souboru vedle řádku kódu, který obsahuje proměnné. Pokud přejděte myší na modrý špendlík se zobrazí hodnota proměnné z poslední relace ladění.

-   **Vymazání příkazového podokna**. Můžete vymazat obsah [podokna](../ide/reference/immediate-window.md) v době návrhu zadáním `>cls` nebo `>Edit.ClearAll`

     Další informace o dalších příkazech najdete v tématu [aliasy příkazů aplikace Visual Studio](../ide/reference/visual-studio-command-aliases.md).

##  <a name="BKMK_Managing"></a> Správa souborů, panelů nástrojů a Windows
 V jednu chvíli můžete být práce ve více souborech s kódem a budete přecházet mezi několika okny nástrojů při vývoji aplikace. Abyste mohli uspořádané pomocí následujících tipů.

-   **Soubory, které často používají ve viditelném stavu v editoru**. Dobře, takže zůstávají viditelné bez ohledu na to, kolik souborů je otevřen v editoru můžete připnout soubory k levé straně karty.

     Pokud chcete připnout soubor, zvolte kartu Soubor a klikněte na tlačítko **změnit stav Připnutí** tlačítko.

-   **Přesuňte dokumenty a okna do jiných monitorů**. Pokud používáte více než jeden monitor při vývoji aplikací, můžete pracovat na částech aplikace snadněji přesunutím souborů, které jsou otevřeny v editoru na jiný monitor. Můžete také přesunout ukotvení okna nástrojů, jako je například okna ladicího programu na jinou kartu a sledování dokumentů a nástrojů systému windows dohromady a vytvoří "řady." Další informace najdete v tématu [postupy: uspořádání a ukotvit Windows](../misc/how-to-arrange-and-dock-windows.md).

     Můžete také spravovat soubory snadněji tak, že vytvoříte jiná instance **Průzkumníka řešení** a jeho přesunutím na jiný monitor. K vytvoření další instance okna **Průzkumníka řešení**, otevřete místní nabídku v **Průzkumníka řešení**a klikněte na tlačítko **nové zobrazení Průzkumníka řešení**.

-   **Přizpůsobte písmo zobrazené v sadě Visual Studio**. Můžete změnit vzhled písma, velikost a barvu, která se používá pro text v integrovaném vývojovém prostředí. Například lze upravit barvu konkrétních prvků kódu v editoru a řez písma v oknech nástrojů nebo v celém rozhraní IDE. Další informace najdete v tématu [postupy: Změna písma a barvy](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) a [postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také
 [Výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [návod: vytvoření jednoduché aplikace](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [tipy k usnadnění přístupu a Triky](../ide/reference/accessibility-tips-and-tricks.md)
