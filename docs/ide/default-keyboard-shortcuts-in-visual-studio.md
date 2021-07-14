---
title: Výchozí klávesové zkratky
description: seznamte se s výchozími klávesovými zkratkami v Visual Studio, které umožňují přístup k nejrůznějším příkazům a systémům windows.
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dec9f76f2b21e11cc79bc55efc4a2de6fb7dedc3
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725518"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Výchozí klávesové zkratky v Visual Studio

k nejrůznějším [příkazům](reference/visual-studio-commands.md) a windows v Visual Studio máte přístup výběrem příslušné klávesové zkratky. Tato stránka obsahuje seznam výchozích klávesových zkratek pro **obecný** profil, které jste mohli zvolit při instalaci Visual Studio. Bez ohledu na to, který profil zvolíte, můžete [zástupce příkazu identifikovat](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) otevřením dialogového okna **Možnosti** , rozbalením uzlu **prostředí** a výběrem **klávesnice**. Klávesové zkratky můžete také upravit přiřazením různých zkratek jakémukoli příkazu.

Seznam běžných klávesových zkratek a další informace o produktivitě najdete v těchto tématech:

- [Tipy klávesnice](../ide/productivity-shortcuts.md)
- [Tipy pro produktivitu](../ide/productivity-features.md).

další informace o usnadnění v Visual Studio najdete v tématech [tipy a triky pro usnadnění](../ide/reference/accessibility-tips-and-tricks.md) a [postupy: použití výhradně klávesnice](../ide/reference/how-to-use-the-keyboard-exclusively.md).

<a name="popular"></a>
## <a name="popular-keyboard-shortcuts-for-visual-studio"></a>Oblíbené klávesové zkratky pro Visual Studio

Všechny zkratky v této části platí globálně, pokud není uvedeno jinak. *Globální* kontext znamená, že zástupce je použitelný v jakémkoli okně nástroje v Visual Studio.

> [!NOTE]
> Zástupce libovolného příkazu můžete [Vyhledat](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) otevřením dialogového okna **Možnosti** , rozbalením uzlu **prostředí** a následným výběrem **klávesnice**.


#### <a name="build-popular-shortcuts"></a>Build: oblíbené zkratky

|Příkazy|Klávesové zkratky |ID příkazu|
|-|-|-|
|Sestavit řešení|**Ctrl+Shift+B** | Build.BuildSolution |
|Zrušit|**Ctrl+Break** | Build.Cancel |
|Sestavení|**Ctrl+F7** | Build.Compile |
|Spustit analýzu kódu pro řešení|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Ladění: oblíbené zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Break on – funkce|**Ctrl+B**| Debug.BreakatFunction |
|Přerušit vše|**Ctrl+Alt+Break**| Debug.BreakAll |
|Odstranit všechny zarážky|**CTRL + SHIFT + F9**| Debug.DeleteAllBreakpoints |
|Výjimky|**Ctrl+Alt+E**| Debug.Exceptions |
|Rychlé kukátko|**Ctrl+Alt+Q**<br /><br />nebo **SHIFT + F9**| Debug.QuickWatch |
|Restartovat|**Ctrl+Shift+F5**| Debug.Restart |
|Spustit ke kurzoru|**Ctrl+F10**| Debug.RunToCursor |
|Nastavit další příkaz|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Spustit|**F5**| Debug.Start |
|Spustit bez ladění|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Krokovat s vnořením|**Kláves**| Debug.StepInto |
|Krok ven|**Shift + F11**| Debug.StepOut |
|Krokovat|**F10**| Debug.StepOver |
|Zastavit ladění|**Shift + F5**| Debug.StopDebugging |
|Přepnout zarážku|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>Upravit: oblíbené zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Oddělovací čára|**zadejte** [textový Editor, návrhář sestav, Návrhář formulářů].<br /><br />nebo **SHIFT + ENTER** [textový editor]| Edit.BreakLine |
|Sbalit do definic|**CTRL + M**, **CTRL + O** [textový editor]| Upravit. CollapseToDefinitions |
|Výběr komentáře|**CTRL + K**, **CTRL + C** [textový editor]| Edit.CommentSelection |
|Dokončit slovo|**ALT + šipka doprava** [textový Editor, Návrhář postupu provádění]<br /><br />nebo **CTRL + MEZERNÍK** [textový Editor, Návrhář postupu provádění]<br /><br />nebo **CTRL + K**, **W** [Návrhář postupu provádění]<br /><br />nebo **CTRL + K, CTRL + W** [Návrhář postupu provádění]| Edit.CompleteWord |
|Kopírovat|**Ctrl+C**<br /><br />nebo **CTRL + INSERT**| Edit.Copy |
|Vyjmout|**Ctrl+X**<br /><br />nebo **SHIFT + DELETE**| Edit.Cut |
|Odstranit|**Odstranit** [Team Explorer]<br /><br />nebo **SHIFT + DELETE** [sekvenční diagram, diagram aktivity UML, Diagram vrstev]<br /><br />nebo **CTRL + Delete** [Class Diagram]| Edit.Delete |
|Vyhledávání|**Ctrl+F**| Edit.Find |
|Najít všechny odkazy|**Shift+F12**| Edit.FindAllReferences |
|Najít v souborech|**Ctrl+Shift+F**| Edit.FindinFiles |
|Najít další|**F3**| Edit.FindNext |
|Najít vybrané další|**Ctrl+F3**| Edit.FindNextSelected |
|Formátování dokumentu|**CTRL + K, CTRL + D** [textový editor]| Edit.FormatDocument |
|Formátování výběru|**CTRL + K, CTRL + F** [textový editor]| Edit.FormatSelection |
|Přejít na|**Ctrl+G**| Edit.GoTo |
|Přejít k deklaraci|**Ctrl+F12**| Edit.GoToDeclaration |
|Přejít k definici|**F12**| Edit.GoToDefinition |
|Přejít na najít pole se seznamem|**Ctrl+D**| Edit.GoToFindCombo |
|Přejít na další umístění|**F8**| Edit.GoToNextLocation |
|Vložit fragment|**CTRL + K**, **CTRL + X**| Edit.InsertSnippet |
|Karta Vložit|**Tab** [návrhář sestav, Návrhář formulářů, textový Editor]| Edit.InsertTab |
|Vyjmutí řádku|**CTRL + L** [textový editor]| Edit.LineCut |
|Řádek dolů – zvětšit sloupec|**SHIFT + ALT + Šipka dolů** [textový editor]| Edit.LineDownExtendColumn |
|Otevřený řádek nahoře|**CTRL + ENTER** [textový editor]| Edit.LineOpenAbove |
|Seznam členů|**CTRL + J** [textový Editor, Návrhář postupu provádění]<br /><br />nebo **CTRL + K, CTRL + L** [Návrhář postupu provádění]<br /><br />nebo **CTRL + K, L** [Návrhář postupu provádění]| Edit.ListMembers |
|Přejděte na adresu .|**CTRL +,**| Edit.NavigateTo |
|Otevřít soubor|**Ctrl+Shift+G**| Edit.OpenFile |
|Režim přepisování|**Vložení** [textový editor]| Edit.OvertypeMode |
|Informace o parametrech|**CTRL + SHIFT + MEZERNÍK** [textový Editor, Návrhář postupu provádění]<br /><br />nebo **CTRL + K, CTRL + P** [Návrhář postupu provádění]<br /><br />nebo **CTRL + K, P** [Návrhář postupu provádění]| Edit.ParameterInfo |
|Vložit|**Ctrl+V**<br /><br />nebo **SHIFT + INSERT**| Edit.Paste |
|Náhled definice|**Alt + F12** [textový editor]| Edit.PeekDefinition |
|Opakovat|**Ctrl+Y**<br /><br />nebo **SHIFT + ALT + BACKSPACE**<br /><br />nebo **CTRL + SHIFT + Z**| Edit.Redo |
|Nahrazení|**Ctrl+H**| Edit.Replace |
|Vybrat vše|**Ctrl+A**| Edit.SelectAll |
|Vybrat aktuální slovo|**CTRL + W** [textový editor]| Edit.SelectCurrentWord |
|Zrušit výběr|**Esc** [textový Editor, návrhář sestav, návrhář Nastavení, Návrhář formulářů, Editor spravovaných prostředků]| Edit.SelectionCancel |
|Obklopit|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Tab doleva|**Shift + Tab** [textový Editor, návrhář sestav, Editor model Windows Forms]| Edit.TabLeft |
|Přepnout všechna sbalení|**CTRL + M, CTRL + L** [textový editor]| Edit.ToggleAllOutlining |
|Přepnout záložku|**CTRL + k, CTRL + k** [textový editor]| Edit.ToggleBookmark |
|Přepnout režim dokončování|**CTRL + ALT + MEZERNÍK** [textový editor]| Edit.ToggleCompletionMode |
|Přepnout rozšíření osnovy|**CTRL + m, CTRL + m** [textový editor]| Edit.ToggleOutliningExpansion |
|Odkomentovat výběr|**CTRL + K, CTRL + U** [textový editor]| Edit.UncommentSelection |
|Zpět|**Ctrl+Z**<br /><br />nebo **ALT + BACKSPACE**| Edit.Undo |
|Odstranit slovo do konce|**CTRL + Delete** [textový editor]| Edit.WordDeleteToEnd |
|Odstranit slovo do začátku|**Ctrl + Backspace** [textový editor]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Soubor: oblíbené zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Ukončit|**Alt+F4**| File.Exit |
|Nový soubor|**Ctrl+N**| File.NewFile |
|Nový projekt|**Ctrl+Shift+N**| File.NewProject |
|Nový web|**Shift+Alt+N**| File.NewWebSite |
|Otevřít soubor|**CTRL + O**| File.OpenFile |
|Otevřený projekt|**Ctrl+Shift+O**| File.OpenProject |
|Otevřít web|**Shift+Alt+O**| File.OpenWebSite |
|přejmenování|**F2** [Team Explorer]| File.Rename |
|Uložit vše|**Ctrl+Shift+S**| File.SaveAll |
|Uložit vybrané položky|**Ctrl+S**| File.SaveSelectedItems |
|Zobrazení v prohlížeči|**Ctrl+Shift+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Project: oblíbené zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Přidat existující položku|**Shift+Alt+A**| Project.AddExistingItem |
|Přidat novou položku|**Ctrl+Shift+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Refaktoring: oblíbené zkratky

|Příkaz|Klávesová zkratka [speciální kontexty]|ID příkazu|
|-|-|-|
|Extrahování metody|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Nástroje: oblíbené zkratky

|Příkaz|Klávesová zkratka [speciální kontexty]|ID příkazu|
|-|-|-|
|Připojení k procesu|**Ctrl+Alt+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Zobrazení: oblíbené klávesové zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Zobrazení třídy|**Ctrl+Shift+C**| View.ClassView |
|Upravit popisek|**F2**| View.EditLabel |
|Seznam chyb|**Ctrl+ \\ , Ctrl+E**<br /><br />nebo **Ctrl+ \\ , E**| View.ErrorList |
|Přejít zpět|**Ctrl+-**| View.NavigateBackward |
|Přejít vpřed|**Ctrl+Shift+-**| View.NavigateForward |
|Prohlížeč objektů|**Ctrl+Alt+J**| View.ObjectBrowser |
|Výstup|**Ctrl+Alt+O**| View.Output |
|Vlastnosti – okno|**F4**| View.PropertiesWindow |
|Aktualizovat|**F5** [Team Explorer]| View.Refresh |
|Průzkumník serveru|**Ctrl+Alt+S**| View.ServerExplorer |
|Zobrazení inteligentní značky|**Ctrl+.**<br /><br />nebo **Shift+Alt+F10** [Html Editor Design View]| View.ShowSmartTag |
|Průzkumník řešení|**Ctrl+Alt+L**| View.SolutionExplorer |
|Tfs Team Explorer|**Ctrl+ \\ , Ctrl+M**| View.TfsTeamExplorer |
|Sada nástrojů|**Ctrl+Alt+X**| View.Toolbox |
|Zobrazení kódu|**Zadejte** [Diagram tříd]<br /><br />nebo **F7** [Nastavení Designer]| View.ViewCode |
|Návrhář zobrazení|**Shift+F7** [HTML Editor Source View]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Okno: oblíbené klávesové zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Okno Aktivovat dokument|**Esc**| Window.ActivateDocumentWindow |
|Zavření okna dokumentu|**Ctrl+F4**| Window.CloseDocumentWindow |
|Okno Dalšího dokumentu|**Ctrl+F6**| Window.NextDocumentWindow |
|Navigace v okně dalšího dokumentu|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Další rozdělené podokno|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Globální klávesové zkratky

Tyto klávesové zkratky jsou *globální,* což znamená, že je můžete použít, když má Visual Studio okno fokus.

- [Analyzovat](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Upravit](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Projekt](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Architektura](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Místní nabídky editoru](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Project nabídky a místní nabídky řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Průzkumník testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Sestavení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [Soubor](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Refaktoring](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [Nástroje](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Zobrazení tříd místní nabídky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Nápověda](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Průzkumník řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Zobrazení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Ladění](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Zátěžový test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Team](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Okno](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Místní nabídky ladicího programu](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Další místní nabídky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Místní nabídky Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [Centrum diagnostiky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> Analyzovat

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přejít zpět|**Shift+Alt+3**| Analyze.NavigateBackward |
|Přejít vpřed|**Shift+Alt+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> Architektura

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nový diagram|**CTRL + \\ , CTRL + N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Budování

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Výběr sestavení|**Ctrl + B** (Visual Studio 2019)| Build. BuildSelection |
|Sestavit řešení|**Ctrl+Shift+B**| Build.BuildSolution |
|Zrušit|**Ctrl+Break**| Build.Cancel |
|Sestavení|**Ctrl+F7**| Build.Compile |
|Spustit analýzu kódu pro řešení|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Zobrazení tříd kontextové nabídky

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vlastnosti|**Alt+Enter**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Ladí

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Použít změny kódu|**Alt+F10**| Debug.ApplyCodeChanges |
|Připojit k procesu|**Ctrl+Alt+P**| Debug. AttachtoProcess |
|Automatické hodnoty|**Ctrl+Alt+V, A**| Debug.Autos |
|Přerušit vše|**Ctrl+Alt+Break**| Debug.BreakAll |
|Zarážky|**Ctrl+Alt+B**| Debug.Breakpoints |
|Zásobník volání|**Ctrl+Alt+C**| Debug.CallStack |
|Odstranit všechny zarážky|**CTRL + SHIFT + F9**| Debug.DeleteAllBreakpoints |
|Spuštění|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Zpětný překlad|**Ctrl+Alt+D**| Debug.Disassembly |
|Průzkumník modelu DOM|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Povolit zarážku|**Ctrl+F9**| Debug.EnableBreakpoint |
|Výjimky|**Ctrl+Alt+E**| Debug.Exceptions |
|Zarážka funkce|**Ctrl + K, B** (Visual Studio 2019)<br />**CTRL** + **B** (Visual Studio 2017)| Debug. FunctionBreakpoint |
|Přejít na předchozí volání nebo událost IntelliTrace|**Ctrl+Shift+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Spustit diagnostiku|**Alt+F5**| Debug.Graphics.StartDiagnostics |
|Projev|**Ctrl+Alt+I**| Debug.Immediate |
|Volání IntelliTrace|**Ctrl+Alt+Y, T**| Debug.IntelliTraceCalls |
|Události IntelliTrace|**Ctrl+Alt+Y, F**| Debug.IntelliTraceEvents |
|Konzola JavaScriptu|**Ctrl+Alt+V, C**| Debug.JavaScriptConsole |
|Místní obyvatelé|**Ctrl+Alt+V, L**| Debug.Locals |
|Process combo|**Ctrl+5**| Debug.LocationToolbar.ProcessCombo |
|Kombinovaný rámec zásobníku|**Ctrl+7**| Debug.LocationToolbar.StackFrameCombo |
|Kombinovaný seznam vláken|**Ctrl+6**| Debug.LocationToolbar.ThreadCombo |
|Přepnutí aktuálního stavu příznaku vlákna|**Ctrl+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Přepnout vlákna označená příznakem|**Ctrl+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Paměť 1|**Ctrl+Alt+M, 1**| Debug.Memory1 |
|Paměť 2|**Ctrl+Alt+M, 2**| Debug.Memory2 |
|Paměť 3|**Ctrl+Alt+M, 3**| Debug.Memory3 |
|Paměť 4|**Ctrl+Alt+M, 4**| Debug.Memory4 |
|Moduly|**Ctrl+Alt+U**| Debug.Modules |
|Paralelní zásobníky|**Ctrl+Shift+D, S**| Debug.ParallelStacks |
|Paralelní sledování 1|**Ctrl+Shift+D, 1**| Debug.ParallelWatch1 |
|Paralelní sledování 2|**Ctrl+Shift+D, 2**| Debug.ParallelWatch2 |
|Paralelní sledování 3|**Ctrl+Shift+D, 3**| Debug.ParallelWatch3 |
|Paralelní sledování 4|**Ctrl+Shift+D, 4**| Debug.ParallelWatch4 |
|Procesy|**Ctrl+Alt+Z**| Debug.Processes |
|Rychlé sledování|**Shift+F9** nebo **Ctrl+Alt+Q**| Debug.QuickWatch |
|Opětovné připojení k procesu|**Shift+Alt+P**| Debug.ReattachtoProcess |
|Aktualizace aplikace WindowsApp|**Ctrl+Shift+R**| Debug.RefreshWindowsapp |
|Registruje|**Ctrl+Alt+G**| Debug.Registers |
|Restartovat|**Ctrl+Shift+F5**| Debug.Restart |
|Spuštění na kurzor|**Ctrl+F10**| Debug.RunToCursor |
|Nastavení dalšího příkazu|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Zobrazení zásobníku volání na mapě kódu|**Ctrl+Shift+'**| Debug.ShowCallStackonCodeMap |
|Zobrazení dalšího příkazu|**Alt+Num** *| Debug.ShowNextStatement |
|Spustit|**F5**| Debug.Start |
|Spuštění analýzy aplikací pro Windows Phone|**Alt+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Spuštění bez ladění|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Krok do|**F11**| Debug.StepInto |
|Krokování s aktuálním procesem|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Krok do konkrétního nastavení|**Shift+Alt+F11**| Debug.StepIntoSpecific |
|Krok ven|**Shift + F11**| Debug.StepOut |
|Krok ven z aktuálního procesu|**Ctrl+Shift+Alt+F11**| Debug.StepOutCurrentProcess |
|Krokovat|**F10** (při ladění: provede krok po akci)| Debug.StepOver |
|Krokovat|**F10** (neladění: Spustí ladění a zastaví se na prvním řádku uživatelského kódu)| Debug.StepOver |
|Krokovat s aktuálním procesem|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Zastavit ladění|**Shift + F5**| Debug.StopDebugging |
|Zastavit analýzu výkonu|**Shift+Alt+F2**| Debug.StopPerformanceAnalysis |
|Úkoly|**Ctrl+Shift+D, K**| Debug.Tasks |
|Vlákna|**Ctrl+Alt+H**| Debug.Threads |
|Přepnout zarážku|**F9**| Debug.ToggleBreakpoint |
|Přepnout zpětný překlad|**Ctrl+F11**| Debug.ToggleDisassembly |
|Kukátko 1|**Ctrl+Alt+W, 1**| Debug.Watch1 |
|Kukátko 2|**CTRL + ALT + W, 2**| Debug.Watch2 |
|Kukátko 3|**CTRL + ALT + W, 3**| Debug.Watch3 |
|Kukátko 4|**CTRL + ALT + W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Kontextové nabídky ladicího programu

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Odstranit|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Přejít na zpětný překlad|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Přejít ke zdrojovému kódu|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Centrum diagnostiky

|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Zastavit shromažďování|**Ctrl+Alt+F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Úpravě

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Kopírovat|**Ctrl+C**<br /><br /> nebo<br /><br /> **Ctrl+Ins**| Edit.Copy |
|Vyjmout|**Ctrl+X**<br /><br /> nebo<br /><br /> **Shift+Delete**| Edit.Cut |
|Cykly ve schránce|**Ctrl+Shift+V**<br /><br /> nebo<br /><br /> **Ctrl+Shift+Ins**| Edit.CycleClipboardRing |
|Odstranit|**Odstranit**| Edit.Delete |
|Duplikovat|**Ctrl+D**| Upravit. duplicitní |
|Vyhledávání|**Ctrl+F**| Edit.Find |
|Najít všechny odkazy|**Shift+F12**| Edit.FindAllReferences |
|Najít v souborech|**Ctrl+Shift+F**| Edit.FindinFiles |
|Najít další|**F3**| Edit.FindNext |
|Najít vybrané další|**Ctrl+F3**| Edit.FindNextSelected |
|Najít předchozí|**SHIFT + F3**| Edit.FindPrevious |
|Najít předchozí vybranou|**Ctrl+Shift+F3**| Edit.FindPreviousSelected |
|Generování metody|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Přejít na|**Ctrl+G**| Edit.GoTo |
|Přejít na vše|**CTRL +,** nebo **CTRL + T**| Upravit. GoToAll |
|Přejít k deklaraci|**Ctrl+F12**| Edit.GoToDeclaration |
|Přejít k definici|**F12**| Edit.GoToDefinition |
|Přejít na člena|**CTRL + 1, CTRL + M** nebo **CTRL + 1, M** nebo **ALT + \\**| Upravit. GoToMember |
|Přejít na další umístění|**F8** (Další chyba v seznam chyb nebo okně výstup)| Edit.GoToNextLocation |
|Přejít na předchozí umístění|**Shift + F8** (předchozí chyba v okně Seznam chyb nebo výstupu)| Edit.GoToPrevLocation |
|Vložit fragment|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Přesunout ovládání dolů|**Ctrl + šipka dolů**| Edit.MoveControlDown |
|Přesunout ovládání v mřížce dolů|**Šipka dolů**| Edit.MoveControlDownGrid |
|Přesunout ovládání doleva|**Ctrl + šipka doleva**| Edit.MoveControlLeft |
|Přesunout ovládání v mřížce vlevo|**Šipka doleva**| Edit.MoveControlLeftGrid |
|Přesunout ovládání Doprava|**Ctrl + šipka doprava**| Edit.MoveControlRight |
|Přesunout ovládání v mřížce doprava|**Šipka doprava**| Edit.MoveControlRightGrid |
|Přesunout ovládání nahoru|**Ctrl + šipka nahoru**| Edit.MoveControlUp |
|Přesunout ovládání v mřížce nahoru|**Šipka nahoru**| Edit.MoveControlUpGrid |
|Další záložka|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Další záložka ve složce|**Ctrl+Shift+K, Ctrl+Shift+N**| Edit.NextBookmarkInFolder |
|Otevřít soubor|**CTRL + SHIFT + G** (otevře se název souboru pod kurzorem)| Edit.OpenFile |
|Vložit|**Ctrl+V**<br /><br /> nebo<br /><br /> **Shift+Ins**| Edit.Paste |
|Předchozí záložka|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Předchozí záložka ve složce|**Ctrl+Shift+K, Ctrl+Shift+P**| Edit.PreviousBookmarkInFolder |
|Rychlé hledání – symbol|**Shift+Alt+F12**| Edit.QuickFindSymbol |
|Opakovat|**Ctrl+Y**<br /><br /> nebo<br /><br /> **Ctrl+Shift+Z**<br /><br /> nebo<br /><br /> **Shift+Alt+Backspace**| Edit.Redo |
|Aktualizovat vzdálené odkazy|**Ctrl+Shift+J**| Edit.RefreshRemoteReferences |
|Nahrazení|**Ctrl+H**| Edit.Replace |
|Nahradit v souborech|**Ctrl+Shift+H**| Edit.ReplaceinFiles |
|Vybrat vše|**Ctrl+A**| Edit.SelectAll |
|Výběr dalšího ovládacího prvku|**Tab**| Edit.SelectNextControl |
|Vybrat předchozí ovládací prvek|**Shift+Tab**| Edit.SelectPreviousControl |
|Zobrazit mřížku dlaždic|**Enter**| Edit.ShowTileGrid |
|Velikost ovládání dolů|**Ctrl + Shift + šipka dolů**| Edit.SizeControlDown |
|Velikost ovládání v mřížce dolů|**Shift + šipka dolů**| Edit.SizeControlDownGrid |
|Velikost ovládání doleva|**Ctrl + Shift + šipka doleva**| Edit.SizeControlLeft |
|Velikost ovládání v mřížce vlevo|**Shift + šipka doleva**| Edit.SizeControlLeftGrid |
|Velikost ovládacího prvku vpravo|**Ctrl + Shift + šipka doprava**| Edit.SizeControlRight |
|Velikost ovládání v mřížce doprava|**Shift + šipka doprava**| Edit.SizeControlRightGrid |
|Velikost ovládání nahoru|**Ctrl + Shift + šipka nahoru**| Edit.SizeControlUp |
|Velikost ovládání v mřížce nahoru|**Shift + šipka nahoru**| Edit.SizeControlUpGrid |
|Zastavit hledání|**Alt+F3, S**| Edit.StopSearch |
|Obklopit|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Zpět|**Ctrl+Z**<br /><br /> nebo<br /><br /> **Alt+Backspace**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Místní nabídky editoru

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Podmínky zarážky|**ALT + F9, C**| EditorContextMenus. CodeWindow. breakpoint. BreakpointConditions |
|Upravit popisky zarážek|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Zobrazit položku|**CTRL + '**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Spuštěním|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Přejít na zobrazení|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Přepnout soubor kódu záhlaví|**CTRL + K, CTRL + O** (Letter ' O ')| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Zobrazit hierarchii volání|**Ctrl+K, Ctrl+T**<br /><br /> nebo<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Souborů

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Ukončit|**Alt+F4**| File.Exit |
|Nový soubor|**Ctrl+N**| File.NewFile |
|Nový projekt|**Ctrl+Shift+N**| File.NewProject |
|Nový web|**Shift+Alt+N**| File.NewWebSite |
|Otevřít soubor|**CTRL + O** (Letter ' O ')| File.OpenFile |
|Otevřený projekt|**CTRL + SHIFT + O** (Letter ' O ')| File.OpenProject |
|Otevřít web|**Shift+Alt+O** (písmeno 'O')| File.OpenWebSite |
|Tisk|**Ctrl+P**| File.Print |
|Uložit vše|**Ctrl+Shift+S**| File.SaveAll |
|Uložení vybraných položek|**Ctrl+S**| File.SaveSelectedItems |
|Zobrazení v prohlížeči|**Ctrl+Shift+W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Pomoc

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přidání a odebrání obsahu nápovědy|**Ctrl+Alt+F1**| Help.AddandRemoveHelpContent |
|Nápověda k F1|**F1**| Help.F1Help |
|Zobrazení nápovědy|**Ctrl+F1**| Help.ViewHelp |
|Nápověda k oknu|**Shift+F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Zátěžový test

|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Přejít do podokna čítačů|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Další místní nabídky

|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Přidání nového diagramu|**Insert**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Projekt

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přidání existující položky|**Shift+Alt+A**| Project.AddExistingItem |
|Přidání nové položky|**Ctrl+Shift+A**| Project.AddNewItem |
|Průvodce třídou|**Ctrl+Shift+X**| Project.ClassWizard |
|Přepis|**Ctrl+Alt+Ins**| Project.Override |
|Náhled změn|**Alt+;** potom **Alt+C**| Project.Previewchanges |
|Publikování vybraných souborů|**Alt+;** pak **Alt+P**| Project.Publishselectedfiles |
|Nahrazení vybraných souborů ze serveru|**Alt+;** pak **Alt+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a>Project a místní nabídky řešení

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přesunout dolů|**Alt + šipka dolů**| ProjectandSolutionContextMenus.Item.MoveDown |
|Přesunout nahoru|**Alt + šipka nahoru**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Refaktoring

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zapouzdření pole|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Extrahování rozhraní|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Extrahování metody|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Odebrání parametrů|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|přejmenování|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Změna pořadí parametrů|**Ctrl+R, Ctrl+O** (písmeno 'O')| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Průzkumník řešení

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Filtr Otevřít soubory|**Ctrl+[**, **O** (písmeno 'O')<br /><br /> nebo<br /><br /> **Ctrl+[**, **Ctrl+O** (písmeno 'O')| SolutionExplorer.OpenFilesFilter |
|Filtr čekajících změn|**Ctrl+[**, **P**<br /><br /> nebo<br /><br /> **Ctrl+[**, **Ctrl+P**| SolutionExplorer.PendingChangesFilter |
|Synchronizace s aktivním dokumentem|**Ctrl+[**, **S**<br /><br /> nebo<br /><br /> **Ctrl+[**, **Ctrl+S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> Tým

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přejít na větve Gitu|**Ctrl+0** (nula), **Ctrl+N**<br /><br /> nebo<br /><br /> **Ctrl+0, N**| Team.Git.GoToGitBranches |
|Přejít na změny gitu|**Ctrl+0** (nula), **Ctrl+G**<br /><br /> nebo<br /><br /> **Ctrl+0, G**| Team.Git.GoToGitChanges |
|Přejít na potvrzení gitu|**Ctrl+0** (nula), **Ctrl+O** (písmeno "O")<br /><br /> nebo<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Hledání v Team Exploreru|**Ctrl+'**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Místní nabídky Team Foundation

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přejít na sestavení|**Ctrl+0** (nula), **Ctrl+B**<br /><br /> nebo<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Přejít k připojení|**Ctrl+0** (nula), **Ctrl+C**<br /><br /> nebo<br /><br /> **Ctrl+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Přejít na dokumenty|**Ctrl+0** (nula), **Ctrl+D**<br /><br /> nebo<br /><br /> **Ctrl+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Přejít na domovskou obrazovku|**Ctrl+0** (nula), **Ctrl+H**<br /><br /> nebo<br /><br /> **Ctrl+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Přejít do práce|**Ctrl+0** (nula), **Ctrl+M**<br /><br /> nebo<br /><br /> **Ctrl+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Přejít k čekajícím změnám|**Ctrl+0** (nula), **Ctrl+P**<br /><br /> nebo<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Přejít na sestavy|**Ctrl+0** (nula), **Ctrl+R**<br /><br /> nebo<br /><br /> **Ctrl+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Přejděte do nastavení.|**Ctrl+0** (nula), **Ctrl+S**<br /><br /> nebo<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Přejít na webový přístup|**Ctrl+0** (nula), **Ctrl+A**<br /><br /> nebo<br /><br /> **Ctrl+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|Přejít k pracovním položkám|**Ctrl+0** (nula), **Ctrl+W**<br /><br /> nebo<br /><br /> **Ctrl+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> Test

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Použití tvůrce programových testů uživatelského rozhraní|**Ctrl+ \\ , Ctrl+C**| Test.UseCodedUITestBuilder |
|Použití existujícího záznamu akce|**Ctrl+ \\ , Ctrl+A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Průzkumník testů

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Ladění všech testů|**Ctrl+R, Ctrl+A**| TestExplorer.DebugAllTests |
|Ladění všech testů v kontextu|**Ctrl+R, Ctrl+T**| TestExplorer.DebugAllTestsInContext |
|Ladění posledního spuštění|**Ctrl+R, D**| TestExplorer.DebugLastRun |
|Opakujte poslední spuštění.|**Ctrl+R, L**| TestExplorer.RepeatLastRun |
|Spuštění všech testů|**Ctrl+R, A**| TestExplorer.RunAllTests |
|Spuštění všech testů v kontextu|**Ctrl+R, T**| TestExplorer.RunAllTestsInContext |
|Zobrazení průzkumníka testů|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |
|Otevření karty|**Ctrl+E, L**| LiveUnitTesting.OpenTab |
|Výsledky pokrytí kódu|**Ctrl+E, C**| Test.CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> Nástroje

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Připojení k procesu|**Ctrl+Alt+P**| Tools.AttachtoProcess |
|Správce fragmentů kódu|**Ctrl+K, Ctrl+B**| Tools.CodeSnippetsManager |
|Vynutit uvolňování paměti|**Ctrl+Shift+Alt+F12, Ctrl+Shift+Alt+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> Prohlédni

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Všechna okna|**Shift+Alt+M**| View.AllWindows |
|Průzkumník architektury|**Ctrl+ \\ , Ctrl+R**| View.ArchitectureExplorer |
|dál|**Alt + šipka doleva** (funkce se liší od View.NavigateBackward v textovém editoru)| View.Backward |
|Okno záložky|**Ctrl+K, Ctrl+W**| View.BookmarkWindow |
|Další procházení|**Ctrl+Shift+1**| View.BrowseNext |
|Procházet předchozí|**Ctrl+Shift+2**| View.BrowsePrevious |
|Hierarchie volání|**Ctrl+Alt+K**| View.CallHierarchy |
|Zobrazení třídy|**Ctrl+Shift+C**| View.ClassView |
|Zobrazení třídy – přejít na hledaný seznam|**Ctrl+K, Ctrl+V**| View.ClassViewGoToSearchCombo |
|Okno definice kódu|**Ctrl+ \\ , D**<br /><br /> nebo<br /><br /> **Ctrl+ \\ , Ctrl+D**| View.CodeDefinitionWindow |
|Okno Příkaz|**Ctrl+Alt+A**| View.CommandWindow |
|Zdroje dat|**Shift+Alt+D**| View.DataSources |
|Osnova dokumentu|**Ctrl+Alt+T**| View.DocumentOutline |
|Upravit popisek|**F2**| View.EditLabel |
|Seznam chyb|**Ctrl+ \\ , E**<br /><br /> nebo<br /><br /> **CTRL + \\ , CTRL + E**| View.ErrorList |
|interaktivní pro jazyk F#|**Ctrl+Alt+F**| View.F#Interactive |
|Výsledky hledání symbolů|**Ctrl+Alt+F12**| View.FindSymbolResults |
|Forward|**ALT + šipka doprava**  (funguje jinak než zobrazení. NavigateForward v textovém editoru)| View.Forward |
|Kontext předávaného procházení|**Ctrl+Shift+7**| View.ForwardBrowseContext |
|Celá obrazovka|**Shift+Alt+Enter**| View.FullScreen |
|Přejít zpět|**CTRL +-**| View.NavigateBackward |
|Přejít vpřed|**CTRL + SHIFT +-**| View.NavigateForward |
|Další chyba|**Ctrl+Shift+F12**| View.NextError |
|Oznámení|**Ctrl+W, N**<br /><br /> nebo<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Prohlížeč objektů|**Ctrl+Alt+J**| View.ObjectBrowser |
|Prohlížeč objektů – přejít na vyhledávací pole se seznamem|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Výstup|**CTRL + ALT + O** (Letter ' O ')| View.Output |
|Místní kontext procházení|**CTRL + SHIFT + 8** (pouze C++)| Zobrazit. PopBrowseContext |
|Vlastnosti – okno|**F4**| View.PropertiesWindow |
|Stránky vlastností|**Shift+F4**| View.PropertyPages |
|Zobrazení prostředků|**Ctrl+Shift+E**| View.ResourceView |
|Průzkumník serveru|**Ctrl+Alt+S**| View.ServerExplorer |
|Zobrazit inteligentní značku|**Shift+Alt+F10**<br /><br /> nebo<br /><br /> **CTRL +.**| View.ShowSmartTag |
|Průzkumník řešení|**Ctrl+Alt+L**| View.SolutionExplorer |
|průzkumník objektů SQL serveru|**CTRL + \\ , CTRL + S**| View.SQLServerObjectExplorer |
|Seznam úkolů|**CTRL + \\ , T**<br /><br /> nebo<br /><br /> **CTRL + \\ , CTRL + T**| View.TaskList |
|Team Explorer TFS|**CTRL + \\ , CTRL + M**| View.TfsTeamExplorer |
|Sada nástrojů|**Ctrl+Alt+X**| View.Toolbox |
|Průzkumník modelů UML|**CTRL + \\ , CTRL + U**| View.UMLModelExplorer |
|Zobrazit kód|**F7**| View.ViewCode |
|Návrhář zobrazení|**Shift+F7**| View.ViewDesigner |
|Webový prohlížeč|**Ctrl+Alt+R**| View.WebBrowser |
|Přiblížit|**CTRL + SHIFT +.**| View.ZoomIn |
|Oddálit|**CTRL + SHIFT +,**| View.ZoomOut |
|Zobrazit Průzkumníka testů|**CTRL + E, T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> Okno

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Aktivovat okno dokumentu|**Esc**| Window.ActivateDocumentWindow |
|Přidat kartu k výběru|**Ctrl + Shift + Alt + mezerník**| Window.AddTabtoSelection |
|Zavřít okno dokumentu|**Ctrl+F4**| Window.CloseDocumentWindow |
|Zavřít okno nástroje|**Shift+Esc**| Window.CloseToolWindow |
|Ponechat otevřenou kartu|**Ctrl+Alt+Home**| Window.KeepTabOpen |
|Přesunout na navigační panel|**Ctrl+F2**| Window.MovetoNavigationBar |
|Další okno dokumentu|**Ctrl+F6**| Window.NextDocumentWindow |
|Další navigační okno dokumentu|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Další podokno|**Alt+F6**| Window.NextPane |
|Další rozdělené podokno|**F6**| Window.NextSplitPane |
|Další karta|**Ctrl+Alt+PgDn**<br /><br /> nebo<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Další karta a přidat k výběru|**Ctrl+Shift+Alt+PgDn**| Window.NextTabandAddtoSelection |
|Další nástroj navigace okna|**Alt+F7**| Window.NextToolWindowNav |
|Předchozí okno dokumentu|**Ctrl+Shift+F6**| Window.PreviousDocumentWindow |
|Předchozí dokument navigace okna|**CTRL + SHIFT + TAB**| Window.PreviousDocumentWindowNav |
|Předchozí podokno|**Shift+Alt+F6**| Window.PreviousPane |
|Předchozí rozdělené podokno|**Shift+F6**| Window.PreviousSplitPane |
|Předchozí karta|**Ctrl+Alt+PgUp**<br /><br /> nebo<br /><br /> **Ctrl+PgUp**| Window.PreviousTab |
|Předchozí karta a přidat k výběru|**Ctrl+Shift+Alt+PgUp**| Window.PreviousTabandAddtoSelection |
|Předchozí nástroj navigace okna|**Shift+Alt+F7**| Window.PreviousToolWindowNav |
|Snadné spuštění|**Ctrl+Q**| Window.QuickLaunch |
|Rychlé spuštění předchozí kategorie|**Ctrl+Shift+Q**| Window.QuickLaunchPreviousCategory |
|Zobrazit ukotvenou nabídku|**ALT + –**| Window.ShowDockMenu |
|Zobrazit seznam souborů na bázi MDI|**Ctrl + Alt + šipka dolů**| Window.ShowEzMDIFileList |
|Hledání v Průzkumníkovi řešení|**CTRL +;**| Window.SolutionExplorerSearch |
|Hledání oken|**ALT + '**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Azure

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Opakovat operaci skriptu mobilní služby|**CTRL + NUM \* , CTRL + R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Zobrazit podrobnosti o chybě skriptu mobilní služby|**CTRL + NUM \* , CTRL + D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>Zkratky specifické pro kontext


### <a name="adonet-entity-data-model-designer"></a>ADO.NET Entity Data Model Designer

Klávesové zkratky, které jsou specifické pro tento kontext:

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Dolů|**Alt + šipka dolů**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Dolů 5|**Alt+PgDn**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Dospod|**Alt+End**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Navrch|**Alt+Home**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Nahoru|**Alt + šipka nahoru**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|Až 5|**Alt+PgUp**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|přejmenování|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Odebrat z diagramu|**Shift+Del**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Prohlížeč modelu entity|**Ctrl+1**| View.EntityDataModelBrowser |
|Podrobnosti o mapování modelu dat entit|**Ctrl+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Diagram tříd

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Sbalit|**Num -**| ClassDiagram.Collapse |
|Rozbalit|**Num +**| ClassDiagram.Expand |
|Odstranit|**Ctrl+Del**| Edit.Delete |
|Rozbalení seznamu sbalení základního typu|**Shift+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Přejděte na lollipop.|**Shift+Alt+L**| Edit.NavigateToLollipop |
|Odebrat z diagramu|**Odstranit**| Edit.RemovefromDiagram |
|Zobrazení kódu|**Enter**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Editor programového testu UI

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Kopírování odkazu do schránky|**Ctrl+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Vložení zpoždění před|**Ctrl+Alt+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Najít vše|**Shift+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Vyhledání ovládacího prvku uživatelského rozhraní|**Ctrl+Shift+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Přesunutí kódu|**Ctrl+Alt+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Rozdělení na novou metodu|**Ctrl+Shift+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Editor DataSet

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vložení sloupce|**Insert**| OtherContextMenus.ColumnContext.InsertColumn |
|Sloupec|**Ctrl+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Prohlížeč rozdílů

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Ignorovat prázdné znaky pro oříznutí|**Ctrl+ \\ , Ctrl + mezerník**| Diff.IgnoreTrimWhitespace |
|Vložené zobrazení|**Ctrl+ \\ , Ctrl+1**| Diff.InlineView |
|Zobrazení pouze vlevo|**Ctrl+ \\ , Ctrl+3**| Diff.LeftOnlyView |
|Další rozdíl|**F8**| Diff.NextDifference |
|Předchozí rozdíl|**Shift+F8**| Diff.PreviousDifference |
|Zobrazení pouze vpravo|**Ctrl+ \\ , Ctrl+4**| Diff.RightOnlyView |
|Zobrazení vedle sebe|**Ctrl+ \\ , Ctrl+2**| Diff.SideBySideView |
|Přepínání mezi levou a pravou doleva|**\\Ctrl+, Ctrl+Tab**| Diff.SwitchBetweenLeftAndRight |
|Synchronizovat přepínač zobrazení|**Ctrl+ \\ , Ctrl + šipka dolů**| Diff.SynchronizeViewToggle |
|Přidání komentáře|**Ctrl+Shift+K**| EditorContextMenus.CodeWindow.AddComment |
|Úprava místního souboru|**Ctrl+Shift+P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>Průzkumník modelu DOM

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Aktualizovat|**F5**| DOMExplorer.Refresh |
|Výběr elementu|**Ctrl+B**| DOMExplorer.SelectElement |
|Zobrazení rozložení|**Ctrl+Shift+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>interaktivní pro jazyk F#

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Zrušení interaktivního vyhodnocení|**Ctrl+Break**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Editor dokumentu grafu

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přidání uzlu|**Insert**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Obě závislosti|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Příchozí závislosti|**I**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Odchozí závislosti|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Nový komentář|**Ctrl+Shift+K**<br /><br /> nebo<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Odebrat|**Odstranit**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|přejmenování|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Diagnostika grafiky

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Snímek snímku|Žádná| Debug.Graphics.CaptureFrame |
|Přesunutí výběru pixelů dolů|**Shift +Alt + šipka dolů**| Graphics.MovePixelSelectionDown |
|Přesunutí výběru pixelů doleva|**Shift + Alt + šipka doleva**| Graphics.MovePixelSelectionLeft |
|Přesunutí výběru pixelů doprava|**Shift + Alt + šipka doprava**| Graphics.MovePixelSelectionRight |
|Přesunutí výběru pixelů nahoru|**Shift + Alt + šipka nahoru**| Graphics.MovePixelSelectionUp |
|Zvětšení skutečné velikosti|**Shift+Alt+0** (nula)| Graphics.ZoomToActualSize |
|Přiblížení, aby se vešel do okna|**Shift+Alt+9**| Graphics.ZoomToFitInWindow |
|Přiblížit|**Shift+Alt+=**| Graphics.ZoomIn |
|Oddálit|**Shift+Alt+-**| Graphics.ZoomOut |

### <a name="html-editor"></a>Editor HTML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Přejít na kontroler|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>Zobrazení návrhu editoru HTML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přesunutí ovládacího prvku dolů|**Ctrl + šipka dolů**| Edit.MoveControlDown |
|Přesunutí ovládacího prvku nahoru|**Ctrl + šipka nahoru**| Edit.MoveControlUp |
|Bold|**Ctrl+B**| Format.Bold |
|Převést na hypertextový odkaz|**Ctrl+L**| Format.ConverttoHyperlink |
|Vložení záložky|**Ctrl+Shift+L**| Format.InsertBookmark |
|Kurzíva|**Ctrl+I**| Format.Italic |
|Podtržení|**Ctrl+U**| Format.Underline |
|Stránka Přidat obsah|**Ctrl+M, Ctrl+C**| Project.AddContentPage |
|Sloupec nalevo|**Ctrl + Alt + šipka doleva**| Table.ColumntotheLeft |
|Sloupec napravo|**Ctrl + Alt + šipka doprava**| Table.ColumntotheRight |
|Řádek výše|**Ctrl+Alt + šipka nahoru**| Table.RowAbove |
|Řádek níže|**Ctrl + Alt + šipka dolů**| Table.RowBelow |
|Net nonvisual controls|**Ctrl+Shift+N**| View.ASP.NETNonvisualControls |
|Úprava hlavního serveru|**Ctrl+M, Ctrl+M**| View.EditMaster |
|Další zobrazení|**Ctrl+PgDn**| View.NextView |
|Zobrazení inteligentní značky|**Shift+Alt+F10**| View.ShowSmartTag |
|Zobrazení kódu|**Shift+F7**| View.ViewMarkup |
|Předchozí karta|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>Zobrazení zdroje editoru HTML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přejít na kontroler|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|Další zobrazení|**Ctrl+PgDn**| View.NextView |
|Synchronizace zobrazení|**Ctrl+Shift+Y**| View.SynchronizeViews |
|Návrhář zobrazení|**Shift+F7**| View.ViewDesigner |
|Předchozí karta|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="layer-diagram"></a>Diagram vrstev

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit|**Shift+Delete**| Edit.Delete |

### <a name="managed-resources-editor"></a>Editor spravovaných prostředků

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Upravit buňku|**F2**| Edit.EditCell |
|Odebrat|**Odstranit**| Edit.Remove |
|Odebrání řádku|**Ctrl+Delete**| Edit.RemoveRow |
|Zrušení výběru|**Escape**| Edit.SelectionCancel |
|Zvuk|**Ctrl+4**| Resources.Audio |
|Soubory|**Ctrl+5**| Resources.Files |
|Ikony|**Ctrl+3**| Resources.Icons |
|Obrázky|**Ctrl+2**| Resources.Images |
|Jiné|**Ctrl+6**| Resources.Other |
|Řetězce|**Ctrl+1**| Resources.Strings |

### <a name="merge-editor-window"></a>Okno Sloučit editor

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nastavení fokusu na levém okně|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Nastavení fokusu na okně výsledků|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Nastavení fokusu na pravém okně|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Datové nástroje Microsoft SQL Server, porovnání schématu

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Porovnání schématu SSDT|**Shift+Alt+C**| SQL.SSDTSchemaCompareCompare |
|Porovnání generování skriptu ve schématu SSDT|**Shift+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|Porovnání schématu SSDT s další změnou|**Shift +Alt+.**| SQL.SSDTSchemaCompareNextChange |
|Porovnání schématu SSDT s předchozí změnou|**Shift+Alt+,**| SQL.SSDTSchemaComparePreviousChange |
|Zastavení porovnání schématu SSDT|**Alt+Break**| SQL.SSDTSchemaCompareStop |
|Porovnání aktualizací zápisu ve schématu SSDT|**Shift+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Datové nástroje Microsoft SQL Server, návrhář tabulky

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Rozbalení zástupných znaků|**Ctrl+R, E**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Plně kvalifikované názvy|**Ctrl+R, Q**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Přechod na schéma|**Ctrl+R, M**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|přejmenování|**F2**<br /><br /> nebo<br /><br /> **Ctrl+R, R**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Shift+Alt+PgDn**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Datové nástroje Microsoft SQL Server, editor T-SQL

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Spuštění s ladicím programem|**Alt+F5**| SQL.ExecuteWithDebugger |
|Rozbalení zástupných znaků|**Ctrl+R, E**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Plně kvalifikované názvy|**Ctrl+R, Q**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Přechod na schéma|**Ctrl+R, M**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|přejmenování|**F2**<br /><br /> nebo<br /><br /> **Ctrl+R, R**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|Zrušení SQL editoru T|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|Spuštění SQL editoru T|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|Výsledky SQL editoru T jako soubor|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|Výsledky SQL editoru jako mřížky|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|Výsledky SQL editoru T jako text|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|V SQL editoru se zobrazí odhadovaný plán|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Přepnutí SQL provádění v editoru|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Přepínací SQL výsledků v editoru|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|Dotaz SQL klonování editoru|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|Seznam databází SQL editoru T|**Shift+Alt+PgDn**|SQL. TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Datové nástroje Microsoft SQL Server, editor T-SQL PDW

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zrušení SQL editoru T|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|Spuštění SQL editoru T|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|Výsledky SQL editoru T jako soubor|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|Výsledky SQL editoru jako mřížky|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|Výsledky SQL editoru T jako text|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|V SQL editoru se zobrazí odhadovaný plán|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Přepnutí SQL provádění v editoru|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Přepínací SQL výsledků v editoru|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|Dotaz SQL klonování editoru|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|Dotaz SQL klonování editoru|**Shift+Alt+PgDn**|SQL. TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Inspektor stránek

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Minimalizovat|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Návrhář dotazu

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zrušení načítání dat|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Kritéria|**Ctrl+2**| QueryDesigner.Criteria |
|Diagram|**Ctrl+1**| QueryDesigner.Diagram |
|Spuštění SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Goto row|**Ctrl+G**| QueryDesigner.GotoRow |
|Režim spojení|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Výsledky|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="query-results"></a>Výsledky dotazu

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nový řádek výsledků dotazu|**Alt+End**| SQL.QueryResultsNewRow |
|Aktualizace výsledků dotazu|**Shift+Alt+R**| SQL.QueryResultsRefresh |
|Zastavení výsledků dotazu|**Alt+Break**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Návrhář sestav

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zalomení řádku|**Enter**| Edit.BreakLine |
|Znak vlevo|**Šipka doleva**| Edit.CharLeft |
|Znak s levým rozšířením|**Shift + šipka doleva**| Edit.CharLeftExtend |
|Znak vpravo|**Šipka doprava**| Edit.CharRight |
|Rozšíření zprava znaků|**Shift + šipka doprava**| Edit.CharRightExtend |
|Karta Vložit|**Tab**| Edit.InsertTab |
|Řádek dolů|**Šipka dolů**| Edit.LineDown |
|Rozšíření o řádek dolů|**Shift + šipka dolů**| Edit.LineDownExtend |
|Sesou řádek nahoru|**Šipka nahoru**| Edit.LineUp |
|Rozšíření o řádek nahoru|**Shift + šipka nahoru**| Edit.LineUpExtend |
|Přesunutí ovládacího prvku dolů|**Ctrl + šipka dolů**| Edit.MoveControlDown |
|Přesunutí ovládacího prvku doleva|**Ctrl + šipka doleva**| Edit.MoveControlLeft |
|Přesunutí ovládacího prvku doprava|**Ctrl + šipka doprava**| Edit.MoveControlRight |
|Přesunout ovládání nahoru|**Ctrl + šipka nahoru**| Edit.MoveControlUp |
|Zrušit výběr|**Esc**| Edit.SelectionCancel |
|Velikost ovládání dolů|**Ctrl + Shift + šipka dolů**| Edit.SizeControlDown |
|Velikost ovládání doleva|**Ctrl + Shift + šipka doleva**| Edit.SizeControlLeft |
|Velikost ovládacího prvku vpravo|**Ctrl + Shift + šipka doprava**| Edit.SizeControlRight |
|Velikost ovládání nahoru|**Ctrl + Shift + šipka nahoru**| Edit.SizeControlUp |
|Tab doleva|**Shift+Tab**| Edit.TabLeft |
| Data sestavy|**Ctrl+Alt+D**| View.ReportData |

### <a name="sequence-diagram"></a>Sekvenční diagram

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přejít ke kódu|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Odstranit|**Shift+Del**| Edit.Delete |

### <a name="settings-designer"></a>Návrhář nastavení

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Upravit buňku|**F2**| Edit.EditCell |
|Odebrat řádek|**Ctrl+Delete**| Edit.RemoveRow |
|Zrušit výběr|**Esc**| Edit.SelectionCancel |
|Zobrazit kód|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>Průzkumník řešení

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Zobrazit v inspektoru stránky|**Ctrl+K, Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Team Explorer

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit|**Odstranit**| Edit.Delete |
|přejmenování|**F2**| File.Rename |
|Přejít na navigaci v Průzkumníkovi týmových souborů|**Alt+Home**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Přejít na obsah dalšího oddílu v Team Exploreru|**Alt + šipka dolů**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Přejít na obsah stránky v Team Exploreru|**ALT + 0** (nula)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Přejít na obsah předchozího oddílu v Team Exploreru|**Alt + šipka nahoru**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Přejít na obsah oddílu 1 v Team Exploreru|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Přejít na obsah oddílu 2 v Team Exploreru|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Přejít na obsah oddílu 3 v Team Exploreru|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Přejít na obsah oddílu 4 v Team Exploreru|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Přejít na obsah oddílu 5 v Team Exploreru|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Přejít na obsah oddílu 6 v Team Exploreru|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Přejít na obsah oddílu 7 v Team Exploreru|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Přejít na obsah oddílu 8 v Team Exploreru|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Přejít na obsah oddílu 9 v Team Exploreru|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Průzkumník týmových témat – zpět|**Alt + šipka doleva**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Průzkumník týmových témat – vpřed|**Alt + šipka doprava**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Stránka TFS kontext má práce vytvořit kopii Wi|**Shift+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Stránka TFS kontext má práce nové propojení Wi|**Shift+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Aktualizovat|**F5**| View.Refresh |

### <a name="test-explorer"></a>Průzkumník testů

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Otevřít test|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Textový editor

Klávesové zkratky, které jsou specifické pro tento kontext:


| Příkazy | Klávesové zkratky |ID příkazu|
|-|-|-|
|Oddělovací čára| **Enter**<br /><br /> nebo<br /><br /> **Shift+Enter** | Edit.BreakLine |
|Znak doleva| **Šipka doleva** | Edit.CharLeft |
|Znak – doleva – zvětšit| **Shift + šipka doleva** | Edit.CharLeftExtend |
|Znak – zvětšit sloupec vlevo| **Shift + Alt + šipka doleva** | Edit.CharLeftExtendColumn |
|Znak doprava| **Šipka doprava** | Edit.CharRight |
|Znak doprava – zvětšit| **Shift + šipka doprava** | Edit.CharRightExtend |
|Znak doprava – zvětšit sloupec| **Shift + Alt + šipka doprava** | Edit.CharRightExtendColumn |
|Vymazat záložky| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Sbalit všechny sbalené| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Sbalit aktuální oblast| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Sbalit značku| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Sbalit do definic| **CTRL + M, CTRL + O** (Letter ' O ') | Upravit. CollapseToDefinitions |
|Výběr kontraktu| **Shift + Alt +-** | Upravit. ContractSelection |
|Výběr komentáře| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Dokončit slovo| **Ctrl + mezerník**<br /><br /> nebo<br /><br /> **Alt + šipka doprava** | Edit.CompleteWord |
|Kopírovat Tip parametru| **Ctrl+Shift+Alt+C** | Edit.CopyParameterTip |
|Snížit úroveň filtru| **Alt+,** | Edit.DecreaseFilterLevel |
|Odstranit zpět| **Backspace**<br /><br /> nebo<br /><br /> **Shift+Bkspce** | Edit.DeleteBackwards |
|Odstranit vodorovné prázdné znaky| **CTRL + K, CTRL +\\** | Edit.DeleteHorizontalWhiteSpace |
|Konec dokumentu| **Ctrl+End** | Edit.DocumentEnd |
|Konec dokumentu – zvětšit| **Ctrl+Shift+End** | Edit.DocumentEndExtend |
|Začátek dokumentu| **Ctrl+Home** | Edit.DocumentStart |
|Začátek dokumentu – zvětšit| **Ctrl+Shift+Home** | Edit.DocumentStartExtend |
|Rozbalit všechny osnovy| **Ctrl+M, Ctrl+X** | Edit.ExpandAllOutlining |
|Rozbalit aktuální oblast| **Ctrl+M, Ctrl+E** | Edit.ExpandCurrentRegion |
|Rozšíření výběru| **Shift + Alt + =** | Upravit. ExpandSelection |
|Rozšířit výběr na obsahující blok| **SHIFT + ALT +]** | Upravit. ExpandSelectiontoContainingBlock |
|Formátování dokumentu| **Ctrl+K, Ctrl+D** | Edit.FormatDocument |
|Formátování výběru| **Ctrl+K, Ctrl+F** | Edit.FormatSelection |
|Přejít vše| **Ctrl+T**<br /><br /> nebo<br /><br /> **CTRL +,** | Upravit. GotoAll |
|Přejít na závorku| **CTRL +]** | Edit.GotoBrace |
|Přejít na závorku – zvětšit| **CTRL + SHIFT +]** | Edit.GotoBraceExtend |
|Přejít na poslední| **CTRL + T, R** | Upravit. GotoRecent |
|Přejít na další problém v souboru| **Alt+PgDn** | Upravit. GotoNextIssueinFile |
|Přejít na předchozí problém v souboru| **Alt+PgUp** | Upravit. GotoPreviousIssueinFile |
|Skrýt výběr| **Ctrl+M, Ctrl+H** | Edit.HideSelection |
|Zvýšit úroveň filtru| **ALT +.** | Edit.IncreaseFilterLevel |
|Přírůstkové vyhledávání| **Ctrl+I** | Edit.IncrementalSearch |
|Vložit blikající kurzory na všechny vyhovující| **Shift + Alt +;** | Upravit. InsertCaretsatAllMatching |
|Vložit další vyhovující blikající kurzor| **Shift + Alt +.** | Upravit. InsertNextMatchingCaret |
|Karta Vložit| **Tab** | Edit.InsertTab |
|Vyjmutí řádku| **Ctrl+L** | Edit.LineCut |
|Odstranění řádku| **Ctrl+Shift+L** | Edit.LineDelete |
|Řádek dolů| **Šipka dolů** | Edit.LineDown |
|Řádek dolů – zvětšit| **Shift + šipka dolů** | Edit.LineDownExtend |
|Řádek dolů – zvětšit sloupec| **Shift +Alt + šipka dolů** | Edit.LineDownExtendColumn |
|Konec řádku| **End** | Edit.LineEnd |
|Konec řádku – prodloužení| **Shift+End** | Edit.LineEndExtend |
|Konec řádku – rozšířené sloupce| **Shift+Alt+End** | Edit.LineEndExtendColumn |
|Otevřený řádek nahoře| **Ctrl+Enter** | Edit.LineOpenAbove |
|Řádek otevřený níže| **Ctrl+Shift+Enter** | Edit.LineOpenBelow |
|Začátek řádku| **Domů** | Edit.LineStart |
|Prodloužení začátku řádku| **Shift+Home** | Edit.LineStartExtend |
|Rozšiřující sloupec začátku řádku| **Shift+Alt+Home** | Edit.LineStartExtendColumn |
|Transponovat čáru| **Shift+Alt+T** | Edit.LineTranspose |
|Sesou řádek nahoru| **Šipka nahoru** | Edit.LineUp |
|Rozšíření o řádek nahoru| **Shift + šipka nahoru** | Edit.LineUpExtend |
|Rozšiřující sloupec o řádek nahoru| **Shift + Alt + šipka nahoru** | Edit.LineUpExtendColumn |
|Seznam členů| **Ctrl+J** | Edit.ListMembers |
|Malá písmena| **Ctrl+U** | Edit.MakeLowercase |
|Velkými písmeny| **Ctrl+Shift+U** | Edit.MakeUppercase |
|Přesunutí vybraných řádků dolů| **Alt + šipka dolů** | Edit.MoveSelectedLinesDown |
|Přesunutí vybraných řádků nahoru| **Alt + šipka nahoru** | Edit.MoveSelectedLinesUp |
|Další zvýrazněný odkaz| **Ctrl + Shift + šipka dolů** | Edit.NextHighlightedReference |
|Režim přepisování| **Insert** | Edit.OvertypeMode |
|O stránku dolů| **PgDn** | Edit.PageDown |
|Rozšíření o stránku dolů| **Shift+PgDn** | Edit.PageDownExtend |
|O stránku nahoru| **PgUp** | Edit.PageUp |
|Rozšíření o stránku nahoru| **Shift+PgUp** | Edit.PageUpExtend |
|Informace o parametrech| **Ctrl + Shift + mezerník** | Edit.ParameterInfo |
|Tip pro vložení parametru| **Ctrl+Shift+Alt+P** | Edit.PasteParameterTip |
|Prohlédnutí zpět| **Ctrl+Alt+-** | Edit.PeekBackward |
|Náhled definice| **Alt+F12** | Edit.PeekDefinition |
|Náhled dopředu| **Ctrl+Alt+=** | Edit.PeekForward |
|Předchozí zvýrazněný odkaz| **Ctrl + Shift + šipka nahoru** | Edit.PreviousHighlightedReference |
|Rychlé informace| **Ctrl+K, Ctrl+I** | Edit.QuickInfo |
|Reverzní přírůstkové vyhledávání| **Ctrl+Shift+I** | Edit.ReverseIncrementalSearch |
|Posun o řádek dolů| **Ctrl + šipka dolů** | Edit.ScrollLineDown |
|Posunutí o řádek nahoru| **Ctrl + šipka nahoru** | Edit.ScrollLineUp |
|Výběr aktuálního slova| **Ctrl+W** | Edit.SelectCurrentWord |
|Zrušení výběru| **Escape** | Edit.SelectionCancel |
|Výběrem možnosti se vrátíte naposledy.| **Ctrl+=** | Edit.SelectToLastGoBack |
|Zobrazení nabídky pro objektivy kódu| **Ctrl+K, Ctrl+\`** | Edit.ShowCodeLensMenu |
|Zobrazit nabídku navigace| **Alt+\`** | Edit.ShowNavigateMenu |
|Zastavení skrytí aktuálního stavu| **Ctrl+M, Ctrl+U** | Edit.StopHidingCurrent |
|Ukončení osnovy| **Ctrl+M, Ctrl+P** | Edit.StopOutlining |
|Prohození ukotvení| **Ctrl+K, Ctrl+A** | Edit.SwapAnchor |
|Karta vlevo| **Shift+Tab** | Edit.TabLeft |
|Přepnutí všech slintů| **Ctrl+M, Ctrl+L** | Edit.ToggleAllOutlining |
|Přepnout záložku| **Ctrl+K, Ctrl+K** | Edit.ToggleBookmark |
|Přepnutí režimu dokončování| **Ctrl + Alt + mezerník** | Edit.ToggleCompletionMode |
|Přepnutí rozbalení osnovy| **Ctrl+M, Ctrl+M** | Edit.ToggleOutliningExpansion |
|Přepínací klávesová zkratka seznamu úloh| **Ctrl+K, Ctrl+H** | Edit.ToggleTaskListShortcut |
|Přepínání zalamování řádků| **Ctrl+E, Ctrl+W** | Edit.ToggleWordWrap |
|Výběr odkomentování| **Ctrl+K, Ctrl+U** | Edit.UncommentSelection |
|Zobrazit dole| **Ctrl+PgDn** | Edit.ViewBottom |
|Zobrazení dolního rozšíření| **Ctrl+Shift+PgDn** | Edit.ViewBottomExtend |
|Zobrazit nahoře| **Ctrl+PgUp** | Edit.ViewTop |
|Zobrazení horního rozšíření| **Ctrl+Shift+PgUp** | Edit.ViewTopExtend |
|Zobrazení mezer| **Ctrl+R, Ctrl+W** | Edit.ViewWhiteSpace |
|Odstranění slova až do konce| **Ctrl+Delete** | Edit.WordDeleteToEnd |
|Začít odstraněním slova| **Ctrl+Backspace** | Edit.WordDeleteToStart |
|Další slovo| **Ctrl + šipka doprava** | Edit.WordNext |
|Další rozšíření slova| **Ctrl + Shift + šipka doprava** | Edit.WordNextExtend |
|Další rozšiřující sloupec slova| **Ctrl + Shift + Alt + šipka doprava** | Edit.WordNextExtendColumn |
|Předchozí slovo| **Ctrl + šipka doleva** | Edit.WordPrevious |
|Předchozí rozšíření aplikace Word| **Ctrl + Shift + šipka doleva** | Edit.WordPreviousExtend |
|Předchozí rozšiřující sloupec aplikace Word| **Ctrl + Shift + Alt + šipka doleva** | Edit.WordPreviousExtendColumn |
|Transponovat slovo| **Ctrl+Shift+T** | Edit.WordTranspose |
|Spuštění v interaktivním režimu| **Alt+Enter** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Spuštění řádku v interaktivním režimu| **Alt+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Zobrazení v inspektoru stránky| **Ctrl+K, Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|Anotace TFS k přesunu další oblasti| **Alt+PgDn** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|Anotace TFS – přesunutí předchozí oblasti| **Alt+PgUp** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>Diagram činnosti UML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit|**Shift+Del**| Edit.Delete |

### <a name="uml-class-diagram"></a>Diagram tříd UML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>Diagram komponent UML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>Diagram případů použití UML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>Editor akcelerátorů VC

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nový akcelerátor|**Insert**| Edit.NewAccelerator |
|Typ dalšího klíče|**Ctrl+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>Editor dialogových oken VC

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přesunutí ovládacího prvku dolů|**Šipka dolů**| Edit.MoveControlDown |
|Přesunutí ovládacího prvku doleva|**Šipka doleva**| Edit.MoveControlLeft |
|Přesunutí ovládacího prvku doprava|**Šipka doprava**| Edit.MoveControlRight |
|Přesunutí ovládacího prvku nahoru|**Šipka nahoru**| Edit.MoveControlUp |
|Posunutí sloupce doleva|**Ctrl + šipka doleva**| Edit.ScrollColumnLeft |
|Posunutí sloupce doprava|**Ctrl + šipka doprava**| Edit.ScrollColumnRight |
|Posun o řádek dolů|**Ctrl + šipka dolů**| Edit.ScrollLineDown |
|Posunutí o řádek nahoru|**Ctrl + šipka nahoru**| Edit.ScrollLineUp |
|Vypnutí ovládacího prvku Velikost|**Shift + šipka dolů**| Edit.SizeControlDown |
|Ovládací prvek Velikost vlevo|**Shift + šipka doleva**| Edit.SizeControlLeft |
|Pravé řízení velikosti|**Shift + šipka doprava**| Edit.SizeControlRight |
|Řízení velikosti nahoru|**Shift + šipka nahoru**| Edit.SizeControlUp |
|Zarovnat dolů|**Ctrl + Shift + šipka dolů**| Format.AlignBottoms |
|Zarovnání středů|**Shift+F9**| Format.AlignCenters |
|Zarovnat doleva|**Ctrl + Shift + šipka doleva**| Format.AlignLefts |
|Zarovnat středy|**F9**| Format.AlignMiddles |
|Zarovnat práva|**Ctrl + Shift + šipka doprava**| Format.AlignRights |
|Zarovnat horní části|**Ctrl + Shift + šipka nahoru**| Format.AlignTops |
|Tlačítko dole|**Ctrl+B**| Format.ButtonBottom |
|Tlačítko vpravo|**Ctrl+R**| Format.ButtonRight |
|Vodorovně na střed|**Ctrl+Shift+F9**| Format.CenterHorizontal |
|Střed svisle|**Ctrl+F9**| Format.CenterVertical |
|Kontrola mnemotechnických symbolů|**Ctrl+M**| Format.CheckMnemonics |
|Velikost obsahu|**Shift+F7**| Format.SizetoContent |
|Mezera mezi|**Alt + šipka doprava**<br /><br /> nebo<br /><br /> **Alt + šipka doleva**| Format.SpaceAcross |
|Mezera dolů|**Alt + šipka nahoru**<br /><br /> nebo<br /><br /> **Alt + šipka dolů**| Format.SpaceDown |
|Pořadí karet|**Ctrl+D**| Format.TabOrder |
|Dialogové okno Test|**Ctrl+T**| Format.TestDialog |
|Přepínací vodítka|**Ctrl+G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>Editor obrázků VC

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nástroj Airbrush|**Ctrl+A**| Image.AirbrushTool |
|Nástroj Brush|**Ctrl+B**| Image.BrushTool |
|Kopírování a výběr obrysu|**Ctrl+Shift+U**| Image.CopyandOutlineSelection |
|Kreslení neprůhledné|**Ctrl+J**| Image.DrawOpaque |
|Nástroj se třemi tečkou|**Alt+P**| Image.EllipseTool |
|Nástroj pro vymazání|**Ctrl+Shift+I**| Image.EraseTool |
|Vyplněný nástroj se třemi tečkou|**Ctrl+Shift+Alt+P**| Image.FilledEllipseTool |
|Nástroj pro vyplněný obdélník|**Ctrl+Shift+Alt+R**| Image.FilledRectangleTool |
|Nástroj vyplněný zaoblený obdélník|**Ctrl+Shift+Alt+W**| Image.FilledRoundedRectangleTool |
|Nástroj Fill|**Ctrl+F**| Image.FillTool |
|Překlopit vodorovně|**Ctrl+H**| Image.FlipHorizontal |
|Překlopit svisle|**Shift+Alt+H**| Image.FlipVertical |
|Větší štětec|**Ctrl+=**| Image.LargerBrush |
|Nástroj Line|**Ctrl+L**| Image.LineTool |
|Nástroj pro zvětšování|**Ctrl+M**| Image.MagnificationTool |
|Zvětšit|**Ctrl+Shift+M**| Image.Magnify |
|Nový typ image|**Insert**| Image.NewImageType |
|Další barva|**Ctrl+]**<br /><br /> nebo<br /><br /> **Ctrl + šipka doprava**| Image.NextColor |
|Barva vpravo vedle|**Ctrl+Shift+]**<br /><br /> nebo<br /><br /> **Ctrl + Shift + šipka doprava**| Image.NextRightColor |
|Nástroj se třemi tečkou|**Shift+Alt+P**| Image.OutlinedEllipseTool |
|Nástroj s obrysem obdélníku|**Shift+Alt+R**| Image.OutlinedRectangleTool |
|Vypsaný Zaoblený obdélníkový nástroj|**Shift+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Nástroj tužka|**Ctrl+I**| Image.PencilTool |
|Předchozí barva|**CTRL + [**<br /><br /> nebo<br /><br /> **Ctrl + šipka doleva**| Image.PreviousColor |
|Předchozí pravá barva|**CTRL + SHIFT + [**<br /><br /> nebo<br /><br /> **Ctrl + Shift + šipka doleva**| Image.PreviousRightColor |
|Nástroj Výběr obdélníku|**Shift+Alt+S**| Image.RectangleSelectionTool |
|Nástroj obdélník|**Alt+R**| Image.RectangleTool |
|Otočit o 90 stupňů|**Ctrl+Shift+H**| Image.Rotate90Degrees |
|Nástroj zaoblený obdélník|**Alt+W**| Image.RoundedRectangleTool |
|Zobrazit mřížku|**Ctrl+Alt+S**| Image.ShowGrid |
|Zobrazit mřížku dlaždic|**Ctrl+Shift+Alt+S**| Image.ShowTileGrid |
|Malý štětec|**CTRL +.**| Image.SmallBrush |
|Menší štětec|**CTRL +-**| Image.SmallerBrush |
|Textový nástroj|**Ctrl+T**| Image.TextTool |
|Použít výběr jako štětec|**Ctrl+U**| Image.UseSelectionasBrush |
|Přiblížit|**CTRL + SHIFT +.**<br /><br /> nebo<br /><br /> **Ctrl + šipka nahoru**| Image.ZoomIn |
|Oddálit|**CTRL + SHIFT +,**<br /><br /> nebo<br /><br /> **Ctrl + šipka dolů**| Image.ZoomOut |

### <a name="vc-string-editor"></a>Editor řetězců VC

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Nový řetězec|**Insert**| Edit.NewString |

### <a name="view-designer"></a>Návrhář zobrazení

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zrušit načítání dat|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Kritéria|**Ctrl+2**| QueryDesigner.Criteria |
|Diagram|**Ctrl+1**| QueryDesigner.Diagram |
|Spustit SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Přejít na řádek|**Ctrl+G**| QueryDesigner.GotoRow |
|Režim JOIN|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Výsledky|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Visual Studio

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Skrýt podokno metody|**Ctrl+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Návrhář formulářů Windows

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Oddělovací čára|**Enter**| Edit.BreakLine |
|Znak doleva|**Šipka doleva**| Edit.CharLeft |
|Znak – doleva – zvětšit|**Shift + šipka doleva**| Edit.CharLeftExtend |
|Znak doprava|**Šipka doprava**| Edit.CharRight |
|Znak doprava – zvětšit|**Shift + šipka doprava**| Edit.CharRightExtend |
|Konec dokumentu|**End**| Edit.DocumentEnd |
|Konec dokumentu – zvětšit|**Shift+End**| Edit.DocumentEndExtend |
|Začátek dokumentu|**Domů**| Edit.DocumentStart |
|Začátek dokumentu – zvětšit|**Shift+Home**| Edit.DocumentStartExtend |
|Karta Vložit|**Tab**| Edit.InsertTab |
|Řádek dolů|**Šipka dolů**| Edit.LineDown |
|Řádek dolů – zvětšit|**Shift + šipka nahoru**| Edit.LineDownExtend |
|Řádek nahoru|**Šipka nahoru**| Edit.LineUp |
|Řádek-nahoru – zvětšit|**Shift + šipka dolů**| Edit.LineUpExtend |
|Přesunout ovládání dolů|**Ctrl + šipka dolů**| Edit.MoveControlDown |
|Přesunout ovládání doleva|**Ctrl + šipka doleva**| Edit.MoveControlLeft |
|Přesunout ovládání Doprava|**Ctrl + šipka doprava**| Edit.MoveControlRight |
|Přesunout ovládání nahoru|**Ctrl + šipka nahoru**| Edit.MoveControlUp |
|Zrušit výběr|**Escape**| Edit.SelectionCancel |
|Velikost ovládání dolů|**Ctrl + Shift + šipka dolů**| Edit.SizeControlDown |
|Velikost ovládání doleva|**Ctrl + Shift + šipka doleva**| Edit.SizeControlLeft |
|Velikost ovládacího prvku vpravo|**Ctrl + Shift + šipka doprava**| Edit.SizeControlRight |
|Velikost ovládání nahoru|**Ctrl + Shift + šipka nahoru**| Edit.SizeControlUp |
|Tab doleva|**Shift+Tab**| Edit.TabLeft |

### <a name="work-item-editor"></a>Editor pracovních položek

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vytvořit kopii pracovní položky|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Aktualizovat pracovní položku|**F5**| Edit.RefreshWorkItem |
|Nová odkazovaná pracovní položka|**Shift+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>Zobrazení dotazu pracovní položky

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vytvořit kopii pracovní položky|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Odrážka|**Shift + Alt + šipka doprava**| Edit.Indent |
|Zdůchlání|**Shift + Alt + šipka doleva**| Edit.Outdent |
|Nová propojená pracovní položka|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Aktualizovat|**F5**| Team.Refresh |
|Přepnout|**Shift+Alt+V**| Window.Toggle |

### <a name="work-item-results-view"></a>Zobrazení výsledků pracovní položky

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vytvoření kopie pracovní položky|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Odrážka|**Shift + Alt + šipka doprava**| Edit.Indent |
|Zdůchlání|**Shift + Alt + šipka doleva**| Edit.Outdent |
|Goto next work item|**Shift+Alt+N**| Team.GotoNextWorkItem |
|Goto previous work item|**Shift+Alt+P**| Team.GotoPreviousWorkItem |
|Nová propojená pracovní položka|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Aktualizovat|**F5**| Team.Refresh |
|Přepnout|**Shift+Alt+V**| Window.Toggle |

### <a name="workflow-designer"></a>Návrhář postupu provádění

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Dokončení slova|**Ctrl+K, W**<br /><br /> nebo<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> nebo<br /><br /> **Ctrl + mezerník**<br /><br /> nebo<br /><br /> **Alt + šipka doprava**| Edit.CompleteWord |
|Snížení úrovně filtru|**Alt+,**| Edit.DecreaseFilterLevel |
|Zvýšení úrovně filtru|**Alt+.**| Edit.IncreaseFilterLevel |
|Seznam členů|**Ctrl+K, L**<br /><br /> nebo<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> nebo<br /><br /> **Ctrl+J**| Edit.ListMembers |
|Informace o parametrech|**Ctrl+K, P**<br /><br /> nebo<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> nebo<br /><br /> **Ctrl + Shift + mezerník**| Edit.ParameterInfo |
|Rychlé informace|**Ctrl+K, I**<br /><br /> nebo<br /><br /> **Ctrl+K, Ctrl+I**| Edit.QuickInfo |
|Sbalit|**Ctrl+E, Ctrl+C**<br /><br /> nebo<br /><br /> **Ctrl+E, C**| WorkflowDesigner.Collapse |
|Sbalit vše|nebo| WorkflowDesigner.CollapseAll |
|Připojení uzly|**Ctrl+E, Ctrl+F**<br /><br /> nebo<br /><br /> **Ctrl+E, F**| WorkflowDesigner.ConnectNodes |
|Vytvoření proměnné|**Ctrl+E, Ctrl+N**<br /><br /> nebo<br /><br /> **Ctrl+E, N**| WorkflowDesigner.CreateVariable |
|Rozbalit vše|**Ctrl+E, Ctrl+X**<br /><br /> nebo<br /><br /> **Ctrl+E, X**| WorkflowDesigner.ExpandAll |
|Rozbalit na místě|**Ctrl+E, Ctrl+E**<br /><br /> nebo<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Přejít na nadřazenou položku|**Ctrl+E, Ctrl+P**<br /><br /> nebo<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Přesunout fokus|**Ctrl+E, Ctrl+M**<br /><br /> nebo<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Navigace přes návrháře|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Obnovení|**Ctrl+E, Ctrl+R**<br /><br /> nebo<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Zobrazit skrýt Návrhář argumentů|**Ctrl+E, Ctrl+A**<br /><br /> nebo<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Zobrazit skrýt Návrhář importů|**Ctrl+E, Ctrl+I**<br /><br /> nebo<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Zobrazit skrýt přehledovou mapu|**CTRL + E, CTRL + O** (Letter ' O ')<br /><br /> nebo<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Zobrazit skrýt Návrhář proměnných|**Ctrl+E, Ctrl+V**<br /><br /> nebo<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Přepnout výběr|**Ctrl+E, Ctrl+S**<br /><br /> nebo<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Přiblížit|**CTRL + NUM +**| WorkflowDesigner.ZoomIn |
|Oddálit|**Ctrl+Num -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>Návrhář v jazyce XAML

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přizpůsobit všem|**CTRL + 0** (nula)| Design.FitAll |
|Zobrazit popisovače|**F9**| Design.ShowHandles |
|Přiblížit|**CTRL + ALT + =**| Design.ZoomIn |
|Oddálit|**Ctrl+Alt+-**| Design.ZoomOut |
|Možnosti návrháře|**CTRL + SHIFT +;**|
|Úprava textu|**F2**| Format.EditText |
|Vše|**Ctrl+Shift+R**| Format.ResetLayout.All |
|Spustit kód projektu|**Ctrl+F9**|
|Skrýt (pouze Blend)|**Ctrl+H**| Timeline. Hide (jenom Blend) |
|Zámek (pouze Blend)|**Ctrl+L**| Timeline. Lock (jenom Blend) |
|Zobrazit (jenom Blend)|**Ctrl+Shift+H**| Timeline. show (jenom Blend) |
|Odemknout (jenom Blend)|**Ctrl+Shift+L**| Timeline. odemčení (pouze Blend) |
|Levý posun doleva|**Ctrl+Shift+,**| View.EdgeLeftMoveLeft |
|Posun doleva na okraji vpravo|**Ctrl+Shift+.**| View.EdgeLeftMoveRight |
|Posun doleva zprava doleva|**Ctrl+Shift+Alt+,**| View.EdgeRightMoveLeft |
|Pravý pohyb hran vpravo|**Ctrl+Shift+Alt+.**| View.EdgeRightMoveRight |
|Zobrazení nabídky značek vlastností|**Ctrl + mezerník**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>Editor XML (textový)

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Spuštění ladění XSLT|**Alt+F5**| XML.StartXSLTDebugging |
|Spuštění XSLT bez ladění|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>Návrhář schématu XML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Shora dolů|**Alt + šipka nahoru**| GraphView.BottomtoTop |
|Zleva doprava|**Alt + šipka doprava**| GraphView.LefttoRight |
|Zprava doleva|**Alt + šipka doleva**| GraphView.RighttoLeft |
|Shora dolů|**Alt + šipka dolů**| GraphView.ToptoBottom |
|Odebrání z pracovního prostoru|**Odstranit**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Zobrazení modelu obsahu|**Ctrl+2**| XsdDesigner.ShowContentModelView |
|Zobrazení grafu|**Ctrl+3**| XsdDesigner.ShowGraphView |
|Zobrazit úvodní zobrazení|**Ctrl+1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](reference/visual-studio-commands.md)
