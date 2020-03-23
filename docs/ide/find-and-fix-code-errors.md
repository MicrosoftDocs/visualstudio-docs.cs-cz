---
title: Oprava chyb programu a vylepšení kódu
description: Tento článek popisuje některé základní způsoby, jak visual studio vám může pomoci najít a opravit problémy v kódu, včetně chyb sestavení, analýzy kódu, ladicí nástroje a testy částí.
ms.date: 05/02/2018
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48fa03dec65bcdc1e6c3af94200cfb6c46907e49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77476860"
---
# <a name="make-code-work-in-visual-studio"></a>Zabezpečení kódu v sadě Visual Studio

Visual Studio poskytuje výkonnou integrovanou sadu nástrojů pro sestavení a ladění projektu. V tomto článku zjistěte, jak visual studio vám může pomoci najít problémy v kódu pomocí výstupu sestavení, analýzy kódu, ladicích nástrojů a testů částí.

Přišel jsi na editor a vytvořil nějaký kód. Nyní se chcete ujistit, že kód funguje správně. V sadě Visual Studio, stejně jako u většiny IDE, existují dvě fáze, které mají dělat práci kódu: vytváření kódu zachytit a vyřešit chyby projektu a kompilátoru a spuštění kódu najít za běhu a dynamické chyby.

## <a name="build-your-code"></a>Sestavení kódu

Existují dva základní typy konfigurace sestavení: **Ladění** a **vydání**. Konfigurace **ladění** vytváří pomalejší, větší spustitelný soubor, který umožňuje bohatší interaktivní prostředí ladění za běhu. Spustitelný soubor **ladění** by nikdy neměl být dodán. Konfigurace **vydání** vytvoří rychlejší, optimalizovaný spustitelný soubor, který je vhodný pro odeslání (alespoň z pohledu kompilátoru). Výchozí konfigurace sestavení je **Ladění**.

Nejjednodušší způsob, jak vytvořit projekt je stiskněte klávesu **F7**, ale můžete také spustit sestavení výběrem **sestavení** > **sestavení řešení** z hlavní nabídky.

![Výběr nabídky projektu sestavení sady Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Proces sestavení můžete sledovat v okně **Výstup** v dolní části uhlavního okna sady Visual Studio. Zde jsou zobrazeny chyby, upozornění a operace sestavení. Pokud máte chyby (nebo pokud máte upozornění nad nakonfigurovanou úroveň), sestavení se nezdaří. Můžete kliknout na chyby a varování jít na řádek, kde k nim došlo. Sestavte projekt buď opětovným stisknutím **klávesy F7** (chcete-li znovu zkompilovat pouze soubory s chybami) nebo **Ctrl**+**Alt**+**F7** (pro čisté a úplné opětovné sestavení).

V okně výsledků pod editorem jsou dvě okna s kartami: okno **Výstup,** které obsahuje výstup raw kompilátoru (včetně chybových zpráv); a okno **Seznam chyb,** které poskytuje seřaditelný a filtrovatelný seznam všech chyb a upozornění.

Když sestavení úspěšné, zobrazí výsledky, jako je tento v okně **Výstup:**

![Výstup úspěšného sestavení sady Visual Studio](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Kontrola seznamu chyb

Pokud jste neprovedli žádné změny kódu, který jste dříve a úspěšně zkompilovali, pravděpodobně dojde k chybě. Pokud jste s kódováním noví, pravděpodobně jich máte spoustu. Chyby jsou někdy zřejmé, například jednoduchá syntaktická chyba nebo nesprávný název proměnné, a někdy je obtížné je pochopit, pouze s tajemným kódem, který vás provede. Chcete-li zobrazit přehled o problémech, přejděte do dolní části okna **Výstup** sestavení a klepněte na kartu **Seznam chyb.** Tím přejdete k přehlednějšímu zobrazení chyb a upozornění pro váš projekt a získáte také několik dalších možností.

![Výstup a seznam chyb sady Visual Studio](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Kliknutím na řádek chyby v okně **Seznam chyb** přejdete na řádek, ve které k chybě dochází. (Nebo zapněte čísla řádků stisknutím **klávesCtrl**+**Q**, zadáním **čísel řádků**a pak zvolte **Zapnout nebo vypnout čísla řádků** z výsledků. Jedná se o nejrychlejší způsob, jak se dostat do dialogového okna **Možnosti,** kde můžete zapnout čísla řádků.)

![Editor Visual Studia s čísly řádků](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Možnost čísla řádků ve visual studiu](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Stisknutím **klávesy Ctrl**+**G** rychle přejděte na číslo řádku, kde došlo k chybě.

Chyba je identifikována červeným "vlnovkou" podtržítkem. Najeďte nad ním pro další podrobnosti. Proveďte opravu a to zmizí, i když můžete zavést novou chybu s opravou. (Tomu se říká "regrese".)

![Najezení chyby visual studia](../ide/media/vs_ide_gs_debug_error_hover1.png)

Projděte si seznam chyb a adresujte všechny chyby v kódu.

![Okno chyb ladění sady Visual Studio](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Podrobné projděte si chyby

Mnoho chyb nemusí mít smysl pro vás, formulované jako jsou v podmínkách kompilátoru. V těchto případech budete potřebovat další informace. V okně **Seznam chyb** můžete provést automatické vyhledávání bingu, kde naleznete další informace o chybě nebo upozornění. Klikněte pravým tlačítkem myši na odpovídající řádek položky a v místní nabídce vyberte zobrazit **nápovědu k chybě** nebo klikněte na hodnotu kódu chyby s hypertextovým odkazem ve sloupci **Kód** **seznamu chyb**.

![Hledání bingu v seznamu chyb sady Visual Studio](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

V závislosti na vašem nastavení se ve webovém prohlížeči zobrazí výsledky hledání kódu chyby a textu nebo se v sadě Visual Studio otevře karta s výsledky hledání Bingem. Výsledky jsou z mnoha různých zdrojů na internetu, a ne všechny mohou být užitečné.

## <a name="use-code-analysis"></a>Použít analýzu kódu

Analyzátory kódu hledat běžné problémy kódu, které mohou vést k chybám za běhu nebo problémy ve správě kódu.

### <a name="c-and-visual-basic-code-analysis"></a>Analýza kódu jazyka C# a jazyka Visual Basic

Visual Studio obsahuje integrovanou sadu [analyzátorů platformy kompilátoru .NET,](../code-quality/roslyn-analyzers-overview.md) které při psaní zkoumají kód jazyka C# a visual basic. Můžete nainstalovat další analyzátory jako rozšíření Sady Visual Studio nebo jako balíček NuGet. Pokud jsou nalezeny porušení pravidel, jsou hlášeny v seznamu chyb a v editoru kódu jako klikyháky pod problematický kód.

### <a name="c-code-analysis"></a>Analýza kódu jazyka C++

Chcete-li analyzovat kód jazyka C++, spusťte [analýzu statického kódu](/cpp/code-quality/quick-start-code-analysis-for-c-cpp). Získejte ve zvyku spustit, jakmile jste vyčistit zjevné chyby, které brání úspěšné sestavení, a nějakou dobu trvat, než řešit varování, která může produkovat. Ušetříte si nějaké bolesti hlavy po silnici, a můžete se naučit několik technik stylu kódu.

Stisknutím **klávesy Alt**+**F11** (nebo vyberte **možnost Analyzovat** > **analýzu kódu spuštění v řešení** v horní nabídce) a spusťte analýzu statického kódu.

![Položka nabídky analýzy kódu aplikace Visual Studio](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Všechna nová nebo aktualizovaná upozornění se zobrazí na kartě **Seznam chyb** v dolní části rozhraní IDE. Klikněte na varování skočit na ně v kódu.

![Seznam chyb sady Visual Studio s upozorněními](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-quick-actions-to-fix-or-refactor-code"></a>Použití rychlých akcí k opravě nebo refaktorování kódu

[Rychlé akce](../ide/quick-actions.md), které jsou k dispozici na ikoně žárovky nebo šroubováku, umožňují refaktorovat kód vtextu. Jedná se o snadný způsob, jak opravit běžné upozornění rychle a efektivně v kódu Jazyka C#, C++ a Visual Basic. Chcete-li k nim získat přístup, klikněte pravým tlačítkem myši na vlnovku upozornění a vyberte **možnost Rychlé akce a refaktoringy**. Nebo když je kurzor na řádku s barevnými vlnovkami, stiskněte **ctrl**+**.** nebo vyberte na okraji žárovku, chybovou žárovku nebo ikonu šroubováku. Zobrazí se seznam možných oprav nebo refaktoringů, které můžete použít pro tento řádek kódu.

![Náhled žárovky Visual Studio](../ide/media/quick-actions-options.png)

Rychlé akce lze použít všude tam, kde analyzátory kódu zjistí, že je příležitost opravit, refaktorovat nebo zlepšit kód. Klikněte na libovolný řádek kódu, kliknutím pravým tlačítkem otevřete kontextovou nabídku a vyberte **rychlé akce a refaktoringy**. Pokud jsou k dispozici možnosti refaktoringu nebo zlepšení, zobrazí se. V opačném případě se v levém dolním rohu rozhraní IDE zobrazí zpráva **Žádné rychlé akce, které jsou k dispozici.**

![Není k dispozici žádný text rychlých akcí](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

Se zkušenostmi můžete rychle použít klávesy se šipkami a **Ctrl**+**.** zkontrolovat snadné možnosti refaktoringu a vyčistit kód!

::: moniker range="vs-2019"

## <a name="run-code-cleanup"></a>Spustit vyčištění kódu

Visual Studio poskytuje formátování kódu [C# na vyžádání](code-styles-and-code-cleanup.md#apply-code-styles), včetně předvoleb stylu kódu, pomocí tlačítka **Vyčištění kódu** v dolní části editoru.

![Tlačítko Vyčištění kódu v Visual Studiu 2019](media/execute-code-cleanup.png)

Kromě formátování souboru pro mezery, odsazení a tak dále, **Vyčištění kódu** také použije sadu konvencí stylu kódu, které definujete. Vaše předvolby pro každý styl kódu jsou čteny ze [souboru EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), pokud máte jeden pro projekt nebo z [nastavení stylu kódu](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) v dialogovém okně **Možnosti.**

::: moniker-end

## <a name="debug-your-running-code"></a>Ladění spuštěný kód

Nyní, když jste úspěšně vytvořili kód a provedli trochu vyčistit, spusťte jej stisknutím **klávesy F5** nebo výběrem **ladění** > **Start Ladění**. Tím se spustí aplikace v prostředí ladění, takže můžete sledovat její chování v detailu. IDE sady Visual Studio se mění, když je vaše aplikace spuštěná: okno **Výstup** je nahrazeno dvěma novými (ve výchozí konfiguraci okna), okno **autos/locals/watch** s kartami a okno **Stojánek/Zarážky/Nastavení výjimek/Výstup.** Tato okna mají více karet, které umožňují kontrolovat a vyhodnocovat proměnné, vlákna, zásobníky volání a různá další chování při jeho spuštění.

![Okna autos a zásobníkvolání sady volání sady Visual Studio](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zastavte aplikaci stisknutím **Shift**+**F5** nebo kliknutím na tlačítko **Zastavit.** Nebo můžete zavřít hlavní okno aplikace (nebo dialogové okno příkazového řádku).

Pokud váš kód běžel perfektně a přesně podle očekávání, gratulujeme! Nicméně, pokud to visel, nebo havaroval, nebo vám nějaké podivné výsledky, budete muset najít zdroj těchto problémů a opravit chyby.

### <a name="set-simple-breakpoints"></a>Nastavení jednoduchých zarážek

[Zarážky](../debugger/using-breakpoints.md) jsou nejzákladnější a základní funkce spolehlivé ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští. Po nastavení a odebrání zarážek není nutné znovu sestavit projekt.

Nastavte zarážku klepnutím na vzdálenější okraj řádku, kde má dojít k zalomení, nebo stisknutím **klávesy F9** nastavte zarážku na aktuálním řádku kódu. Při spuštění kódu se pozastaví (nebo *přeruší)* před provedením pokynů pro tento řádek kódu.

![Zarážka visual studia](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Mezi běžné použití zarážek patří:

- Chcete-li zúžit zdroj selhání nebo zablokování, bodový zarážky v celém kódu volání metody si myslíte, že je příčinou selhání. Při spuštění kódu v ladicím programu odeberte a potom obnovte zarážky blíže k sobě, dokud nenajdete problematický řádek kódu. V další části se dozvíte, jak spustit kód v ladicím programu.

- Při zavádění nového kódu nastavte zarážku na začátku a spusťte kód a ujistěte se, že se chová podle očekávání.

- Pokud jste implementovali složité chování, nastavte zarážky pro algoritmický kód, abyste mohli zkontrolovat hodnoty proměnných a dat při přerušení programu.

- Pokud píšete kód C nebo C++, použijte zarážky k zastavení kódu, abyste mohli zkontrolovat hodnoty adres (vyhledejte hodnotu NULL) a počty odkazů při ladění chyb souvisejících s pamětí.

Další informace o použití zarážek naleznete v článek [Použití zarážek](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Kontrola kódu za běhu

Když váš spuštěný kód narazí na zarážku a pozastaví, řádek kódu označené žlutě (aktuální příkaz) dosud nebylproveden. V tomto okamžiku můžete chtít provést aktuální příkaz a potom zkontrolovat změněné hodnoty. Ke spuštění kódu v ladicím programu můžete použít několik *příkazů kroku.* Pokud je označený kód volání mačkáním, můžete do něj vstoupit stisknutím **klávesy F11**. Můžete také *krok přes* řádek kódu stisknutím **klávesy F10**. Další příkazy a podrobnosti o tom, jak krokovat kód, najdete v části [Navigace v kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).

![Kontrola hodnoty za běhu sady Visual Studio](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

Na předchozím obrázku můžete posunout ladicí program jeden příkaz stisknutím **f10** nebo **F11** (protože zde není volání metody, oba příkazy mají stejný výsledek).

Zatímco ladicí program je pozastaven, můžete zkontrolovat proměnné a zásobníky volání k určení, co se děje. Jsou hodnoty v rozsahu, který očekáváte, že uvidíte? Jsou hovory ve správném pořadí?

![Kontrola hodnoty za běhu sady Visual Studio](../ide/media/vs_ide_gs_debug_inspect_value.png)

Najeďte nad proměnnou, abyste viděli její aktuální hodnotu a odkazy. Pokud se zobrazí hodnota, kterou jste nečekali, pravděpodobně máte chybu v předchozím nebo volajícím kódu. Podrobnější informace o ladění najdete v [dalších informacích](../debugger/debugger-feature-tour.md) o použití ladicího programu.

Visual Studio navíc zobrazí diagnostické **nástroje** okno, kde můžete sledovat využití procesoru a paměti aplikace v průběhu času. Později ve vývoji aplikací můžete pomocí těchto nástrojů vyhledat neočekávané vysoké využití procesoru nebo přidělení paměti. Použijte jej ve spojení s okno **kukátka** a zarážky k určení, co je příčinou neočekávané hojné využití nebo nevydané prostředky. Další informace naleznete v [tématu Profilování funkce turné](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Spuštění testů jednotek

Testy částí jsou vaše první linie obrany proti chybám kódu, protože při správném dokončení testují jednu "jednotku" kódu, obvykle jednu funkci a je snazší ladit než celý program. Visual Studio nainstaluje rozhraní microsoft testování částí pro spravovaný i nativní kód. Pomocí rozhraní testování částí vytvořit testování částí, spusťte je a sestavy výsledků těchto testů. Znovu spustit testy částí při provádění změn, chcete-li otestovat, že váš kód stále pracuje správně. S Visual Studio Enterprise edition, můžete spustit testy automaticky po každém sestavení.

Chcete-li začít, [přečtěte si článek Generovat testy částí kódu pomocí intelliTestu](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Další informace o testování částí v sadě Visual Studio a o tom, jak vám můžou pomoct vytvořit kód lepší kvality, najdete v [základech testování částí](../test/unit-test-basics.md).

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Další informace o používání ladicího programu](../debugger/index.yml)
- [Generování a oprava kódu](../ide/code-generation-in-visual-studio.md)
