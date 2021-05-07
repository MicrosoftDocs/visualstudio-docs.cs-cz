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
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800479"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Nejčastější dotazy – vyhledání funkce ladění, kterou potřebujete v Visual Studio

Pokud potřebujete pomoc s mapováním úlohy ladění na správnou funkci ladicího programu Visual Studio, který je relevantní, použijte odkazy uvedené v tomto článku. Seznam úkolů zde zahrnuje běžné úlohy, jako je pozastavení kódu k ladění, kontrola proměnných a odesílání zpráv do **okna** Výstup. Pokud potřebujete přehled funkcí ladicího programu, podívejte se nejprve [na ladicí program.](debugger-feature-tour.md)

## <a name="fix-an-exception"></a>Oprava výjimky

- Viz [Oprava výjimky](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Pozastavení spuštěného kódu

- **Pozastavení spuštěného kódu pro kontrolu řádku kódu, který může obsahovat chybu**

  Nastavte zarážku. Další informace najdete v tématu [Použití zarážek](using-breakpoints.md).

- **Pozastavení a kontrola aplikace, když dosáhne určitého stavu**

  Vyzkoušejte podmíněnou zarážku, abyste měli kontrolu nad tím, kde a kdy se zarážka aktivuje pomocí podmíněné logiky. Další informace najdete v tématu [Podmínky zarážky](using-breakpoints.md#breakpoint-conditions).

- **Pozastavení kódu pouze v případě, že se změní vlastnost nebo hodnota konkrétního objektu**

  V jazyce C++ nastavte [datovou zarážku](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  Pro aplikace používající .NET Core 3 můžete také nastavit datovou [zarážku](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  Jinak můžete id objektu sledovat pouze pro C# a F# [s podmíněnou zarážkou](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Pozastavení kódu uvnitř smyčky při určité iteraci**

  Nastavte zarážku pomocí **funkce Počet přístupů** jako podmínky. Další informace najdete v tématu [Počet volání](using-breakpoints.md#set-a-hit-count-condition).

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

- **Sledování měnící se hodnoty konkrétní proměnné**

  Nastavte sledování proměnné . Další informace najdete v tématu [Nastavení sledování proměnných](watch-and-quickwatch-windows.md).

- **Zobrazení řetězců, které jsou pro okno ladicího programu příliš dlouhé**

  Při ladění otevřete integrovaný [vizualizér](view-strings-visualizer.md) řetězců.

## <a name="debug-an-app-that-is-already-running"></a>Ladění aplikace, která je už spuštěná

- Viz [Připojení ke spuštěných procesům.](attach-to-running-processes-with-the-visual-studio-debugger.md)

## <a name="debug-multithreaded-applications"></a>Ladění vícevláknových aplikací

- Viz [Ladění vícevláknových aplikací.](debug-multithreaded-applications-in-visual-studio.md)

## <a name="configure-debugging"></a>Konfigurace ladění

- **Konfigurace nastavení ladicího programu**

  Informace o konfiguraci možností ladicího programu a nastavení projektu ladicího programu najdete v tématu [Nastavení a příprava ladicího programu.](debugger-settings-and-preparation.md)

- **Přizpůsobení informací zobrazených v ladicím programu**

  Můžete chtít zobrazit jiné informace než typ objektu jako hodnotu v různých oknech ladicího programu. Pro C# Visual Basic, F# a C++/CLI použijte [atribut DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Pro pokročilejší možnosti můžete uživatelské rozhraní přizpůsobit také vytvořením [vlastního vizualizéru](create-custom-visualizers-of-data.md).

  Pro nativní C++ použijte rozhraní [NatVis.](create-custom-views-of-native-objects.md)

## <a name="additional-tasks"></a>Další úlohy

- **Úprava kódu během ladicí relace**

  Použijte [upravit a pokračovat.](edit-and-continue.md) Pro XAML použijte [Opětovné načítání XAML za provozu](../xaml-tools/xaml-hot-reload.md).

- **Odeslání zpráv do okna Výstup beze změny kódu**

  Nastavte trasovací bod. Další informace najdete v tématu [použití trasováním](using-tracepoints.md).

- **Zobrazit pořadí, ve kterém jsou funkce volány**

  Viz [jak zobrazit zásobník volání](how-to-use-the-call-stack-window.md).

- **Ladit na vzdálených počítačích**

  Viz téma [vzdálené ladění](remote-debugging.md).

- **Řešení problémů s výkonem**

  Viz [první pohled na nástroje pro profilaci](../profiling/profiling-feature-tour.md) .
