---
title: Výchozí klávesové zkratky
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
ms.assetid: c2c64648-00f8-4e48-a8a0-96c67cfd968c
caps.latest.revision: 59
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bfd13bda3e3d7ba416772123ac59ff0136a3725
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665826"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Výchozí klávesové zkratky v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výběrem příslušné klávesové zkratky máte v sadě Visual Studio snazší přístup k různým příkazům a oknům. V tomto tématu jsou uvedeny výchozí klávesové zkratky pro obecný vývojový profil, který jste možná vybrali při instalaci sady Visual Studio. Bez ohledu na to, který profil zvolíte, můžete zástupce příkazu identifikovat otevřením dialogového okna **Možnosti** , rozbalením uzlu **prostředí** a výběrem **klávesnice**. Klávesové zkratky můžete také upravit přiřazením různých zkratek jakémukoli příkazu.

 Seznam běžných klávesových zkratek a další informace o produktivitě najdete v tématu [tipy a triky](../ide/tips-and-tricks-for-visual-studio.md) [pro zvýšení produktivity](../ide/productivity-tips-for-visual-studio.md).

 Oddíly v následující tabulce obsahují příkazy, které jsou globální, takže jsou přístupné z libovolného místa v sadě Visual Studio pomocí klávesových zkratek:

|||||
|-|-|-|-|
|[Analyzovat](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)|[Úpravě](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)|[Projektem](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)|[Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)|
|[Architektura](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)|[Místní nabídky editoru](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)|[Kontextové nabídky projektu a řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)|[Průzkumník testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)|
|[Sestavení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)|[Souborů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)|[Refaktorovat](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)|[Nástroje](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)|
|[Zobrazení tříd kontextové nabídky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)|[Pomoc](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)|[Průzkumník řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)|[Zobrazení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)|
|[Ladí](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)|[Zátěžový test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)|[Hodnotící](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)|[Okno](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)|
|[Kontextové nabídky ladicího programu](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)|[Další kontextové nabídky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)|[Kontextové nabídky Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)|[Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)|
|[Centrum diagnostiky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)||||

 Každý oddíl v následující tabulce obsahuje příkazy, pro které jsou klávesové zkratky specifické v kontextu, pro který je oddíl uveden.

|||||
|-|-|-|-|
|[Návrhář model EDM (Entity Data Model) ADO.NET](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_ADONET)|[Diagram vrstev](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_layerDiagram)|[Návrhář nastavení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SettingsDesigner)|[Editor obrázků VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcimageeditor)|
|[Diagram tříd](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classDiagram)|[Editor spravovaných prostředků](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_managedResources)|[Průzkumník řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SolutionExplorer)|[Editor řetězců VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcstringeditor)|
|[Editor programového testu UI](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_codedUItest)|[Okno editoru sloučení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_MergeEditor)|[Team Explorer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TeamExplorer)|[Návrhář zobrazení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_viewDesigner)|
|[Editor DataSet](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_dataset)|[Nástroje pro Microsoft SQL Server data, porovnání schématu](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SchemaCompare)|[Editor podrobností sestavení Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFBuild)|[Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_visualstudio)|
|[Prohlížeč rozdílů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diff)|[Microsoft SQL Server Data Tools, Návrhář tabulky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TableDesigner)|[Průzkumník testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TestExplorer)|[Návrhář formulářů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_wfdesigner)|
|[Průzkumník modelu DOM](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_DOM)|[Nástroje pro Microsoft SQL Server dat, Editor T-SQL](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TSQLeditor)|[Textový editor](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TextEditor)|[Editor pracovních položek](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_workItemEditor)|
|[F# Interactive](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_FSharp)|[Nástroje pro Microsoft SQL Server dat, Editor T-SQL PDW](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_linkfix)|[Diagram činnosti UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLactivityDiagram)|[Zobrazení dotazu pracovní položky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_WIqueryview)|
|[Editor dokumentu grafu](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graphDoc)|[Inspektor stránky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_PageInspector)|[Diagram tříd UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLclassDiagram)|[Zobrazení výsledků pracovních položek](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_WIresultsview)|
|[Diagnostika grafiky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graphicsDebugger)|[Návrhář dotazů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_QueryDesigner)|[Diagram komponent UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLcomponentDiagram)|[Návrhář postupu provádění](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_workflowdesigner)|
|[Editor HTML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_HTMLeditor)|[Výsledky dotazu](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_QueryResults)|[Diagram případu použití UML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_UMLusecaseDiagram)|[Návrhář uživatelského rozhraní XAML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xamluidesigner)|
|[Zobrazení návrhu editoru HTML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_HTMLeditorDesign)|[Návrhář sestav](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_ReportDesigner)|[Editor akcelerátorů VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcaccelerator)|[Editor XML (textový)](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xmlTextEditor)|
|[Zobrazení zdroje editoru HTML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_HTMLeditorSource)|[Sekvenční diagram](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_SequenceDiagram)|[Editor dialogových oken VC](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vcdialogeditor)|[Návrhář schémat XML](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xmlSchemaDesigner)|

## <a name="bkmk_global"></a>Globální

### <a name="bkmk_analyze"></a>Analyzovat

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Analyze.NavigateBackward|Shift+Alt+3|
|Analyze.NavigateForward|Shift+Alt+4|

### <a name="bkmk_architecture"></a>Architektura

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Architecture.NewDiagram|CTRL + \\, CTRL + N|

### <a name="bkmk_build"></a>Budování

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Build.BuildSolution|Ctrl+Shift+B|
|Build.Cancel|Ctrl+Break|
|Build.Compile|Ctrl+F7|
|Build.RunCodeAnalysisonSolution|Alt+F11|

### <a name="bkmk_classview"></a>Zobrazení tříd kontextové nabídky

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties|Alt+Enter|

### <a name="bkmk_debug"></a>Ladí

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Debug.ApplyCodeChanges|Alt+F10|
|Debug.Autos|Ctrl+Alt+V, A|
|Debug.BreakAll|Ctrl+Alt+Break|
|Debug.BreakatFunction|Ctrl+B|
|Debug.Breakpoints|Ctrl+Alt+B|
|Debug.CallStack|Ctrl+Alt+C|
|Debug.DeleteAllBreakpoints|Ctrl+Shift+F9|
|Debug.DiagnosticsHub.Launch|Alt+F2|
|Debug.Disassembly|Ctrl+Alt+D|
|Debug.DOMExplorer|Ctrl+Alt+V, D|
|Debug.EnableBreakpoint|Ctrl+F9|
|Debug.Exceptions|Ctrl+Alt+E|
|Debug.GoToPreviousCallorIntelliTraceEvent|Ctrl+Shift+F11|
|Debug.Graphics.StartDiagnostics|Alt+F5|
|Debug.Immediate|Ctrl+Alt+I|
|Debug.IntelliTraceCalls|Ctrl+Alt+Y, T|
|Debug.IntelliTraceEvents|Ctrl+Alt+Y, F|
|Debug.JavaScriptConsole|Ctrl+Alt+V, C|
|Debug.Locals|Ctrl+Alt+V, L|
|Debug.LocationToolbar.ProcessCombo|Ctrl+5|
|Debug.LocationToolbar.StackFrameCombo|Ctrl+7|
|Debug.LocationToolbar.ThreadCombo|Ctrl+6|
|Debug.LocationToolbar.ToggleCurrentThreadFlaggedState|Ctrl+8|
|Debug.LocationToolbar.ToggleFlaggedThreads|Ctrl+9|
|Debug.Memory1|Ctrl+Alt+M, 1|
|Debug.Memory2|CTRL + ALT + M, 2|
|Debug.Memory3|CTRL + ALT + M, 3|
|Debug.Memory4|CTRL + ALT + M, 4|
|Debug.Modules|Ctrl+Alt+U|
|Debug.ParallelStacks|Ctrl+Shift+D, S|
|Debug.ParallelWatch1|Ctrl+Shift+D, 1|
|Debug.ParallelWatch2|CTRL + SHIFT + D, 2|
|Debug.ParallelWatch3|CTRL + SHIFT + D, 3|
|Debug.ParallelWatch4|CTRL + SHIFT + D, 4|
|Debug.Processes|Ctrl+Alt+Z|
|Debug.QuickWatch|Shift+F9<br /><br /> or<br /><br /> Ctrl+Alt+Q|
|Debug.RefreshWindowsapp|Ctrl+Shift+R|
|Debug.Registers|Ctrl+Alt+G|
|Debug.Restart|Ctrl+Shift+F5|
|Debug.RunToCursor|Ctrl+F10|
|Debug.SetNextStatement|Ctrl+Shift+F10|
|Debug.ShowCallStackonCodeMap|Ctrl+Shift+`|
|Debug.ShowNextStatement|Alt+Num *|
|Debug.Start|Stisknutím|
|Debug.StartWindowsPhoneApplicationAnalysis|Alt+F1|
|Debug.StartWithoutDebugging|Ctrl+F5|
|Debug.StepInto|Kláves|
|Debug.StepIntoCurrentProcess|Ctrl+Alt+F11|
|Debug.StepIntoSpecific|Shift+Alt+F11|
|Debug.StepOut|Shift+F11|
|Debug.StepOutCurrentProcess|Ctrl+Shift+Alt+F11|
|Debug.StepOver|F10|
|Debug.StepOverCurrentProcess|Ctrl+Alt+F10|
|Debug.StopDebugging|Shift+F5|
|Debug.StopPerformanceAnalysis|Shift+Alt+F2|
|Debug.Tasks|Ctrl+Shift+D, K|
|Debug.Threads|Ctrl+Alt+H|
|Debug.ToggleBreakpoint|Vede|
|Debug.ToggleDisassembly|Ctrl+F11|
|Debug.Watch1|Ctrl+Alt+W, 1|
|Debug.Watch2|CTRL + ALT + W, 2|
|Debug.Watch3|CTRL + ALT + W, 3|
|Debug.Watch4|CTRL + ALT + W, 4|

### <a name="bkmk_debugger"></a>Kontextové nabídky ladicího programu

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|DebuggerContextMenus.BreakpointsWindow.Delete|Alt+F9, D|
|DebuggerContextMenus.BreakpointsWindow.GoToDisassembly|Alt+F9, A|
|DebuggerContextMenus.BreakpointsWindow.GoToSourceCode|Alt+F9, S|

### <a name="bkmk_diagnostics"></a>Centrum diagnostiky

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|DiagnosticsHub.StopCollection|Ctrl+Alt+F2|

### <a name="bkmk_edit"></a>Úpravě

|Příkazy||
|--------------|-|
|Edit.Copy|Ctrl+C<br /><br /> or<br /><br /> Ctrl+Ins|
|Edit.Cut|Ctrl+X<br /><br /> or<br /><br /> Shift+Delete|
|Edit.CycleClipboardRing|Ctrl+Shift+V<br /><br /> or<br /><br /> Ctrl+Shift+Ins|
|Edit.Delete|Odstranit|
|Edit.Find|Ctrl+F|
|Edit.FindAllReferences|Shift+F12|
|Edit.FindinFiles|Ctrl+Shift+F|
|Edit.FindNext|F3|
|Edit.FindNextSelected|Ctrl+F3|
|Edit.FindPrevious|Shift+F3|
|Edit.FindPreviousSelected|Ctrl+Shift+F3|
|Edit.GenerateMethod|Ctrl+K, Ctrl+M|
|Edit.GoTo|Ctrl+G|
|Edit.GoToDeclaration|Ctrl+F12|
|Edit.GoToDefinition|Kláves|
|Edit.GoToFindCombo|Ctrl+D|
|Edit.GoToNextLocation|F8|
|Edit.GoToPrevLocation|Shift+F8|
|Edit.InsertSnippet|Ctrl+K, Ctrl+X|
|Edit.MoveControlDown|Ctrl + šipka dolů|
|Edit.MoveControlDownGrid|Šipka dolů|
|Edit.MoveControlLeft|Ctrl + šipka doleva|
|Edit.MoveControlLeftGrid|Šipka doleva|
|Edit.MoveControlRight|Ctrl + šipka doprava|
|Edit.MoveControlRightGrid|Šipka doprava|
|Edit.MoveControlUp|Ctrl + šipka nahoru|
|Edit.MoveControlUpGrid|Šipka nahoru|
|Edit.NavigateTo|Ctrl+,|
|Edit.NextBookmark|Ctrl+K, Ctrl+N|
|Edit.NextBookmarkInFolder|Ctrl+Shift+K, Ctrl+Shift+N|
|Edit.OpenFile|Ctrl+Shift+G|
|Edit.Paste|Ctrl+V<br /><br /> or<br /><br /> Shift+Ins|
|Edit.PreviousBookmark|Ctrl+K, Ctrl+P|
|Edit.PreviousBookmarkInFolder|Ctrl+Shift+K, Ctrl+Shift+P|
|Edit.QuickFindSymbol|Shift+Alt+F12|
|Edit.Redo|Ctrl+Y<br /><br /> or<br /><br /> Ctrl+Shift+Z<br /><br /> or<br /><br /> Shift+Alt+Backspace|
|Edit.RefreshRemoteReferences|Ctrl+Shift+J|
|Edit.Replace|Ctrl+H|
|Edit.ReplaceinFiles|Ctrl+Shift+H|
|Edit.SelectAll|Ctrl+A|
|Edit.SelectNextControl|Karta|
|Edit.SelectPreviousControl|Shift+Tab|
|Edit.ShowTileGrid|Enter|
|Edit.SizeControlDown|Ctrl + Shift + šipka dolů|
|Edit.SizeControlDownGrid|Shift + šipka dolů|
|Edit.SizeControlLeft|Ctrl + Shift + šipka doleva|
|Edit.SizeControlLeftGrid|Shift + šipka doleva|
|Edit.SizeControlRight|Ctrl + Shift + šipka doprava|
|Edit.SizeControlRightGrid|Shift + šipka doprava|
|Edit.SizeControlUp|Ctrl + Shift + šipka nahoru|
|Edit.SizeControlUpGrid|Shift + šipka nahoru|
|Edit.StopSearch|Alt+F3, S|
|Edit.SurroundWith|Ctrl+K, Ctrl+S|
|Edit.Undo|Ctrl+Z<br /><br /> or<br /><br /> Alt+Backspace|

### <a name="bkmk_editorContext"></a>Místní nabídky editoru

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels|Alt+F9, L|
|EditorContextMenus.CodeWindow.CodeMap.ShowItem|Ctrl+`|
|EditorContextMenus.CodeWindow.Execute|Ctrl+Alt+F5|
|EditorContextMenus.CodeWindow.GoToView|Ctrl+M, Ctrl+G|
|EditorContextMenus.CodeWindow.ToggleHeaderCodeFile|Ctrl+K, Ctrl+O|
|EditorContextMenus.CodeWindow.ViewCallHierarchy|Ctrl+K, Ctrl+T<br /><br /> or<br /><br /> Ctrl+K, T|

### <a name="bkmk_file"></a>Souborů

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|File.Exit|Alt+F4|
|File.NewFile|Ctrl+N|
|File.NewProject|Ctrl+Shift+N|
|File.NewWebSite|Shift+Alt+N|
|File.OpenFile|Ctrl+O|
|File.OpenProject|Ctrl+Shift+O|
|File.OpenWebSite|Shift+Alt+O|
|File.Print|Ctrl+P|
|File.SaveAll|Ctrl+Shift+S|
|File.SaveSelectedItems|Ctrl+S|
|File.ViewinBrowser|Ctrl+Shift+W|

### <a name="bkmk_help"></a>Pomoc

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Help.AddandRemoveHelpContent|Ctrl+Alt+F1|
|Help.F1Help|Kláves|
|Help.ViewHelp|Ctrl+F1|
|Help.WindowHelp|Shift+F1|

### <a name="bkmk_loadtest"></a>Zátěžový test

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|LoadTest.JumpToCounterPane|Ctrl+R, Q|

### <a name="bkmk_otherContext"></a>Další kontextové nabídky

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram|Insert|

### <a name="bkmk_project"></a> Projekt

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Project.AddExistingItem|Shift+Alt+A|
|Project.AddNewItem|Ctrl+Shift+A|
|Project.ClassWizard|Ctrl+Shift+X|
|Project.Override|Ctrl+Alt+Ins|
|Project.Previewchanges|Alt+;, Alt+C|
|Project.Publishselectedfiles|Alt+;, Alt+P|
|Project.Replaceselectedfilesfromserver|Alt+;, Alt+R|

### <a name="bkmk_projectContext"></a>Kontextové nabídky projektu a řešení

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|ProjectandSolutionContextMenus.Item.MoveDown|Alt + šipka dolů|
|ProjectandSolutionContextMenus.Item.MoveUp|Alt + šipka nahoru|

### <a name="bkmk_refactor"></a>Refaktorovat

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Refactor.EncapsulateField|Ctrl+R, Ctrl+E|
|Refactor.ExtractInterface|Ctrl+R, Ctrl+I|
|Refactor.ExtractMethod|Ctrl+R, Ctrl+M|
|Refactor.RemoveParameters|Ctrl+R, Ctrl+V|
|Refactor.Rename|Ctrl+R, Ctrl+R|
|Refactor.ReorderParameters|Ctrl+R, Ctrl+O|

### <a name="bkmk_solutionexplorerGLOBAL"></a>Průzkumník řešení

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|SolutionExplorer.OpenFilesFilter|Ctrl+[, O<br /><br /> or<br /><br /> Ctrl+[, Ctrl+O|
|SolutionExplorer.PendingChangesFilter|Ctrl+[, P<br /><br /> or<br /><br /> Ctrl+[, Ctrl+P|
|SolutionExplorer.SyncWithActiveDocument|Ctrl+[, S<br /><br /> or<br /><br /> Ctrl+[, Ctrl+S|

### <a name="bkmk_team"></a>Hodnotící

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Team.Git.GoToGitBranches|Ctrl+0, Ctrl+N<br /><br /> or<br /><br /> Ctrl+0, N|
|Team.Git.GoToGitChanges|Ctrl+0, Ctrl+G<br /><br /> or<br /><br /> Ctrl+0, G|
|Team.Git.GoToGitCommits|Ctrl+0, Ctrl+O<br /><br /> or<br /><br /> Ctrl+0, O|
|Team.TeamExplorerSearch|Ctrl+'|

### <a name="bkmk_TFcontext"></a>Kontextové nabídky Team Foundation

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|TeamFoundationContextMenus.Commands.GoToBuilds|Ctrl+0, Ctrl+B<br /><br /> or<br /><br /> Ctrl+0, B|
|TeamFoundationContextMenus.Commands.GoToConnect|Ctrl+0, Ctrl+C<br /><br /> or<br /><br /> Ctrl+0, C|
|TeamFoundationContextMenus.Commands.GoToDocuments|Ctrl+0, Ctrl+D<br /><br /> or<br /><br /> Ctrl+0, D|
|TeamFoundationContextMenus.Commands.GoToHome|Ctrl+0, Ctrl+H<br /><br /> or<br /><br /> Ctrl+0, H|
|TeamFoundationContextMenus.Commands.GoToMyWork|Ctrl+0, Ctrl+M<br /><br /> or<br /><br /> Ctrl+0, M|
|TeamFoundationContextMenus.Commands.GoToPendingChanges|Ctrl+0, Ctrl+P<br /><br /> or<br /><br /> Ctrl+0, P|
|TeamFoundationContextMenus.Commands.GoToReports|Ctrl+0, Ctrl+R<br /><br /> or<br /><br /> Ctrl+0, R|
|TeamFoundationContextMenus.Commands.GoToSettings|Ctrl+0, Ctrl+S<br /><br /> or<br /><br /> Ctrl+0, S|
|TeamFoundationContextMenus.Commands.GoToWebAccess|Ctrl+0, Ctrl+A<br /><br /> or<br /><br /> Ctrl+0, A|
|TeamFoundationContextMenus.Commands.GoToWorkItems|Ctrl+0, Ctrl+W<br /><br /> or<br /><br /> Ctrl+0, W|

### <a name="bkmk_test"></a>Napaden

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Test.UseCodedUITestBuilder|CTRL + \\, CTRL + C|
|Test.UseExistingActionRecording|CTRL + \\, CTRL + A|

### <a name="bkmk_testexplorerGLOBAL"></a> Průzkumník testů

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|TestExplorer.DebugAllTests|Ctrl+R, Ctrl+A|
|TestExplorer.DebugAllTestsInContext|Ctrl+R, Ctrl+T|
|TestExplorer.RepeatLastRun|Ctrl+R, L|
|TestExplorer.RunAllTests|Ctrl+R, A|
|TestExplorer.RunAllTestsInContext|Ctrl+R, T|

### <a name="bkmk_tools"></a>Nástroje

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Tools.AttachtoProcess|Ctrl+Alt+P|
|Tools.CodeSnippetsManager|Ctrl+K, Ctrl+B|
|Tools.ForceGC|Ctrl+Shift+Alt+F12, Ctrl+Shift+Alt+F12|
|Tools.GoToCommandLine|Ctrl+/|

### <a name="bkmk_view"></a>Zobrazení

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|View.AllWindows|Shift+Alt+M|
|View.ArchitectureExplorer|CTRL + \\, CTRL + R|
|View.Backward|Alt + šipka doleva|
|View.BookmarkWindow|Ctrl+K, Ctrl+W|
|View.BrowseNext|Ctrl+Shift+1|
|View.BrowsePrevious|Ctrl+Shift+2|
|View.CallHierarchy|Ctrl+Alt+K|
|View.ClassView|Ctrl+Shift+C|
|View.ClassViewGoToSearchCombo|Ctrl+K, Ctrl+V|
|View.CodeDefinitionWindow|CTRL + \\, D<br /><br /> or<br /><br /> CTRL + \\, CTRL + D|
|View.CommandWindow|Ctrl+Alt+A|
|View.DataSources|Shift+Alt+D|
|View.DocumentOutline|Ctrl+Alt+T|
|View.EditLabel|F2|
|View.ErrorList|CTRL + \\, E<br /><br /> or<br /><br /> CTRL + \\, CTRL + E|
|View.F#Interactive|Ctrl+Alt+F|
|View.FindSymbolResults|Ctrl+Alt+F12|
|View.Forward|Alt + šipka doprava|
|View.ForwardBrowseContext|Ctrl+Shift+7|
|View.FullScreen|Shift+Alt+Enter|
|View.NavigateBackward|Ctrl+-|
|View.NavigateForward|Ctrl+Shift+-|
|View.NextError|Ctrl+Shift+F12|
|View.Notifications|Ctrl+W, N<br /><br /> or<br /><br /> Ctrl+W, Ctrl+N|
|View.ObjectBrowser|Ctrl+Alt+J|
|View.ObjectBrowserGoToSearchCombo|Ctrl+K, Ctrl+R|
|View.Output|Ctrl+Alt+O|
|View.PopBrowseContex|Ctrl+Shift+8|
|View.PropertiesWindow|F4|
|View.PropertyPages|Shift+F4|
|View.ResourceView|Ctrl+Shift+E|
|View.ServerExplorer|Ctrl+Alt+S|
|View.ShowSmartTag|Shift+Alt+F10<br /><br /> or<br /><br /> Ctrl+.|
|View.SolutionExplorer|Ctrl+Alt+L|
|View.SQLServerObjectExplorer|CTRL + \\, CTRL + S|
|View.TaskList|CTRL + \\, T<br /><br /> or<br /><br /> CTRL + \\, CTRL + T|
|View.TfsTeamExplorer|CTRL + \\, CTRL + M|
|View.Toolbox|Ctrl+Alt+X|
|View.UMLModelExplorer|CTRL + \\, CTRL + U|
|View.ViewCode|F7|
|View.ViewDesigner|Shift+F7|
|View.WebBrowser|Ctrl+Alt+R|
|View.ZoomIn|Ctrl+Shift+.|
|View.ZoomOut|Ctrl+Shift+,|

### <a name="bkmk_window"></a>Okno

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Window.ActivateDocumentWindow|Esc|
|Window.AddTabtoSelection|Ctrl + Shift + Alt + mezerník|
|Window.CloseDocumentWindow|Ctrl+F4|
|Window.CloseToolWindow|Shift+Esc|
|Window.KeepTabOpen|Ctrl+Alt+Home|
|Window.MovetoNavigationBar|Ctrl+F2|
|Window.NextDocumentWindow|Ctrl+F6|
|Window.NextDocumentWindowNav|Ctrl+Tab|
|Window.NextPane|Alt+F6|
|Window.NextSplitPane|F6|
|Window.NextTab|Ctrl+Alt+PgDn<br /><br /> or<br /><br /> Ctrl+PgDn|
|Window.NextTabandAddtoSelection|Ctrl+Shift+Alt+PgDn|
|Window.NextToolWindowNav|Alt+F7|
|Window.PreviousDocumentWindow|Ctrl+Shift+F6|
|Window.PreviousDocumentWindowNav|Ctrl+Shift+Tab|
|Window.PreviousPane|Shift+Alt+F6|
|Window.PreviousSplitPane|Shift+F6|
|Window.PreviousTab|Ctrl+Alt+PgUp<br /><br /> or<br /><br /> Ctrl+PgUp|
|Window.PreviousTabandAddtoSelection|Ctrl+Shift+Alt+PgUp|
|Window.PreviousToolWindowNav|Shift+Alt+F7|
|Window.QuickLaunch|Ctrl+Q|
|Window.QuickLaunchPreviousCategory|Ctrl+Shift+Q|
|Window.ShowDockMenu|Alt+-|
|Window.ShowEzMDIFileList|Ctrl + Alt + šipka dolů|
|Window.SolutionExplorerSearch|Ctrl+;|
|Window.WindowSearch|Alt+`|

### <a name="bkmk_windowsazure"></a>Azure

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|WindowsAzure.RetryMobileServiceScriptOperation|Ctrl+Num *, Ctrl+R|
|WindowsAzure.ShowMobileServiceScriptErrorDetails|Ctrl+Num *, Ctrl+D|

## <a name="bkmk_ADONET"></a>Návrhář model EDM (Entity Data Model) ADO.NET

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down|Alt + šipka dolů|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5|Alt+PgDn|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom|Alt+End|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop|Alt+Home|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up|Alt + šipka nahoru|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5|Alt+PgUp|
|OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename|Ctrl+R, R|
|OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram|Shift+Del|
|View.EntityDataModelBrowser|Ctrl+1|
|View.EntityDataModelMappingDetails|Ctrl+2|

## <a name="bkmk_classDiagram"></a>Diagram tříd

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|ClassDiagram.Collapse|Num -|
|ClassDiagram.Expand|Num +|
|Edit.Delete|Ctrl+Del|
|Edit.ExpandCollapseBaseTypeList|Shift+Alt+B|
|Edit.NavigateToLollipop|Shift+Alt+L|
|Edit.RemovefromDiagram|Odstranit|
|View.ViewCode|Enter|

## <a name="bkmk_codedUItest"></a>Editor programového testu UI

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard|Ctrl+C|
|OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore|Ctrl+Alt+D|
|OtherContextMenus.UITestEditorContextMenu.LocateAll|Shift+Alt+L|
|OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl|Ctrl+Shift+L|
|OtherContextMenus.UITestEditorContextMenu.Movecode|Ctrl+Alt+C|
|OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod|Ctrl+Shift+T|

## <a name="bkmk_dataset"></a>Editor DataSet

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|OtherContextMenus.ColumnContext.InsertColumn|Insert|
|OtherContextMenus.DbTableContext.Add.Column|Ctrl+L|

## <a name="bkmk_diff"></a>Prohlížeč rozdílů

|||
|-|-|
|Příkazy|Klávesové zkratky|
|Diff.IgnoreTrimWhitespace|CTRL + \\, CTRL + MEZERNÍK|
|Diff.InlineView|CTRL + \\, CTRL + 1|
|Diff.LeftOnlyView|CTRL + \\, CTRL + 3|
|Diff.NextDifference|F8|
|Diff.PreviousDifference|Shift+F8|
|Diff.RightOnlyView|CTRL + \\, CTRL + 4|
|Diff.SideBySideView|CTRL + \\, CTRL + 2|
|Diff.SwitchBetweenLeftAndRight|CTRL + \\, CTRL + TAB|
|Diff.SynchronizeViewToggle|CTRL + \\, Ctrl + šipka dolů|
|EditorContextMenus.CodeWindow.AddComment|Ctrl+Shift+K|
|EditorContextMenus.CodeWindow.EditLocalFile|Ctrl+Shift+P|

## <a name="bkmk_DOM"></a>Průzkumník modelu DOM

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|DOMExplorer.Refresh|Stisknutím|
|DOMExplorer.SelectElement|Ctrl+B|
|DOMExplorer.ShowLayout|Ctrl+Shift+I|

## <a name="bkmk_FSharp"></a>F# Interaktivní

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation|Ctrl+Break|

## <a name="bkmk_graphDoc"></a>Editor dokumentu grafu

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode|Insert|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies|B|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies|I|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies|O|
|ArchitectureContextMenus.DirectedGraphContextMenu.NewComment|Ctrl+Shift+K<br /><br /> or<br /><br /> Ctrl+E, C|
|ArchitectureContextMenus.DirectedGraphContextMenu.Remove|Odstranit|
|ArchitectureContextMenus.DirectedGraphContextMenu.Rename|F2|

## <a name="bkmk_graphicsDebugger"></a>Diagnostika grafiky

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Debug.Graphics.CaptureFrame|Žádné|
|Graphics. MovePixelSelectionDown|Shift +Alt + šipka dolů|
|Graphics. MovePixelSelectionLeft|Shift + Alt + šipka doleva|
|Graphics. MovePixelSelectionRight|Shift + Alt + šipka doprava|
|Graphics. MovePixelSelectionUp|Shift + Alt + šipka nahoru|
|Graphics. ZoomToActualSize|Shift+Alt+0|
|Graphics. ZoomToFitInWindow|Shift + Alt + 9|
|Graphics. ZoomIn|Shift+Alt+=|
|Graphics. zoom|Shift+Alt+-|

## <a name="bkmk_HTMLeditor"></a>Editor HTML

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|OtherContextMenus.HTMLContext.GoToController|Ctrl+M, Ctrl+G|

## <a name="bkmk_HTMLeditorDesign"></a>Zobrazení návrhu editoru HTML

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.MoveControlDown|Ctrl + šipka dolů|
|Edit.MoveControlUp|Ctrl + šipka nahoru|
|Format.Bold|Ctrl+B|
|Format.ConverttoHyperlink|Ctrl+L|
|Format.InsertBookmark|Ctrl+Shift+L|
|Format.Italic|Ctrl+I|
|Format.Underline|Ctrl+U|
|Project.AddContentPage|Ctrl+M, Ctrl+C|
|Table.ColumntotheLeft|Ctrl + Alt + šipka doleva|
|Table.ColumntotheRight|Ctrl + Alt + šipka doprava|
|Table.RowAbove|Ctrl+Alt + šipka nahoru|
|Table.RowBelow|Ctrl + Alt + šipka dolů|
|View.ASP.NETNonvisualControls|Ctrl+Shift+N|
|View.EditMaster|Ctrl+M, Ctrl+M|
|View.NextView|Ctrl+PgDn|
|View.ShowSmartTag|Shift+Alt+F10|
|View.ViewMarkup|Shift+F7|
|Window.PreviousTab|Ctrl+PgUp|

## <a name="bkmk_HTMLeditorSource"></a>Zobrazení zdroje editoru HTML

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|OtherContextMenus.HTMLContext.GoToController|Ctrl+M, Ctrl+G|
|View.NextView|Ctrl+PgDn|
|View.SynchronizeViews|Ctrl+Shift+Y|
|View.ViewDesigner|Shift+F7|
|Window.PreviousTab|Ctrl+PgUp|

## <a name="bkmk_layerDiagram"></a>Diagram vrstev

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.Delete|Shift+Delete|

## <a name="bkmk_managedResources"></a>Editor spravovaných prostředků

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.EditCell|F2|
|Edit.Remove|Odstranit|
|Edit.RemoveRow|Ctrl+Delete|
|Edit.SelectionCancel|Escape|
|Resources.Audio|Ctrl+4|
|Resources.Files|Ctrl+5|
|Resources.Icons|Ctrl+3|
|Resources.Images|Ctrl+2|
|Resources.Other|Ctrl+6|
|Resources.Strings|Ctrl+1|

## <a name="bkmk_MergeEditor"></a>Okno editoru sloučení

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow|Alt+1|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow|Alt+2|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow|Alt+3|

## <a name="bkmk_SchemaCompare"></a>Nástroje pro Microsoft SQL Server data, porovnání schématu

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|SQL.SSDTSchemaCompareCompare|Shift+Alt+C|
|SQL.SSDTSchemaCompareGenerateScript|Shift+Alt+G|
|SQL.SSDTSchemaCompareNextChange|Shift+Alt+.|
|SQL.SSDTSchemaComparePreviousChange|Shift+Alt+,|
|SQL.SSDTSchemaCompareStop|Alt+Break|
|SQL.SSDTSchemaCompareWriteUpdates|Shift+Alt+U|

## <a name="bkmk_TableDesigner"></a>Microsoft SQL Server Data Tools, Návrhář tabulky

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|CommitAllEdits|Shift+Alt+U|
|SQL.ExpandWildcards|Ctrl+R, E<br /><br /> or<br /><br /> Ctrl+R, Ctrl+E|
|SQL.FullyqualifyNames|Ctrl+R, Q<br /><br /> or<br /><br /> Ctrl+R, Ctrl+Q|
|SQL.MovetoSchema|Ctrl+R, M<br /><br /> or<br /><br /> Ctrl+R, Ctrl+M|
|SQL.Rename|F2<br /><br /> or<br /><br /> Ctrl+R, R<br /><br /> or<br /><br /> Ctrl+R, Ctrl+R|
|ViewFileInScriptPanel|Shift+Alt+PgDn|

## <a name="bkmk_TSQLeditor"></a>Nástroje pro Microsoft SQL Server dat, Editor T-SQL

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|CommitAllEdits|Shift+Alt+U|
|SQL.ExecuteWithDebugger|Alt+F5|
|SQL.ExpandWildcards|Ctrl+R, E<br /><br /> or<br /><br /> Ctrl+R, Ctrl+E|
|SQL.FullyqualifyNames|Ctrl+R, Q<br /><br /> or<br /><br /> Ctrl+R, Ctrl+Q|
|SQL.MovetoSchema|Ctrl+R, M<br /><br /> or<br /><br /> Ctrl+R, Ctrl+M|
|SQL.Rename|F2<br /><br /> or<br /><br /> Ctrl+R, R<br /><br /> or<br /><br /> Ctrl+R, Ctrl+R|
|SQL.TSqlEditorCancelQuery|Alt+Break|
|SQL.TSqlEditorExecuteQuery|Ctrl+Shift+E|
|SQL.TSqlEditorResultsAsFile|Ctrl+D, F|
|SQL.TSqlEditorResultsAsGrid|Ctrl+D, G|
|SQL.TSqlEditorResultsAsText|Ctrl+D, T|
|SQL.TSqlEditorShowEstimatedPlan|Ctrl+D, E|
|SQL.TSqlEditorToggleExecutionPlan|Ctrl+D, A|
|SQL.TSqlEditorToggleResultsPane|Ctrl+D, R|
|TSqlEditorCloneQuery|Ctrl+Alt+N|
|TSqlEditorDatabaseCombo|Shift+Alt+PgDn|

## <a name="bkmk_linkfix"></a>Nástroje pro Microsoft SQL Server dat, Editor T-SQL PDW

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|SQL.TSqlEditorCancelQuery|Alt+Break|
|SQL.TSqlEditorExecuteQuery|Ctrl+Shift+E|
|SQL.TSqlEditorResultsAsFile|Ctrl+D, F|
|SQL.TSqlEditorResultsAsGrid|Ctrl+D, G|
|SQL.TSqlEditorResultsAsText|Ctrl+D, T|
|SQL.TSqlEditorShowEstimatedPlan|Ctrl+D, E|
|SQL.TSqlEditorToggleExecutionPlan|Ctrl+D, A|
|SQL.TSqlEditorToggleResultsPane|Ctrl+D, R|
|TSqlEditorCloneQuery|Ctrl+Alt+N|
|TSqlEditorDatabaseCombo|Shift+Alt+PgDn|

## <a name="bkmk_PageInspector"></a>Inspektor stránky

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|PageInspector.Minimize|Kláves|

## <a name="bkmk_QueryDesigner"></a>Návrhář dotazů

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|QueryDesigner.CancelRetrievingData|Ctrl+T|
|QueryDesigner.Criteria|Ctrl+2|
|QueryDesigner.Diagram|Ctrl+1|
|QueryDesigner.ExecuteSQL|Ctrl+R|
|QueryDesigner.GotoRow|Ctrl+G|
|QueryDesigner.JoinMode|Ctrl+Shift+J|
|QueryDesigner.Results|Ctrl+4|
|QueryDesigner.SQL|Ctrl+3|

## <a name="bkmk_QueryResults"></a>Výsledky dotazu

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|SQL.QueryResultsNewRow|Alt+End|
|SQL.QueryResultsRefresh|Shift+Alt+R|
|SQL.QueryResultsStop|Alt+Break|

## <a name="bkmk_ReportDesigner"></a>Návrhář sestav

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.BreakLine|Enter|
|Edit.CharLeft|Šipka doleva|
|Edit.CharLeftExtend|Shift + šipka doleva|
|Edit.CharRight|Šipka doprava|
|Edit.CharRightExtend|Shift + šipka doprava|
|Edit.InsertTab|Karta|
|Edit.LineDown|Šipka dolů|
|Edit.LineDownExtend|Shift + šipka dolů|
|Edit.LineUp|Šipka nahoru|
|Edit.LineUpExtend|Shift + šipka nahoru|
|Edit.MoveControlDown|Ctrl + šipka dolů|
|Edit.MoveControlLeft|Ctrl + šipka doleva|
|Edit.MoveControlRight|Ctrl + šipka doprava|
|Edit.MoveControlUp|Ctrl + šipka nahoru|
|Edit.SelectionCancel|Esc|
|Edit.SizeControlDown|Ctrl + Shift + šipka dolů|
|Edit.SizeControlLeft|Ctrl + Shift + šipka doleva|
|Edit.SizeControlRight|Ctrl + Shift + šipka doprava|
|Edit.SizeControlUp|Ctrl + Shift + šipka nahoru|
|Edit.TabLeft|Shift+Tab|
|View.ReportData|Ctrl+Alt+D|

## <a name="bkmk_SequenceDiagram"></a>Sekvenční diagram

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|ArchitectureDesigner.Sequence.NavigateToCode|Kláves|
|Edit.Delete|Shift+Del|

## <a name="bkmk_SettingsDesigner"></a>Návrhář nastavení

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.EditCell|F2|
|Edit.RemoveRow|Ctrl+Delete|
|Edit.SelectionCancel|Esc|
|View.ViewCode|F7|

## <a name="bkmk_SolutionExplorer"></a>Průzkumník řešení

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector|Ctrl+K, Ctrl+G|

## <a name="bkmk_TeamExplorer"></a> Team Explorer

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.Delete|Odstranit|
|File.Rename|F2|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation|Alt+Home|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent|Alt + šipka dolů|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent|Alt+0|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent|Alt + šipka nahoru|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content|Alt+1|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content|Alt+2|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content|Alt+3|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content|Alt+4|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content|Alt+5|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content|Alt+6|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content|Alt+7|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content|Alt+8|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content|Alt+9|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward|Alt + šipka doleva|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward|Alt + šipka doprava|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI|Shift+Alt+C|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI|Shift+Alt+L|
|View.Refresh|Stisknutím|

## <a name="bkmk_TFBuild"></a>Editor podrobností sestavení Team Foundation

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|View.Refresh|Stisknutím|

## <a name="bkmk_TestExplorer"></a> Průzkumník testů

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|TestExplorer.OpenTest|Kláves|

## <a name="bkmk_TextEditor"></a>Textový editor

|                             Příkazy                              |                  Klávesové zkratky                   |
|-------------------------------------------------------------------|-------------------------------------------------------|
|                          Edit.BreakLine                           |     Enter<br /><br /> or<br /><br /> Shift+Enter      |
|                           Edit.CharLeft                           |                      Šipka doleva                       |
|                        Edit.CharLeftExtend                        |                   Shift + šipka doleva                    |
|                     Edit.CharLeftExtendColumn                     |                 Shift + Alt + šipka doleva                  |
|                          Edit.CharRight                           |                      Šipka doprava                      |
|                       Edit.CharRightExtend                        |                   Shift + šipka doprava                   |
|                    Edit.CharRightExtendColumn                     |                 Shift + Alt + šipka doprava                 |
|                        Edit.CharTranspose                         |                        Ctrl+T                         |
|                        Edit.ClearBookmarks                        |                    Ctrl+K, Ctrl+L                     |
|                     Edit.CollapseAllOutlining                     |                    Ctrl+M, Ctrl+A                     |
|                    Edit.CollapseCurrentRegion                     |                    Ctrl+M, Ctrl+S                     |
|                         Edit.CollapseTag                          |                    Ctrl+M, Ctrl+T                     |
|                    Edit.CollapsetoDefinitions                     |                    Ctrl+M, Ctrl+O                     |
|                       Edit.CommentSelection                       |                    Ctrl+K, Ctrl+C                     |
|                         Edit.CompleteWord                         | Ctrl + mezerník<br /><br /> or<br /><br /> Alt + šipka doprava |
|                       Edit.CopyParameterTip                       |                   Ctrl+Shift+Alt+C                    |
|                     Edit.DecreaseFilterLevel                      |                         Alt+,                         |
|                       Edit.DeleteBackwards                        |   Backspace<br /><br /> or<br /><br /> Shift+Bkspce   |
|                  Edit.DeleteHorizontalWhiteSpace                  |                    Ctrl+K, Ctrl+\                     |
|                         Edit.DocumentEnd                          |                       Ctrl+End                        |
|                      Edit.DocumentEndExtend                       |                    Ctrl+Shift+End                     |
|                        Edit.DocumentStart                         |                       Ctrl+Home                       |
|                     Edit.DocumentStartExtend                      |                    Ctrl+Shift+Home                    |
|                      Edit.ExpandAllOutlining                      |                    Ctrl+M, Ctrl+X                     |
|                     Edit.ExpandCurrentRegion                      |                    Ctrl+M, Ctrl+E                     |
|                        Edit.FormatDocument                        |                    Ctrl+K, Ctrl+D                     |
|                       Edit.FormatSelection                        |                    Ctrl+K, Ctrl+F                     |
|                          Edit.GotoBrace                           |                        Ctrl+]                         |
|                       Edit.GotoBraceExtend                        |                     Ctrl+Shift+]                      |
|                        Edit.HideSelection                         |                    Ctrl+M, Ctrl+H                     |
|                     Edit.IncreaseFilterLevel                      |                         Alt+.                         |
|                      Edit.IncrementalSearch                       |                        Ctrl+I                         |
|                          Edit.InsertTab                           |                          Karta                          |
|                           Edit.LineCut                            |                        Ctrl+L                         |
|                          Edit.LineDelete                          |                     Ctrl+Shift+L                      |
|                           Edit.LineDown                           |                      Šipka dolů                       |
|                        Edit.LineDownExtend                        |                   Shift + šipka dolů                    |
|                     Edit.LineDownExtendColumn                     |                 Shift +Alt + šipka dolů                  |
|                           Edit.LineEnd                            |                          End                          |
|                        Edit.LineEndExtend                         |                       Shift+End                       |
|                     Edit.LineEndExtendColumn                      |                     Shift+Alt+End                     |
|                        Edit.LineOpenAbove                         |                      Ctrl+Enter                       |
|                        Edit.LineOpenBelow                         |                   Ctrl+Shift+Enter                    |
|                          Edit.LineStart                           |                         Domů                          |
|                       Edit.LineStartExtend                        |                      Shift+Home                       |
|                    Edit.LineStartExtendColumn                     |                    Shift+Alt+Home                     |
|                        Edit.LineTranspose                         |                      Shift+Alt+T                      |
|                            Edit.LineUp                            |                       Šipka nahoru                        |
|                         Edit.LineUpExtend                         |                    Shift + šipka nahoru                     |
|                      Edit.LineUpExtendColumn                      |                  Shift + Alt + šipka nahoru                   |
|                         Edit.ListMembers                          |                        Ctrl+J                         |
|                        Edit.MakeLowercase                         |                        Ctrl+U                         |
|                        Edit.MakeUppercase                         |                     Ctrl+Shift+U                      |
|                    Edit.MoveSelectedLinesDown                     |                    Alt + šipka dolů                     |
|                     Edit.MoveSelectedLinesUp                      |                     Alt + šipka nahoru                      |
|                   Edit.NextHighlightedReference                   |                 Ctrl + Shift + šipka dolů                 |
|                         Edit.OvertypeMode                         |                        Insert                         |
|                           Edit.PageDown                           |                         PgDn                          |
|                        Edit.PageDownExtend                        |                      Shift+PgDn                       |
|                            Edit.PageUp                            |                         PgUp                          |
|                         Edit.PageUpExtend                         |                      Shift+PgUp                       |
|                        Edit.ParameterInfo                         |                  Ctrl + Shift + mezerník                  |
|                      Edit.PasteParameterTip                       |                   Ctrl+Shift+Alt+P                    |
|                         Edit.PeekBackward                         |                      Ctrl+Alt+-                       |
|                        Edit.PeekDefinition                        |                        Alt+F12                        |
|                         Edit.PeekForward                          |                      Ctrl+Alt+=                       |
|                 Edit.PreviousHighlightedReference                 |                  Ctrl + Shift + šipka nahoru                  |
|                          Edit.QuickInfo                           |                    Ctrl+K, Ctrl+I                     |
|                   Edit.ReverseIncrementalSearch                   |                     Ctrl+Shift+I                      |
|                        Edit.ScrollLineDown                        |                    Ctrl + šipka dolů                    |
|                         Edit.ScrollLineUp                         |                     Ctrl + šipka nahoru                     |
|                      Edit.SelectCurrentWord                       |                        Ctrl+W                         |
|                       Edit.SelectionCancel                        |                        Escape                         |
|                      Edit.SelectToLastGoBack                      |                        Ctrl+=                         |
|                       Edit.ShowCodeLensMenu                       |                        ALT + \`                         |
|                      Edit.StopHidingCurrent                       |                    Ctrl+M, Ctrl+U                     |
|                        Edit.StopOutlining                         |                    Ctrl+M, Ctrl+P                     |
|                          Edit.SwapAnchor                          |                    Ctrl+K, Ctrl+A                     |
|                           Edit.TabLeft                            |                       Shift+Tab                       |
|                      Edit.ToggleAllOutlining                      |                    Ctrl+M, Ctrl+L                     |
|                        Edit.ToggleBookmark                        |                    Ctrl+K, Ctrl+K                     |
|                     Edit.ToggleCompletionMode                     |                    Ctrl + Alt + mezerník                     |
|                   Edit.ToggleOutliningExpansion                   |                    Ctrl+M, Ctrl+M                     |
|                    Edit.ToggleTaskListShortcut                    |                    Ctrl+K, Ctrl+H                     |
|                        Edit.ToggleWordWrap                        |                    Ctrl+E, Ctrl+W                     |
|                      Edit.UncommentSelection                      |                    Ctrl+K, Ctrl+U                     |
|                          Edit.ViewBottom                          |                       Ctrl+PgDn                       |
|                       Edit.ViewBottomExtend                       |                    Ctrl+Shift+PgDn                    |
|                           Edit.ViewTop                            |                       Ctrl+PgUp                       |
|                        Edit.ViewTopExtend                         |                    Ctrl+Shift+PgUp                    |
|                        Edit.ViewWhiteSpace                        |                    Ctrl+R, Ctrl+W                     |
|                       Edit.WordDeleteToEnd                        |                      Ctrl+Delete                      |
|                      Edit.WordDeleteToStart                       |                    Ctrl+Backspace                     |
|                           Edit.WordNext                           |                   Ctrl + šipka doprava                    |
|                        Edit.WordNextExtend                        |                Ctrl + Shift + šipka doprava                 |
|                     Edit.WordNextExtendColumn                     |              Ctrl + Shift + Alt + šipka doprava               |
|                         Edit.WordPrevious                         |                    Ctrl + šipka doleva                    |
|                      Edit.WordPreviousExtend                      |                 Ctrl + Shift + šipka doleva                 |
|                   Edit.WordPreviousExtendColumn                   |               Ctrl + Shift + Alt + šipka doleva               |
|                        Edit.WordTranspose                         |                     Ctrl+Shift+T                      |
|        EditorContextMenus.CodeWindow.ExecuteInInteractive         |                       Alt+Enter                       |
|      EditorContextMenus.CodeWindow.ExecuteLineInInteractive       |                         Alt+'                         |
|         OtherContextMenus.HTMLContext.ViewinPageInspector         |                    Ctrl+K, Ctrl+G                     |
|   TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion   |                       Alt+PgDn                        |
| TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |                       Alt+PgUp                        |

## <a name="bkmk_UMLactivityDiagram"></a>Diagram činnosti UML

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.Delete|Shift+Del|

## <a name="bkmk_UMLclassDiagram"></a>Diagram tříd UML

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.DeleteFromModel|Shift+Del|

## <a name="bkmk_UMLcomponentDiagram"></a>Diagram komponent UML

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.DeleteFromModel|Shift+Del|

## <a name="bkmk_UMLusecaseDiagram"></a>Diagram případu použití UML

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.DeleteFromModel|Shift+Del|

## <a name="bkmk_vcaccelerator"></a>Editor akcelerátorů VC

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.NewAccelerator|Insert|
|Edit.NextKeyTyped|Ctrl+W|

## <a name="bkmk_vcdialogeditor"></a>Editor dialogových oken VC

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.MoveControlDown|Šipka dolů|
|Edit.MoveControlLeft|Šipka doleva|
|Edit.MoveControlRight|Šipka doprava|
|Edit.MoveControlUp|Šipka nahoru|
|Edit.ScrollColumnLeft|Ctrl + šipka doleva|
|Edit.ScrollColumnRight|Ctrl + šipka doprava|
|Edit.ScrollLineDown|Ctrl + šipka dolů|
|Edit.ScrollLineUp|Ctrl + šipka nahoru|
|Edit.SizeControlDown|Shift + šipka dolů|
|Edit.SizeControlLeft|Shift + šipka doleva|
|Edit.SizeControlRight|Shift + šipka doprava|
|Edit.SizeControlUp|Shift + šipka nahoru|
|Format.AlignBottoms|Ctrl + Shift + šipka dolů|
|Format.AlignCenters|Shift+F9|
|Format.AlignLefts|Ctrl + Shift + šipka doleva|
|Format.AlignMiddles|Vede|
|Format.AlignRights|Ctrl + Shift + šipka doprava|
|Format.AlignTops|Ctrl + Shift + šipka nahoru|
|Format.ButtonBottom|Ctrl+B|
|Format.ButtonRight|Ctrl+R|
|Format.CenterHorizontal|Ctrl+Shift+F9|
|Format.CenterVertical|Ctrl+F9|
|Format.CheckMnemonics|Ctrl+M|
|Format.SizetoContent|Shift+F7|
|Format.SpaceAcross|Alt + šipka doprava<br /><br /> or<br /><br /> Alt + šipka doleva|
|Format.SpaceDown|Alt + šipka nahoru<br /><br /> or<br /><br /> Alt + šipka dolů|
|Format.TabOrder|Ctrl+D|
|Format.TestDialog|Ctrl+T|
|Format.ToggleGuides|Ctrl+G|

## <a name="bkmk_vcimageeditor"></a>Editor obrázků VC

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Image.AirbrushTool|Ctrl+A|
|Image.BrushTool|Ctrl+B|
|Image.CopyandOutlineSelection|Ctrl+Shift+U|
|Image.DrawOpaque|Ctrl+J|
|Image.EllipseTool|Alt+P|
|Image.EraseTool|Ctrl+Shift+I|
|Image.FilledEllipseTool|Ctrl+Shift+Alt+P|
|Image.FilledRectangleTool|Ctrl+Shift+Alt+R|
|Image.FilledRoundedRectangleTool|Ctrl+Shift+Alt+W|
|Image.FillTool|Ctrl+F|
|Image.FlipHorizontal|Ctrl+H|
|Image.FlipVertical|Shift+Alt+H|
|Image.LargerBrush|Ctrl+=|
|Image.LineTool|Ctrl+L|
|Image.MagnificationTool|Ctrl+M|
|Image.Magnify|Ctrl+Shift+M|
|Image.NewImageType|Insert|
|Image.NextColor|Ctrl+]<br /><br /> or<br /><br /> Ctrl + šipka doprava|
|Image.NextRightColor|Ctrl+Shift+]<br /><br /> or<br /><br /> Ctrl + Shift + šipka doprava|
|Image.OutlinedEllipseTool|Shift+Alt+P|
|Image.OutlinedRectangleTool|Shift+Alt+R|
|Image.OutlinedRoundedRectangleTool|Shift+Alt+W|
|Image.PencilTool|Ctrl+I|
|Image.PreviousColor|Ctrl+[<br /><br /> or<br /><br /> Ctrl + šipka doleva|
|Image.PreviousRightColor|Ctrl+Shift+[<br /><br /> or<br /><br /> Ctrl + Shift + šipka doleva|
|Image.RectangleSelectionTool|Shift+Alt+S|
|Image.RectangleTool|Alt+R|
|Image.Rotate90Degrees|Ctrl+Shift+H|
|Image.RoundedRectangleTool|Alt+W|
|Image.ShowGrid|Ctrl+Alt+S|
|Image.ShowTileGrid|Ctrl+Shift+Alt+S|
|Image.SmallBrush|Ctrl+.|
|Image.SmallerBrush|Ctrl+-|
|Image.TextTool|Ctrl+T|
|Image.UseSelectionasBrush|Ctrl+U|
|Image.ZoomIn|Ctrl+Shift+.<br /><br /> or<br /><br /> Ctrl + šipka nahoru|
|Image.ZoomOut|Ctrl+Shift+,<br /><br /> or<br /><br /> Ctrl + šipka dolů|

## <a name="bkmk_vcstringeditor"></a>Editor řetězců VC

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|Edit.NewString|Insert|

## <a name="bkmk_viewDesigner"></a>Návrhář zobrazení

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|QueryDesigner.CancelRetrievingData|Ctrl+T|
|QueryDesigner.Criteria|Ctrl+2|
|QueryDesigner.Diagram|Ctrl+1|
|QueryDesigner.ExecuteSQL|Ctrl+R|
|QueryDesigner.GotoRow|Ctrl+G|
|QueryDesigner.JoinMode|Ctrl+Shift+J|
|QueryDesigner.Results|Ctrl+4|
|QueryDesigner.SQL|Ctrl+3|

## <a name="bkmk_visualstudio"></a>Visual Studio

|Příkaz|Klávesová zkratka|
|-------------|-----------------------|
|OtherContextMenus.ORDesignerContext.HideMethodsPane|Ctrl+1|

## <a name="bkmk_wfdesigner"></a>Návrhář formulářů

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.BreakLine|Enter|
|Edit.CharLeft|Šipka doleva|
|Edit.CharLeftExtend|Shift + šipka doleva|
|Edit.CharRight|Šipka doprava|
|Edit.CharRightExtend|Shift + šipka doprava|
|Edit.DocumentEnd|End|
|Edit.DocumentEndExtend|Shift+End|
|Edit.DocumentStart|Domů|
|Edit.DocumentStartExtend|Shift+Home|
|Edit.InsertTab|Karta|
|Edit.LineDown|Šipka dolů|
|Edit.LineDownExtend|Shift + šipka nahoru|
|Edit.LineUp|Šipka nahoru|
|Edit.LineUpExtend|Shift + šipka dolů|
|Edit.MoveControlDown|Ctrl + šipka dolů|
|Edit.MoveControlLeft|Ctrl + šipka doleva|
|Edit.MoveControlRight|Ctrl + šipka doprava|
|Edit.MoveControlUp|Ctrl + šipka nahoru|
|Edit.SelectionCancel|Escape|
|Edit.SizeControlDown|Ctrl + Shift + šipka dolů|
|Edit.SizeControlLeft|Ctrl + Shift + šipka doleva|
|Edit.SizeControlRight|Ctrl + Shift + šipka doprava|
|Edit.SizeControlUp|Ctrl + Shift + šipka nahoru|
|Edit.TabLeft|Shift+Tab|

## <a name="bkmk_workItemEditor"></a>Editor pracovních položek

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|Shift+Alt+C|
|Edit.RefreshWorkItem|Stisknutím|
|Team.NewLinkedWorkItem|Shift+Alt+L|

## <a name="bkmk_WIqueryview"></a>Zobrazení dotazu pracovní položky

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|Shift+Alt+C|
|Edit.Indent|Shift + Alt + šipka doprava|
|Edit.Outdent|Shift + Alt + šipka doleva|
|Team.NewLinkedWorkItem|Shift+Alt+L|
|Team.Refresh|Stisknutím|
|Window.Toggle|Shift+Alt+V|

## <a name="bkmk_WIresultsview"></a>Zobrazení výsledků pracovních položek

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|Shift+Alt+C|
|Edit.Indent|Shift + Alt + šipka doprava|
|Edit.Outdent|Shift + Alt + šipka doleva|
|Team.GotoNextWorkItem|Shift+Alt+N|
|Team.GotoPreviousWorkItem|Shift+Alt+P|
|Team.NewLinkedWorkItem|Shift+Alt+L|
|Team.Refresh|Stisknutím|
|Window.Toggle|Shift+Alt+V|

## <a name="bkmk_workflowdesigner"></a>Návrhář postupu provádění

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Edit.CompleteWord|Ctrl+K, W<br /><br /> or<br /><br /> Ctrl+K, Ctrl+W<br /><br /> or<br /><br /> Ctrl + mezerník<br /><br /> or<br /><br /> Alt + šipka doprava|
|Edit.DecreaseFilterLevel|Alt+,|
|Edit.IncreaseFilterLevel|Alt+.|
|Edit.ListMembers|Ctrl+K, L<br /><br /> or<br /><br /> Ctrl+K, Ctrl+L<br /><br /> or<br /><br /> Ctrl+J|
|Edit.ParameterInfo|Ctrl+K, P<br /><br /> or<br /><br /> Ctrl+K, Ctrl+P<br /><br /> or<br /><br /> Ctrl + Shift + mezerník|
|Edit.QuickInfo|Ctrl+K, I<br /><br /> or<br /><br /> Ctrl+K, Ctrl+I|
|WorkflowDesigner.Collapse|Ctrl+E, Ctrl+C<br /><br /> or<br /><br /> Ctrl+E, C|
|WorkflowDesigner.CollapseAll|or|
|WorkflowDesigner.ConnectNodes|Ctrl+E, Ctrl+F<br /><br /> or<br /><br /> Ctrl+E, F|
|WorkflowDesigner.CreateVariable|Ctrl+E, Ctrl+N<br /><br /> or<br /><br /> Ctrl+E, N|
|WorkflowDesigner.ExpandAll|Ctrl+E, Ctrl+X<br /><br /> or<br /><br /> Ctrl+E, X|
|WorkflowDesigner.ExpandInPlace|Ctrl+E, Ctrl+E<br /><br /> or<br /><br /> Ctrl+E, E|
|WorkflowDesigner.GoToParent|Ctrl+E, Ctrl+P<br /><br /> or<br /><br /> Ctrl+E, P|
|WorkflowDesigner.MoveFocus|Ctrl+E, Ctrl+M<br /><br /> or<br /><br /> Ctrl+E, M|
|WorkflowDesigner.NavigateThroughDesigner|Ctrl+Alt+F6|
|WorkflowDesigner.Restore|Ctrl+E, Ctrl+R<br /><br /> or<br /><br /> Ctrl+E, R|
|WorkflowDesigner.ShowHideArgumentDesigner|Ctrl+E, Ctrl+A<br /><br /> or<br /><br /> Ctrl+E, A|
|WorkflowDesigner.ShowHideImportsDesigner|Ctrl+E, Ctrl+I<br /><br /> or<br /><br /> Ctrl+E, I|
|WorkflowDesigner.ShowHideOverviewMap|Ctrl+E, Ctrl+O<br /><br /> or<br /><br /> Ctrl+E, O|
|WorkflowDesigner.ShowHideVariableDesigner|Ctrl+E, Ctrl+V<br /><br /> or<br /><br /> Ctrl+E, V|
|WorkflowDesigner.ToggleSelection|Ctrl+E, Ctrl+S<br /><br /> or<br /><br /> Ctrl+E, S|
|WorkflowDesigner.ZoomIn|Ctrl+Num +|
|WorkflowDesigner.ZoomOut|Ctrl+Num -|

## <a name="bkmk_xamluidesigner"></a>Návrhář uživatelského rozhraní XAML

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|Design.FitAll|Ctrl+0|
|Design.ShowHandles|Vede|
|Design.ZoomIn|Ctrl+Alt+=|
|Design.ZoomOut|Ctrl+Alt+-|
|Format.EditText|F2|
|Format.ResetLayout.All|Ctrl+Shift+R|
|View.EdgeLeftMoveLeft|Ctrl+Shift+,|
|View.EdgeLeftMoveRight|Ctrl+Shift+.|
|View.EdgeRightMoveLeft|Ctrl+Shift+Alt+,|
|View.EdgeRightMoveRight|Ctrl+Shift+Alt+.|
|Spustit kód projektu|Ctrl+F9|

## <a name="bkmk_xmlTextEditor"></a>Editor XML (textový)

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|XML.StartXSLTDebugging|Alt+F5|
|XML.StartXSLTWithoutDebugging|Ctrl+Alt+F5|

## <a name="bkmk_xmlSchemaDesigner"></a>Návrhář schématu XML

|Příkazy|Klávesové zkratky|
|--------------|------------------------|
|GraphView.BottomtoTop|Alt + šipka nahoru|
|GraphView.LefttoRight|Alt + šipka doprava|
|GraphView.RighttoLeft|Alt + šipka doleva|
|GraphView.ToptoBottom|Alt + šipka dolů|
|OtherContextMenus.GraphView.RemovefromWorkspace|Odstranit|
|XsdDesigner.ShowContentModelView|Ctrl+2|
|XsdDesigner.ShowGraphView|Ctrl+3|
|XsdDesigner.ShowStartView|Ctrl+1|

## <a name="see-also"></a>Viz také
 [Editor obrázků pro ikony](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd) [pomocí technologie IntelliSense](../ide/using-intellisense.md)
