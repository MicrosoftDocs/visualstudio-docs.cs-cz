---
title: Příkaz aliasy
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
ms.openlocfilehash: b420644672309371ab61f1499e22d4745c69c569
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596408"
---
# <a name="visual-studio-command-aliases"></a>Aliasy příkazů sady Visual Studio

Aliasy příkazů umožňují při spuštění příkazu psát méně znaků. Aliasy zadáte do pole **Najít/Příkaz** nebo Do okna **Příkaz.** Například místo zadání `>File.OpenFile` pro zobrazení dialogového okna **Otevřít soubor** můžete `>of`použít předdefinovaný alias .

`alias` Zadáním **Command** příkazového okna zobrazíte seznam aktuálních aliasů a jejich definic. Chcete-li vymazat obsah okna `>cls` **Příkaz,** zadejte text. Pokud chcete zobrazit alias pro určitý příkaz, zadejte `alias <command name>`.

Můžete snadno vytvořit vlastní alias pro jeden z příkazů sady Visual Studio (s argumenty nebo bez nich). Syntaxe pro aliasování `File.NewFile MyFile.txt` je `alias MyAlias File.NewFile MyFile.txt`například . Jeden ze svých aliasů můžete odstranit pomocí`alias <alias name> /delete`

Níže uvedená tabulka obsahuje seznam předdefinovaných aliasů příkazů sady Visual Studio. Některé názvy příkazů mají více než jeden předdefinovaný alias. Klepnutím na odkazy pro níže uvedené názvy příkazů zobrazíte podrobná témata, která vysvětlují správnou syntaxi, argumenty a přepínače pro tyto příkazy.

|Název příkazu|Alias|Úplný název|
|------------------|-----------|-------------------|
|[Tisk – příkaz](../../ide/reference/print-command.md)|?|Ladění.Tisk|
|[Rychlé kukátko – příkaz](../../ide/reference/quick-watch-command.md)|??|Ladění.Quickwatch|
|Přidat nový projekt|PřidatProj|Soubor.AddNewProject|
|[Příkaz Alias](../../ide/reference/alias-command.md)|Alias|Nástroje.Alias|
|Automatické hodnoty – okno|Auta|Debug.Autos|
|Zarážky – okno|Bl|Debug.Breakpoints|
|Přepnout zarážku|Bp|Debug.ToggleBreakPoint|
|okno Zásobník volání|Zásobník volání|Debug.CallStack|
|Vymazat záložky|ClearBook|Edit.ClearBookmarks|
|Zavřít|Zavřít|Soubor.Zavřít|
|Zavřít všechny dokumenty|Zavřít vše|Window.CloseAllDocuments|
|Vymazat vše|Cls|Upravit.ClearAll|
|Příkazový režim|Cmd|View.CommandWindow|
|Zobrazit kód|kód|View.ViewCode|
|[Listovat paměť – příkaz](../../ide/reference/list-memory-command.md)|d|Ladění.ListMemory|
|[Příkaz Paměti seznamu](../../ide/reference/list-memory-command.md) jako ANSI|Da|Ladění.ListMemory /Ansi|
|[Příkaz Paměť seznamu](../../ide/reference/list-memory-command.md) Jednobajtový formát|Db|Ladění.ListMemory /Formát:OneByte|
|[Příkaz Paměti seznamu](../../ide/reference/list-memory-command.md) jako ANSI s čtyřbajtovým formátem|Dc|Ladění.ListMemory /Formát:FourBytes /Ansi|
|[Příkaz Paměť seznamu](../../ide/reference/list-memory-command.md) Čtyřbajtový formát|dd|Debug.ListMemory /Format:FourBytes|
|Odstranit do BOL|DelBOL|Edit.DeleteToBOL|
|Odstranit do EOL|DelEOL|Edit.DeleteToEOL|
|Odstranit vodorovné prázdné znaky|DelHSp|Upravit.OdstranitHorizontálníPrázdné plochy|
|Návrhář zobrazení|návrhář|View.ViewDesigner|
|[Příkaz Paměť seznamu](../../ide/reference/list-memory-command.md) Plovoucí formát|Df|Ladění.ListMemory/Formát:Float|
|okno Zpětný překlad|disismus|Debug.Disassembly|
|[Příkaz Paměť seznamu](../../ide/reference/list-memory-command.md) Osmibajtový formát|Dq|Debug.ListMemory /Format:Osm bajtů|
|[Příkaz Paměti seznamu](../../ide/reference/list-memory-command.md) jako Unicode|Du|Ladění.ListMemory /Unicode|
|[Příkaz Vyhodnotit příkaz](../../ide/reference/evaluate-statement-command.md)|Eval|Příkaz Debug.EvaluateStatement|
|Ukončit|Ukončit|File.Exit|
|Příkaz Formátovat výběr|formát|Edit.FormatSelection|
|Celá obrazovka|Fullscreen|View.FullScreen|
|[Spustit – příkaz](../../ide/reference/start-command.md)|g|Debug.Start|
|[Přejít na – příkaz](../../ide/reference/go-to-command.md)|Přejít na|Edit.GoTo|
|Přejít na Ortézu|GotoBrace|Edit.GotoBrace|
|F1Nápověda|Nápověda|Help.F1Help|
|Okamžitý režim|immed|Tools.ImmediateMode|
|Vložit soubor jako text|Vložit soubor|Upravit.InsertfileAsText|
|[Listovat zásobník volání – příkaz](../../ide/reference/list-call-stack-command.md)|Kb|Ladění.ListCallStack|
|Vytvořit malá písmena|Lcase|Edit.MakeLowercase|
|Čára řezu|LineCut|Edit.LineCut|
|Odstranit řádek|LineDel|Edit.LineDelete|
|Vypsat členy|Seznam členů|Edit.ListMembers|
|Místní hodnoty – okno|Místní obyvatelé|Debug.Locals|
|[Protokolovat výstup příkazového okna – příkaz](../../ide/reference/log-command-window-output-command.md)|Protokol|Tools.LogCommandWindowOutput|
|Režim označení příkazového okna|Označit|Tools.CommandWindowMarkMode|
|Paměť – okno|Paměť ová1|Debug.Memory1|
|Okno paměti 2|Paměť2|Debug.Memory2|
|Okno paměti 3|Paměť3|Debug.Memory3|
|Okno paměti 4|Paměť4|Debug.Memory4|
|[Nastavit základ – příkaz](../../ide/reference/set-radix-command.md)|n|Ladění.SetRadix|
|[ShowWebBrowser – příkaz](../../ide/reference/showwebbrowser-command.md)|navigace na navigovat|View.ShowWebBrowser|
|Další záložka|NextBook|Edit.NextBookmark|
|[Nový soubor – příkaz](../../ide/reference/new-file-command.md)|Nf|File.NewFile|
|Nový projekt|np NewProj|File.NewProject|
|[Otevřít soubor – příkaz](../../ide/reference/open-file-command.md)|z otevřeného|File.OpenFile|
|[Otevřít projekt – příkaz](../../ide/reference/open-project-command.md)|Op|File.OpenProject|
|Sbalit na definice/Zastavit osnovu|Zastavování osnovy|Edit.CollapseToDefinitions|
|Krok přes|p|Debug.StepOver|
|Informace o parametrech|ParamInfo|Edit.ParameterInfo|
|Krok ven|Pr|Debug.StepOut|
|Předchozí záložka|PrevBook|Edit.PreviousBookmark|
|Tisk souboru|Tisk|File.Print|
|Okno vlastností|Rekvizity|View.PropertiesWindow|
|Zastavit|q|Debug.StopDebugging|
|Opakovat|Znovu|Edit.Redo|
|Registr – okno|registr|Debug.Registers|
|Spustit na kurzor|Rtc|Debug.RunToCursor|
|Uložit vybrané položky|save|File.SaveSelectedItems|
|Uložit vše|Uložit vše|File.SaveAll|
|Uložit jako|Saveas|Soubor.Uložitvybrané položky|
|[Prostředí – příkaz](../../ide/reference/shell-command.md)|prostředí|Nástroje.Prostředí|
|Zastavit hledání v souborech|StopNajít|Edit.FindInFiles /stop|
|Zaměnit kotvu|Swapanchor|Edit.SwapAnchor|
|Krok do|t|Debug.StepInto|
|Výběr tabifikuje|převedení na tabulátory|Upravit.TabifyVýběr|
|Okno Seznam úkolů|Tasklist|View.TaskList|
|Vlákna – okno|Vlákna|Debug.Threads|
|Dlaždice vodorovně|Dlaždice|Window.TileVodorovně|
|Dlaždice svisle|DlaždiceV|Window.TileSvisle|
|Přepnout záložku|Přepnout knihu|Edit.ToggleBookmark|
|Okno panelu nástrojů|sada nástrojů|View.Toolbox|
|[Zobrazit zpětný překlad – příkaz](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisisassembly|
|Vytvořit velká písmena|Ucase|Edit.MakeUppercase|
|Zpět|Zpět|Edit.Undo|
|Zrušit výběr|Zrušit katabifikace|Upravit.UntabifyVýběr|
|Kukátko – okno|Watch|Ladění.WatchN|
|Přepnout zalamování řádků|WordWrap|Edit.ToggleWordWrap|
|Seznam procesů|&#124;|Ladění.ListProcesy|
|[Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)|~ ~*k\*~ kb|Ladění.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
