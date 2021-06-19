---
title: Zobrazení zásobníku volání v ladicím programu | Microsoft Docs
description: Pomocí okna Zásobník volání můžete zobrazit volání funkce nebo procedury, která jsou aktuálně v zásobníku v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: how-to
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e905a509443cd5fd30e860a887dd895c5ee21a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387473"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Zobrazení zásobníku volání a použití okna Zásobník volání v ladicím programu

Pomocí okna **Zásobník volání** můžete zobrazit volání funkce nebo procedury, která jsou aktuálně v zásobníku. V **okně Zásobník** volání se zobrazuje pořadí, ve kterém se volají metody a funkce. Zásobník volání je dobrým způsobem, jak prozkoumat a pochopit tok provádění aplikace.

Pokud [nejsou symboly ladění](#bkmk_symbols) k dispozici pro  část zásobníku volání, nemusí být okno Zásobník volání schopné zobrazit správné informace pro tu část zásobníku volání, které místo toho zobrazuje:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Okno **Zásobník volání** je podobné perspektivě ladění v některých prostředích ID, jako je Eclipse.

> [!NOTE]
> Dialogová okna a příkazy nabídky, které vidíte, se můžou lišit od těch, které jsou zde popsané, v závislosti na aktivním nastavení nebo edici. Pokud chcete nastavení změnit, v **nabídce** Nástroje vyberte Importovat a exportovat **nastavení.**  Viz [Resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Zobrazení zásobníku volání v ladicím programu

- Při ladění v nabídce **Ladit** vyberte **Windows > volání**.

  ![Okno zásobníku volání](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Žlutá šipka identifikuje rámec zásobníku, ve kterém je ukazatel provádění aktuálně umístěn. Ve výchozím nastavení se informace o tomto snímku zásobníku zobrazí ve zdroji, místních **hodnotách**, automatických **hodnotách,** sledování a zpětný **překlad.** Pokud chcete změnit kontext ladicího programu na jiný snímek v zásobníku, [přepněte na jiný rámec zásobníku](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Zobrazení kódu uživatele v okně Zásobník volání

- Klikněte pravým tlačítkem na **okno Call Stack (Zásobník volání)** a vyberte **Show External Code (Zobrazit externí kód).**

Kód bez uživatele je jakýkoli kód, který se nezobrazí, [Pouze můj kód](../debugger/just-my-code.md) je povolený. Ve spravovaném kódu jsou rámce kódu jiných uživatelů ve výchozím nastavení skryté. Místo snímků kódu bez uživatele se zobrazí následující notace:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Přepněte na jiný rámec zásobníku (změňte kontext ladicího programu).

1. V okně **Zásobník volání** klikněte pravým tlačítkem na rámec zásobníku, jehož kód a data chcete zobrazit.

    Nebo můžete dvojitým kliknutím na snímek v **okně Zásobník volání** přepnout na tento rámec.

2. Vyberte **Switch to Frame (Přepnout na snímek).**

     Vedle vybraného rámce zásobníku se zobrazí zelená šipka s složenou chvostem. Ukazatel provádění zůstane v původním snímku, který je stále označen žlutou šipkou. Pokud v **nabídce Ladit** **vyberete** Krok nebo Pokračovat, provádění bude pokračovat v původním snímku, nikoli v rámci, který jste vybrali. 

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Zobrazení zdrojového kódu funkce v zásobníku volání

- V okně **Zásobník volání** klikněte pravým tlačítkem na funkci, jejíž zdrojový kód chcete zobrazit, a vyberte Přejít **ke zdrojovému kódu**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Spuštění na konkrétní funkci z okna Zásobník volání

- V okně **Call Stack (Zásobník** volání) vyberte funkci, klikněte pravým tlačítkem a pak **zvolte Run to Cursor (Spustit do kurzoru).**

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Nastavení zarážky na výstupním bodu volání funkce

- Viz [Nastavení zarážky na funkci zásobníku volání](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Zobrazení volání do nebo z jiného vlákna

- Klikněte pravým tlačítkem na **okno Call Stack (Zásobník volání)** a vyberte **Include Calls To/From Other Threads (Zahrnout volání do a z jiných vláken).**

## <a name="visually-trace-the-call-stack"></a>Vizuální trasování zásobníku volání

V Visual Studio Enterprise (pouze) můžete zobrazit mapy kódu pro zásobník volání během ladění.

- V **okně Zásobník volání** otevřete místní nabídku. Zvolte Show Call Stack on Code Map **(Zobrazit** **zásobník volání na mapě kódu)** ( Ctrl  +  **Shift**  +  **`** ).

    Další informace najdete v tématu [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Zobrazení zásobníku volání na mapě kódu](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Zobrazení kódu pro zpětný překlad funkce v zásobníku volání (C#, C++, Visual Basic, F#)

- V okně **Zásobník volání klikněte** pravým tlačítkem na funkci, jejíž kód pro zpětný překlad chcete zobrazit, a vyberte Přejít na zpětný **překlad**.

## <a name="change-the-optional-information-displayed"></a>Změna zobrazených volitelných informací

- Klikněte pravým tlačítkem do **okna Call Stack (Zásobník volání)** a nastavte nebo zrušte **zaškrtnutí políčka Show (Zobrazit). \<**_the information that you want_**>**

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Symboly zatížení pro modul (C#, C++, Visual Basic, F#)

V okně **Zásobník volání** můžete načíst symboly ladění pro kód, který aktuálně nemá načtené symboly. Tyto symboly mohou být .NET nebo systémové symboly stažené ze serverů veřejných symbolů společnosti Microsoft nebo symboly v cestě symbolů v počítači, který ladíte.

Viz [Zadání symbolu (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)a zdrojových souborů .

### <a name="to-load-symbols"></a>Načtení symbolů

1. V okně **Zásobník volání** klikněte pravým tlačítkem na rámec zásobníku, pro který nejsou načteny symboly. Snímek bude neaktivní.

2. Přejděte na **Load Symbols (Načíst** symboly) a pak vyberte **Microsoft Symbol Servers** (pokud je k dispozici) nebo vyhledejte cestu k symbolu.

### <a name="to-set-the-symbol-path"></a>Nastavení cesty symbolu

1. V okně **Zásobník volání** zvolte v **místní** nabídce Nastavení symbolů.

     Otevře **se** dialogové okno Možnosti a zobrazí **se** stránka Symboly.

2. Vyberte **Nastavení symbolů**.

3. V dialogovém **okně** Možnosti klikněte na ikonu Složka.

     V poli **Umístění souboru symbolů (.pdb)** se zobrazí kurzor.

4. Zadejte cestu k adresáři k umístění symbolu na počítači, který ladíte. Pro místní a vzdálené ladění je to cesta na místním počítači.

5. Výběrem **OK** zavřete **dialogové okno** Možnosti.

## <a name="see-also"></a>Viz také

- [Smíšený kód a chybějící informace v okně Zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Použití zarážek](../debugger/using-breakpoints.md)