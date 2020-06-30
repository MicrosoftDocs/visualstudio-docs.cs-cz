---
title: Psaní kódu v editoru kódu a textovém editoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa647d8a8d52588481d18347cb3400141978bd20
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548028"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Psaní kódu v editoru kódu a textovém editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Editor sady Visual Studio poskytuje mnoho funkcí, které usnadňují zápis a správu kódu. Můžete rozbalit a sbalit různé bloky kódu pomocí sbalení. Další informace o kódu, který používáte, můžete získat pomocí technologie IntelliSense, **Prohlížeč objektů**a hierarchie volání. V rámci kódu můžete procházet pomocí funkcí, jako je například **Přejít na**, **Přejít k definici**a **Najít všechny odkazy**. Můžete vložit bloky kódu s fragmenty kódu a můžete vygenerovat kód pomocí funkcí, jako je **generování z využití**. Pokud jste ještě nikdy nepoužili Editor sady Visual Studio 2015, přečtěte si téma [Úprava kódu](https://www.visualstudio.com/features/ide-vs) pro rychlý přehled.

 Kód můžete zobrazit několika různými způsoby. Chcete-li zobrazit zobrazení tříd vašeho řešení, můžete otevřít okno **zobrazení tříd** nebo rozšířit uzly v **Průzkumník řešení** pod soubory vaší třídy.

 Můžete hledat a nahrazovat text pro jeden nebo více souborů. Další informace najdete v tématu [hledání a nahrazování textu](../ide/finding-and-replacing-text.md). Používáte-li regulární výrazy, Všimněte si, že příkaz Najít a nahradit nyní používá regulární výrazy .NET. Další informace naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Různé jazyky sady Visual Studio nabízejí různé sady funkcí a v některých případech se funkce chovají odlišně v různých jazycích. Mnohé z těchto rozdílů jsou uvedeny v popisech funkcí, ale další informace najdete v oddílech v konkrétních jazycích sady Visual Studio.

> [!IMPORTANT]
> Edice sady Visual Studio a nastavení, které používáte, mohou ovlivnit funkce v integrovaném vývojovém prostředí. Můžou se lišit od těch popsaných v tomto tématu.

## <a name="editor-features"></a>Funkce editoru

|Funkce|Popis|
|-|-|
|Barevné zvýrazňování syntaxe|Některé prvky syntaxe kódu a souborů značek jsou jinak odlišeny. Například klíčová slova (například `using` v jazyce C# a `Imports` v Visual Basic) jsou jedna barva, ale typy (například `Console` a `Uri` ) jsou jinou barvou. Další prvky syntaxe jsou také barevně zabarvené, jako jsou řetězcové literály a komentáře. Jazyk C++ používá barvy k odlišení mezi typy, výčty a makry, mezi jinými tokeny.<br /><br /> Můžete zobrazit výchozí barvu pro každý typ a můžete změnit barvu pro kterýkoli konkrétní prvek syntaxe v [dialogovém okně písma a barvy, prostředí, možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), které můžete otevřít z nabídky **nástroje** .|
|Chybové a varovné značky|Když přidáte kód a sestavíte řešení, může se zobrazit (a) různě zbarvené podtržení vlnovkou (označované jako vlnovky) nebo (b), které se zobrazují ve vašem kódu. Červené vlnovky označují chyby syntaxe, modré značí chyby kompilátoru, varování zelených známek a fialově označuje jiné typy chyb. [Žárovky navrhují](../ide/perform-quick-actions-with-light-bulbs.md) opravy problémů a usnadňují použití opravy.<br /><br /> V dialogovém okně **Nástroje/možnosti/prostředí/písma a barvy** se zobrazí výchozí barva pro každou chybovou a výstražnou vlnovku. Vyhledejte **syntaktickou chybu**, **chybu kompilátoru**, **Upozornění**a **Další chybu**.|
|Spárování složených závorek|Když je kurzor umístěn na levou složenou závorku v souboru kódu, zvýrazní se i pravá složená závorka. Tato funkce poskytuje okamžitou zpětnou vazbu na nesprávně umístěných nebo chybějících složených závorkách. Můžete zapnout nebo vypnout sjednocení složených závorek pomocí nastavení **automatického zvýraznění oddělovače** (**Nástroje/možnosti/textový editor**). Můžete změnit barvu zvýraznění v nastavení **písma a barvy** (**Nástroje/možnosti/prostředí**). Vyhledejte **párové závorky (zvýraznění)** nebo **spárování složených závorek (obdélník)**.|
|Čísla řádků|Čísla řádků se dají zobrazit na levém okraji okna Code (kód). Ve výchozím nastavení se nezobrazují. Tuto možnost můžete zapnout v nastavení **všechny jazyky textového editoru** (**Nástroje/možnosti/textový editor/všechny jazyky**). Čísla řádků pro jednotlivé programovací jazyky můžete zobrazit změnou nastavení pro tyto jazyky (**Nástroje/možnosti/textový editor/ \<language> **). Pro čísla řádků k tisku musíte vybrat možnost zahrnout čísla řádků v dialogovém okně **Tisk** .|
|Sledování změn|Barva levého okraje umožňuje sledovat změny, které jste provedli v souboru. Změny, které jste provedli od otevření souboru, ale nebyly uloženy, jsou označeny žlutým pruhem na levém okraji (známé jako okraj výběru). Po uložení změn (ale před zavřením souboru) se pruh změní na zelený. Pokud po uložení souboru zrušíte změnu, pruh se změní na oranžová. Chcete-li tuto funkci vypnout a zapnout, změňte možnost **sledovat změny** v nastavení **textový editor** (**Nástroje/možnosti/textový editor**).|
|Výběr kódu a textu|Text můžete vybrat buď v režimu standardního souvislého datového proudu, nebo v režimu pole, ve kterém vyberete obdélníkovou část textu namísto sady řádků. Chcete-li provést výběr v režimu pole, stiskněte klávesu ALT při přetahování myší na výběr (nebo stiskněte kombinaci kláves ALT + SHIFT + \<arrow key> ). Výběr zahrnuje všechny znaky v obdélníku definované prvním znakem a posledním znakem ve výběru. Cokoliv, co jste zadali nebo vložili do vybrané oblasti, je vloženo na stejný bod na každém řádku.|
|Zoom|Stisknutím a podržením klávesy CTRL a přesunutím kolečka myši (nebo stisknutím kombinace kláves CTRL + SHIFT +) můžete v jakémkoli okně kódu přiblížit nebo oddálit. pro zvýšení a CTRL + SHIFT +, aby se snížilo). Můžete také použít pole Lupa v levém dolním rohu okna kódu k nastavení konkrétního procenta zvětšení. Funkce přiblížení nefunguje v oknech nástrojů.|
|Virtuální prostor|Ve výchozím nastavení řádky v editorech sady Visual Studio končí za posledním znakem, takže pravá šipka na konci řádku přesune kurzor na začátek dalšího řádku. V některých dalších editorech řádek nekončí za posledním znakem a můžete umístit kurzor kamkoli na řádek. Virtuální prostor můžete v editoru povolit v nastavení **Nástroje/možnosti/textový editor/všechny jazyky** . Všimněte si, že můžete povolit buď **virtuální prostor** , nebo **zalamování řádků**, ale ne obojí.|
|Tisk|Můžete použít možnosti v dialogovém okně **Tisk** pro vložení čísel řádků nebo skrytí sbalených oblastí kódu při tisku souboru. V dialogovém okně **nastavení stránky** můžete také zvolit tisk celé cesty a názvu souboru výběrem **záhlaví stránky**.<br /><br /> Můžete nastavit možnosti tisku barev v dialogovém okně **Nástroje/možnosti/prostředí/písma a barvy** . Zvolením možnosti **tiskárna** v seznamu **Zobrazit nastavení pro** upravte barevný tisk. Můžete určit různé barvy pro tisk souboru, než pro úpravu souboru.|
|Globální akce zpět a znovu|Příkazy **vrátit zpět poslední globální akci** a **znovu provést poslední globální akce** v nabídce **Upravit** vrátí zpět nebo zopakují globální akce, které mají vliv na více souborů. Globální akce zahrnují přejmenování třídy nebo oboru názvů, provedení operace hledání a nahrazení v rámci řešení, refaktoringu databáze nebo jakékoli jiné akce, která změní více souborů. Můžete použít globální příkazy zpět a znovu pro akce v aktuální relaci sady Visual Studio, a to i po zavření řešení, ve kterém byla provedena akce.|

## <a name="advanced-editing-features"></a>Pokročilé funkce pro úpravy
 Řadu pokročilých funkcí najdete v podnabídce **Upravit/Upřesnit** . Ne všechny tyto funkce jsou k dispozici pro všechny typy souborů kódu.

|Funkce|Popis|
|-|-|
|Formátovat dokument|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků v dokumentu.|
|Příkaz Formátovat výběr|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků výběru.|
|Převést na tabulátory vybrané řádky|Změní úvodní mezery na tabulátory tam, kde je to vhodné.|
|Zrušit tabulátory vybrané řádky|Změní úvodní tabulátory na mezery. Pokud chcete převést všechny mezery v souboru na tabulátory (nebo na všechny karty na mezery), můžete použít `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` příkazy a. Tyto příkazy se nezobrazují v nabídkách sady Visual Studio, ale můžete je volat z okna rychlý přístup nebo z příkazového okna.|
|Převést na velká písmena|Změní všechny znaky ve výběru na velká písmena, nebo pokud není vybrán žádný výběr, mění znak na pozici kurzoru na velká písmena.|
|Nastavit malými písmeny|Změní všechny znaky ve výběru na malá písmena nebo pokud není nic vybráno, změní znak na pozici kurzoru na malá písmena.|
|Ověřit dokument|Ověří soubory kódu JScript.|
|Odstranit vodorovné prázdné znaky|Odstraní tabulátory nebo mezery na konci aktuálního řádku.|
|Zobrazit prázdné znaky|Zobrazí mezery jako vystouplé tečky a tabulátory jako šipky. Konec souboru se zobrazí jako obdélníkový glyf. Pokud je vybrána možnost **Nástroje/možnosti/textový editor/všechny jazyky/zalamování řádků/zobrazit viditelné glyfy pro zalamování řádků** , zobrazí se také tento glyf.|
|Zalamování řádků|Způsobí, že všechny řádky v dokumentu budou viditelné v okně Code (kód). Můžete zapnout nebo vypnout zalamování řádků v nastavení textový editor všechny jazyky (**Nástroje/možnosti/textový editor/všechny jazyky**).|
|Odkomentovat výběr|Přidá znaky komentáře do výběru nebo aktuálního řádku.|
|Výběr komentáře|Odebere znaky komentáře z výběru nebo aktuálního řádku.|
|Zvětšit odsazení řádku|Přidá kartu (nebo ekvivalentní mezery) na vybrané řádky nebo aktuální řádek.|
|Zmenšit odsazení řádku|Odebere tabulátor (nebo ekvivalentní mezery) z vybraných řádků nebo aktuálního řádku.|
|Vybrat značku|V dokumentu, který obsahuje značky (například XML nebo HTML), vybere značku.|
|Vybrat obsah značky|V dokumentu, který obsahuje značky (například XML nebo HTML), vybere obsah.|

## <a name="navigate-in-the-code-window"></a>Navigace v okně Code
 Můžete se pohybovat v dokumentu několika různými způsoby. Kromě standardních operací můžete na panelu nástrojů použít tlačítka **Navigovat zpět** (nebo CTRL + minus) a **Procházet vpřed** (CTRL + SHIFT + minus) a přesunout kurzor na předchozí umístění nebo vrátit se do novějších umístění v aktivním dokumentu. Tato tlačítka si zachovávají posledních 20 umístění místa vložení.

 ![Navigační tlačítka pro navigaci a zpět](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")

 Můžete také použít rozšířený posuvník v okně kódu a získat tak pohled na svůj kód v pohledech na oči. V režimu mapy můžete zobrazit náhledy kódu při přesunutí kurzoru nahoru a dolů posuvníku, další informace naleznete v tématu [How to: Track a Tracking a Code by](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

 Následující příkazy jsou metody navigace specifické pro kód:

|Příkaz|Popis|
|-|-|
|Přejít na\<line number>|(**Upravit/přejít na** nebo CTRL + G): přesunout na konkrétní číslo řádku v aktivním dokumentu.|
|Přejít na|(**Upravit/přejít na** nebo CTRL +,): najde symbol nebo soubor v aktivním řešení. Pomůže vám vybrat dobrou sadu vyhovujících výsledků dotazu. Můžete vyhledat klíčová slova, která jsou obsažena v symbolu pomocí ve stylu CamelCase velkých a malých písmen k rozdělení symbolu na klíčová slova.|
|Najít všechny odkazy|(kontextová nabídka): vyhledá všechny odkazy na vybraný prvek v řešení.|
|Přejít k definici|(kontextová nabídka nebo F12): vyhledá definici vybraného elementu.|
|Náhled definice|(kontextová nabídka nebo Alt + F12): najde definici vybraného prvku a zobrazí ho v místním okně. Další informace najdete v tématu [Postup: zobrazení a úpravy kódu pomocí funkce Náhled definice (Alt + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|
|Next – metoda, předchozí metoda|(**Upravit/další metoda, předchozí metoda**) V Visual Basic soubory kódu, použijte tyto příkazy pro přesun kurzoru do různých metod.|
|Zvýrazňování odkazů|Po kliknutí na symbol ve zdrojovém kódu se v dokumentu zvýrazní všechny výskyty tohoto symbolu. Zvýrazněné symboly mohou obsahovat deklarace a odkazy a mnoho dalších symbolů, které **naleznou všechny odkazy** , vrátí. Mezi ně patří názvy tříd, objektů, proměnných, metod a vlastností. V kódu Visual Basic jsou také zvýrazněna klíčová slova pro mnoho řídicích struktur. Chcete-li přejít na další nebo předchozí zvýrazněný symbol, stiskněte klávesy CTRL + SHIFT + šipka dolů nebo CTRL + SHIFT + šipka nahoru. Můžete změnit barvu zvýraznění v **nabídce Nástroje/možnosti/prostředí/písma a barvy/zvýrazněný odkaz.**|
|Najít informace související s kódem|Můžete najít informace o konkrétním kódu, například změny a o tom, kdo provedl tyto změny, odkazy, chyby, pracovní položky, revize kódu a stav testu jednotek při použití CodeLens v editoru kódu. CodeLens funguje jako při použití Visual Studio Enterprise s Team Foundation Server, jako je například zobrazení hlav. Viz téma [Vyhledání změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md).|

 Můžete také použít **navigační panel**, to znamená dvě rozevírací seznamy, které jsou zobrazeny v horní části okna kódu, pro navigaci v souboru kódu. Tento panel umožňuje přejít přímo na konkrétní typ nebo na jeden z členů v rámci typu. Navigační panel se zobrazí se soubory kódu Visual Basic, C# a C++.

 Chcete-li skrýt navigační panel, změňte možnost **navigační panel** v nastavení textový editor všechny jazyky (**Nástroje/možnosti/textový editor/všechny jazyky**, nebo můžete změnit nastavení pro jednotlivé jazyky). V rozevíracích seznamech můžete přejít následujícím způsobem:

- Chcete-li přesunout fokus z okna Code do navigačního panelu, stiskněte kombinaci kláves CTRL + F2.

- Chcete-li vrátit fokus z navigačního panelu do okna kódu, stiskněte klávesu ESC.

- Chcete-li přesunout fokus z položky na položku na navigačním panelu, stiskněte klávesu TAB.

- Pokud chcete vybrat položku navigačního panelu, která má fokus, a vrátit se do prostředí IDE, stiskněte klávesu ENTER.

- Chcete-li přejít na třídu nebo typ, klikněte na její název v rozevíracím seznamu vlevo.

- Chcete-li přejít přímo k proceduře ve třídě, klikněte na proceduru v rozevíracím seznamu vpravo.

  V částečné třídě mohou být členy, kteří jsou definováni mimo aktuální soubor kódu, zobrazeny šedě.

## <a name="find-code-using-navigate-to"></a>Vyhledání kódu pomocí přechodu na
Příkaz "Přejít na" v aplikaci Visual Studio provede cílené hledání kódu, který vám pomůže rychle najít určené prvky v souborech kódu, cestách k souboru a symbolech kódu. Na rozdíl od jiných hledání textu, jako je například najít nebo najít v souborech, přejděte na omezit hledání do oblastí, ve kterých skutečný kód bydlí, jako jsou soubory, formuláře a moduly kódu. Například pokud hledáte řetězec ve webové aplikaci ASP.NET pomocí hledání nebo hledání v souborech v celém řešení, může se zobrazit několik výsledků, včetně instancí řetězce v kódu poznámky. Pomocí funkce Přejít na můžete získat pouze jedinou funkci, která ignoruje všechny výskyty řetězce v kódu poznámky.

### <a name="navigate-code-using-navigate-to"></a>Navigace v kódu pomocí přechodu na

1. Otevřete řešení nebo složku v aplikaci Visual Studio.
1. V hlavní nabídce zvolte možnost **Upravit**, **přejděte na**nebo stiskněte klávesovou **zkratku CTRL +,**.

    V horním rohu editoru kódu se zobrazí malé textové pole.
1. Do textového pole zadejte název prvku kódu, který chcete najít.

    ![Přejít na okno](../ide/media/vside-navigatetowindow.png "Přejít na okno")

    Při psaní se výsledky zobrazí v rozevíracím seznamu pod textovým polem.
1. Chcete-li přejít na prvek, vyberte ho v seznamu.

### <a name="filter-your-search"></a>Filtrovat hledání

Chcete-li omezit hledání pouze na symboly kódu, je nutné přejít na dotaz pomocí znaku " \@ ". Pokud například hledáte `@application` , přejděte k zobrazení, například pouze třídy, které mají v nich slovo "aplikace".

Pokud používáte ve stylu CamelCase velká a malá písmena v kódu, můžete najít prvky kódu rychleji zadáním pouze velkých písmen názvu elementu kódu. Například pokud váš kód má komponentu s názvem `ViewSwitcher` , můžete ji najít zadáním pouze velkých písmen názvu ( `"VS"` ) v okně Přejít na.

![Přejít na okno – vyhledávání pomocí velkých písmen](../ide/media/vside-capitalsearch.png "Přejít na okno – vyhledávání pomocí velkých písmen")

Tato funkce je užitečná hlavně v případě, že váš kód má dlouhé názvy.

## <a name="customize-the-editor"></a>Přizpůsobení editoru
 **Nastavení importu a exportu**: můžete sdílet nastavení s jiným vývojářem, nechat vaše nastavení v souladu se standardem, nebo se můžete vrátit do výchozího nastavení sady Visual Studio pomocí **Průvodce importem a exportem nastavení** v nabídce **nástroje** . Můžete změnit obecná nastavení nebo jazyk a nastavení specifické pro projekt.

 **Mapování klávesnice**: můžete definovat nové klávesové zkratky nebo znovu definovat existující v nastavení nástroje/možnosti/prostředí/klávesnice. Další informace o klávesových zkratkách naleznete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Informace o možnostech editoru pro konkrétní jazyk najdete v následujících tématech:

- [Nastavení Visual Basic](https://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)

- [Použití vývojového prostředí sady Visual Studio pro jazyk C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)

- [Možnosti, Textový editor, JavaScript, Formátování](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="in-this-section"></a>V této části

- [Hledání a nahrazení textu](../ide/finding-and-replacing-text.md)

- [Kódování a zalomení řádků](../ide/encodings-and-line-breaks.md)

- [Sbalování](../ide/outlining.md)

- [Refactoring](../ide/refactoring-in-visual-studio.md)

- [Tipy pro produktivitu](../ide/productivity-tips-for-visual-studio.md)

- [Používání atributu IntelliSense](../ide/using-intellisense.md)

- [Vlastní nastavení editoru](../ide/customizing-the-editor.md)

- [Postupy: Sledování kódu přizpůsobením posuvníku](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

- [Postupy: Zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

- [Rychlé akce pomocí žárovek](../ide/perform-quick-actions-with-light-bulbs.md)

- [Fragmenty kódu](../ide/code-snippets.md)

- [Používání sady nástrojů](../ide/using-the-toolbox.md)

- [Zobrazení struktury kódu](../ide/viewing-the-structure-of-code.md)

- [Nastavení záložek v kódu](../ide/setting-bookmarks-in-code.md)

- [Používání seznamu úkolů](../ide/using-the-task-list.md)

- [Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>Viz také
 [Integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide.md)
