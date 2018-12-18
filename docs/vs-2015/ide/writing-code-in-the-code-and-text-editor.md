---
title: Psaní kódu v editoru kódu a textový Editor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd12cfee50db7dd085fee6c0591dfff3f579e640
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838683"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Psaní kódu v editoru kódu a textovém editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Editor sady Visual Studio poskytuje mnoho funkcí, které usnadňují zápis a správu kódu. Můžete rozbalit nebo sbalit různé bloky kódu pomocí osnovy. Další informace o kódu, který používáte pomocí technologie IntelliSense, **prohlížeče objektů**a hierarchii volání. Můžete přejít dovnitř kódu pomocí funkcí **přejít na**, **přejít k definici**, a **najít všechny odkazy**. Můžete vložit bloky kódu pomocí fragmentů kódu a může generovat kód pomocí funkcí **Generovat z využití**. Pokud jste nikdy nepoužívali před editoru sady Visual Studio 2015, přečtěte si téma [úpravy kódu](https://www.visualstudio.com/features/ide-vs) a získejte rychlý přehled.  

 Zobrazí se váš kód v několika různými způsoby. Zobrazení tříd řešení zobrazíte můžete otevřít **zobrazení tříd** okno nebo rozbalte uzly v **Průzkumníka řešení** v části soubory tříd.  

 Můžete vyhledat a nahradit text pro jeden nebo více souborů. Další informace najdete v tématu [hledání a nahrazení textu](../ide/finding-and-replacing-text.md). Pokud používáte regulární výrazy, Všimněte si, že vyhledání a nahrazení nyní pomocí regulárních výrazů .NET. Další informace najdete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 Různé jazyky Visual Studio nabízí různé sady funkcí a v některých případech se funkce chovají odlišně v různých jazycích. Mnohé z těchto rozdílů jsou uvedeny v popisech funkcí, ale pro další informace najdete v částech na konkrétní jazyky sady Visual Studio.  

> [!IMPORTANT]
>  Edice sady Visual Studio a nastavení, které používáte, může ovlivnit funkce v integrovaném vývojovém prostředí. Mohou se lišit od těch popsaných v tomto tématu.  

## <a name="editor-features"></a>Funkce editoru  

|||  
|-|-|  
|Barevné zvýrazňování syntaxe|Některé prvky syntaxe kódu a kódu souborů jsou různě barevně odlišeny abychom je odlišili. Například klíčová slova (například `using` v jazyce C# a `Imports` v jazyce Visual Basic) jsou jednu barvu, ale typy (například `Console` a `Uri`) mají jinou barvu. Ostatní prvky syntaxe jsou také obarveny, jako je například řetězcové literály a komentáře. C++ používá barvy k rozlišení mezi typy, výčty a makry, mezi další tokeny.<br /><br /> Můžete zobrazit výchozí barvy pro každý typ a můžete změnit barvu libovolného elementu syntaxe v [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), které můžete otevřít z **nástroje** nabídky.|  
|Značky chyba a varování|Jak přidat kód a sestavte řešení, může se zobrazit podtržení vlnovkou (a) různé barvy (známé jako squiggles) nebo (b) návrhy ve vašem kódu. Chyby syntaxe jsou označené červenou vlnovkou, modrá označuje chybu kompilátoru, zelená značí upozornění a nachová označuje jiných typů chyb. [Ikony žárovky](../ide/perform-quick-actions-with-light-bulbs.md) navrhnout opravy problémů a usnadňují použití opravy.<br /><br /> Můžete zobrazit výchozí barvy pro každé chyby a varování vlnovku v **Nástroje/možnosti/prostředí/písma a barvy** dialogové okno. Vyhledejte **Chyba syntaxe**, **Chyba kompilátoru**, **upozornění**, a **jiná chyba**.|  
|Párování závorek|Když je kurzor umístěn na levou složenou závorku v souboru kódu, jsou zvýrazněny ho a pravou složenou závorku. Tato funkce poskytuje okamžitou zpětnou vazbu na nesprávně umístěné nebo chybějící závorky. Můžete zapnout závorky zapnutí nebo vypnutí se **automatické zvýraznění oddělovače** nastavení (**nástroje/Možnosti/textový Editor**). Můžete změnit barvu zvýraznění v **písma a barvy** nastavení (**Nástroje/možnosti/prostředí**). Vyhledejte **závorky (zvýraznit)** nebo **závorky (obdélník)**.|  
|Čísla řádků|Čísla řádků lze zobrazit na levém okraji okna kódu. Ve výchozím nastavení nejsou zobrazeny. Můžete zapnout tuto možnost **všechny jazyky textového editoru** nastavení (**nástroje/Možnosti/textový editor/všechny jazyky**). Čísla řádků pro jednotlivé programovací jazyky můžete zobrazit tak, že změníte nastavení pro tyto jazyky (**nástroje / Možnosti / textový Editor /\<jazyk >**). Čísla řádků k tisku, je nutné vybrat možnost zahrnout čísla řádků v **tisk** dialogové okno.|  
|Sledování změn|Barva levého okraje umožňuje sledovat, změny, které jste provedli v souboru. Změny, které jste provedli, protože soubor byl otevřen, ale nebyl uložen, jsou označeny žlutým pruhem na levý okraj (známé jako okraj výběru). Po uložení změn (ale před zavřením souboru), se panel zbarví zeleně. Pokud vrátíte zpět změnu po uložení souboru, na panelu oranžově. Chcete-li tuto funkci vypnout a znovu zapnout, změňte **sledovat změny** možnost **textový Editor** nastavení (**nástroje/Možnosti/textový Editor**).|  
|Vyberte kód a Text|Text můžete vybrat v režimu standardního souvislého datového toku nebo v režimu pole, ve kterém vyberete obdélníkovou část textu místo sady řádků. Provést výběr v režimu pole, stiskněte klávesu ALT při tažení myší přes výběr (nebo stiskněte klávesy ALT + SHIFT + \<šipka >). Výběr zahrnuje všechny znaky v obdélníku definovaném prvním znakem a posledním znakem ve výběru. Libovolná hodnota zadaná nebo vložit do vybrané oblasti bude vložena na stejné místo na každém řádku.|  
|Lupa|Můžete provést přiblížení nebo navýšení kapacity v jakékoli okno kódu stisknutím a podržením klávesy CTRL a přesunutím kolečka myši (nebo CTRL + SHIFT +. pro zvýšení a CTRL + SHIFT + pro zmenšení). Můžete také použít pole Lupa v levém dolním rohu okna kódu k nastavení konkrétního procenta zvětšení. Funkce Lupa nefunguje v oknech nástrojů.|  
|Virtuální prostor|Ve výchozím nastavení řádky v editoru Visual Studio končí po posledním znaku tak, tak, aby šipka doprava na konci řádku přesunula kurzor na začátek dalšího řádku. V některých jiných editorech řádek nekončí za posledním znakem a můžete umístit kurzor kamkoliv na řádek. Můžete povolit virtuální prostor v editoru v **nástroje/Možnosti/textový editor/všechny jazyky** nastavení. Všimněte si, že můžete povolit buď **virtuální prostor** nebo **zalamování**, ale ne obojí.|  
|Tisk|Můžete použít možnosti v **tisk** dialogové okno pro zahrnutí čísel řádků nebo skrytí sbalených oblasti kódu při tisku souboru. V **vzhled stránky** dialogové okno, můžete také vytisknout úplnou cestu a název souboru výběrem **záhlaví stránky**.<br /><br /> Možnosti tisku barev můžete nastavit **Nástroje/možnosti/prostředí/písma a barvy** dialogové okno. Zvolte **tiskárny** v **zobrazit nastavení pro** seznamu přizpůsobit barevný tisk. Můžete určit různé barvy pro tisk souboru než pro úpravy souboru.|  
|Globální akce zpět a znovu|**Vrátit zpět poslední globální akci** a **znovu provést poslední globální akci** příkazy na **upravit** nabídky vrátit zpět nebo opětovnému provedení globálních akcí, které ovlivňují více souborů. Globální akce zahrnují přejmenování třídy nebo oboru názvů, vykonání operace hledání a nahrazení napříč celým řešení, refaktoringu databáze nebo jakoukoli jinou akci, která se mění více souborů. Můžete použít globální akce zpět a znovu příkazy, které akce v aktuální relaci aplikace Visual Studio, dokonce i po zavření řešení, ve kterém byla použita akce.|  

## <a name="advanced-editing-features"></a>Pokročilé funkce editace  
 Najdete řadu pokročilých funkcí na **upravit/Upřesnit** podnabídka. Ne všechny tyto funkce jsou dostupné pro všechny typy souborů s kódem.  

|||  
|-|-|  
|Formátovat dokument|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků v dokumentu.|  
|Výběr formátu|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků ve výběru.|  
|Vybrané řádky posunout tabulátorem|Změny úvodních mezer na karty, kde je to vhodné.|  
|Zrušit posunutí tabulátorem u vybraných řádků|Změny úvodních karet na mezery. Pokud chcete převést všechny mezery v souboru na tabulátory (nebo všechny tabulátory na mezery), můžete použít `Edit.ConvertSpacesToTabs` a `Edit.ConvertTabsToSpaces` příkazy. Tyto příkazy se nezobrazují v nabídkách aplikace Visual Studio, ale můžete je volat z okna rychlý přístup nebo příkazové okno.|  
|Převést na velká písmena|Změní všechny znaky ve výběru na velká písmena, nebo pokud není nic vybráno, znak na pozici kurzoru na velká písmena se změní.|  
|Nastavit jako malé písmeno|Změní všechny znaky ve výběr na malá písmena, nebo pokud není nic vybráno, znak na pozici kurzoru změní na malá písmena.|  
|Ověřit dokument|Ověřuje soubory kódu JScript.|  
|Odstranit vodorovné prázdné znaky|Odstraní tabulátory nebo mezery na konci aktuálního řádku.|  
|Zobrazit prázdné znaky|Zobrazí mezery jako zvýšené tečky a karty jako šipky. Konec souboru se zobrazí jako obdélníkový glyf. Pokud **nástroje/Možnosti/textový editor/všechny jazyky/Word Wrap/zobrazit viditelné piktogramy pro zalamování řádků** je vybráno, že zobrazí se také piktogram.|  
|Zalamování řádků|Způsobí, že všechny řádky v dokumentu mají být zobrazeny v okně kódu. Zalamování slov můžete vypnout nebo zapnout v nastavení textového editoru všechny jazyky (**nástroje/Možnosti/textový editor/všechny jazyky**).|  
|Odkomentovat výběr|Přidá znaky komentáře do výběru nebo aktuálního řádku.|  
|Zakomentovat výběr|Odebere znaky komentáře z výběru nebo aktuálního řádku.|  
|Zvětšit odsazení řádku|Přidá kartu (nebo ekvivalentní mezery) do vybraných řádků nebo aktuálního řádku.|  
|Zmenšit odsazení řádku|Odebere kartu (nebo ekvivalentní mezery) z vybraných řádků nebo aktuálního řádku.|  
|Vybrat značku|V dokumentu, který obsahuje značky (například XML nebo HTML) vybere značku.|  
|Vybrat obsah značky|V dokumentu, který obsahuje značky (například XML nebo HTML) vybere obsah.|  

## <a name="navigate-in-the-code-window"></a>Přejděte do okna kódu  
 V dokumentu se můžete pohybovat různými způsoby. Kromě standardních operací můžete použít **přejít zpět** (nebo CTRL + mínus) a **přejít vpřed** (CTRL + SHIFT + mínus) na předchozí bod tlačítka na panelu nástrojů pro Posun kurzoru umístění nebo návrat do nedávných umístění v aktivním dokumentu. Tato tlačítka si ponechávají posledních 20 umístění kurzoru.  

 ![Navigační tlačítka vpřed a zpět](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")  

 Můžete také použít rozšířený posuvník v okně s kódem získat reálné zobrazení kódu. V režimu mapy, můžete zobrazit náhledy kódu, když vrátíte kurzor myši a dolů posuvníku, další informace naleznete v tématu [postupy: sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

 Následující příkazy jsou navigační metody specifické pro kód:  

|||  
|-|-|  
|Přejít na \<číslo řádku >|(**Úpravy/přejít na** nebo CTRL + G): přesunout na číslo určitého řádku v aktivním dokumentu.|  
|Přejděte na|(**Úpravy/Navigovat do** nebo CTRL +,): Vyhledá symbol nebo soubor v aktivním řešení. Umožňuje vybrat správnou sadu odpovídajících výsledků z dotazu. Můžete hledat klíčová slova, které jsou obsaženy v symbolu pomocí velbloudí notace a podtržených znaků k rozdělení symbolu na klíčová slova.|  
|Najít všechny odkazy|(kontextová nabídka): Vyhledá všechny odkazy na vybraný prvek v řešení.|  
|Přejít k definici|(kontextová nabídka nebo F12): Najde definici vybraného prvku.|  
|Náhled definice|(kontextová nabídka nebo Alt + F12): Najde definici vybraného prvku a zobrazí ho v místním okně. Další informace najdete v tématu [postupy: zobrazení a úpravy kódu pomocí náhled definice (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Další metoda, předchozí metoda|(**Úpravy/další metoda, předchozí metoda**) soubory kódu v jazyce Visual Basic, pomocí těchto příkazů můžete přesunout kurzor bodu do různých metod.|  
|Zvýraznění odkazů|Po kliknutí na symbol ve zdrojovém kódu se zvýrazní všechny výskyty symbolu v dokumentu. Zvýrazněné symboly mohou obsahovat prohlášení a odkazy a mnoho dalších symbolů, které **najít všechny odkazy** vrátí. Patří sem názvy tříd, objektů, proměnných, metod a vlastností. V kódu jazyka Visual Basic jsou také zvýrazněna klíčová slova pro mnoho řídících struktur. Přesunout na další nebo předchozí zvýrazněný symbol, stiskněte kombinaci kláves CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru. Můžete změnit barvu zvýraznění v **Nástroje/možnosti/prostředí/písma a barvy/zvýrazněný odkaz.**|  
|Najít informace týkající se kódu|Můžete najít informace o konkrétním kódu, jako jsou změny a kdo provedl tyto změny, odkazy, chyby, pracovní položky, revize kódu a stav jednotky testování, při použití CodeLens v editoru kódu. CodeLens funguje jako pohotové zobrazení při použití sady Visual Studio Enterprise s Team Foundation Server. Zobrazit [nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).|  

 Můžete také použít **navigační panel**, to je dva rozevírací seznamy, které jsou zobrazeny v horní části okna kódu k navigaci v souboru kódu. Tento panel umožňuje přejít přímo na určitý typ nebo na jeden z členů v rámci typu. Na navigačním panelu se zobrazí pomocí jazyka Visual Basic, C# a soubory kódu C++.  

 Chcete-li skrýt navigační panel, změňte **navigační panel** možnost v nastavení textového editoru všechny jazyky (**nástroje/Možnosti/textový editor/všechny jazyky**, nebo můžete změnit nastavení pro jednotlivce jazyky). Můžete procházet pole rozevíracího seznamu následujícím způsobem:  

- Chcete-li přesunout fokus z okna kódu na navigační panel, stiskněte kombinaci kláves CTRL + F2.  

- Chcete-li vrátit fokus z navigačního panelu do okna kódu, stiskněte klávesu ESC.  

- Chcete-li přesunout fokus z položek na navigačním panelu stiskněte klávesu Tabulátor.  

- Chcete-li vybrat položku navigačního panelu, který má právě fokus a vrátit se do IDE, stiskněte klávesu ENTER  

- Přejděte do třídy nebo typu, klikněte na jeho název v rozevíracím seznamu vlevo.  

- Pokud chcete přejít přímo k postupu ve třídě, klikněte na postup v rozevíracím seznamu vpravo.  

  V dílčí třídě mohou být členy definovány mimo aktuální soubor kódu šedě.  

## <a name="find-code-using-navigate-to"></a>Vyhledávání kódu pomocí přejít na
Příkaz "Přejít na" Visual Studio nepodporuje cílené hledání kódu vám pomůžou rychle najít zadané elementy v kódu soubory, cesty k souborům a kód symboly. Na rozdíl od jiných text hledání například najít nebo najít v souborech omezuje přejít na hledání do oblastí, kde skutečný kód kdekoli, jako jsou soubory, formuláře a modulů kódu. Například Pokud dáte vyhledat řetězec do webové aplikace ASP.NET pomocí najít nebo najít v souborech v celé řešení, může se zobrazit několik přístupů, včetně instancí řetězce v kódu poznámky. Pomocí přejít na však může být pouze získáte jednu funkci, ignoruje všechny instance řetězce v kódu poznámky.

### <a name="navigate-code-using-navigate-to"></a>Vyhledání kódu pomocí přejít na

1. Otevřete složku nebo řešení v sadě Visual Studio.
1. V hlavní nabídce zvolte **upravit**, **přejít na**, nebo stiskněte klávesu **CTRL +,**.

    Malé textové pole se zobrazí v horní roh editoru kódu.
1. Do textového pole zadejte název prvku kódu, které chcete najít.

    ![Přejít na okno](../ide/media/vside-navigatetowindow.png "přejít na okno")

    Jak budete zadávat, výsledky se zobrazí v rozevíracím seznamu pod textovým polem.
1. Přejít na element, vyberte v seznamu.


### <a name="filter-your-search"></a>Umožňuje filtrovat hledání

Omezit hledání na pouze kód symboly, musí přejít na dotaz s "@" znak. Například, pokud hledáte `@application`, přejít na zobrazí například pouze třídy, které obsahují slovo "aplikace" v nich.

Pokud používáte camelCase ve vašem kódu, najdete prvky kódu rychleji tak, že zadáte pouze písmeny název prvku kódu. Například, pokud váš kód obsahuje komponenty s názvem `ViewSwitcher`, najdete ho tak, že zadáte jenom velká písmena názvu (`"VS"`) v okně Přejít na.

![Přejít na okno - hledání s písmeny](../ide/media/vside-capitalsearch.png "přejít na okno - hledání s písmeny")

Tato funkce je zvláště užitečné, pokud váš kód obsahuje dlouhé názvy.

## <a name="customize-the-editor"></a>Přizpůsobení editoru  
 **Nastavení importu a exportu**: můžete sdílet nastavení s jiným vývojářem, aby vaše nastavení bylo v souladu s normou nebo pomocí vraťte do výchozího nastavení sady Visual Studio **Průvodce importem a exportem nastavení** na **Nástroje** nabídky. Můžete změnit obecné nastavení nebo jazyk a nastavení specifická pro projekt.  

 **Mapování klávesnice**: můžete definovat nové klávesové zkratky nebo změnit existující v nastavení nástroje/Možnosti/prostředí/klávesnice. Další informace o klávesových zkratkách naleznete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

 Informace o možnosti editoru pro konkrétní jazyk naleznete v následujících tématech:  

-   [Nastavení jazyka Visual Basic](http://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)  

-   [Použití vývojového prostředí sady Visual Studio pro jazyk C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)  

-   [Možnosti, Textový editor, JavaScript, Formátování](../ide/reference/options-text-editor-javascript-formatting.md)  

## <a name="in-this-section"></a>V tomto oddílu  

-   [Hledání a nahrazení textu](../ide/finding-and-replacing-text.md)  

-   [Šifrování a zalomení řádků](../ide/encodings-and-line-breaks.md)  

-   [Sbalení](../ide/outlining.md)  

-   [Refactoring](../ide/refactoring-in-visual-studio.md)  

-   [Tipy pro vyšší produktivitu](../ide/productivity-tips-for-visual-studio.md)  

-   [Používání atributu IntelliSense](../ide/using-intellisense.md)  

-   [Vlastní nastavení editoru](../ide/customizing-the-editor.md)  

-   [Postupy: Sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)  

-   [Postupy: Zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  

-   [Rychlé akce pomocí žárovek](../ide/perform-quick-actions-with-light-bulbs.md)  

-   [Fragmenty kódu](../ide/code-snippets.md)  

-   [Používání sady nástrojů](../ide/using-the-toolbox.md)  

-   [Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md)  

-   [Nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md)  

-   [Používání seznamu úkolů](../ide/using-the-task-list.md)  

-   [Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)  

## <a name="see-also"></a>Viz také  
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)


