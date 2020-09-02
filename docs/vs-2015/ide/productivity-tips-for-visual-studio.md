---
title: Tipy k produktivitě | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5b2f2e2dc00eda388b2a2d075924fa72f9eff1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670303"
---
# <a name="productivity-tips-for-visual-studio"></a>Tipy pro vyšší produktivitu v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí těchto tipů můžete rychleji a efektivně psát, Procházet a ladit kód v aplikaci Visual Studio. Další informace o běžných klávesových zkratkách najdete v tématu [tipy a triky](../ide/tips-and-tricks-for-visual-studio.md). Úplnější seznam najdete v tématu [určení a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) a [výchozích klávesových zkratek](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Toto téma zahrnuje následující části:

 [Přístup k Visual Studio Tools](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Psaní kódu](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Navigace v kódu](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Rychlejší hledání položek](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Ladění kódu](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Správa souborů, panelů nástrojů a oken](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

## <a name="accessing-visual-studio-tools"></a><a name="BKMK_Access"></a> Přístup k Visual Studio Tools
 Pokud připnete připnutí na obrazovku Start nebo na hlavní panel, můžete pro Developer Command Prompt nebo jiný nástroj snadněji získat přístup.

1. Na obrazovce Start zadejte `Visual Studio Tools` a pak stiskněte klávesu ENTER.

2. V **Průzkumníku souborů**otevřete místní nabídku pro položku, kterou chcete:

    - Upozornění sestavení

    - Správce balíčků, který lze ladit

    - Developer Command Prompt pro VS2013

    - Microsoft Feedback Client 2013

    - VS2013 ARM Cross Tools Command Prompt

    - VS2013 x64 – příkazový řádek pro různé nástroje

    - VS2013 x64 Native Tools Command Prompt

    - VS2013 x86 Native Tools Command Prompt

3. Vyberte **připnout pro spuštění** nebo **připnutí na hlavní panel**.

## <a name="writing-code"></a><a name="BKMK_Writing"></a> Psaní kódu
 Vytvářejte kód rychleji pomocí následujících funkcí.

- **Použijte ukázkové aplikace**. Vývoj aplikací můžete urychlit stažením a instalací ukázkových aplikací z Galerie kódu na webu MSDN. Můžete si také přečíst konkrétní technologii nebo programovací koncept stažením a prozkoumáním ukázkové sady pro tuto oblast.

- **Použijte technologii IntelliSense**. Při zadávání kódu v editoru se zobrazí informace IntelliSense, jako jsou například členové seznamu, informace o parametrech, rychlé informace, signatura podpisu a hotové slovo. Tyto funkce podporují přibližnou shodu textu; například seznam výsledků pro seznam členů zahrnuje nejen položky, které začínají znaky, které jste zadali, ale také záznamy, které obsahují kombinaci znaků kdekoli v jejich jménu. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md).

- **Umožňuje změnit automatické vkládání možností IntelliSense při zadávání kódu**. Přepnutím technologie IntelliSense na režim návrhu můžete určit, zda jsou možnosti technologie IntelliSense vloženy pouze v případě, že je zvolíte explicitně.

     Chcete-li povolit režim návrhu, stiskněte klávesy CTRL + ALT + MEZERNÍK nebo na panelu nabídek vyberte možnost **Upravit**, **IntelliSense**, **Přepnout režim dokončení**.

- **Použijte fragmenty kódu**. Můžete použít předdefinované fragmenty nebo vytvořit vlastní fragmenty kódu.

     Chcete-li vložit fragment kódu, v panelu nabídek vyberte možnost **Upravit**, **IntelliSense**, **Vložit fragment kódu** nebo otevřete místní nabídku v souboru a vyberte možnost **Vložit fragment**. Další informace naleznete v tématu [fragmenty kódu](../ide/code-snippets.md).

- **Opravte chyby kódu jako vložené**. Inteligentní značky se zobrazí modře nebo červená pole pod řádkem kódu. Možnosti inteligentních značek můžete zobrazit tak, že přejdete na jedno z polí nebo umístíte kurzor na řádek kódu a vyberete kombinaci kláves CTRL +. (tečka) klíče.

     Modré čtverečky navrhují způsoby, jak opravit chyby ve vašem kódu.

     Obrázek 1: inteligentní značky chyby

     ![Chybové návrhy inteligentních značek](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     Červená pole navrhují způsoby refaktorování kódu.

     Obrázek 2: inteligentní značky refaktoringu

     ![Refaktorovat návrhy inteligentních značek](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

- **Zobrazit a upravit definici prvku kódu**. Můžete rychle zobrazit a upravit modul, ve kterém je definován prvek kódu, jako je například člen, proměnná nebo místní,.

     Chcete-li otevřít definici v překryvném okně, zvýrazněte prvek a zvolte klávesy Alt + F12 nebo otevřete místní nabídku pro prvek a pak zvolte možnost **Náhled definice**. Chcete-li otevřít definici v samostatném okně kódu, otevřete místní nabídku pro prvek a zvolte možnost **Přejít k definici**.

## <a name="navigating-within-your-code"></a><a name="BKMK_Navigating"></a> Navigace v kódu
 Můžete použít různé techniky k rychlejšímu vyhledání a přesunu do konkrétních umístění v kódu.

- **Záložek řádků kódu** Pomocí záložek můžete rychle přejít na konkrétní řádky kódu v souboru.

     Chcete-li nastavit záložku, na panelu nabídek vyberte možnost **Upravit**, **záložky**, **Přepnout záložku**. Všechny záložky pro řešení můžete zobrazit v okně **záložky** . Další informace naleznete v tématu [Nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md).

- **Hledání definic symbolů v souboru**. Můžete hledat v rámci řešení a vyhledat definice symbolů a názvy souborů, ale výsledky hledání neobsahují obory názvů nebo místní proměnné.

     Chcete-li získat přístup k této funkci, v řádku nabídek klikněte na položku **Upravit**, **Přejít na**.

- **Projděte si celkovou strukturu kódu**. V **Průzkumník řešení**můžete vyhledávat a procházet třídy a jejich typy a členy v projektech. Můžete také vyhledat symboly, zobrazit hierarchii volání metody, najít odkazy na symboly a provádět další úkoly. Pokud zvolíte prvek kódu v **Průzkumník řešení**, otevře se přidružený soubor na kartě **Preview** a kurzor se přesune do prvku v souboru. Další informace naleznete v tématu [zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md).

## <a name="finding-items-faster"></a><a name="BKMK_Finding"></a> Rychlejší hledání položek
 Můžete hledat v integrovaném vývojovém prostředí (IDE) pro příkazy, soubory a možnosti, kromě filtrování obsahu oken nástrojů, aby se zobrazily pouze relevantní informace pro aktuální úkol.

- **Filtrování obsahu oken nástrojů** Můžete hledat v obsahu mnoha oken nástrojů, jako je například **Sada nástrojů**, okno **vlastnosti** a **Průzkumník řešení**, ale zobrazit pouze položky, jejichž názvy obsahují znaky, které zadáte.

- **Zobrazí jenom chyby, které chcete adresovat**. Pokud zvolíte tlačítko **Filtr** na panelu nástrojů **Seznam chyb** , můžete snížit počet chyb, které se zobrazí v okně **Seznam chyb** . Můžete zobrazit pouze chyby v souborech, které jsou otevřeny v editoru, pouze chyby v aktuálním souboru nebo pouze chyby v aktuálním projektu. Můžete také vyhledat konkrétní chyby v okně Seznam chyb.

- **Najde dialogová okna, příkazy nabídky a možnosti**. V poli [Snadné spuštění, prostředí, dialogové okno Možnosti](../ide/reference/quick-launch-environment-options-dialog-box.md) zadejte klíčová slova nebo fráze pro položky, které se pokoušíte najít. Například následující možnosti se zobrazí, pokud zadáte `new project` :

     Obrázek 3: seznam výsledků snadného spuštění pro `new project`

     ![Výsledky snadného spuštění pro nový projekt](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     **Rychlé spuštění** zobrazuje odkazy na dialogové okno **Nový projekt** , dialogové okno **Přidat novou položku** a stránku projekty a řešení v dialogovém okně **Možnosti** , mimo jiné. Výsledky snadného spuštění můžou také zahrnovat soubory projektu a okna nástrojů.

## <a name="debugging-code"></a><a name="BKMK_Debugging"></a> Ladění kódu
 Ladění může spotřebovat spoustu času, ale následující tipy vám pomůžou tento proces urychlit.

- **Otestujte stejnou stránku, aplikaci nebo web v různých prohlížečích**. Při ladění kódu můžete snadno přepínat mezi nainstalovanými webovými prohlížeči, včetně nástroje [Page Inspector (Visual Studio)](https://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209), aniž byste museli otevřít dialogové okno **Procházet s** . Můžete použít seznam **cílů ladění** , který je na **standardním** panelu nástrojů vedle tlačítka **Spustit ladění** , a rychle ověřit, který prohlížeč používáte při ladění nebo prohlížení stránek.

     ![Vybrat možnosti ladění webového prohlížeče](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

- **Nastavte dočasné zarážky**. Můžete vytvořit dočasnou zarážku v aktuálním řádku kódu a spustit ladicí program současně. Po dosažení tohoto řádku kódu ladicí program přejde do režimu přerušení. Další informace naleznete v tématu [navigace prostřednictvím kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

     Chcete-li použít tuto funkci, zvolte klávesovou zkratku CTRL + F10 nebo otevřete místní nabídku pro řádek kódu, na kterém chcete přerušit, a pak zvolte možnost **Spustit ke kurzoru**.

- **Přesunout bod spuštění během ladění**. Aktuální bod spuštění můžete přesunout do jiné části kódu a pak z tohoto bodu znovu spustit ladění. Tato technika je užitečná, pokud chcete ladit část kódu bez nutnosti znovu vytvořit všechny kroky, které jsou požadovány pro dosažení této části. Další informace naleznete v tématu [navigace prostřednictvím kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

     Chcete-li přesunout bod provádění, přetáhněte žlutou šipku na místo, kde chcete nastavit další příkaz ve stejném zdrojovém souboru, a pak stiskněte klávesu F5 pro pokračování v ladění.

- **Zachytit informace o hodnotě pro proměnné**. Můžete přidat DataTip do proměnné v kódu a připnout ji tak, abyste měli přístup k poslední známé hodnotě pro proměnnou po dokončení ladění. Další informace najdete v tématu [zobrazení hodnot dat v tipech k datům](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Chcete-li přidat DataTip, musí být ladicí program v režimu pozastavení. Umístěte kurzor na proměnnou a pak zvolte tlačítko Připnout na DataTip, které se zobrazí. Při zastavení ladění se ve zdrojovém souboru vedle řádku kódu, který obsahuje proměnnou, zobrazí ikona modrého kódu PIN. Pokud navedete ukazatel na modrý kód PIN, zobrazí se hodnota proměnné z poslední relace ladění.

- **Vymažte okno Immediate**. Obsah [okamžitého okna](../ide/reference/immediate-window.md) můžete vymazat v době návrhu zadáním `>cls` nebo `>Edit.ClearAll`

     Další informace o dalších příkazech naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

## <a name="managing-files-toolbars-and-windows"></a><a name="BKMK_Managing"></a> Správa souborů, panelů nástrojů a oken
 V jednom okamžiku můžete pracovat v několika souborech kódu a při vývoji aplikace se pohybovat mezi několika okny nástrojů. Pomocí následujících tipů můžete dál organizovat.

- **Soubory, které často používáte, se budou zobrazovat v editoru**. Soubory můžete připnout na levou stranu na kartě, aby zůstaly viditelné bez ohledu na to, kolik souborů je v editoru otevřené.

     Chcete-li připnout soubor, zvolte kartu soubor a poté klikněte na tlačítko **Přepnout stav pinu** .

- **Přesuňte dokumenty a okna do jiných monitorů**. Pokud používáte více než jedno monitorování při vývoji aplikací, můžete snadněji pracovat na částech aplikace tím, že přesunete soubory, které jsou otevřeny v editoru, na jiný monitor. Můžete také přesunout okna nástrojů, jako je například okna ladicího programu, na jiný monitor a umístit kartu dokumentů a nástrojů společně a vytvořit "vory". Další informace naleznete v tématu [How to: uspořádávat and Dock Windows](../misc/how-to-arrange-and-dock-windows.md).

     Soubory můžete spravovat i snadněji tím, že vytvoříte jinou instanci **Průzkumník řešení** a přesunete ji do jiného monitoru. Chcete-li vytvořit jinou instanci **Průzkumník řešení**, otevřete místní nabídku v **Průzkumník řešení**a zvolte možnost **zobrazení nového Průzkumník řešení**.

- **Přizpůsobení písem, která se zobrazí v aplikaci Visual Studio**. U textu v integrovaném vývojovém prostředí můžete změnit řez písma, jeho velikost a barvu. Například můžete přizpůsobit barvu konkrétních prvků kódu v editoru a řez písma v oknech nástrojů nebo v celém rozhraní IDE. Další informace najdete v tématu [Postup: Změna písma a barev](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) a [Postupy: Změna písma a barev v editoru](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Viz také
 [Výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [Návod: vytvoření jednoduchých tipů k](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [usnadnění přístupu k aplikacím a triky](../ide/reference/accessibility-tips-and-tricks.md)
