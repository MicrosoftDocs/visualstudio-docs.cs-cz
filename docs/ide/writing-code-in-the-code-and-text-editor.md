---
title: Funkce editoru kódu
ms.date: 02/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca203b0c27906d1f861689953ca55280f73fa894
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160111"
---
# <a name="features-of-the-code-editor"></a>Funkce editoru kódu

Editor sady Visual Studio poskytuje mnoho funkcí, které usnadňují zápis a správu vašeho kódu a text. Můžete rozbalit nebo sbalit různé bloky kódu pomocí osnovy. Další informace o kódu pomocí technologie IntelliSense, **prohlížeče objektů**a hierarchii volání. Kód můžete najít pomocí funkcí **přejít na**, **přejít k definici**, a **najít všechny odkazy**. Můžete vložit bloky kódu pomocí fragmentů kódu a může generovat kód pomocí funkcí **Generovat z využití**. Pokud jste editoru sady Visual Studio před nikdy nepoužívali, přečtěte si téma [úpravy kódu](https://visualstudio.microsoft.com/vs/features/ide/) a získejte rychlý přehled.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [Editor zdrojového kódu (Visual Studio for Mac)](/visualstudio/mac/source-editor).

Zobrazí se váš kód v několika různými způsoby. Ve výchozím nastavení **Průzkumníka řešení** zobrazuje váš kód uspořádané podle souborů. Můžete kliknout na **zobrazení tříd** karta v dolní části okna, chcete-li zobrazit kód uspořádané podle třídy.

Můžete vyhledat a nahradit text v jedné nebo více souborů. Další informace najdete v tématu [najít a nahradit text](../ide/finding-and-replacing-text.md). Regulární výrazy můžete použít k vyhledání a nahrazení textu. Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Různé jazyky Visual Studio nabízí různé sady funkcí a v některých případech se funkce chovají odlišně v různých jazycích. Mnohé z těchto rozdílů jsou uvedeny v popisech funkcí, ale pro další informace najdete v částech na konkrétní jazyky sady Visual Studio.

## <a name="editor-features"></a>Funkce editoru

|||
|-|-|
|Barevné zvýrazňování syntaxe|Některé prvky syntaxe kódu a kódu souborů jsou různě barevně odlišeny abychom je odlišili. Například klíčová slova (například `using` v jazyce C# a `Imports` v jazyce Visual Basic) jsou jednu barvu, ale typy (například `Console` a `Uri`) mají jinou barvu. Ostatní prvky syntaxe jsou také obarveny, jako je například řetězcové literály a komentáře. C++ používá barvy k rozlišení mezi typy, výčty a makry, mezi další tokeny.<br /><br /> Můžete zobrazit výchozí barvy pro každý typ a můžete změnit barvu libovolného elementu syntaxe v [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), které můžete otevřít z **nástroje** nabídky.|
|Značky chyba a varování|Jak přidat kód a sestavte řešení, může se zobrazit podtržení vlnovkou (a) různé barvy (známé jako squiggles) nebo (b) návrhy ve vašem kódu. Chyby syntaxe jsou označené červenou vlnovkou, modrá označuje chybu kompilátoru, zelená značí upozornění a nachová označuje jiných typů chyb. [Rychlé akce](../ide/quick-actions.md) navrhnout opravy problémů a usnadňují použití opravy.<br /><br /> Můžete zobrazit výchozí barvy pro každé chyby a varování vlnovku v **nástroje** > **možnosti** > **prostředí**  >   **Písma a barvy** dialogové okno. Vyhledejte **Chyba syntaxe**, **Chyba kompilátoru**, **upozornění**, a **jiná chyba**.|
|Párování závorek|Když je kurzor umístěn na levou složenou závorku v souboru kódu, jsou zvýrazněny ho a pravou složenou závorku. Tato funkce poskytuje okamžitou zpětnou vazbu na nesprávně umístěné nebo chybějící závorky. Můžete zapnout závorky zapnutí nebo vypnutí se **automatické zvýraznění oddělovače** nastavení (**nástroje** > **možnosti**  >   **Textový Editor**). Můžete změnit barvu zvýraznění v **písma a barvy** nastavení (**nástroje** > **možnosti** > **prostředí**). Vyhledejte **závorky (zvýraznit)** nebo **závorky (obdélník)**.|
|Vizualizér struktur|Tečkované čáry připojení odpovídající složené závorky v kódu soubory usnadnit zobrazíte levá a pravá složená závorka dvojice. To může pomoct najít kód vašeho základu kódu rychleji. Tyto řádky může zapnout nebo vypnout pomocí **zobrazit strukturu pokyny** v **zobrazení** část **nástroje** > **možnosti**  >  **Textový Editor** > **Obecné** stránky.|
|Čísla řádků|Čísla řádků lze zobrazit na levém okraji okna kódu. Ve výchozím nastavení nejsou zobrazeny. Můžete zapnout tuto možnost **všechny jazyky textového editoru** nastavení (**nástroje** > **možnosti** > **textový Editor**  >  **Všechny jazyky**). Čísla řádků pro jednotlivé programovací jazyky můžete zobrazit tak, že změníte nastavení pro tyto jazyky (**nástroje** > **možnosti** > **textový Editor**   >   **\<jazyk >**). Čísla řádků k tisku, musíte vybrat **zahrnutí čísel řádků** v **tisk** dialogové okno.|
|Sledování změn|Barva levého okraje umožňuje sledovat, změny, které jste provedli v souboru. Změny, které jste provedli, protože soubor byl otevřen, ale nebyl uložen, jsou označeny žlutým pruhem na levý okraj (známé jako okraj výběru). Po uložení změn (ale před zavřením souboru), se panel zbarví zeleně. Pokud vrátíte zpět změnu po uložení souboru, na panelu oranžově. Chcete-li tuto funkci vypnout a znovu zapnout, změňte **sledovat změny** možnost **textový Editor** nastavení (**nástroje** > **možnosti**  >  **Textový Editor**).|
|Vyberte kód a Text|Text můžete vybrat v režimu standardního souvislého datového toku nebo v režimu pole, ve kterém vyberete obdélníkovou část textu místo sady řádků. Chcete-li provést výběr v režimu pole, stiskněte **Alt** tažení myší přes výběr (nebo stiskněte klávesu **Alt**+**Shift** +  **\<šipka >**). Výběr zahrnuje všechny znaky v obdélníku definovaném prvním znakem a posledním znakem ve výběru. Libovolná hodnota zadaná nebo vložit do vybrané oblasti bude vložena na stejné místo na každém řádku.|
|Lupa|Můžete provést přiblížení nebo navýšení kapacity v jakékoli okno kódu stisknutím a podržením **Ctrl** klíč a přesunutím kolečka myši (nebo **Ctrl**+**Shift** +**.** pro zvýšení a **Ctrl**+**Shift**+**,** snížení). Můžete také použít **přiblížení** pole v levém dolním rohu okna kódu k nastavení konkrétního procenta zvětšení. Funkce Lupa nefunguje v oknech nástrojů.|
|Virtuální prostor|Ve výchozím nastavení, řádky v end editory sady Visual Studio po poslední znak tak, aby **šipka vpravo** klíč na konci řádku přesunula kurzor na začátek dalšího řádku. V některých jiných editorech řádek nekončí za posledním znakem a můžete umístit kurzor kamkoliv na řádek. Můžete povolit virtuální prostor v editoru v **nástroje** > **možnosti** > **textový Editor** > **všechny Jazyky** nastavení. Všimněte si, že můžete povolit buď **virtuální prostor** nebo **zalamování**, ale ne obojí.|
|Tisk|Můžete použít možnosti v **tisk** dialogové okno pro zahrnutí čísel řádků nebo skrytí sbalených oblasti kódu při tisku souboru. V **vzhled stránky** dialogové okno, můžete také vytisknout úplnou cestu a název souboru výběrem **záhlaví stránky**.<br /><br /> Možnosti tisku barev můžete nastavit **nástroje** > **možnosti** > **prostředí** > **písma a Barvy** dialogové okno. Zvolte **tiskárny** v **zobrazit nastavení pro** seznamu přizpůsobit barevný tisk. Můžete určit různé barvy pro tisk souboru než pro úpravy souboru.|
|Globální akce zpět a znovu|**Vrátit zpět poslední globální akci** a **znovu provést poslední globální akci** příkazy na **upravit** nabídky vrátit zpět nebo opětovnému provedení globálních akcí, které ovlivňují více souborů. Globální akce zahrnují přejmenování třídy nebo oboru názvů, vykonání operace hledání a nahrazení napříč celým řešení, refaktoringu databáze nebo jakoukoli jinou akci, která se mění více souborů. Můžete použít globální akce zpět a znovu příkazy, které akce v aktuální relaci aplikace Visual Studio, dokonce i po zavření řešení, ve kterém byla použita akce.|

## <a name="advanced-editing-features"></a>Pokročilé funkce pro úpravy

Najdete řadu pokročilých funkcí na **upravit** > **Upřesnit** nabídka na panelu nástrojů. Všechny tyto funkce jsou dostupné pro všechny typy souborů s kódem.

|||
|-|-|
|[Formátovat dokument](code-styles-and-quick-actions.md#format-document-command)|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků v dokumentu.|
|Výběr formátu|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků ve výběru.|
|Vybrané řádky posunout tabulátorem|Změny úvodních mezer na karty, kde je to vhodné.|
|Zrušit posunutí tabulátorem u vybraných řádků|Změny úvodních karet na mezery. Pokud chcete převést všechny mezery v souboru na tabulátory (nebo všechny tabulátory na mezery), můžete použít `Edit.ConvertSpacesToTabs` a `Edit.ConvertTabsToSpaces` příkazy. Tyto příkazy se nezobrazují v nabídkách aplikace Visual Studio, ale můžete je z volat **rychlý přístup** okna nebo příkazové okno.|
|Převést na velká písmena|Změní všechny znaky ve výběru na velká písmena, nebo pokud není nic vybráno, znak na pozici kurzoru na velká písmena se změní.|
|Nastavit jako malé písmeno|Změní všechny znaky ve výběr na malá písmena, nebo pokud není nic vybráno, znak na pozici kurzoru změní na malá písmena.|
|Přesunout vybrané řádky nahoru|Posune vybraný řádek jeden řádek nahoru. Zástupce: **ALT**+**šipka nahoru**.|
|Přesunout vybrané řádky dolů|Posune vybraný řádek jeden řádek dolů. Zástupce: **ALT**+**šipka dolů**.|
|Odstranit vodorovné prázdné znaky|Odstraní tabulátory nebo mezery na konci aktuálního řádku.|
|Zobrazit prázdné znaky|Zobrazí mezery jako zvýšené tečky a karty jako šipky. Konec souboru se zobrazí jako obdélníkový glyf. Pokud **nástroje** > **možnosti** > **textový Editor** > **všechny jazyky**  >  **Zalamování** > **zobrazit viditelné piktogramy pro zalamování řádků** je vybráno, že zobrazí se také piktogram.|
|Zalamování řádků|Způsobí, že všechny řádky v dokumentu mají být zobrazeny v okně kódu. Zalamování slov můžete vypnout nebo zapnout v **všechny jazyky textového editoru** nastavení (**nástroje** > **možnosti** > **textový Editor**   >  **Všechny jazyky**).|
|Zakomentovat výběr|Přidá znaky komentáře do výběru nebo aktuálního řádku.|
|Odkomentovat výběr|Odebere znaky komentáře z výběru nebo aktuálního řádku.|
|Zvětšit odsazení řádku|Přidá kartu (nebo ekvivalentní mezery) do vybraných řádků nebo aktuálního řádku.|
|Zmenšit odsazení řádku|Odebere kartu (nebo ekvivalentní mezery) z vybraných řádků nebo aktuálního řádku.|
|Vybrat značku|V dokumentu, který obsahuje značky (například XML nebo HTML) vybere značku.|
|Vybrat obsah značky|V dokumentu, který obsahuje značky (například XML nebo HTML) vybere obsah.|

## <a name="navigate-and-find-code"></a>Orientuje a hledá kód

Můžete pohybovat v editoru kódu v několika různými způsoby, včetně zpětné navigace a předává do předchozích bodů vložení, zobrazování definice typu nebo členu a přechod na konkrétní metodu, pomocí navigačního panelu. Další informace najdete v části [vyhledání kódu](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Hledání odkazů v vašeho základu kódu

Chcete-li zjistit, kde jsou prvky konkrétního kódu odkazovat v rámci vašeho základu kódu, můžete použít **najít všechny odkazy** příkazu. Také, když kliknete na typ nebo člen, **zvýraznění odkazů** funkce automaticky zvýrazní všechny odkazy na tento typ nebo člen. Další informace najdete v tématu [najít odkazy ve vašem kódu](finding-references.md).

## <a name="customize-the-editor"></a>Přizpůsobení editoru

Můžete sdílet nastavení sady Visual Studio s jiným vývojářem, aby vaše nastavení bylo v souladu s normou nebo pomocí vraťte do výchozího nastavení sady Visual Studio **Průvodce importem a exportem nastavení** příkaz  **Nástroje** nabídky. V **Průvodce importem a exportem nastavení**, můžete změnit obecné nastavení nebo jazyk a nastavení specifická pro projekt.

Pokud chcete definovat nové klávesové zkratky nebo změnit existujícího klávesové zkratky, přejděte na **nástroje** > **možnosti** > **prostředí**  >  **Klávesnice**. Další informace o klávesových zkratkách naleznete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Další informace o přizpůsobení editoru, najdete v části [přizpůsobit editor](../ide/customizing-the-editor.md). Možnosti editoru jazyka JavaScript specifické najdete v tématu [možnosti editoru jazyka JavaScript](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Viz také:

- [Editor zdrojového kódu (Visual Studio for Mac)](/visualstudio/mac/source-editor)
- [Integrované vývojové prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
- [Začínáme s C++ v sadě Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md)
- [Začínáme s C# a technologie ASP.NET v sadě Visual Studio](../ide/tutorial-csharp-aspnet-core.md)
- [Začněte používat Python v sadě Visual Studio](../ide/quickstart-python.md)