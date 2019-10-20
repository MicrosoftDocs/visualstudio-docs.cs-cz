---
title: Funkce editoru kódu
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86cab4db7c732aeb33d9adf61bfdcb2c4563da57
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647049"
---
# <a name="features-of-the-code-editor"></a>Funkce editoru kódu

Editor sady Visual Studio poskytuje mnoho funkcí, které usnadňují zápis a správu kódu a textu. Můžete rozbalit a sbalit různé bloky kódu pomocí sbalení. Další informace o kódu lze získat pomocí technologie IntelliSense, **Prohlížeč objektů**a hierarchie volání. Kód můžete najít pomocí funkcí, jako je například **Přejít na**, **Přejít k definici**a **Najít všechny odkazy**. Můžete vložit bloky kódu s fragmenty kódu a můžete vygenerovat kód pomocí funkcí, jako je **generování z využití**. Pokud jste ještě nikdy nepoužívali Editor sady Visual Studio, přečtěte si téma [informace o použití editoru kódu](../get-started/tutorial-editor.md).

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [Editor zdrojového kódu (Visual Studio pro Mac)](/visualstudio/mac/source-editor).

Kód můžete zobrazit několika různými způsoby. Ve výchozím nastavení **Průzkumník řešení** zobrazuje kód uspořádaný podle souborů. Kliknutím na kartu **zobrazení tříd** v dolní části okna můžete zobrazit kód uspořádaný podle tříd.

Můžete hledat a nahrazovat text v jednom nebo více souborech. Další informace najdete v tématu [vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md). K vyhledání a nahrazení textu můžete použít regulární výrazy. Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Různé jazyky sady Visual Studio nabízejí různé sady funkcí a v některých případech se funkce chovají odlišně v různých jazycích. Mnohé z těchto rozdílů jsou uvedeny v popisech funkcí, ale další informace najdete v oddílech v konkrétních jazycích sady Visual Studio.

## <a name="editor-features"></a>Funkce editoru

|||
|-|-|
|Barevné zvýrazňování syntaxe|Některé prvky syntaxe kódu a souborů značek jsou jinak odlišeny. Například klíčová slova (například `using` v C# a `Imports` v Visual Basic) jsou jedna barva, ale typy (například `Console` a `Uri`) mají jinou barvu. Další prvky syntaxe jsou také barevně zabarvené, jako jsou řetězcové literály a komentáře. C++používá barvy k odlišení mezi typy, výčty a makry, mezi jinými tokeny.<br /><br /> Můžete zobrazit výchozí barvu pro každý typ a můžete změnit barvu pro kterýkoli konkrétní prvek syntaxe v [dialogovém okně písma a barvy, prostředí, možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), které můžete otevřít z nabídky **nástroje** .|
|Chybové a varovné značky|Když přidáte kód a sestavíte řešení, může se zobrazit (a) různě zbarvené podtržení vlnovkou (označované jako vlnovky) nebo (b), které se zobrazují ve vašem kódu. Červené vlnovky označují chyby syntaxe, modré značí chyby kompilátoru, varování zelených známek a fialově označuje jiné typy chyb. [Rychlé akce](../ide/quick-actions.md) naznačují opravy problémů a usnadňují použití opravy.<br /><br /> V dialogovém okně **nástroje**  > **možnosti**  > **prostředí**  > **písma a barvy** se zobrazí výchozí barva pro každou chybovou vlnovku a upozornění. Vyhledejte **syntaktickou chybu**, **chybu kompilátoru**, **Upozornění**a **Další chybu**.|
|Spárování složených závorek|Když je kurzor umístěn na levou složenou závorku v souboru kódu, zvýrazní se i pravá složená závorka. Tato funkce poskytuje okamžitou zpětnou vazbu na nesprávně umístěných nebo chybějících složených závorkách. Můžete zapnout nebo vypnout sjednocení složených závorek pomocí nastavení **automatického zvýraznění oddělovače** (**nástroje** > **Možnosti**-2  > **textový editor**). Můžete změnit barvu zvýraznění v nastavení **písma a barvy** (**nástroje** > **Možnosti**-2**prostředí** > ). Vyhledejte **párové závorky (zvýraznění)** nebo **spárování složených závorek (obdélník)** .|
|Vizualizér struktury|Tečkované čáry spojují párové závorky v souborech kódu, což usnadňuje zobrazení levé a pravé páry složených závorek. To vám pomůže rychle najít kód v základu kódu. Tyto řádky můžete zapnout nebo vypnout pomocí pokynů pro zobrazení **struktury** **v části Zobrazit** **na stránce** **nástroje** > **Možnosti** > **textový editor** > .|
|Čísla řádků|Čísla řádků se dají zobrazit na levém okraji okna Code (kód). Ve výchozím nastavení se nezobrazují. Tuto možnost můžete zapnout v nastavení **všechny jazyky v textovém editoru** (**nástroje** > **Možnosti**-2  > **textový editor** > **všechny jazyky**). Čísla řádků pro jednotlivé programovací jazyky můžete zobrazit tak, že změníte nastavení těchto jazyků (**nástroje** > **možnosti**-1  > **textový editor** >  **\<language >** ). Pro čísla řádků k tisku musíte vybrat možnost **Zahrnout čísla řádků** v dialogovém okně **Tisk** .|
|Sledování změn|Barva levého okraje umožňuje sledovat změny, které jste provedli v souboru. Změny, které jste provedli od otevření souboru, ale nebyly uloženy, jsou označeny žlutým pruhem na levém okraji (známé jako okraj výběru). Po uložení změn (ale před zavřením souboru) se pruh změní na zelený. Pokud po uložení souboru zrušíte změnu, pruh se změní na oranžová. Chcete-li tuto funkci vypnout a zapnout, změňte možnost **sledovat změny** v nastavení **textový editor** (**nástroje** > **Možnosti** > **textový editor**).|
|Výběr kódu a textu|Text můžete vybrat buď v režimu standardního souvislého datového proudu, nebo v režimu pole, ve kterém vyberete obdélníkovou část textu namísto sady řádků. Chcete-li provést výběr v režimu pole, stiskněte klávesu **ALT** při přetahování myší na výběr (nebo stiskněte klávesu **ALT**+**SHIFT**+ **\<arrow Key >** ). Výběr zahrnuje všechny znaky v obdélníku definované prvním znakem a posledním znakem ve výběru. Cokoliv, co jste zadali nebo vložili do vybrané oblasti, je vloženo na stejný bod na každém řádku.|
|Lupa|Stisknutím a podržením klávesy **CTRL** a přesunutím rolovacího kolečka myši (nebo **CTRL**+**SHIFT**+ můžete v jakémkoli okně kódu přiblížit nebo oddálit **.** pro zvýšení a **Ctrl**+**SHIFT**+ **,** aby se snížilo). Můžete také použít pole **Lupa** v levém dolním rohu okna kódu k nastavení konkrétního procenta zvětšení. Funkce přiblížení nefunguje v oknech nástrojů.|
|Virtuální prostor|Ve výchozím nastavení řádky v editorech sady Visual Studio končí za posledním znakem, takže **pravá šipka** na konci řádku přesune kurzor na začátek dalšího řádku. V některých dalších editorech řádek nekončí za posledním znakem a můžete umístit kurzor kamkoli na řádek. Virtuální prostor můžete v editoru povolit v nastavení **nástroje** > **možnosti**-1  >  v**textovém editoru** > **všechny jazyky** . Všimněte si, že můžete povolit buď **virtuální prostor** , nebo **zalamování řádků**, ale ne obojí.|
|Tisk|Můžete použít možnosti v dialogovém okně **Tisk** pro vložení čísel řádků nebo skrytí sbalených oblastí kódu při tisku souboru. V dialogovém okně **nastavení stránky** můžete také zvolit tisk celé cesty a názvu souboru výběrem **záhlaví stránky**.<br /><br /> Možnosti tisku barev můžete nastavit v dialogovém okně **nástroje**  > **možnosti**  > **prostředí**  > **písma a barvy** . Zvolením možnosti **tiskárna** v seznamu **Zobrazit nastavení pro** upravte barevný tisk. Můžete určit různé barvy pro tisk souboru, než pro úpravu souboru.|
|Globální akce zpět a znovu|Příkazy **vrátit zpět poslední globální akci** a **znovu provést poslední globální akce** v nabídce **Upravit** vrátí zpět nebo zopakují globální akce, které mají vliv na více souborů. Globální akce zahrnují přejmenování třídy nebo oboru názvů, provedení operace hledání a nahrazení v rámci řešení, refaktoringu databáze nebo jakékoli jiné akce, která změní více souborů. Můžete použít globální příkazy zpět a znovu pro akce v aktuální relaci sady Visual Studio, a to i po zavření řešení, ve kterém byla provedena akce.|

## <a name="advanced-editing-features"></a>Pokročilé funkce pro úpravy

Řadu pokročilých funkcí najdete v**Rozšířené** nabídce **Upravit** >  na panelu nástrojů. Ne všechny tyto funkce jsou k dispozici pro všechny typy souborů kódu.

|||
|-|-|
|Formátovat dokument|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků v dokumentu.|
|Příkaz Formátovat výběr|Nastaví správné odsazení řádků kódu a přesune složené závorky do samostatných řádků výběru.|
|Převést na tabulátory vybrané řádky|Změní úvodní mezery na tabulátory tam, kde je to vhodné.|
|Zrušit tabulátory vybrané řádky|Změní úvodní tabulátory na mezery. Pokud chcete převést všechny mezery v souboru na tabulátory (nebo na všechny karty na mezery), můžete použít příkazy `Edit.ConvertSpacesToTabs` a `Edit.ConvertTabsToSpaces`. Tyto příkazy se nezobrazují v nabídkách sady Visual Studio, ale můžete je volat z okna **rychlý přístup** nebo z příkazového okna.|
|Převést na velká písmena|Změní všechny znaky ve výběru na velká písmena, nebo pokud není vybrán žádný výběr, mění znak na pozici kurzoru na velká písmena. Zástupce: **Ctrl**+**SHIFT**+**U**.|
|Nastavit malými písmeny|Změní všechny znaky ve výběru na malá písmena nebo pokud není nic vybráno, změní znak na pozici kurzoru na malá písmena. Zástupce: **Ctrl**+**U**.|
|Přesunout vybrané řádky nahoru|Přesune vybraný řádek o jeden řádek nahoru. Zástupce: **Alt**+**šipka nahoru**.|
|Přesunout vybrané řádky dolů|Přesune vybraný řádek o jeden řádek dolů. Zástupce: **Alt**+**šipka dolů**.|
|Odstranit vodorovné prázdné znaky|Odstraní tabulátory nebo mezery na konci aktuálního řádku. Zástupce: **ctrl**+**K**, **CTRL**+ **\\**|
|Zobrazit prázdné znaky|Zobrazí mezery jako vystouplé tečky a tabulátory jako šipky. Konec souboru se zobrazí jako obdélníkový glyf. Pokud **nástroje**  > **Možnosti**  > **textový editor**  > **všechny jazyky**  > **zalamování** řádků  >  je vybrána možnost**Zobrazit viditelné glyfy pro zalamování řádků** , zobrazí se také tento glyf.|
|Zalamování řádků|Způsobí, že všechny řádky v dokumentu budou viditelné v okně Code (kód). Můžete zapnout nebo vypnout zalamování řádků v nastaveních **všechny jazyky v textovém editoru** (**nástroje** > **Možnosti**-2  > **textový editor** > **všechny jazyky**).|
|Výběr komentáře|Přidá znaky komentáře do výběru nebo aktuálního řádku. Zástupce: **ctrl**+**K**, **CTRL**+**C**|
|Odkomentovat výběr|Odebere znaky komentáře z výběru nebo aktuálního řádku. Zástupce: **ctrl**+**K**, **CTRL**+**U**|
|Zvětšit odsazení řádku|Přidá kartu (nebo ekvivalentní mezery) na vybrané řádky nebo aktuální řádek.|
|Zmenšit odsazení řádku|Odebere tabulátor (nebo ekvivalentní mezery) z vybraných řádků nebo aktuálního řádku.|
|Vybrat značku|V dokumentu, který obsahuje značky (například XML nebo HTML), vybere značku.|
|Vybrat obsah značky|V dokumentu, který obsahuje značky (například XML nebo HTML), vybere obsah.|

## <a name="navigate-and-find-code"></a>Navigace a hledání kódu

Můžete se pohybovat v editoru kódu několika různými způsoby, včetně přechodu zpět a vpřed na předchozí body vložení, zobrazení definice typu nebo člena a přechodem na konkrétní metodu pomocí navigačního panelu. Další informace najdete v tématu [Navigace v kódu](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Najít odkazy v základu kódu

Chcete-li zjistit, kde se v rámci základu kódu odkazuje na konkrétní prvky kódu, můžete použít příkaz **Najít všechny odkazy** nebo stiskněte klávesu **SHIFT**+**F12**. Kromě toho, když kliknete na typ nebo člen, funkce **zvýrazňování odkazů** automaticky zvýrazní všechny odkazy na daný typ nebo člen. Další informace najdete v tématu [Hledání odkazů v kódu](finding-references.md).

## <a name="customize-the-editor"></a>Přizpůsobení editoru

Nastavení sady Visual Studio můžete sdílet s jiným vývojářem, nechat vaše nastavení v souladu se standardem, nebo se můžete vrátit do výchozího nastavení sady Visual Studio pomocí příkazu **Průvodce importem a exportem nastavení** v nabídce **nástroje** . V **Průvodci importem a exportem nastavení**můžete změnit vybraná obecná nastavení nebo jazyk a nastavení specifické pro projekt.

Pro definování nových klávesových zkratek nebo předefinování existujících klávesových zkratek použijte**možnost** **nástroje**  >  možnosti  > **prostředí**  > **klávesnice**. Další informace o klávesových zkratkách naleznete v tématu [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Možnosti editoru specifické pro jazyk JavaScript najdete v tématu [Možnosti editoru JavaScriptu](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Viz také:

- [Editor zdrojového kódu (Visual Studio pro Mac)](/visualstudio/mac/source-editor)
- [Integrované vývojové prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
- [Začínáme s nástrojem C++ v aplikaci Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Začínáme s C# a ASP.NET v prostředí Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Začínáme s Pythonem v aplikaci Visual Studio](../ide/quickstart-python.md)
