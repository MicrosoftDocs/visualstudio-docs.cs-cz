---
title: Zobrazit zásobník volání v ladicím programu | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa91807459ea5c2d8f576891d0eafc35336347bc
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348740"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Zobrazení zásobníku volání a použití okna zásobník volání v ladicím programu

Pomocí okna **zásobník volání** můžete zobrazit volání funkce nebo procedury, které jsou aktuálně v zásobníku. Okno **zásobník volání** zobrazuje pořadí, ve kterém jsou metody a funkce volány. Zásobník volání je dobrým způsobem, jak prostudovat a pochopit tok spuštění aplikace.

Pokud nejsou [symboly ladění](#bkmk_symbols) k dispozici pro část zásobníku volání, okno **zásobník volání** nemusí být schopno zobrazit správné informace pro danou část zásobníku volání, zobrazení:

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> Okno **zásobník volání** je podobné perspektivě ladění v některých prostředích, jako je například zatmění.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **Nastavení importu a exportu** v nabídce **nástroje** .  Viz [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Zobrazit zásobník volání během ladicího programu

- Při ladění vyberte v nabídce **ladění** možnost **zásobník volání Windows >**.

  ![Okno zásobníku volání](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Žlutá šipka identifikuje rámec zásobníku, kde se aktuálně nachází ukazatel provádění. Ve výchozím nastavení se tyto informace rámce zásobníku zobrazí v oknech zdroj, **místní**hodnoty, **Automatické**hodnoty, **kukátko**a **zpětný překlad** . Chcete-li změnit kontext ladicího programu na jiný rámec v zásobníku, [přepněte na jiný rámec zásobníku](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Zobrazit neuživatelský kód v okně zásobník volání

- Klikněte pravým tlačítkem myši na okno **zásobník volání** a vyberte možnost **Zobrazit externí kód**.

Neuživatelský kód je jakýkoli kód, který není zobrazen, je-li povoleno [pouze můj kód](../debugger/just-my-code.md) . Ve spravovaném kódu jsou ve výchozím nastavení skryté i rámečky bez uživatelského kódu. Místo rámců neuživatelských kódů se zobrazí následující notace:

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a>Přepnout na jiný rámec zásobníku (změnit kontext ladicího programu)

1. V okně **zásobník volání** klikněte pravým tlačítkem myši na rámec zásobníku, jehož kód a data chcete zobrazit.

    Nebo můžete dvakrát kliknout na rámec v okně **zásobník volání** a přepnout na tento snímek.

2. Vyberte **přepínač přepnout na rámec**.

     Zelená šipka se složenou zakončení se zobrazí vedle rámce zásobníku, který jste vybrali. Ukazatel spuštění zůstane v původním snímku, který je stále označený žlutou šipkou. Pokud vyberete **Krok** nebo **pokračovat** z nabídky **ladění** , bude spuštění pokračovat v původním snímku, nikoli v rámci vybraného rámce.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Zobrazení zdrojového kódu funkce v zásobníku volání

- V okně **zásobník volání** klikněte pravým tlačítkem myši na funkci, jejíž zdrojový kód chcete zobrazit, a vyberte **Přejít ke zdrojovému kódu**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Spuštění konkrétní funkce z okna zásobník volání

- V okně **zásobník volání** vyberte funkci, klikněte pravým tlačítkem myši a pak zvolte možnost **Spustit ke kurzoru**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Nastavení zarážky v bodu ukončení volání funkce

- Viz [Nastavení zarážky ve funkci zásobníku volání](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Zobrazení volání do nebo z jiného vlákna

- Klikněte pravým tlačítkem myši na okno **zásobník volání** a vyberte možnost **Zahrnout volání do/z jiných vláken**.

## <a name="visually-trace-the-call-stack"></a>Vizuální trasování zásobníku volání

V Visual Studio Enterprise (pouze) můžete zobrazit mapy kódu pro zásobník volání během ladění.

- V okně **zásobník volání** otevřete místní nabídku. Vyberte možnost **Zobrazit zásobník volání na mapě kódu** (**CTRL**  +  **SHIFT**  +  **`** ).

    Další informace naleznete v tématu [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Zobrazit zásobník volání na mapě kódu](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Zobrazení kódu zpětného překladu pro funkci v zásobníku volání (C#, C++, Visual Basic, F #)

- V okně **zásobník volání** klikněte pravým tlačítkem myši na funkci, jejíž kód zpětného překladu chcete zobrazit, a vyberte možnost **Přejít na zpětný překlad**.

## <a name="change-the-optional-information-displayed"></a>Změna zobrazených volitelných informací

- V okně **zásobník volání** klikněte pravým tlačítkem myši a nastavte nebo zrušte zaškrtnutí **Zobrazit \<**_the information that you want_**> **.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a>Načtení symbolů pro modul (C#, C++, Visual Basic, F #)

V okně **zásobník volání** můžete načíst symboly ladění pro kód, který aktuálně nemá načteny symboly. Tyto symboly mohou být rozhraní .NET nebo systémové symboly stažené ze serverů veřejných symbolů společnosti Microsoft nebo symboly v cestě symbolů v počítači, který ladíte.

Viz [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Načtení symbolů

1. V okně **zásobník volání** klikněte pravým tlačítkem myši na rámec zásobníku, pro který nejsou načteny symboly. Rámec bude ztlumený.

2. Přejděte na **načíst symboly** a potom vyberte **Microsoft Symbol Servers** (Pokud je k dispozici) nebo přejděte na cestu k symbolu.

### <a name="to-set-the-symbol-path"></a>Nastavení cesty k symbolu

1. V okně **zásobník volání** vyberte v místní nabídce možnost **Nastavení symbolu** .

     Otevře se dialogové okno **Možnosti** a zobrazí se stránka **symboly** .

2. Vyberte **Nastavení symbolu**.

3. V dialogovém okně **Možnosti** klikněte na ikonu složky.

     V poli **umístění souborů symbolů (. pdb)** se zobrazí kurzor.

4. Zadejte cestu k adresáři do umístění symbolu v počítači, který ladíte. Pro místní a vzdálené ladění se jedná o cestu na místním počítači.

5. Kliknutím na **tlačítko OK** zavřete dialogové okno **Možnosti** .

## <a name="see-also"></a>Viz také

- [Smíšený kód a chybějící informace v okně zásobník volání](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Použití zarážek](../debugger/using-breakpoints.md)