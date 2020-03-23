---
title: Funkce editoru kódu
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de209e0a940fe7f7c64644cea37de3762df0d643
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588548"
---
# <a name="features-of-the-code-editor"></a>Funkce editoru kódu

Editor sady Visual Studio poskytuje mnoho funkcí, které usnadňují psaní a správu kódu a textu. Můžete rozbalit a sbalit různé bloky kódu pomocí osnovy. Další informace o kódu můžete získat pomocí technologie IntelliSense, **prohlížeče objektů**a hierarchie volání. Kód můžete najít pomocí funkcí, jako je **Přejít na**, **Přejít na definici**a **Najít všechny odkazy**. Můžete vložit bloky kódu s fragmenty kódu a můžete generovat kód pomocí funkcí, jako je **generovat z použití**. Pokud jste nikdy předtím editor Visual Studio nepoužívali, přečtěte si informace [o používání editoru kódu](../get-started/tutorial-editor.md).

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Zdrojový editor (Visual Studio pro Mac).](/visualstudio/mac/source-editor)

Kód můžete zobrazit několika různými způsoby. Ve výchozím nastavení **Průzkumník řešení** zobrazuje kód uspořádaný podle souborů. Kliknutím na kartu **Zobrazení tříd** v dolní části okna zobrazíte kód uspořádaný podle tříd.

Text můžete prohledávat a nahrazovat v jednom nebo více souborech. Další informace naleznete v tématu [Hledání a nahrazování textu](../ide/finding-and-replacing-text.md). K vyhledání a nahrazení textu můžete použít regulární výrazy. Další informace naleznete v [tématu Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Různé jazyky sady Visual Studio nabízejí různé sady funkcí a v některých případech se funkce chovají odlišně v různých jazycích. Mnohé z těchto rozdílů jsou uvedeny v popisech funkcí, ale další informace můžete zobrazit v částech o konkrétních jazycích sady Visual Studio.

## <a name="editor-features"></a>Funkce editoru

|||
|-|-|
|Zbarvení syntaxe|Některé prvky syntaxe kódu a soubory značek jsou zbarveny odlišně, aby se odlišily. Například klíčová slova `using` (například v `Imports` jazyce C# a v jazyce `Console` `Uri`Visual Basic) jsou jednu barvu, ale typy (například a ) jsou jinou barvou. Ostatní prvky syntaxe jsou také obarveny, například řetězcové literály a komentáře. C++ používá barvu k rozlišení mezi typy, výčty a makra, mimo jiné tokeny.<br /><br /> Můžete zobrazit výchozí barvu pro každý typ a můžete změnit barvu pro libovolný konkrétní prvek syntaxe v [dialogovém okně Písma a barvy, Prostředí, Volby](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), které můžete otevřít z nabídky **Nástroje.**|
|Chybové a varovné značky|Při přidávání kódu a vytváření řešení se může zobrazit (a) různě barevné podtržení vlnovkou (označované jako vlnovky) nebo (b) žárovky, které se zobrazují ve vašem kódu. Červené vlnovky označují syntaktické chyby, modrá označuje chyby kompilátoru, zelená označují varování a fialová označuje jiné typy chyb. [Rychlé akce](../ide/quick-actions.md) navrhnou opravy problémů a usnadní její použití.<br /><br /> Výchozí barvu pro každou chybu a vlnovku upozornění zobrazíte v dialogovém okně**Environment** > **Písma a barvy** **prostředí nástrojů.** > **Options** >  Vyhledejte **syntaktickou chybu**, **chybu kompilátoru**, **upozornění**a **další chybu**.|
|Porovnávání závorek|Když je textový kurzor umístěn na otevřené závorce v souboru kódu, je zvýrazněn jak na něm, tak na uzavírací závorku. Tato funkce poskytuje okamžitou zpětnou vazbu o chybně umístěných nebo chybějících závorkách. Pomocí nastavení **Automatické zvýraznění oddělovače** (Textový editor**možností** > **nástroje)** > můžete zapnout nebo vypnout shodu složených závorek.**Text Editor** Barvu zvýraznění můžete změnit v nastavení **Písma a barvy** **(Prostředí****voleb** > **nástrojů).** >  Vyhledejte **shodu svorek (zvýraznění)** nebo **složených závorek (obdélník).**|
|Vizualizér struktury|Tečkované čáry spojují odpovídající složená závorky v souborech kódu, což usnadňuje zobrazení párů počátečnía uzavírací svorky. To vám může pomoci najít kód v základu kódu rychleji. Tyto řádky můžete zapnout nebo vypnout pomocí **pokynů zobrazit strukturu** v části **Zobrazení** na stránce**Obecné** **textovéeditory** > **možností** >  **nástrojů.** > |
|Čísla řádků|Čísla řádků lze zobrazit v levém okraji okna kódu. Ve výchozím nastavení nejsou zobrazeny. Tuto možnost můžete zapnout v nastavení **Text editoru Všechny jazyky** **(Textové** > **editory** > **možností nástrojů** > **Všechny jazyky**). Čísla řádků pro jednotlivé programovací jazyky můžete zobrazit změnou nastavení pro tyto jazyky **(Možnosti** > **Options** > nástrojů**Text Editor** > **\<jazyk>**). Chcete-li vytisknout čísla řádků, musíte v **tiskovém** dialogovém okně vybrat zahrnout **čísla řádků.**|
|Sledování změn|Barva levého okraje umožňuje sledovat změny, které jste provedli v souboru. Změny provedené od otevření, ale neuložené souboru jsou označeny žlutým pruhem na levém okraji (označovaný jako okraj výběru). Po uložení změn (ale před zavřením souboru) se pruh změní na zelenou. Pokud po uložení souboru změnu vrátíte, změní se na oranžovou. Chcete-li tuto funkci vypnout a zapnout, změňte možnost **Sledovat změny** v nastavení **textového editoru** **(Textový editor****možností** > **nástrojů).** > |
|Výběr kódu a textu|Text můžete vybrat buď ve standardním režimu spojitého datového proudu, nebo v režimu rámečku, ve kterém vyberete obdélníkovou část textu namísto sady řádků. Chcete-li provést výběr v režimu pole, stiskněte **klávesu Alt** při tažení myší nad výběrem (nebo stiskněte**\<klávesu Alt ** **Alt**+**shift**+se šipkou>). Výběr zahrnuje všechny znaky v obdélníku definované prvním znakem a poslední znak ve výběru. Vše, co je zadáno nebo vloženo do vybrané oblasti, se vloží do stejného bodu na každém řádku.|
|Zoom|V libovolném okně kódu můžete přiblížit nebo oddálit stisknutím a podržením **klávesy Ctrl** a posunutím kolečka myši (nebo **Klávesy Ctrl**+**Shift**+**.** a **Ctrl**+**Shift**+**,** chcete-li snížit). Pole **Lupa** v levém dolním rohu okna kódu můžete také použít k nastavení určitého procenta zvětšení. Funkce lupy nefunguje v oknech nástrojů.|
|Virtuální prostor|Ve výchozím nastavení řádky v editorech sady Visual Studio končí za posledním znakem, takže **klávesa Šipka vpravo** na konci řádku přesune kurzor na začátek dalšího řádku. V některých jiných editorech řádek nekončí za posledním znakem a kurzor můžete umístit kdekoli na řádek. Virtuální prostor v editoru můžete povolit v nastavení**Textový editor** > **Možnosti** >  **nástrojů** > **Všechny jazyky.** Všimněte si, že můžete povolit **virtuální prostor** nebo **zalamování řádků**, ale ne obojí.|
|Tisk|Volby v **tiskovém** dialogovém okně můžete použít k zahrnutí čísel řádků nebo ke skrytí sbalených oblastí kódu při tisku souboru. V dialogovém okně **Vzhled stránky** můžete také zvolit tisk úplné cesty a názvu souboru výběrem **záhlaví Stránky**.<br /><br /> Volby barevného tisku můžete nastavit v dialogovém okně**Options** > **Environment** > **Písma a barvy** **prostředí nástrojů.** >  Chcete-li přizpůsobit barevný tisk, zvolte **Tiskárna** v seznamu **Zobrazit nastavení.** Pro tisk souboru můžete určit různé barvy než pro úpravy souboru.|
|Globální vrátit a znovu|Příkazy **Zpět na poslední globální akci** a Znovu provést poslední globální **akci** v nabídce **Úpravy** vrátit zpět nebo znovu provést globální akce, které mají vliv na více souborů. Globální akce zahrnují přejmenování třídy nebo oboru názvů, provedení operace hledání a nahrazení v rámci řešení, refaktoring databáze nebo jakoukoli jinou akci, která změní více souborů. Globální příkazy zpět a znovu můžete použít na akce v aktuální relaci sady Visual Studio, a to i po zavření řešení, ve kterém byla akce použita.|

## <a name="advanced-editing-features"></a>Pokročilé funkce úprav

V nabídce **Upravit** > **upřesnit** najdete na panelu nástrojů řadu pokročilých funkcí. Ne všechny tyto funkce jsou k dispozici pro všechny typy souborů kódu.

|||
|-|-|
|Formátovat dokument|Nastaví správné odsazení řádků kódu a přesune složené závorky tak, aby oddělovaly řádky v dokumentu.|
|Příkaz Formátovat výběr|Nastaví správné odsazení řádků kódu a přesune složené závorky tak, aby oddělily řádky ve výběru.|
|Tabulfikovat vybrané řádky|V případě potřeby změní úvodní mezery na tabulátory.|
|Zrušit zabezpečení vybraných řádků|Změní úvodní karty na mezery. Chcete-li převést všechny mezery v souboru na tabulátory (nebo `Edit.ConvertSpacesToTabs` `Edit.ConvertTabsToSpaces` všechny karty na mezery), můžete použít příkazy a. Tyto příkazy se nezobrazují v nabídkách sady Visual Studio, ale můžete je volat z okna **Rychlý přístup** nebo z příkazového okna.|
|Vytvořit velká písmena|Změní všechny znaky ve výběru na velká písmena, nebo pokud není žádný výběr, změní znak v kurzoru na velká písmena. Zástupce: **Ctrl**+**Shift**+**U**.|
|Vytvořit malá písmena|Změní všechny znaky ve výběru na malá písmena, nebo pokud není žádný výběr, změní znak v kurzoru na malá písmena. Zástupce: **Ctrl**+**U**.|
|Přesunout vybrané řádky nahoru|Přesune vybraný řádek o jeden řádek nahoru. Zástupce: **Alt**+**Šipka nahoru**.|
|Přesunout vybrané čáry dolů|Přesune vybranou čáru o jeden řádek dolů. Zástupce: **Alt**+**Šipka dolů**.|
|Odstranit vodorovné prázdné místo|Odstraní karty nebo mezery na konci aktuálního řádku. Zástupce: **Ctrl**+**K**, **Ctrl**+**\\**|
|Zobrazit prázdné místo|Zobrazí mezery jako zvýšené tečky a tabulátory jako šipky. Konec souboru je zobrazen jako obdélníkový glyf. Pokud je**vybraná** > volba**volby** >  **nástrojů** > Textový editor**Všechny jazyky,** > **zalamování** > **slov: Zobrazí se viditelné glyfy pro zalamování slov,** zobrazí se také tento glyf.|
|Zalamování řádků|Způsobí, že všechny řádky v dokumentu, které mají být viditelné v okně kódu. Zalamování a zapínání textu můžete vypnout a zapnout v**Options** >  **textovém editoru Všechny jazyky** (Textové**editory** > **možností nástrojů** > **Všechny jazyky).**|
|Výběr komentáře|Přidá znaky komentáře k výběru nebo k aktuálnímu řádku. Zástupce: **Ctrl**+**K**, **Ctrl**+**C**|
|Odkomentování výběru|Odebere znaky komentáře z výběru nebo aktuálního řádku. Zástupce: **Ctrl**+**K**, **Ctrl**+**U**|
|Zvětšit odsazení řádku|Přidá kartu (nebo ekvivalentní mezery) k vybraným řádkům nebo aktuálnímu řádku.|
|Zmenšení odsazení čáry|Odebere kartu (nebo ekvivalentní mezery) z vybraných řádků nebo aktuálního řádku.|
|Vybrat značku|V dokumentu, který obsahuje tagy (například XML nebo HTML), vybere značku.|
|Vybrat obsah značky|V dokumentu, který obsahuje tagy (například XML nebo HTML), vybere obsah.|

## <a name="navigate-and-find-code"></a>Navigace a hledání kódu

V editoru kódu se můžete pohybovat několika různými způsoby, včetně navigace vpřed a vpřed k předchozím kurzorovým bodům, zobrazení definice typu nebo člena a přechodu na konkrétní metodu pomocí navigačního panelu. Další informace naleznete v [tématu Navigate code](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Vyhledání referencí v základu kódu

Chcete-li zjistit, kde jsou v celém základu kódu odkazovány určité **prvky** kódu, můžete použít příkaz Najít všechny odkazy nebo stiskněte **klávesu Shift**+**F12**. Také když kliknete na typ nebo člen, funkce **zvýraznění odkazů** automaticky zvýrazní všechny odkazy na daný typ nebo člen. Další informace naleznete [v tématu Hledání odkazů v kódu](finding-references.md).

## <a name="customize-the-editor"></a>Přizpůsobení editoru

Nastavení sady Visual Studio můžete sdílet s jiným vývojářem, nastavit, aby odpovídalo standardu, nebo se vrátit k výchozímu nastavení sady Visual Studio pomocí **příkazu Průvodce nastavením importu a exportu** v nabídce **Nástroje.** V **Průvodci importem a exportem nastavení**můžete změnit vybraná obecná nastavení nebo nastavení jazyka a konkrétního projektu.

Chcete-li definovat nové klávesové zkratky nebo předefinovat existující klávesové zkratky, přejděte na tlačítko Klávesnice**prostředí** >  **Nástroje** > **možnosti** > **.** Další informace o klávesových zkratkách naleznete [v tématu Výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Možnosti editoru specifické pro JavaScript najdete v tématu [Možnosti editoru JavaScriptu](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Viz také

- [Zdrojový editor (Visual Studio pro Mac)](/visualstudio/mac/source-editor)
- [IDE visual studia](../get-started/visual-studio-ide.md)
- [Začínáme s C++ ve Visual Studiu](/cpp/get-started/tutorial-console-cpp)
- [Začínáme s C# a ASP.NET v Sadě Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Začínáme s Pythonem ve Visual Studiu](../ide/quickstart-python.md)
