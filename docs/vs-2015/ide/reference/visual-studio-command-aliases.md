---
title: Aliasy příkazů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7e9419e64cd211490fc1d3785045b5de117d392e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657856"
---
# <a name="visual-studio-command-aliases"></a>Aliasy příkazů sady Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aliasy poskytují způsob, jak zadat příkaz do pole **Najít/příkaz** nebo **příkazové** okno zkrácením textu potřebného ke spuštění příkazu. Například namísto zadání `>File.OpenFile` pro zobrazení dialogového okna **otevřít soubor** můžete použít předem definovaný alias `>of` .

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
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát s jedním bytem|inženýr|Debug. ListMemory –/Format: OneByte|
|[Výpis paměti – příkaz](../../ide/reference/list-memory-command.md) jako ANSI se čtyřmi formáty Byte|DC|Debug. ListMemory –/Format: FourBytes/ANSI|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát formátu 4 bajty|dd|Debug. ListMemory –/Format: FourBytes|
|Odstranit do knihách online|DelBOL|Upravit. DeleteToBOL|
|Odstranit do konce řádku|DelEOL|Upravit. DeleteToEOL|
|Odstranit horizontální prázdné znaky|DelHSp|Upravit. DeleteHorizontalWhitespace|
|Návrhář zobrazení|návrhář|View.ViewDesigner|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát float|příznak|Debug. ListMemory –/Format: float|
|okno Zpětný překlad|DISASM|Debug.Disassembly|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md) Formát 8 bajtů|DQ|Debug. ListMemory –/Format: EightBytes|
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
|Sbalit do definic/zastavit sbalení|OutlineDefs StopOutlining|Edit.CollapsetoDefinitions|
|Krokovat|p|Debug.StepOver|
|Informace o parametrech|ParamInfo|Edit.ParameterInfo|
|Krok ven|Pronájem|Debug.StepOut|
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

## <a name="see-also"></a>Viz také
 [Příkazové okno](../../ide/reference/command-window.md) příkazů pro [hledání/příkaz](../../ide/find-command-box.md) v [aplikaci Visual Studio](../../ide/reference/visual-studio-commands.md)
