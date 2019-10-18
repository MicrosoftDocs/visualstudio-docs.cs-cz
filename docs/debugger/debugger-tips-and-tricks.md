---
title: Tipy a triky v ladicím programu
description: Seznamte se s některými méně známými funkcemi, které podporuje ladicí program sady Visual Studio.
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92d1c327c168bfd2881ad014b7f9ab87f771b95d
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536076"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Přečtěte si tipy a triky k produktivitě pro ladicí program v aplikaci Visual Studio.

Přečtěte si toto téma, kde se dozvíte několik tipů a triky pro produktivitu pro ladicí program sady Visual Studio. Pokud se chcete podívat na základní funkce ladicího programu, podívejte se na téma [první pohled na ladicí program](../debugger/debugger-feature-tour.md). V tomto tématu se zaměříme na některé oblasti, které nejsou zahrnuté v prohlídce funkcí.

## <a name="pin-data-tips"></a>Tipy k datům pro připnutí

Pokud při ladění často najedete na tipy k datům, možná budete chtít připnout tip k datům pro proměnnou a získat tak rychlý přístup. Proměnná zůstane připnutá i po restartování. Pokud chcete špičku dat připnout, klikněte na ikonu připnutí při najetí myší. Můžete připnout více proměnných.

![Připnutí datové špičky](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Úprava kódu a pokračování ladění (C#, VB,) C++

Ve většině jazyků podporovaných v rámci sady Visual Studio můžete upravit kód uprostřed relace ladění a pokračovat v ladění. Chcete-li použít tuto funkci, klikněte na svůj kód v průběhu pozastaveného ladicího programu, proveďte úpravy a stisknutím klávesy **F5**, **F10**nebo **F11** pokračujte v ladění.

![Upravit a pokračovat v ladění](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Další informace o používání funkce a omezení funkcí najdete v tématu [Upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Upravit kód XAML a pokračovat v ladění

Chcete-li upravit kód XAML během relace ladění, [Přečtěte si téma zápis a ladění spouštění kódu XAML pomocí programu XAML Hot reloading](xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Ladění problémů, které je těžké reprodukce

Pokud je obtížné nebo časově náročné, aby se v aplikaci znovu vytvořil konkrétní stav, zvažte, jestli může pomáhat použití podmíněné zarážky. Můžete použít [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a filtrovat zarážky, abyste se vyhnuli zatržení do kódu aplikace, dokud aplikace nevstoupí do požadovaného stavu (například stav, ve kterém proměnná ukládá chybná data). Můžete nastavit podmínky pomocí výrazů, filtrů, počtů přístupů a tak dále.

#### <a name="to-create-a-conditional-breakpoint"></a>Vytvoření podmíněné zarážky

1. Klikněte pravým tlačítkem myši na ikonu zarážky (červenou míč) a vyberte možnost **podmínky**.

2. V okně **Nastavení zarážky** zadejte výraz.

    ![Podmíněná zarážka](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Pokud vás zajímá jiný typ podmínky, vyberte v dialogovém okně **nastavení zarážek** možnost **Filtr** místo **podmíněného výrazu** a pak postupujte podle tipů pro filtry.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Konfigurace dat, která se mají zobrazit v ladicím programu

Pro C#, Visual Basic a C++ (C++pouze kód/CLI) můžete sdělit ladicímu programu, které informace se mají zobrazit pomocí atributu [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . Pro C++ kód můžete stejný postup provést pomocí [vizualizací Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Změna toku spuštění

Když je ladicí program pozastaven na řádku kódu, použijte myš k umístění žlutého ukazatele šipky vlevo. Přesuňte žlutý ukazatel šipky na jiný bod v cestě spuštění kódu. Pak použijete příkaz F5 nebo krok k pokračování v používání aplikace.

![Přesunout ukazatel spuštění](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Přesunout ukazatel spuštění")

Změnou toku spuštění můžete provádět akce, jako je například testování různých cest spuštění kódu nebo opětovné spuštění kódu bez restartování ladicího programu.

> [!WARNING]
> Tuto funkci často potřebujete pečlivě a v popisu se zobrazí upozornění. Můžou se zobrazit i další upozornění. Přesunutí ukazatele nemůže vrátit aplikaci do dřívějšího stavu aplikace.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Sledování objektu mimo rozsah (C#, Visual Basic)

Můžete snadno zobrazit proměnné pomocí ladicího programu, jako je okno **kukátko** . Pokud je však proměnná mimo rozsah v okně **kukátka** , můžete si všimnout, že je šedá. V některých scénářích aplikací se hodnota proměnné může změnit i v případě, že proměnná je mimo rozsah a je možné ji chtít sledovat úzce (například proměnná může získat uvolňování paměti). Proměnnou můžete sledovat vytvořením ID objektu v okně **kukátko** .

#### <a name="to-create-an-object-id"></a>Vytvoření ID objektu

1. Nastavte zarážku poblíž proměnné, kterou chcete sledovat.

2. Spusťte ladicí program (**F5**) a zastavte zarážku.

3. V okně **místních** hodnot Najděte proměnnou (**ladění > Windows > lokálních**), klikněte pravým tlačítkem na PROMĚNNOU a vyberte **vytvořit ID objektu**.

    ![Vytvoření ID objektu](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. V okně **místní** hodnoty by se měla zobrazit **$** plus číslo. Tato proměnná je ID objektu.

5. Klikněte pravým tlačítkem myši na proměnnou ID objektu a vyberte možnost **Přidat kukátko**.

Další informace najdete v tématu [vytvoření ID objektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Zobrazit návratové hodnoty pro funkce

Chcete-li zobrazit návratové hodnoty pro vaše funkce, podívejte se na funkce, které se zobrazí v okně **Automatické** hodnoty při procházení kódu. Pokud se chcete podívat na vrácenou hodnotu pro funkci, ujistěte se, že funkce, kterou vás zajímá, je už spuštěná (Pokud v tuto chvíli zastavíte voláním funkce, stiskněte **F10** ). Pokud je okno zavřeno, otevřete okno **Automatické** hodnoty pomocí příkazu **Debug > > Windows Autos** .

![Okno Automatické hodnoty](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Kromě toho můžete zadat funkce v **příkazovém** okně a zobrazit tak návratové hodnoty. (Otevřete ho pomocí **> ladění > Windows**.)

![Příkazové podokno](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

[Pseudoproměnné](../debugger/pseudovariables.md) můžete použít také v okně **kukátko** a **Immediate** , jako je například `$ReturnValue`.

## <a name="string_visualizer"></a>Kontrola řetězců v Vizualizér

Při práci s řetězci může být užitečné zobrazit celý formátovaný řetězec. Chcete-li zobrazit prostý text, soubor XML, HTML nebo řetězec JSON, klikněte na ikonu lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru") při najetí myší na proměnnou obsahující řetězcovou hodnotu.

![Otevřete Vizualizér řetězců](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Vizualizér řetězců vám může pomáhat zjistit, jestli je řetězec poškozený, v závislosti na typu řetězce. Například pole s prázdnou **hodnotou** indikuje, že typ Vizualizér nerozpoznal řetězec. Další informace najdete v tématu [dialogové okno Vizualizér řetězců](../debugger/string-visualizer-dialog-box.md).

![Vizualizér řetězců JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Pro několik dalších typů, například datových sad a objektů DataTable, které se zobrazují v oknech ladicího programu, můžete také otevřít vestavěný Vizualizér.

## <a name="break-into-code-on-handled-exceptions"></a>Přerušit kód při zpracovávaných výjimkách

Ladicí program se do kódu přeruší v neošetřených výjimkách. Nicméně zpracování výjimek (například výjimek, ke kterým dojde v rámci `try/catch`ho bloku) může být také zdrojem chyb a může být vhodné je prozkoumat při jejich výskytu. Můžete nakonfigurovat, aby ladicí program mohl přerušit kód pro zpracování výjimek, a to pomocí konfigurace možností v dialogovém okně **Nastavení výjimek** . Otevřete toto dialogové okno tak, že vyberete možnost **ladění > > Windows nastavení výjimek**.

Dialogové okno **Nastavení výjimek** vám umožní sdělit ladicímu programu, aby se do kódu přestaly konkrétními výjimkami. Na následujícím obrázku je ladicí program rozdělen do kódu vždy, když dojde k `System.NullReferenceException`. Další informace najdete v tématu [Správa výjimek](../debugger/managing-exceptions-with-the-debugger.md).

![Dialogové okno Nastavení výjimek](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Ladění zablokování a konfliktů časování

Pokud potřebujete ladit druhy problémů, které jsou společné pro vícevláknové aplikace, často pomáhá při ladění zobrazit umístění vláken. To lze provést snadno pomocí tlačítka **Zobrazit vlákna ve zdroji** .

#### <a name="to-show-threads-in-your-source-code"></a>Zobrazení vláken ve zdrojovém kódu

1. Při ladění klikněte na tlačítko **Zobrazit vlákna ve zdroji** ![Zobrazit vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") na panelu nástrojů **ladění** .

2. Podívejte se na hřbet na levé straně okna. Na tomto řádku vidíte ![značku vlákna](../debugger/media/dbg-thread-marker.png "ThreadMarker") ikony *vlákna, která se* podobá dvěma vláknům látky. Značka vlákna označuje, že vlákno je v tomto umístění zastaveno.

    Všimněte si, že značka vlákna může být částečně skryta zarážkou.

3. Najeďte ukazatelem myši na značku vlákna. Zobrazí se DataTip. DataTip oznamuje název a ID vlákna pro každé zastavené vlákno.

    Můžete také zobrazit umístění vláken v [okně paralelní zásobníky](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Kontrola datových částí pro webové služby a síťové prostředky (UWP)

V aplikacích pro UWP můžete analyzovat síťové operace prováděné pomocí rozhraní `Windows.Web.Http` API. Pomocí tohoto nástroje můžete ladit webové služby a síťové prostředky. Chcete-li použít nástroj, vyberte možnost **ladit > Performance Profiler**. Vyberte **síť**a pak zvolte **Spustit**. Ve své aplikaci Projděte scénář, který používá `Windows.Web.Http` a pak zvolte možnost **Zastavit shromažďování** pro vygenerování sestavy.

![Nástroj pro profilaci využití sítě](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Výběrem operace v souhrnném zobrazení zobrazíte další podrobnosti.

![Podrobné informace v nástroji využití sítě](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Další informace najdete v tématu [využití sítě](../profiling/network-usage.md).

## <a name="modules_window"></a>Seznamte se s tím, jak se ladicí program připojí k vašíC#aplikaci C++(,, F#Visual Basic,).

Pro připojení ke svojí spuštěné aplikaci ladicí program načítají soubory symbolů (PDB) vygenerované pro přesně stejné sestavení aplikace, kterou se pokoušíte ladit. V některých scénářích může být užitečné trochu znalost souborů symbolů. Můžete kontrolovat, jak aplikace Visual Studio načítá soubory symbolů pomocí okna **moduly** .

Otevřete okno **moduly** při ladění výběrem možnosti **ladit > moduly > Windows**. Okno **moduly** vám může sdělit, které moduly ladicí program zpracovává jako uživatelský kód nebo [*můj kód*](../debugger/just-my-code.md)a jaký je stav načítání symbolů pro daný modul. Ve většině scénářů ladicí program automaticky vyhledává soubory symbolů pro uživatelský kód, ale pokud chcete krokovat (nebo ladit) kód .NET, systémový kód nebo kód knihovny třetí strany, je potřeba, abyste získali správné soubory symbolů.

![Zobrazit informace o symbolech v okně moduly](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Informace o symbolech lze načíst přímo z okna **moduly** kliknutím pravým tlačítkem myši a zvolením možnosti **načíst symboly**.

V některých případech vývojáři aplikací dodávají aplikace bez odpovídajícího souboru symbolů (pro snížení nároky), ale udržují kopii odpovídajícího souboru symbolů pro sestavení tak, aby mohli později ladit vydanou verzi.

Chcete-li zjistit, jak ladicí program klasifikuje kód jako uživatelský kód, přečtěte si téma [pouze můj kód](../debugger/just-my-code.md). Další informace o souborech symbolů naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů v ladicím programu sady Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Víc se uč

Další tipy a triky a podrobnější informace najdete v těchto blogových příspěvcích:

- [7 méně známý hackatony pro ladění v aplikaci Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 skrytých Gems v aplikaci Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Viz také:

[Klávesové zkratky](../ide/productivity-shortcuts.md)
