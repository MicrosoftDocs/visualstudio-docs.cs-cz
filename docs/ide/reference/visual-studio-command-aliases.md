---
title: Aliasy příkazů
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f56161e1fd89ce29924368b6029ee12c17e75a65
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747705"
---
# <a name="visual-studio-command-aliases"></a>Aliasy příkazů sady Visual Studio

Aliasy příkazů umožňují zadat méně znaků, pokud chcete spustit příkaz. Aliasy zadáte do pole **Najít/příkaz** nebo **příkazového** řádku. Například namísto zadání `>File.OpenFile` pro zobrazení dialogového okna **otevřít soubor** můžete použít předdefinovaný `>of` alias.

Do **příkazového** řádku zadejte `alias`, aby se zobrazil seznam aktuálních aliasů a jejich definice. Zadejte `>cls` pro vymazání obsahu okna **příkazového** řádku. Pokud chcete zobrazit alias pro určitý příkaz, zadejte `alias <command name>`.

Můžete snadno vytvořit vlastní alias pro jeden z příkazů sady Visual Studio (s argumenty nebo bez). Například syntaxe pro aliasing `File.NewFile MyFile.txt` je `alias MyAlias File.NewFile MyFile.txt`. Jeden z vašich aliasů můžete odstranit pomocí `alias <alias name> /delete`

Následující tabulka obsahuje seznam předem definovaných aliasů příkazů sady Visual Studio. Některé názvy příkazů mají více než jeden předem definovaný alias. Kliknutím na odkazy níže uvedených názvů příkazů zobrazíte podrobná témata, která vysvětlují správnou syntaxi, argumenty a přepínače pro tyto příkazy.

|Název příkazu|Alias|Úplný název|
|------------------|-----------|-------------------|
|[Příkaz Tisk](../../ide/reference/print-command.md)|?|Ladit. tisk|
|[Příkaz Rychlé kukátko](../../ide/reference/quick-watch-command.md)|??|Debug. QuickWatch|
|Přidat nový projekt|AddProj|Soubor. AddNewProject|
|[Příkaz Alias](../../ide/reference/alias-command.md)|Alias|Tools. alias|
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
|[Příkaz Listovat paměť](../../ide/reference/list-memory-command.md)|d|Debug. ListMemory –|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako ANSI|&|Ladit. ListMemory –/ANSI|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát s jedním bytem|inženýr|Debug. ListMemory –/Format: OneByte|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako ANSI se formátem na 4 bajty|DC|Debug. ListMemory –/Format: FourBytes/ANSI|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát se čtyřmi bajty|DD|Debug. ListMemory –/Format: FourBytes|
|Odstranit do knihách online|DelBOL|Upravit. DeleteToBOL|
|Odstranit do konce řádku|DelEOL|Upravit. DeleteToEOL|
|Odstranit horizontální prázdné znaky|DelHSp|Upravit. DeleteHorizontalWhitespace|
|Návrhář zobrazení|návrhář|View.ViewDesigner|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát float|příznak|Debug. ListMemory –/Format: float|
|okno Zpětný překlad|DISASM|Debug.Disassembly|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát 8 bajtů|DQ|Debug. ListMemory –/Format: EightBytes|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako Unicode|du|Ladit. ListMemory –/Unicode|
|[Příkaz Ohodnotit příkaz](../../ide/reference/evaluate-statement-command.md)|platnost|Debug. EvaluateStatement|
|Ukončit|Ukončit|File.Exit|
|Příkaz Formátovat výběr|formát|Edit.FormatSelection|
|Celá obrazovka|Celoobrazovkového|View.FullScreen|
|[Příkaz Spustit](../../ide/reference/start-command.md)|Věcn|Debug.Start|
|[Příkaz Přejít na](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Přejít na složenou závorku|GotoBrace|Edit.GotoBrace|
|F1Help|Nápověda|Help.F1Help|
|Přímý režim|immed|Tools. ImmediateMode|
|Vložit soubor jako text|InsertFile|Upravit. InsertFileAsText|
|[Příkaz Listovat zásobník volání](../../ide/reference/list-call-stack-command.md)|Knowledge|Debug. ListCallStack|
|Převést na malá písmena|LCase|Edit.MakeLowercase|
|Vyjmout řádek|LineCut|Edit.LineCut|
|Odstranit řádek|LineDel|Edit.LineDelete|
|Vypsat členy|ListMembers|Edit.ListMembers|
|Místní hodnoty – okno|Místní hodnoty|Debug.Locals|
|[Příkaz Okno výstupu příkazů protokolu](../../ide/reference/log-command-window-output-command.md)|protokolu|Tools. LogCommandWindowOutput|
|Režim značek příkazového okna|lomítk|Tools. CommandWindowMarkMode|
|Paměť – okno|Memory1 paměti|Debug.Memory1|
|Okno paměti 2|Memory2|Debug.Memory2|
|Okno paměti 3|Memory3|Debug.Memory3|
|Okno paměti 4|Memory4|Debug.Memory4|
|[Příkaz Nastavit základ](../../ide/reference/set-radix-command.md)|N|Debug. SetRadix|
|[Příkaz ShowWebBrowser (Zobrazit webový prohlížeč)](../../ide/reference/showwebbrowser-command.md)|navigace navigace|Zobrazit. ShowWebBrowser –|
|Další záložka|NextBook|Edit.NextBookmark|
|[Příkaz Nový soubor](../../ide/reference/new-file-command.md)|NF|File.NewFile|
|Nový projekt|NP NewProj|File.NewProject|
|[Příkaz Otevřít soubor](../../ide/reference/open-file-command.md)|Otevřené|File.OpenFile|
|[Příkaz Otevřít projekt](../../ide/reference/open-project-command.md)|evřít|File.OpenProject|
|Sbalit do definic/zastavit sbalení|OutlineDefs StopOutlining|Upravit. CollapseToDefinitions|
|Krokovat|Trub|Debug.StepOver|
|Informace o parametrech|ParamInfo|Edit.ParameterInfo|
|Krok ven|Pronájem|Debug.StepOut|
|Předchozí záložka|PrevBook|Edit.PreviousBookmark|
|Tisk souboru|Tisk|File.Print|
|Okno vlastností|props|View.PropertiesWindow|
|Zastavit|č|Debug.StopDebugging|
|Proveďte|Proveďte|Edit.Redo|
|Registr – okno|registr|Debug.Registers|
|Spustit ke kurzoru|RTC|Debug.RunToCursor|
|Uložit vybrané položky|uloží|File.SaveSelectedItems|
|Uložit vše|SaveAll|File.SaveAll|
|Uložit jako|Nám|Soubor. SaveSelectedItemsAs|
|[Příkaz Prostředí](../../ide/reference/shell-command.md)|prostředí|Nástroje. Shell|
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
|[Příkaz Zobrazit zpětný překlad](../../ide/reference/list-disassembly-command.md)|u|Debug. ListDisassembly|
|Převést na velká písmena|UCase|Edit.MakeUppercase|
|Vrátit zpět|Vrátit zpět|Edit.Undo|
|Zrušit tabulátory výběr|Zrušit tabulátory|Upravit. UntabifySelection|
|Kukátko – okno|Sledovací|Debug. WatchN|
|Přepnout zalamování řádků|WordWrap|Edit.ToggleWordWrap|
|Výpis procesů|&#124;|Debug. ListProcesses|
|[Příkaz Listovat vlákna](../../ide/reference/list-threads-command.md)|~ ~ * k ~ \*kb|Debug. Listthreads – Debug. ListTheads/AllThreads|

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)