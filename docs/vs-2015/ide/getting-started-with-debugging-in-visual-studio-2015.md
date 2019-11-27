---
title: Začínáme s laděním v sadě Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe8b158fd870b83b39b9d316e68582f2726d89bb
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300198"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Začínáme s laděním v sadě Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2015 poskytuje výkonné integrované sady sestavení projektu a nástroje pro ladění. V tomto tématu zjistěte, jak chcete začít používat nejzákladnější nastavení ladění funkcí uživatelského rozhraní.

 Poznámka: Jsou odkazy na další pokročilé funkce a témata konkrétní platformy nebo funkce v dolní části této stránky.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Můj kód nebude fungovat. Pomozte mi, sadě Visual Studio 2015.
 Takže stanovíte editoru a vytvoříte nějaký kód. Teď budete chtít spustit ladění kódu. V sadě Visual Studio 2015, stejně jako u většiny prostředí IDE, jsou dvě fáze až po ladění: sestavování kódu zachytit a řešení chyb při projektu a kompilátoru; a spuštění kódu v prostředí k zachycení a řešení chyb za běhu a dynamické.

### <a name="configuring-a-build"></a>Konfigurace sestavení
 Existují dva základní typy konfigurace sestavení: **ladění** a **vydání**. První konfigurace vytvoří pomalejší, větší spustitelný soubor, který umožňuje pohodlnější a pestřejší interaktivní ladění prostředí za běhu, ale nikdy dodání. Druhá sestavení rychlejší, více optimalizované spustitelný soubor, který je vhodný k odeslání (alespoň z hlediska kompilátor).

 Výchozí konfigurace sestavení je **ladit**.

 ![Tlačítko pro sestavení ladění sady Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Můžete také zadat konkrétní platformu sestavení, kterou chcete cílit, jako je například **x86** (32 procesory Intel), **x64** (64 procesory Intel) a **ARM** (procesory ARM, podporované jenom pro určité typy aplikací). Výchozí hodnota je **x86** pro spravované a nativní projekty. Pokud ho chcete změnit, klikněte na rozevírací seznam Build Platform a vyberte jinou platformu nebo **Configuration Manager...**

 ![Okno Správce konfiguračních souborů sady Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Můžete zadat cílovou konfiguraci sestavení pomocí **Configuration Manager**. Spusťte ji, klikněte na rozevírací seznam **Konfigurace** nebo **procesor** a vyberte **Nový...** Chcete-li vytvořit nové sestavení nebo platformu.

 ![Okno Configuration Manager sady Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Od toho stačí použít **ladění** a **x86** jako konfiguraci a platformu sestavení v uvedeném pořadí. Až budete hotovi s kódováním a laděním, změňte konfiguraci na **release** a Zaměřte se na konkrétní platformu. (Starší verze sady Visual Studio poskytovaly výchozí platformu **anycpu** pro projekty kódu .NET.)

 Poznámka: Při sestavování projektu hodnoty konfigurace a platforma se také používají k určení, jaké cesta k adresáři projektu se vytvoří spustitelný soubor. Obvykle se jedná **o\<>ch cest k projektu\\< Project-name\>\\< configuration\>\\< platform\>** . Například projekt s konfigurací `Debug` a platformou `x86` se nachází v části `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. To může být užitečné, pokud máte vlastní nástroje nebo skripty, které Správa těchto sestavené spustitelné soubory.

### <a name="building-your-code"></a>Vytváření kódu
 Ve vašem sestavení nakonfigurované je čas vytvořit projekt. Nejjednodušší způsob, jak to provést stisknutím klávesy F7, můžete také spustit sestavení výběrem **řešení sestavení Build-> Build** z hlavní nabídky.

 ![Výběr nabídky projektu Visual Studio Build](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Proces sestavení můžete sledovat v okně stav **výstupu** v dolní části uživatelského rozhraní sady Visual Studio. Zde jsou zobrazeny chyby, varování a operace sestavení. Pokud už máte chyby (nebo pokud máte nad nakonfigurovanou úrovní upozornění), vaše sestavení se nezdaří. Můžete kliknout na chyby a upozornění přejít na řádek, kde k nim došlo. Znovu sestavte projekt stisknutím klávesy **F7** znovu (Chcete-li znovu kompilovat pouze soubory s chybami) nebo **CTRL + ALT + F7** (pro vyčištění a dokončení opětovného sestavení).

 V okně výsledky pod editorem jsou dvě okna sestavení s kartami: **výstupní** okno obsahující nezpracovaný výstup kompilátoru (včetně chybových zpráv); a okno **Seznam chyb** , které poskytuje seřaditelné a filtrovatelné seznamy všech chyb a upozornění.

 Po úspěšném zobrazení v okně **výstup** se zobrazí podobné výsledky.

 ![Výstup buildu pro Visual Studio se úspěšně vytvořil.](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Kontrola seznamu chyb
 Pokud jste provedli žádné úpravy kódu, který jste dříve a úspěšně sestavili, pravděpodobně jste chybu. Pokud začínáte programování, pravděpodobně máte mnoho z nich. Chyby jsou někdy zřejmé, například Chyba jednoduché syntaxe nebo nesprávný název proměnné a někdy jsou těžko pochopitelné, nejasné kód a provede vás. Pro vyčištění zobrazení problémů přejděte do dolní části okna **výstup** sestavení a klikněte na kartu **Seznam chyb** . Tím přejdete k lépe organizovanému zobrazení chyb a upozornění pro váš projekt a získáte i další možnosti.

 ![Výstup a Seznam chyb sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 V okně **Seznam chyb** klikněte na chybový řádek a přejděte na řádek, ve kterém se nachází chyba. (Nebo zapněte čísla řádků kliknutím na panel **snadného spuštění** v pravém horním rohu zadejte "čísla řádků" a stiskněte klávesu ENTER. Toto je nejrychlejší způsob, jak se dostat do položky okna **Možnosti** , kde můžete zapnout čísla řádků. Naučte se používat panel **snadného spuštění** a ušetřit spoustu kliknutí na uživatelské rozhraní.

 ![Editor sady Visual Studio s čísly řádků](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Možnost čísel řádků sady Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Pomocí kombinace kláves Ctrl + G rychle přejít k číslu řádku kde došlo k chybě.

 Chyba je identifikována red "klikatá" podtržítkem. Najeďte myší nad ním další podrobnosti. Ujistěte se, oprava a jeho přestane být zobrazována, i když zavádíte novou chybu s opravou. (Tomu se říká "regrese".)

 ![Chyba sady Visual Studio při najetí myší](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Projděte si seznam chyb a vyřešit všechny chyby v kódu.

 ![Okno chyby ladění sady Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Kontrola chyb podrobně
 Mnoho chyb může žádný smysl pro vás obsahuje jiné spojení jsou v podmínkách kompilátor. V takových případech můžete potřebovat další informace. V okně **Seznam chyb** můžete provést automatické vyhledávání Bingu, kde najdete další informace o chybě (nebo upozornění) tak, že kliknete pravým tlačítkem myši na odpovídající vstupní řádek a v místní nabídce vyberete **Zobrazit nápovědu k chybám** .

 ![Seznam chyb v aplikaci Visual Studio – vyhledávání Bingu](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Tím se spustí na kartě Visual Studio 2015, že hostitelé výsledky Bingu vyhledat kód chyby a text. Výsledky jsou z mnoha různých zdrojů v Internetu, a nemusí být některé užitečné.

 Případně můžete kliknout na hodnotu kódu chyby s hypertextovými odkazy ve sloupci **kód** **Seznam chyb**. Tím se spustí vyhledávání Bingu pouze kód chyby.

### <a name="performing-static-code-analysis"></a>Provádí statickou analýzu kódu
 "Statickou analýzu kódu" je nápadité způsob říkáme "Automatická kontrola můj kód pro běžné problémy, které může mít za následek chyby za běhu nebo problémy v kódu správy". Získejte v podporují ho spustíte, když jste odstranili jasné chyby, kvůli kterým sestavení a k vyřešení upozornění, který může vytvořit nějakou dobu trvat. Vás bude ušetříte si některé obrovskému dolů cestách, jakož i další několik technik styl kódu.

 Stiskněte ALT + F11 (nebo vyberte **analyzovat-> spustit analýzu kódu v rámci řešení** v horní nabídce) a spusťte tak statickou analýzu kódu. Pokud máte velké množství kódu, může to chvíli trvat.

 ![Položka nabídky analýzy kódu sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Všechna nová nebo aktualizovaná upozornění se zobrazí na kartě **Seznam chyb** v dolní části rozhraní IDE. Klikněte na upozornění můžete přejít k nim.

 ![Visual Studio 2015 Seznam chyb s upozorněními](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Upozornění budou označena jasné vlnovku žlutá zelená místo červené. Najeďte myší nad nimi další podrobnosti a klikněte pravým tlačítkem na, abyste získali kontextové nabídky, které pomáhají při opravy nebo možnosti refaktorování.

 ![Upozornění analýzy Visual Studio Code – najetí myší](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Pomocí nabídky návrhy pro opravu nebo Refaktorování kódu
 Ikony žárovky jsou novou funkcí pro Visual Studio 2015, které vám umožňují vložený kód Refaktorovat. Jsou snadný způsob, jak vyřešit běžné upozornění rychle a efektivně. Pro přístup k nim, klikněte pravým tlačítkem na varování vlnovku (nebo stiskněte klávesy Ctrl +. Při najetí myší na vlnovku) a pak vyberte **rychlé akce**.

 ![Rychlé možnosti žárovky sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Zobrazí se seznam možných opravy nebo refactors, které můžete provést u tohoto řádku kódu.

 ![Visual Studio 2015 – Preview verze Preview](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Ikony žárovky je možné bez ohledu na to analyzátorů kódu určit, že není příležitost opravit, refaktorace, nebo vylepšení vašeho kódu. Klikněte na libovolný řádek kódu, kliknutím pravým tlačítkem otevřete kontextovou nabídku a vyberte možnost **rychlé možnosti** (nebo znovu, pokud chcete preferovat efektivitu, stiskněte kombinaci kláves CTRL +.). Pokud jsou k dispozici možnosti refaktoringu a vylepšení oblasti, zobrazí se. v opačném případě se `No quick options available here` zpráva zobrazí v levém dolním rohu integrovaného vývojového prostředí (IDE).

 ![Text "bez možnosti" sady Visual Studio 2015 Light žárovky](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 S prostředím můžete rychle použít klávesy se šipkami a Ctrl +. ke kontrole rychlé možnost refaktoring příležitosti a vyčistit váš kód!

 Další informace o žárovkách najdete v článku [provádění rychlých akcí pomocí](../ide/perform-quick-actions-with-light-bulbs.md)žárovek.

### <a name="debugging-your-running-code"></a>Ladění spouštění kódu
 Teď, když jste úspěšně vytvořili kód a provedli trochu vyčištění, spusťte ho stisknutím klávesy F5 nebo výběrem **ladění > spustit ladění**. Tím se spustí vaši aplikaci v prostředí ladění, tak můžete sledovat jeho chování podrobně. Rozhraní IDE sady Visual Studio 2015 se během vaší aplikace změní: okno **výstup** je nahrazeno dvěma novými (ve výchozím nastavení výchozí okno), okna Automatické hodnoty **/místní hodnoty/moduly/kukátko** a okno **volání/zarážky/nastavení výjimky/výstup** okna s kartami. Tato okna mít více karet, které vám umožní kontrolovat a vyhodnocovat proměnné vaší aplikace, vlákna, zásobníky volání a různé další chování za běhu.

 ![Okna Automatické hodnoty a zásobník volání VS2015](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Zkuste různé akce s vaší aplikací a sledování změn. Pokud se vyskytne něco neobvyklého, pozastaví aplikaci stisknutím kombinace kláves CTRL + ALT + BREAK (nebo klikněte na tlačítko **pozastavit** ).

 ![Tlačítko Rozdělit vše v aplikaci Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Stisknutím klávesy F5 pokračujte v používání aplikace (nebo klikněte na tlačítko **pokračovat** ).

 ![Tlačítko pro pokračování ladění sady Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Aplikaci můžete zastavit stisknutím SHIFT + F5 nebo kliknutím na tlačítko **zastavit** . Nebo můžete jednoduše zavřít hlavní okno aplikace (nebo dialogové okno příkazového řádku).

 Pokud váš kód běžel dokonale a přesně tak, jak bylo očekáváno, Blahopřejeme! Změňte konfiguraci buildu na **release** a znovu ji Sestavte pro nasazení. (Odborníci můžou chtít přejít na bit testování částí na konci, ale.) Pokud se ale přestala nebo došlo k chybě nebo vám poskytla nějaké neobvyklé výsledky, bude nutné najít zdroje těchto problémů a opravit chyby.

### <a name="setting-simple-breakpoints"></a>Nastavení jednoduché zarážky
 Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští. NENÍ nutné znovu sestavit projekt po nastavení a odebrání zarážky.

 Nastavte zarážku kliknutím v úplně okraj řádku, kde chcete, aby se zarážka, nebo vyberte řádek kódu a stiskněte klávesu F9. Při spuštění kódu, přestane předtím, než se spustí pokyny pro tento řádek kódu.

 ![Zarážka sady Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Pokud kód přeruší, nebyl proveden označený řádek kódu. V tomto okamžiku můžete spustit pokyny pro řádek kódu, označen zarážky a zkontrolovat změněné hodnoty. Tomu se říká "krokování" kód. Pokud volání metody je označené jako kód, můžete krokovat s vnořením ji stisknutím klávesy F11. Můžete také "Krokovat přes" řádek kódu stisknutím klávesy F10. Chcete-li získat další informace o akcích kroků zarážek, přečtěte si téma [navigace pomocí kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

 Mezi běžná použití pro zarážky patří:

1. Abyste omezili příčiny zhroucení nebo zablokování, bodový je v průběhu a ohraničení kódu volání metody, které si myslíte, že je příčinou selhání. Krokovat kód, odebrat a současně resetovat zarážce blíže, dokud nenajdete problematický řádek kódu.

2. Pokud chcete zavést nový kód, nastavte zarážku na začátku a krokovat kód, abyste měli jistotu, že se nechová podle očekávání.

3. Pokud jste implementovali složité chování, nastavte zarážky pro kód vylepšením, aby poškodí program si můžete prohlédnout hodnoty proměnných a data.

4. Pokud píšete kód C nebo C++, použijte zarážky pro zastavení kód, takže si můžete prohlédnout hodnoty adres (vyhledejte NULL) a počty odkazů, při ladění chyby související s pamětí.

   Další informace o použití zarážek najdete v tématu [použití zarážek](../debugger/using-breakpoints.md) .

### <a name="setting-conditional-breakpoints"></a>Nastavení podmíněné zarážky
 Pokud máte zarážku ve smyčce nebo rekurzi, nebo pokud máte velké množství zarážky, které často projdete, použijte podmíněné zarážky a zkontrolujte, že váš kód je pozastavený, pouze v případě, že jsou splněny konkrétní podmínky. V opačném případě je budete být klávesy F11 awful hodně.

 Nastavení podmíněné zarážky a pozastavit kódu, pokud je nastavena na určitou hodnotu proměnné nebo předá určité prahové hodnoty, klikněte na tlačítko pro nastavení zarážky na okraji a potom vyberte "kolečko" ze zobrazené nabídky při najetí myší.

 ![Nastavení zarážky sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Zobrazí se dialogové okno, který vypadá takto kde můžete nastavit konkrétní podmínky, aby se zarážka objevila.

 ![Podmíněná zarážka sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Další informace o tom, jak deklarovat výrazy používané pro vyhodnocení podmíněné zarážky, najdete [v tématu prostředí pro konfiguraci zarážek channel9 video v aplikaci Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Kontrola kódu za běhu
 Při spuštění kódu narazí na zarážku a zastaví, můžete zkontrolovat proměnných a k určení, co se děje zásobníky volání. Jsou hodnoty v oblasti, které byste měli vidět? Volá se provádějí ve správném pořadí?

 ![Kontrola hodnoty doby běhu&#45;sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Najeďte myší zobrazíte hodnoty a odkazy, které aktuálně obsahuje proměnné. Pokud se zobrazí hodnotu, kterou jste neočekávali, pravděpodobně chyby v předchozích nebo volání řádků kódu. Zarážky nahoru nebo přidání podmínky do existující zarážky můžete zpřesnit hledání další.

 Kromě toho Visual Studio 2015 se zobrazí okno diagnostické nástroje, kde můžete sledovat vaše aplikace CPU a využití paměti v čase. Je použijte k vyhledání neočekávané náročné využití nebo paměť přidělení procesoru. Použijte ji ve spojení s oknem **kukátka** a zarážkami k určení toho, co způsobuje neočekávané vysoké využití nebo uvolnění prostředků.

 ![Okno sady Visual Studio 2015 Diagnostické nástroje](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Provádění testů jednotek
 Testování jednotek je programy, které vykonávají cesty kódu ve vaší aplikaci nebo službě. Visual Studio 2015 se nainstaluje rozhraní testování částí Microsoft pro spravovaný i nativní kód. Použití jednotkových testů vytvořit testy jednotek, spustit je a ohlásí výsledky těchto testů. Pokud provedete změny k testování, že váš kód stále pracuje správně testů jednotek spusťte znovu. Pokud používáte Visual Studio 2015 Enterprise, můžete spustit testy automaticky po každém sestavení.

 Chcete-li začít, přečtěte si téma [generování testů jednotek pro kód pomocí IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Chcete-li získat další informace o testování částí v aplikaci Visual Studio 2015 a o tom, jak vám pomohou vytvořit lepší kód kvality, přečtěte si [základy testování částí](../test/unit-test-basics.md).

## <a name="see-also"></a>Viz také
 [Ladění v](../debugger/debugging-in-visual-studio.md) [nastavení ladicího programu sady Visual Studio a přípravné](../debugger/debugger-settings-and-preparation.md) [ladění 64](../debugger/debug-64-bit-applications.md) . [základní informace o ladicím programu](../debugger/debugger-basics.md) aplikace
