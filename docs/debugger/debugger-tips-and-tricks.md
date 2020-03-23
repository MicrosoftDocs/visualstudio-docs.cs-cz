---
title: Tipy a triky v ladicím programu
description: Informace o některých méně známých funkcích podporovaných ladicím programem sady Visual Studio
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
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302215"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Naučte se tipy a triky pro produktivitu pro ladicí program v sadě Visual Studio

Přečtěte si toto téma, kde se dozvíte několik tipů a triků pro zvýšení produktivity pro ladicí program sady Visual Studio. Podívejte se na základní funkce ladicího programu, viz [První pohled na ladicí program](../debugger/debugger-feature-tour.md). V tomto tématu se zabýváme některými oblastmi, které nejsou zahrnuty do prohlídky funkcí.

## <a name="pin-data-tips"></a>Tipy pro připnutí dat

Pokud při ladění často najedete na datové tipy, můžete připnout tip na data pro proměnnou, abyste měli rychlý přístup. Proměnná zůstane připnutá i po restartování. Pokud chcete připnout tip na data, klikněte na ikonu špendlíku a najeďte na ni. Můžete připnout více proměnných.

![Připnutí datového tipu](../debugger/media/dbg-tips-data-tips-pinned.png "Připnutídatového tipu")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Upravte kód a pokračujte v ladění (C#, VB, C++)

Ve většině jazyků podporovaných visual studio, můžete upravit kód uprostřed relace ladění a pokračovat v ladění. Chcete-li tuto funkci použít, klikněte do kódu kurzorem, zatímco pozastaveno v ladicím programu, provést úpravy a stiskněte **Klávesu F5**, **F10**nebo **F11** pokračovat ladění.

![Úprava a pokračování ladění](../debugger/media/dbg-tips-edit-and-continue.gif "Editand Pokračovat")

Další informace o používání funkce a omezeních funkcí naleznete v tématu [Úpravy a pokračování](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Úprava kódu XAML a pokračování v ladění

Chcete-li upravit kód XAML během relace ladění, přečtěte si informace o [zápisu a ladění se spuštěným kódem XAML s opětovným načtením xaml.](../xaml-tools/xaml-hot-reload.md)

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Ladění problémů, které se těžko reprodukují

Pokud je obtížné nebo časově náročné znovu vytvořit určitý stav ve vaší aplikaci, zvažte, zda může pomoci použití podmíněné zarážky. Pomocí [podmíněných zarážek](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a zarážek filtru zabráníte rozdělení kódu aplikace, dokud aplikace nezadá požadovaný stav (například stav, ve kterém proměnná ukládá chybná data). Podmínky můžete nastavit pomocí výrazů, filtrů, počtu přístupů a tak dále.

#### <a name="to-create-a-conditional-breakpoint"></a>Vytvoření podmíněné zarážky

1. Klepněte pravým tlačítkem myši na ikonu zarážky (červená koule) a zvolte **Podmínky**.

2. Do okna **Nastavení zarážky** zadejte výraz.

    ![Podmíněná zarážka](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Podmíněný bod přerušení")

3. Pokud vás zajímá jiný typ podmínky, vyberte **filtrovat** místo **podmíněného výrazu** v dialogovém okně **Nastavení zarážky** a postupujte podle tipů filtru.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Konfigurace dat, která se mají zobrazovat v ladicím programu

Pro C#, Visual Basic a C++ (pouze kód C++/CLI) můžete ladicímu programu sdělit, jaké informace se mají zobrazit pomocí [atributu DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) Pro kód C++ můžete provést totéž pomocí [vizualizací Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Změna toku spuštění

S ladicí program pozastaven a na řádku kódu, pomocí myši uchopit žlutou šipku ukazatel na levé straně. Přesuňte ukazatel žluté šipky do jiného bodu v cestě spuštění kódu. Potom můžete použít F5 nebo krok příkaz pokračovat ve spuštění aplikace.

![Přesunutí ukazatele spuštění](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Přesunutí ukazatele spuštění")

Změnou toku spuštění můžete dělat věci, jako je testování různých cest spuštění kódu nebo znovu spustit kód bez restartování ladicího programu.

> [!WARNING]
> Často je třeba být opatrní s touto funkcí a zobrazí se upozornění v popisku. Můžete vidět i další varování. Přesunutí ukazatele se nemůže vrátit do dřívějšího stavu aplikace.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Sledování objektu mimo rozsah (C#, Visual Basic)

Je snadné zobrazit proměnné pomocí ladicích oken, jako je okno **Kukátko.** Však při proměnné přejde mimo rozsah v okně **kukátka,** můžete si všimnout, že je šedě. V některých scénářích aplikace se hodnota proměnné může změnit i v případě, že je proměnná mimo rozsah, a můžete ji pozorně sledovat (například proměnná může získat uvolněné odpadky). Proměnnou můžete sledovat vytvořením ID objektu v okně **Kukátka.**

#### <a name="to-create-an-object-id"></a>Vytvoření ID objektu

1. Nastavte zarážku poblíž proměnné, kterou chcete sledovat.

2. Spusťte ladicí program (**F5**) a zastavte na zarážky.

3. Najděte proměnnou v okně **Locals** **(Ladění > Windows > Locals),** klepněte pravým tlačítkem myši na proměnnou a vyberte **příkaz Vytvořit ID objektu**.

    ![Vytvoření ID objektu](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. V okně **$** **Locals** byste měli vidět plus číslo. Tato proměnná je ID objektu.

5. Klepněte pravým tlačítkem myši na proměnnou ID objektu a zvolte **Přidat hodinky**.

Další informace naleznete [v tématu Vytvoření ID objektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Zobrazit vrácené hodnoty pro funkce

Chcete-li zobrazit vrácené hodnoty pro vaše funkce, podívejte se na funkce, které se zobrazí v okně **Autos** při krokování kódu. Chcete-li zobrazit vrácenou hodnotu funkce, ujistěte se, že funkce, která vás zajímá, již byla provedena (stiskněte **klávesu F10** jednou, pokud jste aktuálně zastaveni při volání funkce). Pokud je okno zavřené, otevřete okno **Autos** pomocí **ladění > windows > Autos.**

![Okno Autos](../debugger/media/dbg-tips-autos-window.png "AutosOkno")

Kromě toho můžete zadat funkce v okně **Okamžité** pro zobrazení vrácené hodnoty. (Otevřete jej pomocí **ladění > Windows > Okamžité**.)

![Příkazové podokno](../debugger/media/dbg-tips-immediate-window.png "Okamžité Okno")

[Pseudoproměnné](../debugger/pseudovariables.md) můžete také použít v okně **Kukátko** a **Okamžité,** například `$ReturnValue`.

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Kontrola řetězců ve vizualizéru

Při práci s řetězci může být užitečné zobrazit celý formátovaný řetězec. Chcete-li zobrazit prostý text, řetězec XML, HTML nebo JSON, klepněte na ikonu lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona vizualizéru") a najeďte nad proměnnou obsahující hodnotu řetězce.

![Otevření vizualizéru řetězce](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Vizualizér řetězce vám může pomoci zjistit, zda je řetězec poškozený, v závislosti na typu řetězce. Například prázdné pole **Hodnota** označuje, že řetězec není rozpoznán typem vizualizéru. Další informace naleznete v [dialogovém okně Vizualizér řetězců](../debugger/string-visualizer-dialog-box.md).

![Vizualizér řetězců JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVizizér")

Pro několik dalších typů, jako je Například DataSet a DataTable objekty, které se zobrazí v oknech ladicího programu, můžete také otevřít vestavěný vizualizér.

## <a name="break-into-code-on-handled-exceptions"></a>Rozdělit na kód na zpracovávaných výjimkách

Ladicí program se rozdělí do kódu na neošetřené výjimky. Však zpracované výjimky (například výjimky, ke kterým dochází v rámci `try/catch` bloku) může být také zdrojem chyb a můžete chtít prozkoumat, když k nim dojde. Ladicí program můžete nakonfigurovat tak, aby se rozdělil na kód pro zpracované výjimky také konfigurací možností v dialogovém okně **Nastavení výjimek.** Otevřete toto dialogové okno tak, že zvolíte **Ladění > nastavení výjimky systému Windows >**.

Dialogové okno **Nastavení výjimek** umožňuje sdělit ladicímu programu, aby se rozdělil na kód u konkrétních výjimek. Na následujícím obrázku ladicí program se `System.NullReferenceException` rozdělí do kódu vždy, když dojde k výskytu. Další informace naleznete v [tématu Správa výjimek](../debugger/managing-exceptions-with-the-debugger.md).

![Dialogové okno Nastavení výjimky](../debugger/media/dbg-tips-exception-settings.png "Dialogové okno ExceptionSettingsDialog")

## <a name="debug-deadlocks-and-race-conditions"></a>Ladicí patové situace a sporové podmínky

Pokud potřebujete ladit druhy problémů, které jsou společné pro aplikace s více vlákny, často pomáhá zobrazit umístění podprocesů při ladění. Můžete to udělat snadno pomocí tlačítka **Zobrazit vlákna ve zdroji.**

#### <a name="to-show-threads-in-your-source-code"></a>Zobrazení vláken ve zdrojovém kódu

1. Při ladění klikněte na tlačítko **Zobrazit vlákna ve zdroji** Zobrazit ![vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") na panelu nástrojů **Ladění.**

2. Podívejte se na okap na levé straně okna. Na tomto řádku se zobrazí ikona *značky závitu* ![Značka závitu,](../debugger/media/dbg-thread-marker.png "ThreadMarker") která se podobá dvěma látkovým vláknům. Značka vlákna označuje, že vlákno je zastaveno v tomto umístění.

    Všimněte si, že značka vlákna může být částečně skryta zarážkou.

3. Najeďte myší na značku závitu. Zobrazí se datový tip. DataTip vám sdělí název a číslo ID vlákna pro každé zastavené vlákno.

    Můžete také zobrazit umístění podprocesů v [okně Paralelní hromádky](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Zkontrolujte datové části pro webové služby a síťové prostředky (UPW)

V aplikacích UPW můžete analyzovat síťové `Windows.Web.Http` operace prováděné pomocí rozhraní API. Tento nástroj můžete použít k ladění webových služeb a síťových prostředků. Chcete-li nástroj použít, vyberte **možnost Ladění > profileru výkonu**. Vyberte **Síť**a pak zvolte **Spustit**. Ve vaší aplikaci projděte `Windows.Web.Http`scénář, který používá , a pak zvolte **Zastavit kolekci** pro generování sestavy.

![Nástroj pro profilování využití sítě](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Vyberte operaci v souhrnném zobrazení, chcete-li zobrazit další podrobnosti.

![Podrobné informace v nástroji Používání sítě](../profiling/media/prof-tour-network-usage-details.png "Podrobné zobrazení sítěVyužití")

Další informace naleznete v [tématu Usage Network](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Seznamte se s tím, jak se ladicí program připojuje k vaší aplikaci (C#, C++, Visual Basic, F#)

Chcete-li připojit k běžící aplikaci, ladicí program načte symbol (.pdb) soubory generované pro přesně stejné sestavení aplikace, kterou se pokoušíte ladit. V některých scénářích může být užitečná malá znalost souborů symbolů. Můžete zkontrolovat, jak Visual Studio načte soubory symbolů pomocí okna **Moduly.**

Otevřete okno **Moduly** při ladění výběrem **možnosti Ladění > moduly > systému Windows**. Okno **Moduly** vám může říct, jaké moduly ladicí program je považován za uživatelský kód nebo [*Můj kód*](../debugger/just-my-code.md)a stav načítání symbolu pro modul. Ve většině scénářů ladicí program automaticky vyhledá soubory symbolů pro uživatelský kód, ale pokud chcete krokovat do (nebo ladit) kód .NET, systémový kód nebo kód knihovny jiného výrobce, jsou k získání správných souborů symbolů vyžadovány další kroky.

![Zobrazení informací o symbolu v okně Moduly](../debugger/media/dbg-tips-modules-window.png "Zobrazit informace o symbolech")

Informace o symbolech můžete načíst přímo z okna **Moduly** kliknutím pravým tlačítkem myši a výběrem **možnosti Načíst symboly**.

Někdy vývojáři aplikací dodávají aplikace bez odpovídajících souborů symbolů (aby se snížila stopa), ale uchovávají kopii odpovídajících souborů symbolů pro sestavení, aby mohli později ladit vydanou verzi.

Chcete-li zjistit, jak ladicí program klasifikuje kód jako uživatelský kód, [přečtěte si stránku Pouze můj kód](../debugger/just-my-code.md). Další informace o souborech symbolů naleznete v [tématu Určení symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Další informace

Další tipy a triky a podrobnější informace najdete v těchto příspěvcích na blogu:

- [7 méně známých hacků pro ladění v sadě Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 skrytých drahokamů v sadě Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Viz také

[Klávesové zkratky](../ide/productivity-shortcuts.md)
