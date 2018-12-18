---
title: Opravte chyby programu a zlepšit kódu
description: Tento článek popisuje některé základní způsoby Visual Studio můžete najít a opravit problémy ve vašem kódu, včetně chyby sestavení analýza kódu, ladění, nástroje a testování částí.
ms.date: 05/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c3a14d28-d811-4ff3-bd09-21dce14025ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 320615daa95ba9fad69fe48490f83c19ccf8e1ce
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
ms.locfileid: "34065114"
---
# <a name="make-code-work-in-visual-studio"></a>Ujistěte se, kód pracovat v sadě Visual Studio

Visual Studio poskytuje výkonnou sadu integrované sestavení projektu a nástroje pro ladění. V tomto článku zjistit, jak lze pomocí sady Visual Studio můžete najít problémy ve vašem kódu používání sestavení výstupu analýza kódu, nástroje pro ladění a testování částí.

Jste započítáno out editoru a vytvořit nějaký kód. Chcete nyní, ujistěte se, že kód funguje správně. V sadě Visual Studio, stejně jako u většina integrovaného vývojového prostředí, existují dvě fáze k provádění kódu pracovní: vytváření kódu zachytit a vyřešit chyby projektu a kompilátoru a spuštění kódu k vyhledání chyby spuštění a dynamické.

## <a name="build-your-code"></a>Sestavení kódu

Existují dva základní typy konfigurace sestavení: **ladění** a **verze**. **Ladění** konfigurace vytváří pomalejší, větší spustitelný soubor, který umožňuje bohatší interaktivní ladění možnosti spuštění. **Ladění** by mělo být dodáno nikdy spustitelný soubor. **Verze** konfigurace sestavení rychlejší, optimalizované spustitelný soubor, který je vhodný pro odeslání (alespoň z perspektivy kompilátor). Výchozí konfigurace sestavení **ladění**.

Nejjednodušší způsob, jak sestavit projekt je ke stisknutí **F7**, ale můžete také spustit sestavení tak, že vyberete **sestavení** > **sestavit řešení** z hlavní nabídky.

![Výběr nabídky projektu sestavení sady Visual Studio](../ide/media/vs_ide_gs_debug_build_menu_item.png)

Můžete sledovat v procesu sestavení **výstup** okna v dolní části rozhraní Visual Studia. Operace sestavení, upozornění a chyb se zobrazí tady. Pokud máte chyby (nebo pokud máte výše nakonfigurované úroveň upozornění), vaše sestavení selže. Kliknutím na s chybami a upozorněními přejít na řádek, kde k nim došlo. Znovu sestavte projekt stisknutím **F7** znovu (a znovu zkompiluje pouze soubory s chybami) nebo **Ctrl**+**Alt**+**F7**  (pro vyčištění a úplné opětovné sestavení).

V okně výsledky níže editoru existují dvě záložkách windows: **výstup** okno, které obsahuje nezpracovaná kompilátoru výstup (včetně chybových zpráv) a **seznam chyb** okno, které poskytuje řazení a filtrování seznam všechny chyby a upozornění.

Při úspěšném sestavení se zobrazí výsledky jako to **výstup** okno:

![Visual Studio úspěšném sestavení výstupu](../ide/media/vs_ide_gs_debug_success_build.png)

## <a name="review-the-error-list"></a>Zkontrolujte seznam chyb

Pokud jste udělali žádné úpravy kód, který jste si dříve a úspěšně zkompilovány, pravděpodobně jste chybu. Pokud jste nové kódování, pravděpodobně máte spoustu je. Chyby jsou někdy zřejmé, jako je jednoduchý syntaktickou chybu nebo nesprávný název proměnné a někdy jsou těžko srozumitelné s pouze jako nesrozumitelné kód na vás. Čisticí zobrazit problémy, přejděte k dolnímu okraji sestavení **výstup** a klikněte na **seznam chyb** kartě. Tím přejdete na více uspořádaný náhled chyb a varování pro svůj projekt a vám dává některé další možnosti.

![Výstup sady Visual Studio a seznam chyb](../ide/media/vs_ide_gs_debug_bad_build_error_list.png)

Klikněte na řádek chyby ve **seznam chyb** okno Přejít na řádek chyba dojde v. (Nebo zapnout čísla řádků kliknutím v **Snadné spuštění** panel v pravém horním, zadáním "čísla řádků" do ní a klávesy **Enter**. Toto je nejrychlejší způsob, jak získat na **možnosti** dialogové okno, kde můžete zapnout čísla řádků. Naučte se používat **Snadné spuštění** panel a ušetřit mnoho klikne na uživatelském rozhraní!)

![Visual Studio editor s čísla řádků](../ide/media/vs_ide_gs_debug_line_numbers.png)

![Visual Studio čísla řádku](../ide/media/vs_ide_gs_debug_options_line_numbers.png)

Stiskněte klávesu **Ctrl**+**G** k rychlému přechodu do číslo řádku, na kterém došlo k chybě.

Chyba je identifikována red "klikatá" podtržítka. Pozastavte ukazatel myši nad jeho další podrobnosti. Proveďte opravu a jeho zmizí, i když může znamenat nové chyby s oprava. (To se nazývá "regrese".)

![Visual Studio chyba hover](../ide/media/vs_ide_gs_debug_error_hover1.png)

Provede v seznamu chyb a vyřešte všechny chyby v kódu.

![Okno chyby pro Visual Studio ladění](../ide/media/vs_ide_gs_debug_error_list.png)

### <a name="review-errors-in-detail"></a>Zkontrolujte chyby v podrobností

Mnoho chyb má smysl žádné vám obsahuje jiné spojení, jako jsou v podmínkách kompilátoru. V takových případech budete potřebovat další informace. Z **seznam chyb** okno, můžete provést automatické vyhledávání Bing Další informace o chybě nebo upozornění. Klikněte pravým tlačítkem na řádku odpovídající položky a vyberte **zobrazit nápovědu k chybě** z kontextové nabídky, nebo klikněte na hodnotu s hypertextovým odkazem chyba kódu v **kód** sloupec **seznam chyb**.

![Visual Studio seznam chyb Bing vyhledávání](../ide/media/vs_ide_gs_debug_error_list_error_help.png)

V závislosti na nastavení buď webového prohlížeče zobrazí výsledky hledání jsou kód chyby a text, nebo na kartě se otevře v sadě Visual Studio a zobrazí výsledky hledání Bing. Výsledky jsou z mnoha různých zdrojů v síti Internet, a ne všechny může být užitečné.

## <a name="use-code-analysis"></a>Pomocí analýzy kódu

Analyzátorů kódu vyhledejte běžné problémy kódu, které můžou vést k běhové chyby nebo problémy ve správě kódu.

### <a name="c-and-visual-basic-code-analysis"></a>Analýza kódu C# a Visual Basic

Visual Studio 2017 zahrnuje integrovanou sadu [platformy .NET kompilátoru analyzátorů](../code-quality/roslyn-analyzers-overview.md) kódu jazyka C# a Visual Basic, zkontrolujte, jak budete zadávat. Můžete nainstalovat další analyzátorů jako rozšíření sady Visual Studio, nebo jako balíčku NuGet. Pokud se nenajdou porušení pravidel, se zvyšují v editoru kódu jako vlnovkou pod kód problematické a v **seznam chyb**.

### <a name="c-code-analysis"></a>Analýza kódu C++

Chcete-li provést analýzu kódu C++, spusťte [analýza statické kódu](../code-quality/quick-start-code-analysis-for-c-cpp.md). Získání v jeho spuštění, když jste odstranili zřejmé chyby, které brání úspěšném sestavení a nějakou dobu adres, které může vytvořit upozornění která podporují. Sami budete uložte některé hlavu dolů na cestách, a dozvíte na některé techniky styl kódu.

Stiskněte klávesu **Alt**+**F11** (nebo vyberte **analyzovat** > **spustit analýza kódu v řešení** z hlavní nabídky) na Analýza kódu statických spusťte.

![Visual Studio Code Analysis položky nabídky](../ide/media/vs_ide_gs_debug_run_code_analysis.png)

Všechny nové nebo aktualizované upozornění se zobrazí v **seznam chyb** karta v dolní části rozhraní IDE. Klikněte na upozornění k nim přejít v kódu.

![Seznam chyb sady Visual Studio s upozorněními.](../ide/media/cpp-code-analysis-warning.png)

## <a name="use-light-bulbs-to-fix-or-refactor-code"></a>Pomocí žárovek opravíte nebo Refaktorovat kódu

[Rychlé akce](../ide/quick-actions.md), k dispozici z žárovky nebo šroubovák ikonu, umožňují Refaktorovat vloženého kódu. Jsou snadný způsob, jak opravit běžné upozornění rychle a efektivně v kódu jazyka C#, C++ a Visual Basic. Chcete-li přistupovat k nim, klikněte pravým tlačítkem na vlnovku upozornění a vyberte **rychlé akce a refaktoring**. Nebo, pokud je kurzor na řádku s barevnou vlnovka, stiskněte klávesu **Ctrl**+**.** nebo vyberte žárovky nebo ikonu šroubovák u okraje. Zobrazí se seznam možných opravy nebo refaktoring, které můžete provést u tohoto řádku kódu.

![Visual Studio žárovky preview](../ide/media/quick-actions-options.png)

Rychlé akce lze použít bez ohledu na analyzátorů kódu určit, že je možnost pro opravu, refactor, nebo vylepšení vašeho kódu. Klikněte na každý řádek kódu, pravým tlačítkem a otevřete kontextu nabídku a vyberte **rychlé akce a refaktoring**. Refaktoring nebo zlepšování možnosti jsou k dispozici, jsou zobrazeny. V opačném zprávu **zde k dispozici žádné rychlé akce** se zobrazí v levém dolním rohu okna IDE.

![Žádný text k dispozici rychlé akce](../ide/media/vs_ide_gs_debug_light_bulb_no_options.png)

V prostředí, můžete rychle použít klávesy se šipkami a **Ctrl**+**.** pro kontrolu snadno refaktoringu příležitostí a vyčistit kódu!

## <a name="debug-your-running-code"></a>Ladění spuštěním kódu

Teď, když jste úspěšně sestaven kódu a provést trochu vyčistit, spusťte stisknutím **F5** nebo výběr **ladění** > **spustit ladění**. Tím spustíte aplikaci v prostředí ladění, můžete sledovat své chování podrobně. Visual Studio IDE změní, když aplikace běží: **výstup** okno nahrazeno dva nové (v konfiguraci okna výchozí), **automobily/místní hodnoty nebo sledování** – záložkami okno a **Volání nastavení výstupní zásobník/zarážky nebo výjimka** okno s kartami. Tyto windows mají několik karet, které vám umožní prohlédnout a vyhodnocení proměnné vaší aplikace, vláken, zpětná volání a různé další chování při jeho spuštění.

![Visual Studio automobily a Windows zásobníku volání](../ide/media/vs_ide_gs_debug_autos_and_call_stack.png)

Zastavte aplikaci stisknutím **Shift**+**F5** nebo kliknutím **Zastavit** tlačítko. Nebo můžete jednoduše zavřít hlavní okno aplikace (nebo dialogové okno příkazového řádku).

V případě kódu spustil perfektně a přesně podle očekávání, Blahopřejeme! Ale pokud přestala, nebo došlo k chybě nebo vám Dal některé neobvyklé výsledky, budete potřebovat najít zdroj těchto problémů a opravte chyby.

### <a name="set-simple-breakpoints"></a>Nastavit jednoduché zarážky

[Zarážky](../debugger/using-breakpoints.md) jsou nejvíce základní a základní funkce spolehlivé ladění. Zarážku Určuje, kde by měl Visual Studio pozastavit spuštěním kódu, můžete si prohlédněte hodnoty proměnných nebo chování paměti, nebo zda získávání větev kódu běží. Není nutné znovu sestavit projekt po nastavení a odebírání zarážky.

Zarážku kliknutím v úplně okraj řádku místo rozdělení dojít nebo stiskněte klávesu **F9** nastavit zarážky na aktuálním řádku kódu. Při spuštění kódu se pozastaví (nebo *zalomení*) předtím, než se spustí pokyny pro tento řádek kódu.

![Visual Studio zarážek](../ide/media/vs_ide_gs_debug_breakpoint1.png)

Mezi běžná použití pro zarážky patří:

- Chcete-li zúžit zdroj chybě nebo zablokování, bodový zarážky v celé a kolem kód, který si myslíte, že je příčinou selhání volání metody. Jako při spuštění kódu v ladicím programu odebrat a poté resetujte zarážky blíže společně vyhledejte problematické řádek kódu. Najdete v další části se dozvíte, jak spustit kód v ladicím programu.

- Když zavedete nový kód, zarážku na začátku ji a spusťte kód a ujistěte se, že se chová podle očekávání.

- Pokud jste implementovali složité chování, nastavte zarážky pro algoritmické kód, tak při rozdělení si můžete prohlédnout hodnoty proměnných a data.

- Pokud psaní kódu jazyka C nebo C++, použijte zarážky pro zastavení kód, takže si můžete prohlédnout hodnoty adres (podívejte se na hodnotu NULL) a počty odkazů při ladění chyby související s pamětí.

Další informace o použití zarážek, najdete v tématu [použití zarážek](../debugger/using-breakpoints.md).

### <a name="inspect-your-code-at-run-time"></a>Kontrola kódu v době běhu

Při spuštění kódu dotkne boru přerušení a pozastaví, nebyl ještě provést řádek kódu označena žlutě (aktuální příkaz). V tomto okamžiku můžete provést aktuální příkaz a zkontrolujte změněné hodnoty. Můžete použít několik *krok* příkazů pro spuštění kódu v ladicím programu. Pokud je označen jako kód volání metody, můžete do ní krok stisknutím **F11**. Můžete také *krok přes* řádek kódu stisknutím **F10**. Další příkazy a podrobnosti o tom, jak procházet kód, přečtěte si [přejděte kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md).

![Visual Studio hodnota doby běhu kontroly](../ide/media/vs_ide_gs_debug_hit_breakpoint.png)

V předchozí ilustraci postoupíte ladicí program jeden příkaz stisknutím buď **F10** nebo **F11** (vzhledem k tomu, že není zde žádná volání metody, jak příkazy mají stejný výsledek).

Při ladicího programu je pozastavena, můžou kontrolovat proměnných a k určení, co se děje zásobníky volání. Hodnoty jsou v oblastech, které byste měli vidět? Jsou volání určené ve správném pořadí?

![Visual Studio hodnota doby běhu kontroly](../ide/media/vs_ide_gs_debug_inspect_value.png)

Podržte ukazatel nad proměnné zobrazíte jeho aktuální hodnota a odkazy. Pokud se zobrazí hodnota, kterou by neměl být, pravděpodobně chyby v předchozích nebo volání kód. Další podrobné informace ladění [Další](../debugger/getting-started-with-the-debugger.md) o používání ladicího programu.

Kromě toho Visual Studio zobrazí **diagnostické nástroje** okno, kde můžete sledovat využití procesoru a paměti vaší aplikace v čase. Později ve vývoji vaší aplikace můžete tyto nástroje Pokud chcete vyhledat neočekávané velkou využití nebo paměť přidělení procesoru. Použít ve spojení s **sledovat** okno a zarážky pro příčinu neočekávané velkou využití nebo nevydané prostředky. Další informace najdete v tématu [profilace prohlídka funkce](../profiling/profiling-feature-tour.md).

## <a name="run-unit-tests"></a>Spouštění testování částí

Testy jednotek jsou vaše první linií obrany před kódu chyby, protože, pokud jsou správně provedené, testování jedné "jednotka" kódu, obvykle jednu funkci a jsou jednodušší než vaše úplné program ladění. Visual Studio nainstaluje rozhraní testování částí Microsoft pro spravovaná a nativní kód. Použijte testování framework částí vytvářet testy částí, spustit je a ohlásí výsledky tyto testy. Testování částí spusťte při provádění změn, testování, aby váš kód stále funguje správně. S Visual Studio Enterprise edition je možné spustit testy automaticky po každé sestavení.

Chcete-li začít, přečtěte si [generování testů částí kódu s IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

Další informace o testování částí v sadě Visual Studio a jak se vám pomůžou vytvořit lepší kvality kódu, přečtěte si [jednotkové testování Základy](../test/unit-test-basics.md).

## <a name="see-also"></a>Viz také

- [Prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md)
- [Další informace o používání ladicího programu](../debugger/getting-started-with-the-debugger.md)
- [Generování a opravte kódu](../ide/code-generation-in-visual-studio.md)