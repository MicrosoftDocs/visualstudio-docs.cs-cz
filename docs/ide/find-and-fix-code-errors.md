---
title: Oprava chyb programu a vylepšení kódu
description: Tento článek popisuje některé základní způsoby, jak Visual Studio může pomoct najít a opravit problémy v kódu, včetně chyb sestavení, analýzy kódu, ladicích nástrojů a testování částí.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fa03dec65bcdc1e6c3af94200cfb6c46907e49
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476860"
---
# <a name="make-code-work-in-visual-studio"></a>Udělejte v aplikaci Visual Studio práci s kódem

Sada Visual Studio poskytuje výkonnou integrovanou sadu nástrojů pro sestavení a ladění projektu. V tomto článku zjistíte, jak vám může Visual Studio najít problémy v kódu pomocí výstupu sestavení, analýzy kódu, ladicích nástrojů a testování částí.

Načetli jste Editor a vytvořili nějaký kód. Nyní se chcete ujistit, že kód funguje správně. V aplikaci Visual Studio, stejně jako u většiny IDEs, existují dvě fáze pro provádění kódu: sestavení kódu pro zachycení a vyřešení chyb projektů a kompilátorů a spuštění kódu pro vyhledání běhového a dynamického chyb.

## <a name="build-your-code"></a>Sestavení kódu

Existují dva základní typy konfigurace sestavení: **ladění** a **vydání**. Konfigurace **ladění** vytváří pomalejší a větší spustitelný soubor, který umožňuje bohatší interaktivní prostředí ladění za běhu. Spustitelný soubor **ladění** by nikdy neměl být dodán. Konfigurace **vydané verze** vytváří rychlejší a optimalizovaný spustitelný soubor, který je vhodný k odeslání (alespoň z perspektivy kompilátoru). Výchozí konfigurace sestavení je **ladit**.

Nejjednodušší způsob, jak sestavit projekt, je stisknout **F7**, ale můžete také spustit sestavení výběrem možnosti **sestavit** > sestavit **řešení** z hlavní nabídky.

![Výběr nabídky projektu Visual Studio Build](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Proces sestavení můžete sledovat v okně **výstup** v dolní části uživatelského rozhraní sady Visual Studio. Zde jsou zobrazeny chyby, varování a operace sestavení. Pokud máte chyby (nebo pokud máte upozornění nad konfigurovanou úroveň), sestavení selhalo. Můžete kliknout na chyby a upozornění přejít na řádek, kde k nim došlo. Znovu sestavte projekt tak, že znovu stisknete klávesu **F7** (Chcete-li znovu kompilovat pouze soubory s chybami), nebo **Ctrl**+**ALT**+**F7** (pro vyčištění a dokončení opětovného sestavení).

V okně výsledky pod editorem jsou dvě okna s kartami: **výstupní** okno obsahující nezpracovaný výstup kompilátoru (včetně chybových zpráv); a okno **Seznam chyb** , které poskytuje seřaditelné a filtrovatelné seznamy všech chyb a upozornění.

Po úspěšném sestavení se v okně **výstup** zobrazí podobné výsledky:

![Výstup buildu pro Visual Studio se úspěšně vytvořil.](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Kontrola Seznam chyb

Pokud jste neudělali žádné úpravy kódu, který jste předtím a úspěšně zkompilujei, pravděpodobně došlo k chybě. Pokud začínáte s kódováním, pravděpodobně jich máte spoustu. Chyby jsou někdy zjevné, jako je například jednoduchá Chyba syntaxe nebo nesprávný název proměnné, někdy je obtížné porozumět s jediným nešifrovaným kódem, který vás provede. Pro vyčištění zobrazení problémů přejděte do dolní části okna **výstup** sestavení a klikněte na kartu **Seznam chyb** . Tím přejdete k lépe organizovanému zobrazení chyb a upozornění pro váš projekt a získáte i další možnosti.

![Výstup a Seznam chyb sady Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknutím na chybový řádek v okně **Seznam chyb** přejdete na řádek, ve kterém se nachází chyba. (Nebo zapněte čísla řádků stisknutím **kombinace kláves Ctrl**+**Q**, zadáním **čísel řádků**a výběrem možnosti **zapnout nebo vypnout čísla řádků** z výsledků. Toto je nejrychlejší způsob, jak se dostat do dialogového okna **Možnosti** , kde můžete zapnout čísla řádků.)

![Editor sady Visual Studio s čísly řádků](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Možnost čísel řádků sady Visual Studio](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Stisknutím **kombinace kláves Ctrl**+**G** můžete rychle přejít na číslo řádku, kde došlo k chybě.

Chyba je identifikována podtržením červené "vlnovce". Najeďte myší nad ním další podrobnosti. Ujistěte se, oprava a jeho přestane být zobrazována, i když zavádíte novou chybu s opravou. (Tato možnost se nazývá "regrese".)

![Chyba sady Visual Studio při najetí myší](../ide/media/vs_ide_gs_debug_error_hover1.png)

Projděte si seznam chyb a vyřešit všechny chyby v kódu.

![Okno chyby ladění sady Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Podrobně zkontrolovat chyby

Mnoho chyb může žádný smysl pro vás obsahuje jiné spojení jsou v podmínkách kompilátor. V těchto případech budete potřebovat další informace. V okně **Seznam chyb** můžete provést automatické vyhledávání Bingu, kde najdete další informace o chybě nebo upozornění. Pravým tlačítkem myši klikněte na odpovídající řádek vstupu a v místní nabídce vyberte možnost **zobrazit chybovou** nabídku nebo klikněte na hodnotu kódu chyby s hypertextovými odkazy ve sloupci **kód** **Seznam chyb**.

![Seznam chyb v aplikaci Visual Studio – vyhledávání Bingu](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

V závislosti na nastavení zobrazí webový prohlížeč výsledky hledání pro kód chyby a text, nebo se otevře karta v aplikaci Visual Studio a zobrazí výsledky vyhledávání Bingu. Výsledky jsou z mnoha různých zdrojů v Internetu, a nemusí být některé užitečné.

## <a name="use-code-analysis"></a>Použití analýzy kódu

Analyzátory kódu hledají běžné problémy s kódem, které mohou vést k chybám za běhu nebo problémům se správou kódu.

### <a name="c-and-visual-basic-code-analysis"></a>C#a Visual Basic analýzy kódu

Sada Visual Studio obsahuje integrovanou sadu [.NET Compiler Platform analyzátorů](../code-quality/roslyn-analyzers-overview.md) , které při psaní C# procházejí a Visual Basic kód. Můžete nainstalovat další analyzátory jako rozšíření sady Visual Studio nebo jako balíček NuGet. Pokud jsou porušení pravidel nalezena, jsou uvedena v Seznam chyb a v editoru kódu jako vlnovka pod problematickým kódem.

### <a name="c-code-analysis"></a>C++Analýza kódu

Chcete- C++ li analyzovat kód, spusťte [statickou analýzu kódu](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Buďte ve chvíli, kdy jste vyčistili zjevné chyby, které brání úspěšnému sestavení, a nějakou dobu chvíli vyřešíte, aby se zobrazila upozornění, která může vytvořit. Ušetříte si pár souvisejícím problémům správou po silnici a můžete se seznámit s několika technikami stylu kódu.

Stiskněte **Alt**+**F11** (nebo vyberte **analyzovat** > **Spustit analýzu kódu v rámci řešení** v horní nabídce) a spusťte tak statickou analýzu kódu.

![Položka nabídky analýzy Visual Studio Code](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Všechna nová nebo aktualizovaná upozornění se zobrazí na kartě **Seznam chyb** v dolní části rozhraní IDE. Kliknutím na upozornění můžete na ně přejít v kódu.

![Seznam chyb sady Visual Studio s upozorněními](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Použití rychlých akcí k opravě nebo refaktorování kódu

[Rychlé akce](../ide/quick-actions.md), které jsou k dispozici na žárovku nebo ikoně Screwdriver, umožňují refaktorování vloženého kódu. Představují snadný způsob, jak rychle a efektivně řešit běžná upozornění v C#, C++a Visual Basic kódu. Pokud k nim chcete přistupovat, klikněte pravým tlačítkem na vlnovku upozornění a vyberte **rychlé akce a refaktoring**. Pokud je kurzor na řádku s barevným vlnovkou, stiskněte klávesu **Ctrl**+ **.** nebo v okraji vyberte žárovku, chybovou žárovku nebo ikonu Screwdriver. Zobrazí se seznam možných oprav nebo refaktoringů, které můžete použít na tento řádek kódu.

![Ukázková žárovka sady Visual Studio – Preview](../ide/media/quick-actions-options.png)

Rychlé akce lze použít všude, kde analyzátory kódu určují možnost opravit, Refaktorovat nebo zdokonalit váš kód. Klikněte na libovolný řádek kódu, kliknutím pravým tlačítkem otevřete místní nabídku a vyberte **rychlé akce a refaktoring**. Pokud jsou k dispozici možnosti refaktoringu nebo vylepšení, jsou zobrazeny. Jinak zpráva **žádné rychlé akce, které jsou zde k dispozici** , se zobrazí v levém dolním rohu integrovaného vývojového prostředí (IDE).

![Text k dispozici nejsou žádné rychlé akce.](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Díky prostředí můžete rychle použít klávesy se šipkami a **Ctrl**+ **.** pro kontrolu jednoduchých příležitostí refaktoringu a vyčištění kódu!

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Spustit čištění kódu

Visual Studio poskytuje [formátování C# souboru kódu na vyžádání](code-styles-and-code-cleanup.md#apply-code-styles), včetně předvoleb stylu kódu, prostřednictvím tlačítka pro **Vyčištění kódu** v dolní části editoru.

![Tlačítko pro vyčištění kódu v aplikaci Visual Studio 2019](media/execute-code-cleanup.png)

Kromě formátování souboru pro prostory, odsazení, et zajistila, **Vyčištění kódu** také používá sadu konvencí stylu kódu, které definujete. Vaše předvolby pro jednotlivé styly kódu jsou čteny ze [souboru EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), pokud máte jeden pro projekt, nebo z [Nastavení stylu kódu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) v dialogovém okně **Možnosti** .

::: moniker-end

## <a name="debug-your-running-code"></a>Ladění spuštěného kódu

Teď, když jste úspěšně vytvořili kód a provedli trochu vyčištění, spusťte ho stisknutím klávesy **F5** nebo výběrem možnosti **ladění** > **Spustit ladění**. Tím spustíte aplikaci v ladicím prostředí, abyste mohli sledovat její chování podrobněji. Rozhraní IDE sady Visual Studio se změní, když je vaše aplikace spuštěná: okno **výstup** je nahrazeno dvěma novými (ve výchozí konfiguraci okna), okna Automatické hodnoty, místní hodnoty a **kukátko** a **zásobník volání/zarážky/nastavení výjimek/výstup** okna s kartami. Tato okna mají několik karet, které umožňují kontrolovat a vyhodnocovat proměnné aplikace, vlákna, zásobníky volání a různá další chování při jejich spuštění.

![Okna Automatické hodnoty a zásobník volání sady Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zastavte aplikaci stisknutím **klávesy Shift**+**F5** nebo kliknutím na tlačítko **zastavit** . Nebo můžete pouze Zavřít hlavní okno aplikace (nebo dialogové okno příkazového řádku).

Pokud váš kód běžel dokonale a přesně tak, jak bylo očekáváno, Blahopřejeme! Pokud se ale přestala nebo došlo k chybě nebo vám poskytla nějaké neobvyklé výsledky, bude nutné najít zdroje těchto problémů a opravit chyby.

### <a name="set-simple-breakpoints"></a>Nastavení jednoduchých zarážek

Základní a základní funkce spolehlivého ladění jsou [zarážky](../debugger/using-breakpoints.md) . Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští. Po nastavení a odebrání zarážek není nutné znovu sestavit projekt.

Nastavte zarážku kliknutím na téměř okraj řádku, kde chcete, aby došlo k přerušení, nebo stisknutím klávesy **F9** nastavte zarážku na aktuálním řádku kódu. Při spuštění kódu se pozastaví (nebo *přeruší*) před provedením pokynů pro tento řádek kódu.

![Zarážka sady Visual Studio](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Mezi běžná použití pro zarážky patří:

- Chcete-li zúžit zdroj chyby nebo zablokování, bodových zarážek v celém a kolem kódu volání metody, o které se domníváte, že to způsobuje chybu. Při spouštění kódu v ladicím programu odeberte a pak resetujte zarážky společně, dokud nenajdete problematický řádek kódu. V další části se dozvíte, jak spustit kód v ladicím programu.

- Při zavedení nového kódu nastavte zarážku na začátku a spusťte kód, abyste se ujistili, že se chová podle očekávání.

- Pokud jste implementovali složité chování, nastavte zarážky pro algoritmus Code, abyste mohli zkontrolovat hodnoty proměnných a dat při přerušení programu.

- Pokud píšete jazyk C nebo C++ kód, pomocí zarážek zastavte kód, abyste mohli zkontrolovat hodnoty adres (Hledat hodnoty null) a počty odkazů při ladění selhání souvisejících s pamětí.

Další informace o použití zarážek naleznete v tématu [použití zarážek](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Kontrola kódu v době běhu

Když váš běžící kód narazí na zarážku a pozastaví, řádek kódu označený žlutě (aktuální příkaz) ještě nebyl proveden. V tomto okamžiku můžete chtít spustit aktuální příkaz a potom zkontrolovat změněné hodnoty. K provedení kódu v ladicím programu můžete použít několik příkazů *kroku* . Pokud je označený kód volání metody, můžete do něj krokovat stisknutím klávesy **F11**. Můžete také *Krokovat* s řádkem kódu stisknutím klávesy **F10**. Další příkazy a podrobnosti o tom, jak procházet kód, najdete v tématu [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

![Kontrola běhové hodnoty v aplikaci Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na předchozí ilustraci můžete posunout ladicí program jedním příkazem stisknutím klávesy **F10** nebo **F11** (protože zde není žádné volání metody, oba příkazy mají stejný výsledek).

I když je ladicí program pozastaven, můžete zkontrolovat proměnné a zásobníky volání a zjistit, co se chystá. Jsou hodnoty v oblasti, které byste měli vidět? Volá se provádějí ve správném pořadí?

![Kontrola běhové hodnoty v aplikaci Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.png)

Pokud chcete zobrazit aktuální hodnotu a odkazy, najeďte myší na proměnnou. Pokud se zobrazí hodnota, kterou jste neočekávali, pravděpodobně máte chybu v předchozím nebo volajícím kódu. Chcete-li získat podrobné informace o ladění, [Přečtěte si další](../debugger/debugger-feature-tour.md) informace o používání ladicího programu.

Kromě toho Visual Studio zobrazí okno **diagnostické nástroje** , kde můžete sledovat využití procesoru a paměti vaší aplikace v průběhu času. Později ve vývoji aplikací můžete pomocí těchto nástrojů vyhledat neočekávané vysoké využití procesoru nebo přidělení paměti. Použijte ji ve spojení s oknem **kukátka** a zarážkami k určení toho, co způsobuje neočekávané vysoké využití nebo uvolnění prostředků. Další informace najdete v tématu [prohlídka funkcí profilace](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Spouštění testů jednotek

Testování částí jsou vaše první linií obrany proti chybám kódu, protože při správném provedení otestuje jednu "jednotku" kódu, obvykle jedinou funkci a je snazší ladit než úplný program. Visual Studio nainstaluje architektury testování částí od společnosti Microsoft pro spravovaný i nativní kód. Použití jednotkových testů vytvořit testy jednotek, spustit je a ohlásí výsledky těchto testů. Po provedení změn znovu spusťte testy jednotek, abyste otestovali, že váš kód stále pracuje správně. Pomocí edice Visual Studio Enterprise můžete testy spouštět automaticky po každém sestavení.

Chcete-li začít, přečtěte si téma [generování testů jednotek pro kód pomocí IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Chcete-li získat další informace o testování částí v aplikaci Visual Studio a o tom, jak vám pomohou vytvořit lepší kód kvality, přečtěte si [základy testování částí](../test/unit-test-basics.md).

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Další informace o používání ladicího programu](../debugger/index.yml)
- [Generování a oprava kódu](../ide/code-generation-in-visual-studio.md)
