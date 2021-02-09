---
title: Nejčastější dotazy – vyhledání funkce ladění
description: Nejčastější dotazy, které vám pomůžou identifikovat funkci ladicího programu, která vám pomůže s laděním aplikace
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c215b232c64b97c57285618056ee4675587b48e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870711"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Nejčastější dotazy – v aplikaci Visual Studio najdete funkci ladění, kterou potřebujete.

Pokud potřebujete pomáhat při mapování úlohy ladění na správnou funkci ladicího programu sady Visual Studio, který je relevantní, použijte odkazy uvedené v tomto článku. Seznam úkolů zde zahrnuje běžné úkoly, jako je například pozastavení kódu pro ladění, kontrolu proměnných a odesílání zpráv do okna **výstup** . Pokud potřebujete přehled funkcí ladicího programu, podívejte se na místo toho v [ladicím programu](debugger-feature-tour.md) .

## <a name="fix-an-exception"></a>Opravit výjimku

- Viz [Oprava výjimky](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Pozastavit běh kódu

- **Pozastavení spuštěného kódu pro kontrolu řádku kódu, který může obsahovat chybu**

  Nastavte zarážku. Další informace najdete v tématu [použití zarážek](using-breakpoints.md).

- **Pozastavení a kontrola aplikace, když dosáhnou určitého stavu**

  Vyzkoušejte podmíněný bod přerušení pro řízení, kde a kdy se zarážka aktivuje pomocí podmíněné logiky. Další informace najdete v tématu [podmínky zarážky](using-breakpoints.md#breakpoint-conditions).

- **Pozastavit kód pouze v případě, že dojde ke změně vlastnosti nebo hodnoty konkrétního objektu**

  V jazyce C++ nastavte [datovou zarážku](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  Pro aplikace využívající .NET Core 3 můžete také nastavit [datovou zarážku](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  V opačném případě pro C# a F # můžete [sledovat ID objektu s podmíněnou zarážkou](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Pozastavení kódu uvnitř smyčky v určité iteraci**

  Nastavte zarážku pomocí **čítače přístupů** jako podmínky. Další informace najdete v tématu [Počet volání](using-breakpoints.md#set-a-hit-count-condition).

- **Pozastaví kód na začátku funkce, pokud znáte název funkce, ale ne její umístění.**

  Můžete to provést pomocí zarážky funkce. Další informace najdete v tématu [nastavení zarážek funkce](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Pozastavit kód na začátku více funkcí se stejným názvem**

  Pokud máte více funkcí se stejným názvem (přetížené funkce nebo funkce v různých projektech), můžete použít [zarážku funkce](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Správa a sledování zarážek**

  Použijte okno **zarážky** . Další informace najdete v tématu [Správa zarážek](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Pozastavit kód a ladit při vyvolání konkrétní ošetřené nebo neošetřené výjimky**

  I když Pomocník pro výjimky ukazuje, kde došlo k chybě, pokud chcete pozastavit a ladit konkrétní chybu, můžete [ladicímu programu sdělit, že se má přerušit, pokud je vyvolána výjimka](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Nastavení zarážky ze zásobníku volání**

  Pokud chcete pozastavit a ladit kód při kontrole toku spuštění nebo zobrazení funkcí v oknech **zásobník volání** , přečtěte si téma [Nastavení zarážky v okně zásobník volání](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Pozastavit kód v konkrétní instrukci sestavení**

  To lze provést [nastavením zarážky z okna](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows)zpětného překladu.

## <a name="execute-code"></a>Spustit kód

- **Přečtěte si příkazy pro procházení kódu během ladění.**

  Další informace naleznete v tématu [Navigace v kódu pomocí ladicího programu](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Kontrola dat

- **Kontrolovat hodnotu proměnných při spuštění aplikace**

  Najeďte myší na proměnné pomocí [tipů k datům](view-data-values-in-data-tips-in-the-code-editor.md) nebo [Prozkoumejte proměnné v okně Automatické hodnoty a místní](autos-and-locals-windows.md)hodnoty.

- **Sledovat měnící se hodnotu konkrétní proměnné**

  Nastavte kukátko pro proměnnou. Další informace najdete v tématu [Nastavení kukátka pro proměnné](watch-and-quickwatch-windows.md).

- **Zobrazit řetězce, které jsou pro okno ladicího programu příliš dlouhé**

  Při ladění otevřete vestavěný [Vizualizér řetězců](view-strings-visualizer.md) .

## <a name="debug-an-app-that-is-already-running"></a>Ladění aplikace, která je již spuštěna

- Viz [připojit ke spuštěným procesům](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Ladění vícevláknových aplikací

- Viz [Ladění vícevláknových aplikací](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Konfigurace ladění

- **Konfigurovat nastavení ladicího programu**

  Konfigurace možností ladicího programu a nastavení projektu ladicího programu naleznete v tématu [nastavení a příprava ladicího](debugger-settings-and-preparation.md)programu.

- **Přizpůsobení informací zobrazených v ladicím programu**

  Můžete chtít zobrazit jiné informace než typ objektu jako hodnotu v různých oknech ladicího programu. Pro kód C#, Visual Basic, F # a C++/CLI, použijte atribut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Pro pokročilejší možnosti můžete uživatelské rozhraní přizpůsobit také vytvořením [vlastního Vizualizátoru](create-custom-visualizers-of-data.md).

  V případě nativního kódu C++ použijte [architekturu NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Další úlohy

- **Úprava kódu během relace ladění**

  Použijte [Upravit a pokračovat](edit-and-continue.md). Pro XAML použijte [Hot reloading XAML](../xaml-tools/xaml-hot-reload.md).

- **Odeslat zprávy do okna výstupu beze změny kódu**

  Nastavte zarážka s trasováním. Další informace najdete v tématu [použití trasováním](using-tracepoints.md).

- **Zobrazit pořadí, ve kterém jsou funkce volány**

  Viz [jak zobrazit zásobník volání](how-to-use-the-call-stack-window.md).

- **Ladit na vzdálených počítačích**

  Viz téma [vzdálené ladění](remote-debugging.md).

- **Řešení problémů s výkonem**

  Viz [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md) .
