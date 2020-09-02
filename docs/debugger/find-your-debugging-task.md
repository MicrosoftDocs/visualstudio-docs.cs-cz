---
title: Nalezení úlohy ladění
description: Identifikujte funkci ladicího programu, která vám pomůže s laděním aplikace
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89314898"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Hledání úlohy ladění v aplikaci Visual Studio

Pokud potřebujete pomáhat při mapování úlohy ladění na správnou funkci ladicího programu sady Visual Studio, který je relevantní, použijte odkazy uvedené v tomto článku. Seznam úkolů zde zahrnuje běžné úkoly, jako je například pozastavení kódu pro ladění, kontrolu proměnných a odesílání zpráv do okna **výstup** . Pokud potřebujete přehled funkcí ladicího programu, podívejte se na místo toho v [ladicím programu](debugger-feature-tour.md) .

## <a name="pause-running-code"></a>Pozastavit běh kódu

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pozastavení spuštěného kódu pro kontrolu řádku kódu, který může obsahovat chybu

Nastavte zarážku. Další informace najdete v tématu [použití zarážek](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pozastavení a kontrola aplikace, když dosáhnou určitého stavu

Vyzkoušejte podmíněný bod přerušení pro řízení, kde a kdy se zarážka aktivuje pomocí podmíněné logiky. Další informace najdete v tématu [podmínky zarážky](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pozastavit kód pouze v případě, že dojde ke změně vlastnosti nebo hodnoty konkrétního objektu

V jazyce C++ nastavte [datovou zarážku](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
Pro aplikace využívající .NET Core 3 můžete také nastavit [datovou zarážku](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

V opačném případě pro C# a F # můžete [sledovat ID objektu s podmíněnou zarážkou](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pozastavení kódu uvnitř smyčky v určité iteraci

Nastavte zarážku pomocí **čítače přístupů** jako podmínky. Další informace najdete v tématu [Počet volání](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pozastaví kód na začátku funkce, pokud znáte název funkce, ale ne její umístění.

Můžete to provést pomocí zarážky funkce. Další informace najdete v tématu [nastavení zarážek funkce](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Pozastavit kód na začátku více funkcí se stejným názvem

Pokud máte více funkcí se stejným názvem (přetížené funkce nebo funkce v různých projektech), můžete použít [zarážku funkce](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Správa a sledování zarážek

Použijte okno **zarážky** . Další informace najdete v tématu [Správa zarážek](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pozastavit kód a ladit při vyvolání konkrétní ošetřené nebo neošetřené výjimky

I když Pomocník pro výjimky ukazuje, kde došlo k chybě, pokud chcete pozastavit a ladit konkrétní chybu, můžete [ladicímu programu sdělit, že se má přerušit, pokud je vyvolána výjimka](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Nastavení zarážky ze zásobníku volání

Pokud chcete pozastavit a ladit kód při kontrole toku spuštění nebo zobrazení funkcí v oknech **zásobník volání** , přečtěte si téma [Nastavení zarážky v okně zásobník volání](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pozastavit kód v konkrétní instrukci sestavení

To lze provést [nastavením zarážky z okna](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)zpětného překladu.

## <a name="execute-code"></a>Spustit kód

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Přečtěte si příkazy pro procházení kódu během ladění.

Další informace naleznete v tématu [Navigace v kódu pomocí ladicího programu](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Kontrola dat

### <a name="check-the-value-of-variables-while-running-your-app"></a>Kontrolovat hodnotu proměnných při spuštění aplikace

Najeďte myší na proměnné pomocí [tipů k datům](view-data-values-in-data-tips-in-the-code-editor.md) nebo [Prozkoumejte proměnné v okně Automatické hodnoty a místní](autos-and-locals-windows.md)hodnoty.

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Sledovat měnící se hodnotu konkrétní proměnné

Nastavte kukátko pro proměnnou. Další informace najdete v tématu [Nastavení kukátka pro proměnné](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Zobrazit řetězce, které jsou pro okno ladicího programu příliš dlouhé

Při ladění otevřete vestavěný [Vizualizér řetězců](view-strings-visualizer.md) .

## <a name="configure-debugging"></a>Konfigurace ladění

### <a name="customize-information-shown-in-the-debugger"></a>Přizpůsobení informací zobrazených v ladicím programu

Můžete chtít zobrazit jiné informace než typ objektu jako hodnotu v různých oknech ladicího programu. Pro kód C#, Visual Basic, F # a C++/CLI, použijte atribut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Pro pokročilejší možnosti můžete uživatelské rozhraní přizpůsobit také vytvořením [vlastního Vizualizátoru](create-custom-visualizers-of-data.md).

V případě nativního kódu C++ použijte [architekturu NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Konfigurovat nastavení ladicího programu

Konfigurace možností ladicího programu a nastavení projektu ladicího programu naleznete v tématu [nastavení a příprava ladicího](debugger-settings-and-preparation.md)programu.

## <a name="additional-tasks"></a>Další úlohy

### <a name="fix-an-exception"></a>Opravit výjimku

Viz [Oprava výjimky](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Úprava kódu během relace ladění

Použijte [Upravit a pokračovat](edit-and-continue.md). Pro XAML použijte [Hot reloading XAML](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Odeslat zprávy do okna výstupu beze změny kódu

Nastavte zarážka s trasováním. Další informace najdete v tématu [použití trasováním](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Zobrazit pořadí, ve kterém jsou funkce volány

Viz [jak zobrazit zásobník volání](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Ladit na vzdálených počítačích

Viz téma [vzdálené ladění](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Ladění aplikace, která je již spuštěna

Viz [připojit ke spuštěným procesům](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Ladění vícevláknových aplikací

Viz [Ladění vícevláknových aplikací](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Vyřešit problémy s výkonem

Viz [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md) .