---
title: Začínáme s laděním v aplikaci Visual Studio 2015 | Microsoft Docs
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
ms.openlocfilehash: 08e317555042bbc63707cc6eccd0177e78b6ddcc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645669"
---
# <a name="getting-started-with-debugging-in-visual-studio-2015"></a>Začínáme s laděním v sadě Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada Visual Studio 2015 poskytuje výkonnou integrovanou sadu nástrojů pro sestavení a ladění projektu. V tomto tématu zjistíte, jak začít používat nejvíce základní sadu funkcí pro ladění uživatelského rozhraní.

 Poznámka: odkazy na pokročilejší funkce a témata týkající se platforem nebo funkcí jsou v dolní části této stránky.

## <a name="my-code-doesnt-work-help-me-visual-studio-2015"></a>Můj kód nefunguje. Potřebuji pomoc s Visual Studiem 2015!
 Takže jste si vyzkoušeli Editor a vytvořili jste nějaký kód. Nyní chcete spustit ladění tohoto kódu. V aplikaci Visual Studio 2015, stejně jako u většiny IDEs, existují dvě fáze ladění: sestavení kódu pro zachycení a řešení chyb projektů a kompilátoru; a spuštění tohoto kódu v prostředí za účelem zachycení a vyřešení dynamických chyb běhu.

### <a name="configuring-a-build"></a>Konfigurace sestavení
 Existují dva základní typy konfigurace sestavení: **ladění** a **vydání**. První konfigurace vytvoří pomalejší, větší spustitelný soubor, který umožňuje bohatší interaktivní prostředí pro ladění za běhu, ale nemělo by být odesláno. Druhý vytvoří rychlejší, více optimalizovaný spustitelný soubor, který je vhodný k odeslání (alespoň z perspektivy kompilátoru).

 Výchozí konfigurace sestavení je **ladit**.

 ![Tlačítko pro sestavení ladění sady Visual Studio](../ide/media/vs-ide-gs-debug-build-type1.PNG "Vs_ide_gs_debug_build_type1")

 Můžete také zadat konkrétní platformu sestavení, kterou chcete cílit, jako je například **x86** (32 procesory Intel), **x64** (64 procesory Intel) a **ARM** (procesory ARM, podporované jenom pro určité typy aplikací). Výchozí hodnota je **x86** pro spravované a nativní projekty. Pokud ho chcete změnit, klikněte na rozevírací seznam Build Platform a vyberte jinou platformu nebo **Configuration Manager...**

 ![Okno Správce konfiguračních souborů sady Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr.PNG "Vs_ide_gs_debug_build_cf_mgr")

 Můžete zadat cílovou konfiguraci sestavení pomocí **Configuration Manager**. Spusťte ji, klikněte na rozevírací seznam **Konfigurace** nebo **procesor** a vyberte **Nový...** Chcete-li vytvořit nové sestavení nebo platformu.

 ![Okno Configuration Manager sady Visual Studio](../ide/media/vs-ide-gs-debug-build-cf-mgr-2.PNG "Vs_ide_gs_debug_build_cf_mgr_2")

 Od toho stačí použít **ladění** a **x86** jako konfiguraci a platformu sestavení v uvedeném pořadí. Až budete hotovi s kódováním a laděním, změňte konfiguraci na **release** a Zaměřte se na konkrétní platformu. (Starší verze sady Visual Studio poskytovaly výchozí platformu **anycpu** pro projekty kódu .NET.)

 Poznámka: při sestavování projektu se použijí také hodnoty konfigurace a platforma k určení, která cesta k adresáři projektu je vytvořena pro uložení spustitelného souboru. Obvykle se jedná **o > \<path-to-project \\ < Project-name \> \\ < configuration \> \\ < platform \>** . Například projekt s konfigurací `Debug` a platformou `x86` se nachází v části `Projects\MyProjectNameHere\MyProjectNameHere\bin\Debug\x86`. To může být užitečné, pokud máte vlastní nástroje nebo skripty, které spravují tyto sestavené spustitelné soubory.

### <a name="building-your-code"></a>Sestavení kódu
 Po nakonfigurovaném sestavení je čas ve skutečnosti sestavit projekt. Nejjednodušší způsob, jak to provést stisknutím klávesy F7, můžete také spustit sestavení výběrem **řešení sestavení Build-> Build** z hlavní nabídky.

 ![Výběr nabídky projektu Visual Studio Build](../ide/media/vs-ide-gs-debug-build-menu-item.png "Vs_ide_gs_debug_build_menu_item")

 Proces sestavení můžete sledovat v okně stav **výstupu** v dolní části uživatelského rozhraní sady Visual Studio. Zde jsou uvedeny chyby, varování a operace sestavení. Pokud máte chyby (nebo pokud máte upozornění nad nakonfigurovanou úroveň), sestavení se nezdaří. Můžete kliknout na chyby a upozornění a přejít na řádek, ve kterém k nim došlo. Znovu sestavte projekt stisknutím klávesy **F7** znovu (Chcete-li znovu kompilovat pouze soubory s chybami) nebo **CTRL + ALT + F7** (pro vyčištění a dokončení opětovného sestavení).

 V okně výsledky pod editorem jsou dvě okna sestavení s kartami: **výstupní** okno obsahující nezpracovaný výstup kompilátoru (včetně chybových zpráv); a okno **Seznam chyb** , které poskytuje seřaditelné a filtrovatelné seznamy všech chyb a upozornění.

 Po úspěšném zobrazení v okně **výstup** se zobrazí podobné výsledky.

 ![Výstup buildu pro Visual Studio se úspěšně vytvořil.](../ide/media/vs-ide-gs-debug-success-build.PNG "vs_ide_gs_debug_success_build")

### <a name="reviewing-the-error-list"></a>Kontrola Seznam chyb
 Pokud jste neudělali žádné úpravy kódu, který jste předtím a úspěšně zkompilujei, pravděpodobně došlo k chybě. Pokud začínáte s kódováním, pravděpodobně jich máte spoustu. Chyby jsou někdy zřejmé, jedná se o jednoduchou chybu syntaxe nebo nesprávný název proměnné a někdy je obtížné porozumět, s pouze nešifrovaným kódem, který vás provede. Pro vyčištění zobrazení problémů přejděte do dolní části okna **výstup** sestavení a klikněte na kartu **Seznam chyb** . Tím přejdete k lépe organizovanému zobrazení chyb a upozornění pro váš projekt a získáte i další možnosti.

 ![Výstup a Seznam chyb sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-bad-build-error-list.PNG "Vs_ide_gs_debug_bad_build_error_list")

 V okně **Seznam chyb** klikněte na chybový řádek a přejděte na řádek, ve kterém se nachází chyba. (Nebo zapněte čísla řádků kliknutím na panel **snadného spuštění** v pravém horním rohu zadejte "čísla řádků" a stiskněte klávesu ENTER. Toto je nejrychlejší způsob, jak se dostat do položky okna **Možnosti** , kde můžete zapnout čísla řádků. Naučte se používat panel **snadného spuštění** a ušetřit spoustu kliknutí na uživatelské rozhraní.

 ![Editor sady Visual Studio s čísly řádků](../ide/media/vs-ide-gs-debug-line-numbers.png "Vs_ide_gs_debug_line_numbers")

 ![Možnost čísel řádků sady Visual Studio](../ide/media/vs-ide-gs-debug-options-line-numbers.png "Vs_ide_gs_debug_options_line_numbers")

 Pomocí kombinace kláves CTRL + G můžete rychle přejít na číslo řádku, kde došlo k chybě.

 Chyba je identifikována podtržením červené "vlnovce". Další podrobnosti najdete najetím myší na něj. Opravte tuto opravu a zmizí, i když ale můžete zavést novou chybu s opravou. (Tato možnost se nazývá "regrese".)

 ![Chyba sady Visual Studio při najetí myší](../ide/media/vs-ide-gs-debug-error-hover1.png "Vs_ide_gs_debug_error_hover1")

 Projděte si seznam chyb a vyřešte všechny chyby ve vašem kódu.

 ![Okno chyby ladění sady Visual Studio](../ide/media/vs-ide-gs-debug-error-list.PNG "Vs_ide_gs_debug_error_list")

### <a name="reviewing-errors-in-detail"></a>Podrobné kontrola chyb
 Mnoho chyb by vám nemohlo být nijak nesmyslem, protože jsou v souladu s podmínkami kompilátoru. V těchto případech budete potřebovat další informace. V okně **Seznam chyb** můžete provést automatické vyhledávání Bingu, kde najdete další informace o chybě (nebo upozornění) tak, že kliknete pravým tlačítkem myši na odpovídající vstupní řádek a v místní nabídce vyberete **Zobrazit nápovědu k chybám** .

 ![Seznam chyb v aplikaci Visual Studio – vyhledávání Bingu](../ide/media/vs-ide-gs-debug-error-list-error-help.png "Vs_ide_gs_debug_error_list_error_help")

 Tím se spustí karta uvnitř sady Visual Studio 2015, která je hostitelem výsledků hledání Bingu pro kód chyby a text. Výsledky jsou z mnoha různých zdrojů v Internetu a ne všechny můžou být užitečné.

 Případně můžete kliknout na hodnotu kódu chyby s hypertextovými odkazy ve sloupci **kód** **Seznam chyb**. Tím se spustí vyhledávání Bingu jenom pro kód chyby.

### <a name="performing-static-code-analysis"></a>Provádění statické analýzy kódu
 "Analýza statického kódu" je ozdobný způsob vyslovení "automaticky kontrolovat můj kód pro běžné problémy, které mohou vést k chybám za běhu nebo problémům se správou kódu". Buďte ve chvíli, kdy jste vyčistili zjevné chyby zabraňující sestavování, a chvíli si vyřešte upozornění, která může vytvořit. Ušetříte si pár souvisejícím problémům správou po silnici a také se naučíte několik technik stylu kódu.

 Stiskněte ALT + F11 (nebo vyberte **analyzovat-> spustit analýzu kódu v rámci řešení** v horní nabídce) a spusťte tak statickou analýzu kódu. To může nějakou dobu trvat, pokud máte spoustu kódu.

 ![Položka nabídky analýzy kódu sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-run-code-analysis.png "Vs_ide_gs_debug_run_code_analysis")

 Všechna nová nebo aktualizovaná upozornění se zobrazí na kartě **Seznam chyb** v dolní části rozhraní IDE. Kliknutím na upozornění můžete na ně přejít.

 ![Visual Studio 2015 Seznam chyb s upozorněními](../ide/media/vs-ide-gs-debug-code-analysis-warning-error-list.PNG "vs_ide_gs_debug_code_analysis_warning_error_list")

 Upozornění se identifikují jasně žlutou zelenou vlnovkou namísto červeného podtržení. Poklikáním na ně získáte další podrobnosti a kliknutím pravým tlačítkem myši získáte kontextovou nabídku, která vám pomůže s opravami nebo refaktoringem možností.

 ![Upozornění analýzy Visual Studio Code – najetí myší](../ide/media/vs-ide-gs-debug-code-analysis-warning-hover.png "vs_ide_gs_debug_code_analysis_warning_hover")

### <a name="using-light-bulbs-to-fix-or-refactor-code"></a>Použití žárovek k opravě nebo refaktorování kódu
 Žárovky jsou novou funkcí sady Visual Studio 2015, která umožňuje Refaktorovat vložený kód. Představují snadný způsob, jak rychle a efektivně řešit běžná upozornění. Pokud k nim chcete získat přístup, klikněte pravým tlačítkem na vlnovku upozornění (nebo stiskněte kombinaci kláves CTRL +. Při najetí myší na vlnovku) a pak vyberte **rychlé akce**.

 ![Rychlé možnosti žárovky sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-light-bulb1.png "Vs_ide_gs_debug_light_bulb1")

 Zobrazí se seznam možných oprav nebo refaktorů, které můžete použít na tento řádek kódu.

 ![Visual Studio 2015 – Preview verze Preview](../ide/media/vs-ide-gs-debug-light-bulb-preview-changes.PNG "Vs_ide_gs_debug_light_bulb_preview_changes")

 Žárovky lze použít všude, kde analyzátory kódu určují možnost opravit, Refaktorovat nebo zdokonalit váš kód. Klikněte na libovolný řádek kódu, kliknutím pravým tlačítkem otevřete kontextovou nabídku a vyberte možnost **rychlé možnosti** (nebo znovu, pokud chcete preferovat efektivitu, stiskněte kombinaci kláves CTRL +.). Pokud jsou k dispozici možnosti refaktoringu a vylepšení oblasti, zobrazí se. v opačném případě se `No quick options available here` zpráva zobrazí v levém dolním rohu integrovaného vývojového prostředí (IDE).

 ![Text "bez možnosti" sady Visual Studio 2015 Light žárovky](../ide/media/vs-ide-gs-debug-light-bulb-no-options.PNG "Vs_ide_gs_debug_light_bulb_no_options")

 Díky prostředí můžete rychle používat klávesy se šipkami a CTRL +. pro kontrolu příležitostí refaktoringu rychlých možností a vyčištění kódu!

 Další informace o žárovkách najdete v článku [provádění rychlých akcí pomocí](../ide/perform-quick-actions-with-light-bulbs.md)žárovek.

### <a name="debugging-your-running-code"></a>Ladění spuštěného kódu
 Teď, když jste úspěšně vytvořili kód a provedli trochu vyčištění, spusťte ho stisknutím klávesy F5 nebo výběrem **ladění > spustit ladění**. Tím se spustí aplikace v ladicím prostředí, abyste mohli sledovat její chování podrobněji. Rozhraní IDE sady Visual Studio 2015 se během vaší aplikace změní: okno **výstup** je nahrazeno dvěma novými (ve výchozím nastavení výchozí okno), okno Automatické hodnoty **/místní hodnoty/moduly/kukátko** a **zásobník volání, zarážky a výjimka Nastavení/výstup** okna s kartami Tato okna mají několik karet, které umožňují kontrolovat a vyhodnocovat proměnné aplikace, vlákna, zásobníky volání a různá další chování při jejich spuštění.

 ![Okna Automatické hodnoty a zásobník volání VS2015](../ide/media/vs-ide-gs-debug-autos-and-call-stack.PNG "Vs_ide_gs_debug_autos_and_call_stack")

 Vyzkoušejte různé akce s vaší aplikací a sledujte změny. Pokud se vyskytne něco neobvyklého, pozastaví aplikaci stisknutím kombinace kláves CTRL + ALT + BREAK (nebo klikněte na tlačítko **pozastavit** ).

 ![Tlačítko Rozdělit vše v aplikaci Visual Studio](../ide/media/vs-ide-gs-debug-break-all-button.png "vs_ide_gs_debug_break_all_button")

 Stisknutím klávesy F5 pokračujte v používání aplikace (nebo klikněte na tlačítko **pokračovat** ).

 ![Tlačítko pro pokračování ladění sady Visual Studio](../ide/media/vs-ide-gs-debug-continue-button.png "Vs_ide_gs_debug_continue_button")

 Aplikaci můžete zastavit stisknutím SHIFT + F5 nebo kliknutím na tlačítko **zastavit** . Nebo můžete jednoduše Zavřít hlavní okno aplikace (nebo dialogové okno příkazového řádku).

 Pokud váš kód běžel dokonale a přesně podle očekávání, Blahopřejeme! Změňte konfiguraci buildu na **release** a znovu ji Sestavte pro nasazení. (Odborníci můžou chtít přejít na bit testování částí na konci, ale.) Pokud se ale přestala nebo došlo k chybě nebo vám poskytla nějaké neobvyklé výsledky, bude nutné najít zdroje těchto problémů a opravit chyby.

### <a name="setting-simple-breakpoints"></a>Nastavení jednoduchých zarážek
 Zarážky jsou základní a nejjednodušší funkcí spolehlivého ladění. Zarážka určuje, kde má Visual Studio spuštěný kód pozastavit, abyste mohli zkontrolovat hodnoty proměnných či chování paměti, nebo abyste zjistili, jestli se nějaká větev kódu spouští. Po nastavení a odebrání zarážek není nutné znovu sestavit projekt.

 Nastavte zarážku kliknutím na nejvyšší okraj řádku, kde chcete, aby došlo k přerušení, nebo vyberte řádek kódu a stiskněte klávesu F9. Při spuštění kódu se zastaví, než se spustí pokyny pro tento řádek kódu.

 ![Zarážka sady Visual Studio](../ide/media/vs-ide-gs-debug-breakpoint1.png "Vs_ide_gs_debug_breakpoint1")

 Po zalomení kódu nebyl dosud proveden označený řádek kódu. V tomto okamžiku může být vhodné provést pokyny pro řádek kódu označený zarážkou a zkontrolovat změněné hodnoty. Tento kód se nazývá "krokování do" kódu. Pokud je označený kód volání metody, můžete do něj krokovat stisknutím klávesy F11. Můžete také "krokovat přes" řádek kódu stisknutím klávesy F10. Chcete-li získat další informace o akcích kroků zarážek, přečtěte si téma [navigace pomocí kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md).

 Mezi běžná použití zarážek patří:

1. Chcete-li zúžit celkový stav selhání nebo zablokování, rozptýlené v celém a kolem kódu volání metody, o které se domníváte, že to způsobuje chybu. Při procházení kódu odeberte a pak vynulujte zarážky, dokud nenajdete problematický řádek kódu.

2. Když zavádíte nový kód, nastavíte zarážku na začátku a provedete krok kódu, abyste se ujistili, že se chová podle očekávání.

3. Pokud jste implementovali složité chování, nastavte zarážky pro algoritmusový kód, abyste mohli zkontrolovat hodnoty proměnných a dat při přerušení programu.

4. Pokud píšete jazyk C nebo C++ kód, pomocí zarážek zastavte kód, abyste mohli zkontrolovat hodnoty adresy (hledání hodnoty null) a počty odkazů při ladění selhání souvisejících s pamětí.

   Další informace o použití zarážek najdete v tématu [použití zarážek](../debugger/using-breakpoints.md) .

### <a name="setting-conditional-breakpoints"></a>Nastavení podmíněné zarážky
 Pokud máte zarážku ve smyčce nebo rekurze, nebo pokud máte hodně zarážek, které často projdete, použijte podmíněnou zarážku, abyste zajistili, že je váš kód pozastaven pouze v případě, že jsou splněny určité podmínky. Jinak stisknete F11 awful spoustu.

 Chcete-li nastavit podmíněný bod přerušení a pozastavit váš kód, pokud je proměnná nastavena na určitou hodnotu nebo předává určitou prahovou hodnotu, klikněte na okraj pro nastavení zarážky a potom vyberte "ozubeného kola" z zobrazené nabídky přechodu.

 ![Nastavení zarážky sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-settings.png "Vs_ide_gs_debug_breakpoint_settings")

 Zobrazí se dialogové okno, ve kterém můžete nastavit konkrétní podmínky pro přerušení, které je třeba provést.

 ![Podmíněná zarážka sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-breakpoint-conditional.PNG "Vs_ide_gs_debug_breakpoint_conditional")

 Další informace o tom, jak deklarovat výrazy používané pro vyhodnocení podmíněné zarážky, najdete [v tématu prostředí pro konfiguraci zarážek channel9 video v aplikaci Visual Studio 2015](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711).

### <a name="inspecting-your-code-at-run-time"></a>Kontrola kódu za běhu
 Když váš běžící kód narazí na zarážku a zastaví se, můžete zkontrolovat proměnné a zásobníky volání a zjistit, co se chystá. Jsou hodnoty v rozsahu, které očekáváte, abyste viděli? Jsou volání prováděna ve správném pořadí?

 ![Kontrola hodnoty doby běhu&#45;sady Visual Studio 2015](../ide/media/vs-ide-gs-debug-inspect-value.PNG "vs_ide_gs_debug_inspect_value")

 Najeďte myší na proměnnou, aby se zobrazily hodnoty a odkazy, které aktuálně obsahují. Pokud se zobrazí hodnota, kterou jste neočekávali, pravděpodobně máte chybu v předchozím nebo volajícím řádku kódu. Přesunutím zarážek nahoru nebo přidáním podmínek do stávajících zarážek upřesněte hledání.

 Kromě toho Visual Studio 2015 zobrazí okno Diagnostické nástroje, kde můžete sledovat využití procesoru a paměti vaší aplikace v průběhu času. Použijte je k vyhledání neočekávaného vysokého využití procesoru nebo přidělení paměti. Použijte ji ve spojení s oknem **kukátka** a zarážkami k určení toho, co způsobuje neočekávané vysoké využití nebo uvolnění prostředků.

 ![Okno sady Visual Studio 2015 Diagnostické nástroje](../ide/media/vs-ide-gs-debug-diagnostic-tools.PNG "Vs_ide_gs_debug_diagnostic_tools")

### <a name="running-unit-tests"></a>Spouštění testů jednotek
 Testování částí jsou programy, které vykonávají cesty kódu ve vaší aplikaci nebo službě. Visual Studio 2015 nainstaluje architektury testování částí od společnosti Microsoft pro spravovaný i nativní kód. Pomocí architektury jednotkového testování můžete vytvořit testy jednotek, spustit je a ohlásit výsledky těchto testů. Spusťte testy jednotek znovu, když provedete změny a otestujete, zda váš kód stále pracuje správně. Při použití sady Visual Studio 2015 Enterprise můžete testy spouštět automaticky po každém sestavení.

 Chcete-li začít, přečtěte si téma [generování testů jednotek pro kód pomocí IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

 Chcete-li získat další informace o testování částí v aplikaci Visual Studio 2015 a o tom, jak vám pomohou vytvořit lepší kód kvality, přečtěte si [základy testování částí](../test/unit-test-basics.md).

## <a name="see-also"></a>Viz také
 [Ladění v](../debugger/debugging-in-visual-studio.md) [nastavení ladicího programu sady Visual Studio a přípravné](../debugger/debugger-settings-and-preparation.md) [ladění 64](../debugger/debug-64-bit-applications.md) . [základní informace o ladicím programu](../debugger/debugger-basics.md) aplikace
