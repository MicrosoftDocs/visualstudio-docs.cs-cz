---
title: Aliasy příkazů
description: Naučte se používat aliasy příkazů k psaní méně znaků, když chcete spustit příkaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9dda564939652a09b64fec65747ca14d1315b3f1
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561068"
---
# <a name="visual-studio-command-aliases"></a>Aliasy příkazů sady Visual Studio

Aliasy příkazů umožňují zadat méně znaků, pokud chcete spustit příkaz. Aliasy zadáte do pole **Najít/příkaz** nebo **příkazového** řádku. Například namísto zadání `>File.OpenFile` pro zobrazení dialogového okna **otevřít soubor** můžete použít předem definovaný alias `>of` .

`alias`Do **příkazového** řádku zadejte, aby se zobrazil seznam aktuálních aliasů a jejich definice. Zadejte `>cls` , chcete-li vymazat obsah okna **příkazového** řádku. Pokud chcete zobrazit alias pro určitý příkaz, zadejte `alias <command name>` .

Můžete snadno vytvořit vlastní alias pro jeden z příkazů sady Visual Studio (s argumenty nebo bez). Například syntaxe pro aliasing `File.NewFile MyFile.txt` je `alias MyAlias File.NewFile MyFile.txt` . Jeden z vašich aliasů můžete odstranit pomocí `alias <alias name> /delete`

Následující tabulka obsahuje seznam předem definovaných aliasů příkazů sady Visual Studio. Některé názvy příkazů mají více než jeden předem definovaný alias. Kliknutím na odkazy níže uvedených názvů příkazů zobrazíte podrobná témata, která vysvětlují správnou syntaxi, argumenty a přepínače pro tyto příkazy.

|Název příkazu|Alias|Úplný název|
|------------------|-----------|-------------------|
|[Tisk – příkaz](../../ide/reference/print-command.md)|?|Ladit. tisk|
|[Rychlé kukátko – příkaz](../../ide/reference/quick-watch-command.md)|??|Debug. QuickWatch|
|Přidat nový projekt|AddProj|Soubor. AddNewProject|
|[Alias – příkaz](../../ide/reference/alias-command.md)|Alias|Tools. alias|
|Automatické hodnoty – okno|Automatické hodnoty|Debug.Autos|
|Zarážky – okno|BL|Debug.Breakpoints|
|Přepnout zarážku|kontrol|Debug. Togglebreakpoint –|
|okno Zásobník volání|Zásobník volání|Debug.CallStack|
|Vymazat záložky|ClearBook|Edit.ClearBookmarks|
|Zavřít|Zavřít|Soubor. Zavřít|
|Zavřít všechny dokumenty|CloseAll|Window. CloseAllDocuments|
|Vymazat vše|specifikaci|Upravit. ClearAll|
|Režim příkazu|přepsat|View.CommandWindow|
|Zobrazit kód|kód|View.ViewCode|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md)|d|Debug. ListMemory –|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako ANSI|&|Ladit. ListMemory –/ANSI|
|Příkaz One-Byte Format pro [Výpis paměti](../../ide/reference/list-memory-command.md)|inženýr|Debug. ListMemory –/Format: OneByte|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako ANSI s formátem Four-Byte|DC|Debug. ListMemory –/Format: FourBytes/ANSI|
|Příkaz Four-Byte Format pro [Výpis paměti](../../ide/reference/list-memory-command.md)|dd|Debug. ListMemory –/Format: FourBytes|
|Odstranit do knihách online|DelBOL|Upravit. DeleteToBOL|
|Odstranit do konce řádku|DelEOL|Upravit. DeleteToEOL|
|Odstranit horizontální prázdné znaky|DelHSp|Upravit. DeleteHorizontalWhitespace|
|Návrhář zobrazení|návrhář|View.ViewDesigner|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát float|příznak|Debug. ListMemory –/Format: float|
|okno Zpětný překlad|DISASM|Debug.Disassembly|
|Příkaz Eight-Byte Format pro [Výpis paměti](../../ide/reference/list-memory-command.md)|DQ|Debug. ListMemory –/Format: EightBytes|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako Unicode|du|Ladit. ListMemory –/Unicode|
|[Evaluate – příkaz příkazu](../../ide/reference/evaluate-statement-command.md)|platnost|Debug. EvaluateStatement|
|Ukončit|Ukončit|File.Exit|
|Příkaz Formátovat výběr|formát|Edit.FormatSelection|
|Celá obrazovka|Celoobrazovkového|View.FullScreen|
|[Spustit příkaz](../../ide/reference/start-command.md)|g|Debug.Start|
|[Přejít na příkaz](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Přejít na složenou závorku|GotoBrace|Edit.GotoBrace|
|F1Help|Nápověda|Help.F1Help|
|Přímý režim|immed|Tools. ImmediateMode|
|Vložit soubor jako text|InsertFile|Upravit. InsertFileAsText|
|[Listovat zásobník volání – příkaz](../../ide/reference/list-call-stack-command.md)|Knowledge|Debug. ListCallStack|
|Převést na malá písmena|LCase|Edit.MakeLowercase|
|Vyjmout řádek|LineCut|Edit.LineCut|
|Odstranit řádek|LineDel|Edit.LineDelete|
|Vypsat členy|ListMembers|Edit.ListMembers|
|Místní hodnoty – okno|Místní hodnoty|Debug.Locals|
|[Příkaz pro výstup příkazového okna v protokolu](../../ide/reference/log-command-window-output-command.md)|Protokol|Tools. LogCommandWindowOutput|
|Režim značek příkazového okna|lomítk|Tools. CommandWindowMarkMode|
|Paměť – okno|Memory1 paměti|Debug.Memory1|
|Okno paměti 2|Memory2|Debug.Memory2|
|Okno paměti 3|Memory3|Debug.Memory3|
|Okno paměti 4|Memory4|Debug.Memory4|
|[Nastavit základ – příkaz](../../ide/reference/set-radix-command.md)|n|Debug. SetRadix|
|[ShowWebBrowser – – příkaz](../../ide/reference/showwebbrowser-command.md)|navigace navigace|Zobrazit. ShowWebBrowser –|
|Další záložka|NextBook|Edit.NextBookmark|
|[Nový soubor – příkaz](../../ide/reference/new-file-command.md)|NF|File.NewFile|
|Nový projekt|NP NewProj|File.NewProject|
|[Otevřít soubor – příkaz](../../ide/reference/open-file-command.md)|Otevřené|File.OpenFile|
|[Otevřít projekt – příkaz](../../ide/reference/open-project-command.md)|evřít|File.OpenProject|
|Sbalit do definic/zastavit sbalení|OutlineDefs StopOutlining|Upravit. CollapseToDefinitions|
|Krokovat|p|Debug.StepOver|
|Informace o parametrech|ParamInfo|Edit.ParameterInfo|
|Krok ven|pr|Debug.StepOut|
|Předchozí záložka|PrevBook|Edit.PreviousBookmark|
|Tisk souboru|Tisk|File.Print|
|Okno vlastností|props|View.PropertiesWindow|
|Zastavit|q|Debug.StopDebugging|
|Opakovat|proveďte|Edit.Redo|
|Registr – okno|registr|Debug.Registers|
|Spustit ke kurzoru|RTC|Debug.RunToCursor|
|Uložit vybrané položky|save|File.SaveSelectedItems|
|Uložit vše|SaveAll|File.SaveAll|
|Uložit jako|Nám|Soubor. SaveSelectedItemsAs|
|[Příkaz Shell](../../ide/reference/shell-command.md)|prostředí|Nástroje. Shell|
|Zastavit hledání v souborech|StopFind|Edit. FindInFiles/stop|
|Prohodit kotvu|SwapAnchor|Edit.SwapAnchor|
|Krokovat s vnořením|t|Debug.StepInto|
|Převést na tabulátory výběr|převedení na tabulátory|Upravit. TabifySelection|
|Okno tasklist|TaskList|View.TaskList|
|Vlákna – okno|Vlákna|Debug.Threads|
|Vedle sebe vodorovně|TileH|Window. TileHorizontally|
|Svisle vedle sebe|TileV|Window. TileVertically|
|Přepnout záložku|ToggleBook|Edit.ToggleBookmark|
|Okno panelu nástrojů|sada nástrojů|View.Toolbox|
|[Výpis zpětného překladu příkazu](../../ide/reference/list-disassembly-command.md)|u|Debug. ListDisassembly|
|Převést na velká písmena|UCase|Edit.MakeUppercase|
|Zpět|vrátit zpět|Edit.Undo|
|Zrušit tabulátory výběr|Zrušit tabulátory|Upravit. UntabifySelection|
|Kukátko – okno|Watch|Debug. WatchN|
|Přepnout zalamování řádků|WordWrap|Edit.ToggleWordWrap|
|Výpis procesů|&#124;|Debug. ListProcesses|
|[Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)|~ ~ * k ~ \* KB|Debug. Listthreads – Debug. ListTheads/AllThreads|

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
