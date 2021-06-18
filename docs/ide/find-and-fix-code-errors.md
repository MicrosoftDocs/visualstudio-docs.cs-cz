---
title: Oprava chyb programu a vylepšení kódu
description: Tento článek popisuje některé základní způsoby Visual Studio vám můžou pomoct najít a opravit problémy v kódu, včetně chyb sestavení, analýzy kódu, ladicích nástrojů a testů jednotek.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5af76de5dbcc7a70722acf0ee01cfed93dbad761
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308256"
---
# <a name="make-code-work-in-visual-studio"></a>Zpracujte kód v Visual Studio

Visual Studio poskytuje výkonnou integrovanou sadu nástrojů pro sestavování a ladění projektů. V tomto článku zjistíte, jak Visual Studio s hledáním problémů v kódu pomocí výstupu sestavení, analýzy kódu, ladicích nástrojů a testů jednotek.

Vy jste vytyšili editor a vytvořili nějaký kód. Teď se chcete ujistit, že kód funguje správně. V Visual Studio, stejně jako u většiny prostředí IDE, existují dvě fáze, jak kód fungovat: sestavení kódu pro zachycení a vyřešení chyb projektu a kompilátoru a spuštění kódu za běhu a dynamických chyb.

## <a name="build-your-code"></a>Sestavení kódu

Existují dva základní typy konfigurace sestavení: **Debug (Ladění)** a **Release (Verze).** Konfigurace **ladění** vytváří pomalejší, větší spustitelný soubor, který umožňuje bohatší interaktivní ladění za běhu. Spustitelný **soubor ladění** by nikdy neměl být odeslán. Konfigurace **vydání** sestaví rychlejší optimalizovaný spustitelný soubor, který je vhodný k odeslání (alespoň z pohledu kompilátoru). Výchozí konfigurace sestavení je **Debug (Ladit).**

Nejjednodušším způsobem, jak sestavit projekt, je stisknout **klávesu F7,** ale sestavení můžete spustit také tak, že v hlavní nabídce vyberete Sestavit řešení   >   sestavení.

![Visual Studio nabídky projektu sestavení](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Proces sestavení můžete sledovat v okně **Výstup** v dolní části Visual Studio uživatelského rozhraní. Tady se zobrazí chyby, upozornění a operace sestavení. Pokud dojde k chybám (nebo pokud máte upozornění vyšší než nakonfigurovaná úroveň), sestavení selže. Kliknutím na chyby a upozornění můžete přejít na řádek, kde k nim došlo. Znovu sestavte projekt opětovným stisknutím **klávesy F7** (aby se znovu zkompiloval pouze soubory s chybami) nebo **Ctrl** + **Alt** + **F7** (pro vyčištění a dokončení opětovného sestavení).

V okně výsledků pod editorem jsou dvě okna s kartami: okno **Výstup,** které obsahuje nezpracovaný výstup kompilátoru (včetně chybových zpráv). a **Seznam chyb,** které poskytuje seřaditelný a filtrovatelný seznam všech chyb a upozornění.

Po úspěšném sestavení se v okně Výstup zobrazí **následující** výsledky:

![Visual Studio úspěšného výstupu sestavení](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Kontrola Seznam chyb

Pokud jste ještě neupravili kód, který jste dříve a úspěšně zkompiloval, pravděpodobně se zobrazí chyba. Pokud s kódováním ještě nejste, pravděpodobně jich máte hodně. Chyby jsou někdy zřejmé, jako je jednoduchá chyba syntaxe nebo nesprávný název proměnné, a někdy jsou obtížně pochopitelné, ale jenom nesrozumitelný kód, který vás provede. Pokud chcete tyto problémy zobrazit čistější, přejděte  do dolní části okna výstupu sestavení a klikněte **na kartu Seznam chyb** sestavení. Tím získáte přehlednější přehled o chybách a upozorněních pro váš projekt a získáte také další možnosti.

![Visual Studio výstup a Seznam chyb](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknutím na řádek chyby v okně **Seznam chyb** přejdete na řádek, ve které dochází k chybě. (Nebo zapněte čísla řádků stisknutím kláves **Ctrl.** + **Otázka:** Zadejte **čísla řádků** a pak ve výsledcích zvolte Zapnout **nebo** vypnout čísla řádků. Jedná se o nejrychlejší způsob, jak se dostat do dialogového okna **Možnosti,** kde můžete zapnout čísla řádků.)

![Visual Studio editor s čísly řádků](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio čísla řádků](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Stisknutím **kláves Ctrl** + **G** můžete rychle přejít na číslo řádku, kde došlo k chybě.

Chybu identifikovalo červené podtržítko "squiggle". Další podrobnosti zobrazíte tak, že na něj najedete myší. Proveďte opravu a ta zmizí, i když s opravou můžete zavést novou chybu. (Tomu se říká "regrese".)

![Visual Studio chyba při najetí myší](../ide/media/vs_ide_gs_debug_error_hover1.png)

Projděte si seznam chyb a zaměňte všechny chyby v kódu.

![Visual Studio okno Chyby ladění](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Podrobná kontrola chyb

Mnoho chyb vám nemusí dávat smysl, protože jsou formulované v podmínkách kompilátoru. V těchto případech budete potřebovat další informace. V **Seznam chyb** můžete pomocí automatického vyhledávání Bingu vyhledat další informace o chybě nebo upozornění. Klikněte pravým tlačítkem na odpovídající  vstupní řádek a v místní nabídce vyberte Zobrazit nápovědu  k chybě nebo klikněte na hodnotu kódu chyby s hypertextovým odkazem ve sloupci Kód v **Seznam chyb**.

![Visual Studio seznamu chyb vyhledávání Bingu](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

V závislosti na nastavení buď webový prohlížeč zobrazí výsledky hledání kódu a textu chyby, nebo se uvnitř Visual Studio otevře karta a zobrazí výsledky vyhledávání Bingu. Výsledky jsou z mnoha různých zdrojů na internetu a ne všechny mohou být užitečné.

## <a name="use-code-analysis"></a>Použití analýzy kódu

Analyzátory kódu hledejí běžné problémy s kódem, které mohou vést k chybám za běhu nebo problémům při správě kódu.

### <a name="c-and-visual-basic-code-analysis"></a>C# a Visual Basic analýzy kódu

Visual Studio obsahuje integrovanou sadu analyzátorů .NET Compiler Platform, které prozkoumává jazyk C# a Visual Basic při psaní kódu. [](../code-quality/roslyn-analyzers-overview.md) Další analyzátory můžete nainstalovat jako Visual Studio nebo jako balíček NuGet. Pokud jsou nalezena porušení pravidel, nahlásily se v Seznam chyb i v editoru kódu jako podtržení podtržení pod nežádoucím kódem.

### <a name="c-code-analysis"></a>Analýza kódu C++

Pokud chcete analyzovat kód C++, spusťte [analýzu statického kódu](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Jakmile vyčistíte zřejmé chyby, které brání úspěšnému sestavení, můžete si zvykat jeho spuštění a chvíli trvat, než se budete zabývat upozorněními, která může vytvořit. Ušetříte si na cestách určité problémy a možná se naučíte několik technik stylu kódu.

Stisknutím **klávesy** + **Alt F11** (nebo výběrem možnosti Analyzovat spuštění Code Analysis v horní nabídce Řešení) spusťte  >  statickou analýzu kódu.

![Visual Studio Code nabídky Analýza](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

V dolní části integrovaného vývojového prostředí **se Seznam chyb** nová nebo aktualizovaná upozornění. Kliknutím na upozornění na ně přejdete v kódu.

![Visual Studio Seznam chyb s upozorněními](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Použití rychlých akcí k opravě nebo refaktoringu kódu

[Rychlé akce,](../ide/quick-actions.md)které jsou k dispozici na ikonu žárovky nebodriveru, umožňují refaktorovat vložený kód. Jsou snadným způsobem, jak rychle a efektivně opravit běžná upozornění v jazyce C#, C++ a Visual Basic kódu. Pokud k nim chcete získat přístup, klikněte pravým tlačítkem na upozornění a vyberte Rychlé akce a **refaktoring.** Nebo když je kurzor na čáře s barevným pohybem, stiskněte **Ctrl** + **.** nebo vyberte žárovku, žárovku s chybou nebo ikonudriveru na okraji. Zobrazí se seznam možných oprav nebo refaktoringů, které můžete použít pro tento řádek kódu.

![Visual Studio žárovky ve verzi Preview](../ide/media/quick-actions-options.png)

Rychlé akce lze použít všude tam, kde analyzátory kódu určují, že existuje příležitost k opravě, refaktoringu nebo vylepšení kódu. Klikněte na libovolný řádek kódu, kliknutím pravým tlačítkem otevřete místní nabídku a vyberte Rychlé akce a **refaktoring.** Pokud jsou k dispozici možnosti refaktoringu nebo vylepšení, zobrazí se. Jinak se v levém dolním **rohu integrovaného** vývojového prostředí zobrazí zpráva Žádné rychlé akce.

![Text nejsou k dispozici žádné rychlé akce](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Se zkušenostmi můžete rychle použít klávesy se šipkami a **ctrl** + **.** pro kontrolu snadných příležitostí refaktoringu a vyčištění kódu.

::: moniker range=">=vs-2019"

## <a name="run-code-cleanup"></a>Spuštění vyčištění kódu

Visual Studio poskytuje formátování souboru kódu [C#](code-styles-and-code-cleanup.md#apply-code-styles)na vyžádání , včetně předvoleb stylu kódu, prostřednictvím tlačítka **Vyčištění** kódu v dolní části editoru.

![Tlačítko Vyčištění kódu v Visual Studio 2019](media/execute-code-cleanup.png)

Kromě formátování souborů pro mezery, odsazení a další  funkce čištění kódu platí také sada konvencí stylu kódu, které definujete. Předvolby pro jednotlivé styly kódu se načtou ze souboru [EditorConfig,](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)pokud ho máte pro projekt, nebo z nastavení stylu kódu v **dialogovém okně** Možnosti. [](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box)

::: moniker-end

## <a name="debug-your-running-code"></a>Ladění spuštěného kódu

Teď, když jste úspěšně vytvořili kód a provedli trochu vyčištění, spusťte ho stisknutím **klávesy F5** nebo **výběrem možnosti Debug**  >  **Start Debugging (Ladění spustit ladění).** Tím spustíte aplikaci v ladicím prostředí, abyste mohli podrobně sledovat její chování. Integrované vývojové prostředí Visual Studio se změní, když  je vaše aplikace spuštěná: okno Výstup se nahradí dvěma novými okny (ve výchozí konfiguraci okna), oknem s kartami Automatické **hodnoty,** Místní hodnoty/ Sledování a Zásobník volání **/ Zarážky /** Nastavení výjimky / Výstup. Tato okna mají několik karet, které umožňují kontrolovat a vyhodnocovat proměnné, vlákna, zásobníky volání a různá další chování při spuštění aplikace.

![Visual Studio automatické funkce a okna zásobníku volání](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zastavte aplikaci stisknutím **klávesy Shift** + **F5** nebo kliknutím na **tlačítko Zastavit.** Nebo stačí zavřít hlavní okno aplikace (nebo dialogové okno příkazového řádku).

Pokud váš kód běžel dokonale a přesně podle očekávání, blahopřejeme! Pokud ale přestane reagovat nebo havaruje nebo vám poskytl neobvyklé výsledky, budete muset najít zdroj těchto problémů a opravit chyby.

### <a name="set-simple-breakpoints"></a>Nastavení jednoduchých zarážek

[Zarážky jsou](../debugger/using-breakpoints.md) nejzákladnější a nejzákladnější funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští. Po nastavení a odebrání zarážek nemusíte projekt znovu sestavovat.

Zarážku nastavíte kliknutím na okraj řádku, kde chcete přerušení procházet, nebo stisknutím klávesy **F9** nastavte zarážku na aktuálním řádku kódu. Když kód spustíte, pozastaví se (nebo přeruší) před provedením pokynů pro tento řádek kódu.

![Visual Studio zarážka](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Mezi běžná použití zarážek patří:

- Chcete-li zúžit zdroj chyby nebo nereagující program, bodové zarážky v celém kódu volání metody, o které si myslíte, že způsobuje selhání. Při spouštění kódu v ladicím programu odeberte a pak resetujte zarážky blíže k sobě, dokud nenajdete urážející řádek kódu. V další části se dozvíte, jak spustit kód v ladicím programu.

- Když zavádíte nový kód, nastavte zarážku na jeho začátku a spusťte kód, abyste se ujistili, že se chová podle očekávání.

- Pokud jste implementovali složité chování, nastavte zarážky algoritmického kódu, abyste mohli zkontrolovat hodnoty proměnných a dat, když se program přeruší.

- Pokud píšete kód jazyka C nebo C++, zastavte kód pomocí zarážek, abyste mohli kontrolovat hodnoty adres (hledejte hodnotu NULL) a počty odkazů při ladění chyb souvisejících s pamětí.

Další informace o používání zarážek najdete v oddílu [Použití zarážek](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Kontrola kódu za běhu

Když spuštěný kód narazí na zarážku a pozastaví se, řádek kódu označený žlutě (aktuální příkaz) se ještě nespouštěl. V tomto okamžiku můžete chtít spustit aktuální příkaz a pak zkontrolovat změněné hodnoty. Ke spuštění kódu v *ladicím* programu můžete použít několik krokových příkazů. Pokud je označený kód voláním metody, můžete do něj krokovat stisknutím **klávesy F11**. Stisknutím *klávesy* **F10** můžete také krokovat přes řádek kódu. Další příkazy a podrobnosti o krokování kódu najdete v tématu [Procházení kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

![Snímek obrazovky s Visual Studio kódu Červená tečka v levé okapové oblasti označuje zarážku na řádku kódu označeném žlutou barvou.](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na předchozím obrázku můžete pomocí **klávesy F10** nebo **F11** postoupit k jednomu příkazu ladicího programu (protože zde není žádné volání metody, oba příkazy mají stejný výsledek).

Když je ladicí program pozastavený, můžete zkontrolovat proměnné a zásobníky volání a určit, co se děje. Jsou hodnoty v rozsahu, které očekáváte? Provádí se volání ve správném pořadí?

![Snímek obrazovky s Visual Studio kódu Na řádku kódu označeném žlutě se vybere proměnná a v rozevíracím seznamu se zobrazí její aktuální hodnota a odkazy.](../ide/media/vs_ide_gs_debug_inspect_value.png)

Najeďte myší na proměnnou a zobrazte její aktuální hodnotu a odkazy. Pokud se zobrazí hodnota, kterou jste neočekává, pravděpodobně jste v předchozím nebo volajícím kódu měli chybu. Podrobnější informace o ladění najdete v [dalších informacích](../debugger/debugger-feature-tour.md) o používání ladicího programu.

Kromě Visual Studio okno **Diagnostické nástroje,** ve kterém můžete sledovat využití procesoru a paměti vaší aplikace v průběhu času. Později ve vývoji aplikace můžete pomocí těchto nástrojů hledat neočekávané vysoké využití procesoru nebo přidělení paměti. Použijte ho ve spojení s **oknem** watch a zarážkami k určení, co způsobuje neočekávané vysoké využití nebo nevydálené prostředky. Další informace najdete v tématu [Prohlídka funkcí profilace.](../profiling/profiling-feature-tour.md)

## <a name="run-unit-tests"></a>Spuštění testů jednotek

Testy jednotek jsou vaší první linií obrany proti chybám kódu, protože když se to dělá správně, testují jednu "jednotku" kódu, obvykle jednu funkci a jsou jednodušší ladit než celý program. Visual Studio nainstaluje rozhraní Microsoftu pro testování částí pro spravovaný i nativní kód. Pomocí rozhraní pro testování částí můžete vytvářet testy jednotek, spouštět je a hlásit výsledky těchto testů. Při provedení změn znovu spusťte testy jednotek a otestujte, jestli váš kód stále funguje správně. V Visual Studio Enterprise edici můžete testy spouštět automaticky po každém sestavení.

Pokud chcete začít, přečtěte si [o generování testů jednotek pro váš kód pomocí IntelliTestu.](../test/generate-unit-tests-for-your-code-with-intellitest.md)

Další informace o testech jednotek v Visual Studio a o tom, jak vám můžou pomoct vytvořit kód s lepší kvalitou, najdete v tématu [Základy testování částí.](../test/unit-test-basics.md)

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Další informace o používání ladicího programu](../debugger/index.yml)
- [Generování a oprava kódu](../ide/code-generation-in-visual-studio.md)
