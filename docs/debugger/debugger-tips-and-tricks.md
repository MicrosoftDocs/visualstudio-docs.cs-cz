---
title: Tipy a triky v ladicím programu
description: Přečtěte si o některých funkcích méně známé podporována ladicím programu sady Visual Studio
ms.custom: seodec18
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 238236df48adab491cd8a1f9282a8f6a440c5321
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055222"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Další tipy pro vyšší produktivitu a triky pro ladicí program v sadě Visual Studio

Přečtěte si toto téma a další pár produktivitu tipy a triky pro ladicí program sady Visual Studio. Podívejte se na základní funkce ladicího programu, najdete v části [prohlídka funkcí ladicího programu](../debugger/debugger-feature-tour.md). V tomto tématu se budeme zabývat některé oblasti, které nejsou součástí prohlídka funkcí.

## <a name="pin-data-tips"></a>PIN kód datových tipech

Pokud často najedete myší datových tipech při ladění, můžete připnout datový tip pro proměnnou, abyste měli rychlý přístup. Proměnná zůstane připojený i po restartování počítače. Připnout popisu dat, klikněte na ikonu Připnutí při najetí myší nad ním. Můžete připnout více proměnných.

![Připnutí popisu dat.](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Váš kód upravit a pokračovat v ladění (C#, VB, C++)

Ve většině jazyky podporované v aplikaci Visual Studio můžete upravit kódu během relace ladění a pokračovat v ladění. Chcete-li tuto funkci použít, klikněte na tlačítko do kódu s kurzorem při pozastavení v ladicím programu, zkontrolujte úpravy a stiskněte klávesu **F5**, **F10**, nebo **F11** pro pokračování v ladění.

![Upravit a pokračovat v ladění](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Další informace o použití funkce a omezení funkcí, naleznete v tématu [upravit a pokračovat](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Ladění problémů, které je těžké reprodukovat

Pokud je obtížné nebo znovu vytvořit určitého stavu ve vaší aplikaci časově náročné, zvažte, zda může pomoci použití podmíněné zarážky. Můžete použít [podmíněné zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) a filtrovat zarážky vyhnuli narušení funkčnosti do kódu aplikace, dokud aplikace přejde do požadovaného stavu (jako je například stav, ve kterém je proměnná ukládání chybnými daty). Můžete nastavit podmínky, pomocí výrazů, filtry, počty přístupů a tak dále.

#### <a name="to-create-a-conditional-breakpoint"></a>Chcete-li vytvořit podmíněné zarážky

1. Klikněte pravým tlačítkem na ikonu zarážky (červená koule) a zvolte **podmínky**.

2. V **nastavení zarážek** okna, typ je to výraz.

    ![Podmíněné zarážky](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Pokud vás zajímají další typ podmínky, vyberte **filtr** místo **podmíněný výraz** v **nastavení zarážek** dialogové okno a pak proveďte Tipy pro filtr.

## <a name="change-the-execution-flow"></a>Změna toku provádění

Pomocí ladicího programu pomocí myši pozastavena na řádek kódu, získejte ukazatel žlutá šipka na levé straně. Přesuňte ukazatel žlutá šipka k jinému bodu v cestě k provádění kódu. Potom použijte klávesu F5 nebo příkaz kroku bude moct být spuštěná aplikace.

![Přesuňte ukazatel spuštění](../debugger/media/dbg-tour-move-the-execution-pointer.gif "přesunout ukazatel spuštění")

Změnou provádění toku můžete provést kroky, jako je test cesty spuštění odlišný kód nebo znovu spustit kód bez restartování ladicího programu.

> [!WARNING]
> Často je potřeba pečlivě s touto funkcí a zobrazit upozornění v popisu. Příliš se může zobrazit další varování. Ukazatele nejde vrátit zpět na vaši aplikaci do předchozího stavu aplikace.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Sledování objektu mimo rozsah (C#, Visual Basic)

Lze snadno zobrazit proměnné pomocí ladicího programu systému windows, stejně jako **Watch** okna. Nicméně pokud proměnnou dostane mimo rozsah v **Watch** okna, můžete si všimnout, že se šedě. V některých scénářích aplikace může změnit hodnotu proměnné i, když je proměnná mimo rozsah, a můžete chtít sledovat úzce (například proměnná může získat uvolněna z paměti). Proměnnou můžete sledovat tak, že vytvoříte pro něj v ID objektu **Watch** okna.

#### <a name="to-create-an-object-id"></a>Chcete-li vytvořit ID objektu

1.  Nastavte zarážku v proměnné, které chcete sledovat.

2.  Spuštění ladicího programu (**F5**) a zastavení na zarážce.

3. Vyhledejte proměnnou v **místní hodnoty** okno (**ladění > Windows > místní hodnoty**), klikněte pravým tlačítkem na proměnnou a vyberte **Ujistěte se, ID objektu**.

    ![Vytvoření ID objektu](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Měli byste vidět **$** plus číslo v **místní hodnoty** okna. Tato proměnná je ID objektu.
  
5.  Klikněte pravým tlačítkem na ID proměnné objektu a zvolte **Přidat kukátko**.

Další informace najdete v tématu [vytvořit ID objektu](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Zobrazit návratové hodnoty pro funkce

Chcete-li zobrazit návratové hodnoty pro vaše funkce, podívejte se na funkce, které se zobrazují v **automatické hodnoty** okno při krokování kódu. Pokud chcete zobrazit návratovou hodnotu funkce, ujistěte se, že funkce, které vás zajímají už se provedla (stiskněte **F10** jednou, pokud jsou nyní zastaveny u volání funkce). Pokud je okno zavřeno, použijte **ladit > Windows > Automatické hodnoty** otevřete **automatické hodnoty** okna.

![Okno Automatické hodnoty](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Kromě toho můžete zadat funkce v **okamžité** pro zobrazení návratových hodnot. (Otevřete ho pomocí **ladit > Windows > okamžité**.)

![Příkazové podokno](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Můžete také použít [pseudoproměnné](../debugger/pseudovariables.md) v **Watch** a **okamžité** okno, jako například `$ReturnValue`.

## <a name="string_visualizer"></a>Kontrola řetězců ve vizualizéru

Při práci s řetězci, může být užitečné, chcete-li zobrazit celý formátovaný řetězec. Chcete-li zobrazit prostý text, XML, HTML nebo JSON řetězec, klikněte na ikonu lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Vizualizéru ikonu") při najetí myší nad proměnné obsahující hodnotu řetězce.

![Otevřete Vizualizéru řetězce](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Vizualizér řetězce může vám pomůžou zjistit, jestli řetězec má chybný formát, v závislosti na typu řetězec. Například prázdnou hodnotu **hodnotu** pole označuje řetězec nerozpoznají typ vizualizéru. Další informace najdete v tématu [dialogové okno Vizualizéru řetězce](../debugger/string-visualizer-dialog-box.md).

![Vizualizér řetězce JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

U několika jiných typů jako je například WPF objekty, které se zobrazují v oknech ladicího programu můžete také otevřít vizualizéry.

## <a name="break-into-code-on-handled-exceptions"></a>Přepnutí do kódu na zpracování výjimek

Ladicí program přeruší do kódu v případě neošetřených výjimek. Ale zpracované výjimky (jako jsou například výjimky, ke kterým dochází v rámci `try/catch` bloku) může být také příčiny chyby a možná budete chtít zjistit, kdy k nim dojde. Ladicí program proniknout do kódu pro zpracování výjimky a tím, že nakonfigurujete možnosti můžete nakonfigurovat **nastavení výjimek** dialogové okno. Dialogové okno otevřít výběrem **ladit > Windows > Nastavení výjimek**.

**Nastavení výjimek** dialogové okno umožňuje zjistit, ladicí program proniknout do kódu na specifických výjimek. Na obrázku níže, ladicí program přeruší do kódu pokaždé, když se `System.NullReferenceException` vyvolá. Další informace najdete v tématu [Správa výjimek](../debugger/managing-exceptions-with-the-debugger.md).

![Dialogové okno nastavení výjimky](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Ladění zablokování a konflikty časování

Pokud musíte ladit druhy problémů, které jsou společné pro vícevláknové aplikace, často pomůže Chcete-li zobrazit umístění vlákna během ladění. Můžete provést jednoduše pomocí **zobrazit vlákna ve zdroji** tlačítko.

#### <a name="to-show-threads-in-your-source-code"></a>Chcete-li zobrazit vlákna ve zdrojovém kódu

1.  Při ladění, klikněte na tlačítko **zobrazit vlákna ve zdroji** tlačítko ![zobrazit vlákna ve zdroji](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") v **ladění** nástrojů.
  
2.  Podívejte se na ovládací prvek na levé straně okna. Na tomto řádku se zobrazí *značky vlákna* ikonu ![značky vlákna](../debugger/media/dbg-thread-marker.png "ThreadMarker") , který se podobá dvěma vlákny látky. Značky vlákna označuje, že je vlákno zastavené v tomto umístění.

    Všimněte si, že značky vlákna mohou být částečně zakryty podle zarážku.
  
3.  Ukazatel myši značky vlákna. Zobrazí se DataTip. DataTip zjistíte číslo ID názvu a vlákna pro každé vlákno zastavené.

    Můžete také zobrazit umístění vlákna [okna paralelní zásobníky](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Prozkoumat datové části pro webové služby a síťovým prostředkům (UPW)

V aplikacích pro UPW, můžete analyzovat pomocí provádí síťové operace `Windows.Web.Http` rozhraní API. Tento nástroj můžete použít k ladění webových služeb a síťových prostředků. Chcete-li použít nástroj, vyberte **ladit > Profiler výkonu**. Vyberte **sítě**a klikněte na tlačítko **Start**. Ve vaší aplikaci, projděte si scénáře, který používá `Windows.Web.Http`a klikněte na tlačítko **zastavit shromažďování** generování sestav.

![Síť používání nástrojů pro profilaci](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Vyberte operaci v souhrnné zobrazení zobrazte další podrobnosti.

![Podrobné informace o nástroji pro využití sítě](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Další informace najdete v tématu [využití sítě](../profiling/network-usage.md).

## <a name="modules_window"></a> Seznamte se s jak ladicí program připojí k vaší aplikaci (C#, C++, Visual Basic, F#)

Připojit k vaší běžící aplikaci, ladicí program načte soubory symbolů (PDB) vygenerovat pro přesně stejný build aplikaci, kterou se pokoušíte ladit. V některých případech může být užitečné trochu znalost soubory symbolů. Můžete prozkoumat, jak Visual Studio načte soubory symbolů pomocí **moduly** okna.

Otevřít **moduly** okno při ladění tak, že vyberete **ladit > Windows > moduly**. **Moduly** okno lze zjistit, jaké moduly ladicí program se zpracuje jako uživatelský kód, nebo [ *můj kód*](../debugger/just-my-code.md)a načítání stavu pro modul symbolů. Ve většině scénářů ladicí program automaticky vyhledá soubory symbolů pro uživatelský kód, ale pokud chcete krokovat s vnořením (nebo ladění) kódu rozhraní .NET framework, systémový kód nebo kód knihovny třetích stran, je potřeba získat soubory symbolů správné pár kroků navíc.

![Zobrazení informací o symbolu v okně moduly](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Můžete načíst informace o symbolech přímo z **moduly** okna tak, že kliknete pravým tlačítkem a zvolíte **načíst symboly**.

V některých případech Vývojáři aplikací dodávat aplikace bez odpovídající soubory symbolů (Chcete-li snížit nároky na), ale zachovat kopii odpovídající symbol souborů pro sestavení tak, aby se později ladit vydané verze.

Chcete-li zjistit, jak ladicí program klasifikuje kód jako uživatelský kód, naleznete v tématu [pouze můj kód](../debugger/just-my-code.md). Další informace o soubory symbolů, najdete v tématu [zadání symbolu (.pdb) a zdrojových souborů v ladicím programu sady Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Víc se uč

Další tipy a triky a podrobné informace najdete v těchto příspěvcích blogu:

- [7 menší známé hackatony pro ladění v sadě Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 skryté gems v sadě Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Viz také
[Klávesové zkratky](../ide/tips-and-tricks-for-visual-studio.md)
