---
title: Nalezení úlohy ladění
description: Identifikujte funkci ladicího programu, která vám pomůže ladit aplikaci
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302180"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Vyhledání úlohy ladění v sadě Visual Studio

Pokud potřebujete pomoc s mapováním úlohy ladění na správnou funkci ladicího programu sady Visual Studio, která je relevantní, použijte odkazy uvedené v tomto článku. Seznam úkolů zde obsahuje běžné úkoly, jako je například pozastavení kódu pro ladění, kontrola proměnných a odesílání zpráv do okna **Výstup.** Pokud potřebujete přehled funkcí ladicího programu, přečtěte si místo toho [první pohled na ladicí program.](debugger-feature-tour.md)

## <a name="pause-running-code"></a>Pozastavení spuštěný kód

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pozastavit spuštění kódu a zkontrolovat řádek kódu, který může obsahovat chybu

Nastavte zarážku. Další informace naleznete [v tématu Použití zarážek](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pozastavení a kontrola aplikace, když dosáhne určitého stavu

Zkuste podmíněné zarážky řídit, kde a kdy se aktivuje zarážka pomocí podmíněné logiky. Další informace naleznete v tématu [Podmínky zarážky](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pozastavení kódu pouze v případě, že se změní vlastnost nebo hodnota určitého objektu

Pro c++ nastavte [zarážky dat](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
U aplikací používajících rozhraní .NET Core 3 můžete také nastavit [zarážky dat](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

V opačném případě pouze pro C# a F# můžete [sledovat ID objektu s podmíněnou zarážkou](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pozastavení kódu uvnitř smyčky v určité iteraci

Nastavte zarážku pomocí **počtu přístupů** jako podmínku. Další informace naleznete v tématu [Počet přístupů](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pozastavení kódu na začátku funkce, pokud znáte název funkce, ale ne její umístění

Můžete to provést s zarážkou funkce. Další informace naleznete v tématu [Nastavení zarážek funkce](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Pozastavení kódu na začátku více funkcí se stejným názvem

Pokud máte více funkcí se stejným názvem (přetížené funkce nebo funkce v různých projektech), můžete použít [zarážky funkce](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Správa a sledování zarážek

Použijte okno **Zarážky.** Další informace naleznete v [tématu Správa zarážek](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pozastavení kódu a ladění při vyvolání určité zpracované nebo neošetřené výjimky

Přestože pomocník výjimek ukazuje, kde došlo k chybě, pokud chcete pozastavit a ladit konkrétní chybu, můžete [říct ladicí program přerušit při vyvolání výjimky](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Nastavení zarážky ze zásobníku volání

Pokud chcete pozastavit a ladit kód při zkoumání toku spuštění nebo zobrazení funkcí v oknech **zásobníku volání,** přečtěte si část [Nastavení zarážky v okně Zásobník volání](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pozastavení kódu na konkrétní instrukci sestavení

To lze provést [nastavením zarážky z okna Demontáže](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Spustit kód

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Naučte se příkazy pro krokování kódu při ladění

Další informace naleznete v [tématu Navigate code with the ladicí program](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Kontrola dat

### <a name="check-the-value-of-variables-while-running-your-app"></a>Kontrola hodnoty proměnných při spuštění aplikace

Najeďte na proměnné pomocí [datových tipů](view-data-values-in-data-tips-in-the-code-editor.md) nebo [zkontrolujte proměnné v okně Autos a Locals](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Dodržujte měnící se hodnotu určité proměnné

Nastavte hodinky na proměnnou. Další informace naleznete [v tématu Nastavení hodinek na proměnné](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Zobrazit řetězce, které jsou pro okno ladicího programu příliš dlouhé

Otevřete vestavěný [vizualizér řetězce](view-strings-visualizer.md) při ladění.

## <a name="configure-debugging"></a>Konfigurace ladění

### <a name="customize-information-shown-in-the-debugger"></a>Přizpůsobení informací zobrazených v ladicím programu

Můžete chtít zobrazit jiné informace než typ objektu jako hodnotu v různých oknech ladicího programu. Pro kód C#, Visual Basic, F# a C++/CLI použijte atribut [DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Pro pokročilejší možnosti můžete také přizpůsobit ui vytvořením [vlastního vizualizéru](create-custom-visualizers-of-data.md).

Pro nativní C++ použijte [architekturu NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Konfigurace nastavení ladicího programu

Pokud chcete nakonfigurovat možnosti ladicího programu a nastavení projektu ladicího programu, přečtěte si informace o [nastavení ladicího programu a přípravě](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Další úlohy

### <a name="fix-an-exception"></a>Oprava výjimky

Viz [Oprava výjimky](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Úprava kódu během relace ladění

Použijte [upravit a pokračujte](edit-and-continue.md). Pro XAML použijte [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Odesílání zpráv do okna Výstup bez úpravy kódu

Nastavte trasovací bod. Další informace naleznete v tématu [Using tracepoints](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Zobrazení pořadí, ve kterém jsou funkce volány

Viz [Jak zobrazit zásobník volání](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Ladění na vzdálených počítačích

Viz [Vzdálené ladění](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Ladění aplikace, která je již spuštěna

Viz [Připojení ke spuštěným procesům](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Ladění vícevláknových aplikací

Viz [Ladění vícevláknových aplikací](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Oprava problémů s výkonem

Viz [První pohled na nástroje profilování](../profiling/profiling-feature-tour.md)