---
title: Příkaz aliasy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0caaea4b3bdb8c3b1018006f2943e49ac545744d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052507"
---
# <a name="visual-studio-command-aliases"></a>Aliasy příkazů sady Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]


Aliasy umožňují pro zadání příkazu do **najít/příkaz** pole nebo **příkaz** okno zkrácením text potřebné ke spuštění příkazu. Například místo zadávání `>File.OpenFile` zobrazíte **otevřít soubor** dialogové okno, můžete použít předdefinované alias `>of`.

 Typ `alias` v **příkaz** okno zobrazí seznam aktuálních aliasů a jejich definice. Typ `>cls` vymazat obsah **příkaz** okna. Pokud chcete zobrazit jako alias pro ke konkrétnímu příkazu, zadejte `alias <command name>`.

 Můžete snadno vytvořit vlastní alias pro jeden z příkazů sady Visual Studio (s nebo bez argumentů). Příklad syntaxe pro aliasy `File.NewFile MyFile.txt` je `alias MyAlias File.NewFile MyFile.txt`. Můžete odstranit jeden z vašich aliasů `alias <alias name> /delete`

 Následující tabulka obsahuje seznam předdefinované aliasy příkazů sady Visual Studio. Některé názvy příkazů mít více než jeden předem definovaný alias. Kliknutím na odkazy níže zobrazíte podrobné témata, která popisují správnou syntaxi, argumentů a přepínačů pro tyto příkazy názvy příkazů.

|Název příkazu|Alias|Úplný název|
|------------------|-----------|-------------------|
|[Příkaz Tisk](../../ide/reference/print-command.md)|?|Debug.Print –|
|[Příkaz Rychlé kukátko](../../ide/reference/quick-watch-command.md)|??|Debug.QuickWatch –|
|Přidat nový projekt|AddProj|File.AddNewProject|
|[Příkaz Alias](../../ide/reference/alias-command.md)|Alias|Tools.alias –|
|Automatické hodnoty – okno|Automatické hodnoty|Debug.Autos|
|Zarážky – okno|BL|Debug.Breakpoints|
|Přepnout zarážku|doporučených postupů|Debug.togglebreakpoint –|
|okno Zásobník volání|Zásobník volání|Debug.CallStack|
|Vymazat záložky|ClearBook|Edit.ClearBookmarks|
|Zavřít|Zavřít|File.Close|
|Zavřete všechny dokumenty|CloseAll|Window.CloseAllDocuments|
|Vymazat vše|specifikace CLS|Edit.ClearAll|
|Režim příkazů|cmd|View.CommandWindow|
|Zobrazit kód|kód|View.ViewCode|
|[Příkaz Listovat paměť](../../ide/reference/list-memory-command.md)|d|Debug.listmemory –|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) standardu ANSI|da|Debug.listmemory – /Ansi|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) formátu jeden bajt|DB|Debug.listmemory – /Format:OneByte|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) jako ANSI s formátem 4 bajty|řadič domény|Debug.listmemory – /Format:FourBytes /Ansi|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) formát 4 bajty|dd|Debug.listmemory – /Format:FourBytes|
|Vymazat do začátku řádku|DelBOL|Edit.DeleteToBOL|
|Vymazat do konce řádku|DelEOL|Edit.DeleteToEOL|
|Odstranit vodorovné prázdné znaky|DelHSp|Edit.DeleteHorizontalWhitespace|
|Návrhář zobrazení|návrhář|View.ViewDesigner|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) formátu s plovoucí desetinnou čárkou|DF|Debug.ListMemory/Format:Float|
|okno Zpětný překlad|disasm|Debug.Disassembly|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) formátu osm bajtů|dq|Debug.listmemory – /Format:EightBytes|
|[Výpis paměti příkaz](../../ide/reference/list-memory-command.md) jako Unicode|rozlišované sjednocení typu|Debug.listmemory – Unicode|
|[Příkaz Ohodnotit příkaz](../../ide/reference/evaluate-statement-command.md)|(V angličtině)|Debug.evaluatestatement –|
|Ukončit|Ukončit|File.Exit|
|Výběr formátu|formát|Edit.FormatSelection|
|Zobrazení na celé obrazovce|Celá obrazovka|View.FullScreen|
|[Příkaz Spustit](../../ide/reference/start-command.md)|G|Debug.Start|
|[Příkaz Přejít na](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Jít na závorku|GotoBrace|Edit.GotoBrace|
|F1Help|Nápověda|Help.F1Help|
|Přímý režim|ihned|Tools.ImmediateMode|
|Vložit soubor jako Text|InsertFile|Edit.InsertFileAsText|
|[Příkaz Listovat zásobník volání](../../ide/reference/list-call-stack-command.md)|znalostní báze|Debug.listcallstack –|
|Převést na malá písmena|LCase|Edit.MakeLowercase|
|Vyjmout řádek|LineCut|Edit.LineCut|
|Odstranit řádek|LineDel|Edit.LineDelete|
|Vypsat členy|Vypisovat členy|Edit.ListMembers|
|Místní hodnoty – okno|Místní hodnoty|Debug.Locals|
|[Příkaz Okno výstupu příkazů protokolu](../../ide/reference/log-command-window-output-command.md)|protokol|Tools.LogCommandWindowOutput|
|Režim označení příkazového okna|Označit|Tools.CommandWindowMarkMode|
|Paměť – okno|Memory1 paměti|Debug.Memory1|
|Paměť – okno 2|Memory2|Debug.Memory2|
|Paměť – okno 3|Memory3|Debug.Memory3|
|Paměť – okno 4|Paměť4|Debug.Memory4|
|[Příkaz Nastavit základ](../../ide/reference/set-radix-command.md)|n|Debug.setradix –|
|[Příkaz ShowWebBrowser (Zobrazit webový prohlížeč)](../../ide/reference/showwebbrowser-command.md)|přejděte NAV|View.showwebbrowser –|
|Další záložku|NextBook|Edit.NextBookmark|
|[Příkaz Nový soubor](../../ide/reference/new-file-command.md)|NF|File.NewFile|
|Nový projekt|NP NewProj|File.NewProject|
|[Příkaz Otevřít soubor](../../ide/reference/open-file-command.md)|z Open|File.OpenFile|
|[Příkaz Otevřít projekt](../../ide/reference/open-project-command.md)|OP|File.OpenProject|
|Sbalit do definic/Stop osnovy|OutlineDefs StopOutlining|Edit.CollapsetoDefinitions|
|Krok přes|p|Debug.StepOver|
|Informace o parametrech|ParamInfo|Edit.ParameterInfo|
|Krokovat s Vystoupením|žádost o přijetí změn|Debug.StepOut|
|Předchozí záložka|PrevBook|Edit.PreviousBookmark|
|Tisk souboru|Tisk|File.Print|
|Okno vlastností|Vlastnosti|View.PropertiesWindow|
|Zastavit|q|Debug.StopDebugging|
|Znovu:|Znovu:|Edit.Redo|
|Registr – okno|registr|Debug.Registers|
|Spustit ke kurzoru|RTC|Debug.RunToCursor|
|Uložit vybrané položky|Uložit|File.SaveSelectedItems|
|Uložit vše|SaveAll|File.SaveAll|
|Uložit jako|Uložit jako|File.SaveSelectedItemsAs|
|[Příkaz Prostředí](../../ide/reference/shell-command.md)|prostředí|Tools.Shell –|
|Zastavit hledání v souborech|StopFind|Edit.findinfiles – / stop|
|Označit zaměnit kotvu|SwapAnchor|Edit.SwapAnchor|
|Krokovat s vnořením|t|Debug.StepInto|
|Výběr převést na tabulátory|převedení na tabulátory|Edit.TabifySelection|
|Okno seznamu úkolů|Seznamu úkolů|View.TaskList|
|Vlákna – okno|Vlákna|Debug.Threads|
|Vodorovně nad sebe|TileH|Window.TileHorizontally|
|Svisle vedle sebe|TileV|Window.TileVertically|
|Přepnout záložku|ToggleBook|Edit.ToggleBookmark|
|Okno nástrojů|sada nástrojů|View.Toolbox|
|[Příkaz Zobrazit zpětný překlad](../../ide/reference/list-disassembly-command.md)|u|Debug.listdisassembly –|
|Převést na velká písmena|UCase|Edit.MakeUppercase|
|Vrácení zpět|Vrácení zpět|Edit.Undo|
|Zrušit tabulátory výběru|Zrušit tabulátory|Edit.UntabifySelection|
|Kukátko – okno|Sledování|Debug.WatchN|
|Změnit zalamování řádků|WordWrap|Edit.ToggleWordWrap|
|Listovat procesy|&#124;|Debug.ListProcesses|
|[Příkaz Listovat vlákna](../../ide/reference/list-threads-command.md)|~ ~ * k ~\*kb|Debug.listthreads – Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Viz také
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md) [Zové okno](../../ide/reference/command-window.md) [pole najít/příkaz](../../ide/find-command-box.md)
