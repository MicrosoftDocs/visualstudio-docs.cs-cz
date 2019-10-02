---
title: Zobrazit zásobník volání v ladicím programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 10/29/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0b9fb6e809f1124a10a6a2b4e35bc59806787a6
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814333"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Zobrazení zásobníku volání a použití okna zásobník volání v ladicím programu

S použitím **zásobník volání** okně můžete zobrazit volání funkce nebo procedury, které jsou aktuálně na zásobníku. **Zásobník volání** okno zobrazuje pořadí, ve kterém jsou získávání volány metody a funkce. Zásobník volání je dobrým způsobem, jak zkoumat a pochopit provádění toku aplikace.

Když [symboly ladění](#bkmk_symbols) nejsou k dispozici pro celý zásobník volání **zásobník volání** okna nemusí být schopno zobrazit správné informace pro tuto část zásobníku volání, místo zobrazení:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> **Zásobník volání** okno je podobné ladění perspektivy v některých prostředí IDE, jako je Eclipse.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch zde popsaných v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, vyberte **nastavení importu a exportu** na **nástroje** nabídky.  Zobrazit [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Zobrazit zásobník volání v ladicím programu

- Při ladění v **ladění** nabídce vyberte možnost **Windows > zásobník volání**.

  ![Okno zásobník volání](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Žlutá šipka označuje zásobník snímků, kde je nyní umístěn ukazatel spuštění. Ve výchozím nastavení, zobrazí tento rámec zásobníku informace ve zdroji, **lokální**, **automatické hodnoty**, **Watch**, a **zpětný překlad** systému windows. Chcete-li změnit kontext ladicího programu na jiný rámec v zásobníku, [přepnout do jiného zásobníku](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Zobrazení kódu nepocházejícího od uživatele v okně zásobník volání

- Klikněte pravým tlačítkem myši **zásobník volání** okna a vyberte **zobrazit externí kód**.

Neuživatelský kód je jakýkoli kód, který se zobrazí při [pouze můj kód](../debugger/just-my-code.md) je povolená. Ve spravovaném kódu jsou ve výchozím nastavení skryje neuživatelský kód snímků. Zobrazí se následující zápis místo snímků neuživatelský kód:

`[<External Code>]`

## <a name="bkmk_switch"></a> Přepnout na jiný rámec zásobníku (Změna kontextu ladicího programu)

1. V **zásobník volání** okna, klikněte pravým tlačítkem na snímek zásobníku, jehož kód a data, která chcete zobrazit.

    Nebo můžete dvakrát kliknout na snímek v **zásobník volání** okna přepnout na rámec.

2. Vyberte **přepnout na rámec**.

     Zelená šipka s vlnitým ocáskem se objeví vedle snímku zásobníku, který jste vybrali. Spuštění ukazatele zůstane v původním rámci stále označeno žlutou šipkou. Pokud vyberete **krok** nebo **pokračovat** z **ladění** nabídky, spuštění bude pokračovat v původním rámci, ne ve vámi vybraném.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Zobrazit zdrojový kód pro funkci v zásobníku volání

- V **zásobník volání** okna, klikněte pravým tlačítkem na funkci, jejíž zdrojový kód chcete zobrazit a vybrat **přejít ke zdrojovému kódu**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Spuštění specifické funkce z okna zásobník volání

- V **zásobník volání** okna, vyberte funkci, klepněte pravým tlačítkem myši a klikněte na tlačítko **spustit ke kurzoru**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Nastavení zarážky ve výstupním bodě volání funkce

- Zobrazit [nastavení zarážky na volání funkce zásobníku](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Zobrazení volání do nebo z jiného vlákna

- Klikněte pravým tlačítkem myši **zásobník volání** okna a vyberte **zahrnout hovory do/z jiných podprocesů**.

## <a name="visually-trace-the-call-stack"></a>Vizuální trasování zásobníku volání

V sadě Visual Studio Enterprise (pouze) můžete zobrazit map kódu pro zásobníku volání při ladění.

- V **zásobník volání** okno, otevřete místní nabídku. Zvolte **zobrazit zásobník volání na mapě kódu** (**Ctrl** + **Shift** +  **`** ).

    Další informace najdete v tématu [mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Zobrazit zásobník volání na mapě kódu](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Zobrazení zpětného překladu funkce v zásobníku volání (C#, C++, Visual Basic, F#)

- V **zásobník volání** okna, klikněte pravým tlačítkem na funkci, jejíž zpětně přeložený kód chcete zobrazit a vybrat **přejít na zpětný překlad**.

## <a name="change-the-optional-information-displayed"></a>Změna zobrazených volitelných informací

- Klikněte pravým tlačítkem **zásobník volání** okna a nastavení nebo vymazat **zobrazit \<**  _informace, které mají_ **>** .

## <a name="bkmk_symbols"></a> Načtení symbolů pro modul (C#, C++, Visual Basic, F#)

V **zásobník volání** okno, které můžete načíst symboly ladění pro kód, který nemá aktuálně načtené symboly. Tyto symboly mohou být v rozhraní .NET Framework nebo systémové symboly stažené ze serverů Microsoft veřejnými symboly nebo symboly v symbolické cestě v počítači, který ladíte.

Zobrazit [zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Načtení symbolů

1. V **zásobník volání** okna, klikněte pravým tlačítkem na rámce zásobníku pro symboly, které nejsou načtené. Snímek bude nepřístupný.

2. Přejděte na **načíst symboly** a pak vyberte **Microsoft Symbol Servers** (Pokud je k dispozici), nebo vyhledejte cestu k symbolu.

### <a name="to-set-the-symbol-path"></a>Chcete-li nastavit cestu k symbolu

1. V **zásobník volání** okně zvolte **nastavení symbolu** z místní nabídky.

     **Možnosti** zobrazí se dialogové okno a **symboly** zobrazí se stránka.

2. Vyberte **Symbol nastavení**.

3. V **možnosti** dialogovém okně klikněte na ikonu složky.

     V **Symbol umístění souborů (.pdb)** pole, se zobrazí kurzor.

4. Zadejte cestu adresáře do umístění symbolu v počítači, který ladíte. Pro místní a vzdálené ladění, je cesta k místnímu počítači.

5. Vyberte **OK** zavřete **možnosti** dialogové okno.

## <a name="see-also"></a>Viz také:

- [Smíšený kód a chybějící informace v okně Zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Použití zarážek](../debugger/using-breakpoints.md)