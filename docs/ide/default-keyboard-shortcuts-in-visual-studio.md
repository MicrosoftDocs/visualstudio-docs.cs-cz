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
ms.openlocfilehash: a63dbc1ad3ec544e52974a7ced9a69d4585ab629
ms.sourcegitcommit: b5744be07b7882e30bae67ef2810db56cf68344f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2021
ms.locfileid: "113487715"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Výchozí klávesové zkratky v Visual Studio

k nejrůznějším [příkazům](reference/visual-studio-commands.md) a windows v Visual Studio máte přístup výběrem příslušné klávesové zkratky. Tato stránka obsahuje seznam výchozích klávesových zkratek pro **obecný** profil, které jste mohli zvolit při instalaci Visual Studio. Bez ohledu na to, který profil zvolíte, můžete [zástupce příkazu identifikovat](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) otevřením dialogového okna **Možnosti** , rozbalením uzlu **prostředí** a výběrem **klávesnice**. Klávesové zkratky můžete také upravit přiřazením různých zkratek jakémukoli příkazu.

Seznam běžných klávesových zkratek a další informace o produktivitě najdete v těchto tématech:

- [Tipy klávesnice](../ide/productivity-shortcuts.md)
- [Tipy pro produktivitu](../ide/productivity-features.md).

další informace o usnadnění v Visual Studio najdete v tématech [tipy a triky pro usnadnění](../ide/reference/accessibility-tips-and-tricks.md) a [postupy: použití výhradně klávesnice](../ide/reference/how-to-use-the-keyboard-exclusively.md).

## <a name="most-popular-keyboard-shortcuts"></a>Nejoblíbenější klávesové zkratky

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
|Kopírovat|**Ctrl+C**<br /><br />nebo **Ctrl+Insert**| Edit.Copy |
|Vyjmout|**Ctrl+X**<br /><br />nebo **Shift+Delete**| Edit.Cut |
|Odstranit|**Odstranění** [Team Explorer]<br /><br />nebo **Shift+Delete** [sekvenční diagram, diagram činnosti UML, diagram vrstev]<br /><br />nebo **Ctrl+Delete** [Class Diagram]| Edit.Delete |
|Vyhledávání|**Ctrl+F**| Edit.Find |
|Vyhledání všech odkazů|**Shift+F12**| Edit.FindAllReferences |
|Hledání v souborech|**Ctrl+Shift+F**| Edit.FindinFiles |
|Najít další|**F3**| Edit.FindNext |
|Najít další vybrané|**Ctrl+F3**| Edit.FindNextSelected |
|Formátování dokumentu|**Ctrl+K, Ctrl+D** [Text Editor]| Edit.FormatDocument |
|Formátování výběru|**Ctrl+K, Ctrl+F** [Text Editor]| Edit.FormatSelection |
|Přejít na|**Ctrl+G**| Edit.GoTo |
|Přejít na deklaraci|**Ctrl+F12**| Edit.GoToDeclaration |
|Přejít k definici|**F12**| Edit.GoToDefinition |
|Přejít na seznam hledání|**Ctrl+D**| Edit.GoToFindCombo |
|Přejít na další umístění|**F8**| Edit.GoToNextLocation |
|Vložení fragmentu kódu|**Ctrl+K,** **Ctrl+X**| Edit.InsertSnippet |
|Karta Vložit|**Tab** [Návrhář sestav, Windows Forms Designer, Text Editor]| Edit.InsertTab |
|Vyjmutí čáry|**Ctrl+L** [Text Editor]| Edit.LineCut |
|Rozšiřující sloupec o řádek dolů|**Shift+Alt+šipka dolů** [Text Editor]| Edit.LineDownExtendColumn |
|Řádek otevřený výše|**Ctrl+Enter** [Text Editor]| Edit.LineOpenAbove |
|Seznam členů|**Ctrl+J** [Text Editor, Návrhář postupu provádění]<br /><br />nebo **Ctrl+K, Ctrl+L** [Návrhář postupu provádění]<br /><br />nebo **Ctrl+K, L** [Návrhář postupu provádění]| Edit.ListMembers |
|Přejděte na adresu .|**Ctrl+,**| Edit.NavigateTo |
|Otevřít soubor|**Ctrl+Shift+G**| Edit.OpenFile |
|Režim přepisování|**Insert** [Text Editor]| Edit.OvertypeMode |
|Informace o parametrech|**Ctrl+Shift+mezerník** [Text Editor, Návrhář postupu provádění]<br /><br />nebo **Ctrl+K, Ctrl+P** [Návrhář postupu provádění]<br /><br />nebo **Ctrl+K, P** [Návrhář postupu provádění]| Edit.ParameterInfo |
|Vložit|**Ctrl+V**<br /><br />nebo **Shift+Insert**| Edit.Paste |
|Náhled definice|**Alt+F12** [Text Editor]| Edit.PeekDefinition |
|Opakovat|**Ctrl+Y**<br /><br />nebo **Shift+Alt+Backspace**<br /><br />nebo **Ctrl+Shift+Z**| Edit.Redo |
|Nahrazení|**Ctrl+H**| Edit.Replace |
|Vybrat vše|**Ctrl+A**| Edit.SelectAll |
|Výběr aktuálního slova|**Ctrl+W** [Text Editor]| Edit.SelectCurrentWord |
|Zrušení výběru|**Esc** [Text Editor, Návrhář sestav, Nastavení Designer, Windows Forms Designer, Managed Resources Editor]| Edit.SelectionCancel |
|Ohraničovat|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Karta vlevo|**Shift+Tab** [Text Editor, Návrhář sestav, Windows Forms Editor]| Edit.TabLeft |
|Přepnutí všech slintů|**Ctrl+M, Ctrl+L** [Text Editor]| Edit.ToggleAllOutlining |
|Přepnout záložku|**Ctrl+K, Ctrl+K** [Text Editor]| Edit.ToggleBookmark |
|Přepnutí režimu dokončování|**Ctrl+Alt+mezerník** [Text Editor]| Edit.ToggleCompletionMode |
|Přepnutí rozbalení osnovy|**Ctrl+M, Ctrl+M** [Text Editor]| Edit.ToggleOutliningExpansion |
|Výběr odkomentování|**Ctrl+K, Ctrl+U** [Text Editor]| Edit.UncommentSelection |
|Zpět|**Ctrl+Z**<br /><br />nebo **Alt+Backspace**| Edit.Undo |
|Odstranění slova až do konce|**Ctrl+Delete** [Text Editor]| Edit.WordDeleteToEnd |
|Začít odstraněním slova|**Ctrl+Backspace** [Text Editor]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Soubor: oblíbené klávesové zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Ukončit|**Alt+F4**| File.Exit |
|Nový soubor|**Ctrl+N**| File.NewFile |
|Nový projekt|**Ctrl+Shift+N**| File.NewProject |
|Nový web|**Shift+Alt+N**| File.NewWebSite |
|Otevřít soubor|**Ctrl+O**| File.OpenFile |
|Otevřený projekt|**Ctrl+Shift+O**| File.OpenProject |
|Otevření webu|**Shift+Alt+O**| File.OpenWebSite |
|přejmenování|**F2** [Team Explorer]| File.Rename |
|Uložit vše|**Ctrl+Shift+S**| File.SaveAll |
|Uložení vybraných položek|**Ctrl+S**| File.SaveSelectedItems |
|Zobrazení v prohlížeči|**Ctrl+Shift+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Project: oblíbené klávesové zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Přidání existující položky|**Shift+Alt+A**| Project.AddExistingItem |
|Přidání nové položky|**Ctrl+Shift+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Refaktoring: oblíbené klávesové zkratky

|Příkaz|Klávesová zkratka [speciální kontexty]|ID příkazu|
|-|-|-|
|Extrahování metody|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Nástroje: oblíbené zkratky

|Příkaz|Klávesová zkratka [speciální kontexty]|ID příkazu|
|-|-|-|
|Připojení k procesu|**Ctrl+Alt+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Zobrazení: oblíbené zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Zobrazení tříd|**Ctrl+Shift+C**| View.ClassView |
|Upravit popisek|**F2**| View.EditLabel |
|Seznam chyb|**CTRL + \\ , CTRL + E**<br /><br />nebo **CTRL + \\ , E**| View.ErrorList |
|Přejít zpět|**CTRL +-**| View.NavigateBackward |
|Přejít vpřed|**CTRL + SHIFT +-**| View.NavigateForward |
|Prohlížeč objektů|**Ctrl+Alt+J**| View.ObjectBrowser |
|Výstup|**Ctrl+Alt+O**| View.Output |
|Vlastnosti – okno|**F4**| View.PropertiesWindow |
|Aktualizovat|**F5** [Team Explorer]| View.Refresh |
|Průzkumník serveru|**Ctrl+Alt+S**| View.ServerExplorer |
|Zobrazit inteligentní značku|**CTRL +.**<br /><br />nebo **SHIFT + ALT + F10** [zobrazení návrhu editoru HTML]| View.ShowSmartTag |
|Průzkumník řešení|**Ctrl+Alt+L**| View.SolutionExplorer |
|Team Explorer TFS|**CTRL + \\ , CTRL + M**| View.TfsTeamExplorer |
|Sada nástrojů|**Ctrl+Alt+X**| View.Toolbox |
|Zobrazit kód|**ENTER** [Class Diagram]<br /><br />nebo **F7** [Nastavení Designer]| View.ViewCode |
|Návrhář zobrazení|**SHIFT + F7** [zobrazení zdrojového kódu editoru HTML]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Okno: oblíbené zkratky

|Příkazy|Klávesové zkratky [speciální kontexty]|ID příkazu|
|-|-|-|
|Aktivovat okno dokumentu|**Esc**| Window.ActivateDocumentWindow |
|Zavřít okno dokumentu|**Ctrl+F4**| Window.CloseDocumentWindow |
|Další okno dokumentu|**Ctrl+F6**| Window.NextDocumentWindow |
|Další navigační okno dokumentu|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Další rozdělené podokno|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Globální zástupci

tyto klávesové zkratky jsou *globální*, což znamená, že je můžete použít, když má libovolné Visual Studio okno fokus.

- [Analyzovat](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Upravit](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Projekt](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Architektura](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Místní nabídky editoru](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [místní nabídky Project a řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Průzkumník testů](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Sestavení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [Soubor](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Refaktoring](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [Nástroje](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Zobrazení tříd kontextové nabídky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Nápověda](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Průzkumník řešení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Zobrazení](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Ladění](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Zátěžový test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Team](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Okno](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Kontextové nabídky ladicího programu](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Další kontextové nabídky](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Kontextové nabídky Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
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
|Nový diagram|**Ctrl+ \\ , Ctrl+N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Budovat

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Výběr sestavení|**Ctrl+B** (Visual Studio 2019)| Build.BuildSelection |
|Sestavení řešení|**Ctrl+Shift+B**| Build.BuildSolution |
|Zrušit|**Ctrl+Break**| Build.Cancel |
|Kompilaci|**Ctrl+F7**| Build.Compile |
|Spuštění analýzy kódu v řešení|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Zobrazení tříd místní nabídky

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vlastnosti|**Alt+Enter**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Ladění

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Použití změn kódu|**Alt+F10**| Debug.ApplyCodeChanges |
|Připojení k procesu|**Ctrl+Alt+P**| Debug.AttachtoProcess |
|Auta|**Ctrl+Alt+V, A**| Debug.Autos |
|Break all|**Ctrl+Alt+Break**| Debug.BreakAll |
|Zarážky|**Ctrl+Alt+B**| Debug.Breakpoints |
|Zásobník volání|**Ctrl+Alt+C**| Debug.CallStack |
|Odstranění všech zarážek|**Ctrl+Shift+F9**| Debug.DeleteAllBreakpoints |
|Spuštění|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Demontáž|**Ctrl+Alt+D**| Debug.Disassembly |
|Průzkumník modelu Dom|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Povolení zarážky|**Ctrl+F9**| Debug.EnableBreakpoint |
|Výjimky|**Ctrl+Alt+E**| Debug.Exceptions |
|Zarážka funkce|**Ctrl+K, B** (Visual Studio 2019)<br />**Ctrl** + **B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Přejít na předchozí volání nebo událost IntelliTrace|**Ctrl+Shift+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Spuštění diagnostiky|**Alt+F5**| Debug.Graphics.StartDiagnostics |
|Okamžité|**Ctrl+Alt+I**| Debug.Immediate |
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
|Krok ven|**Shift+F11**| Debug.StepOut |
|Krokování aktuálního procesu|**Ctrl+Shift+Alt+F11**| Debug.StepOutCurrentProcess |
|Krok přes|**F10** (při ladění: Provede krok přes akci)| Debug.StepOver |
|Krok přes|**F10** (Pokud není ladění: Spustí ladění a zastaví se na prvním řádku uživatelského kódu)| Debug.StepOver |
|Krok přes aktuální proces|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Zastavení ladění|**Shift+F5**| Debug.StopDebugging |
|Zastavení analýzy výkonu|**Shift+Alt+F2**| Debug.StopPerformanceAnalysis |
|Úkoly|**Ctrl+Shift+D, K**| Debug.Tasks |
|Vlákna|**Ctrl+Alt+H**| Debug.Threads |
|Přepnutí zarážky|**F9**| Debug.ToggleBreakpoint |
|Přepnutí zpětných překladů|**Ctrl+F11**| Debug.ToggleDisassembly |
|Sledování 1|**Ctrl+Alt+W, 1**| Debug.Watch1 |
|Sledovat 2|**Ctrl+Alt+W, 2**| Debug.Watch2 |
|Sledování 3|**Ctrl+Alt+W, 3**| Debug.Watch3 |
|Sledování 4|**Ctrl+Alt+W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Místní nabídky ladicího programu

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Odstranit|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Přejít na zpětný překlad|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Přejít ke zdrojovému kódu|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Centrum diagnostiky

|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Zastavení shromažďování|**Ctrl+Alt+F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Upravit

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Kopírovat|**Ctrl+C**<br /><br /> nebo<br /><br /> **Ctrl+Ins**| Edit.Copy |
|Vyjmout|**Ctrl+X**<br /><br /> nebo<br /><br /> **Shift+Delete**| Edit.Cut |
|Cyklus okruhu schránky|**Ctrl+Shift+V**<br /><br /> nebo<br /><br /> **Ctrl+Shift+Ins**| Edit.CycleClipboardRing |
|Odstranit|**Odstranit**| Edit.Delete |
|Duplikovat|**Ctrl+D**| Edit.Duplicate |
|Vyhledávání|**Ctrl+F**| Edit.Find |
|Vyhledání všech odkazů|**Shift+F12**| Edit.FindAllReferences |
|Hledání v souborech|**Ctrl+Shift+F**| Edit.FindinFiles |
|Najít další|**F3**| Edit.FindNext |
|Najít další vybrané|**Ctrl+F3**| Edit.FindNextSelected |
|Najít předchozí|**Shift+F3**| Edit.FindPrevious |
|Najít předchozí vybrané|**Ctrl+Shift+F3**| Edit.FindPreviousSelected |
|Generování metody|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Přejít na|**Ctrl+G**| Edit.GoTo |
|Přejít ke všem|**Ctrl+,** nebo **Ctrl+T**| Edit.GoToAll |
|Přejít na deklaraci|**Ctrl+F12**| Edit.GoToDeclaration |
|Přejít k definici|**F12**| Edit.GoToDefinition |
|Přejít na člena|**Ctrl+1, Ctrl+M** nebo **Ctrl+1, M** nebo **Alt+ \\**| Edit.GoToMember |
|Přejít na další umístění|**F8** (další chyba v Seznam chyb nebo okně Výstup)| Edit.GoToNextLocation |
|Přejděte do předchozího umístění.|**Shift+F8** (předchozí chyba v Seznam chyb nebo okně Výstup)| Edit.GoToPrevLocation |
|Vložení fragmentu kódu|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Přesunutí ovládacího prvku dolů|**Ctrl + šipka dolů**| Edit.MoveControlDown |
|Přesunutí ovládacího prvku dolů do mřížky|**Šipka dolů**| Edit.MoveControlDownGrid |
|Přesunutí ovládacího prvku doleva|**Ctrl + šipka doleva**| Edit.MoveControlLeft |
|Přesunutí levé mřížky ovládacího prvku|**Šipka doleva**| Edit.MoveControlLeftGrid |
|Přesunutí ovládacího prvku doprava|**Ctrl + šipka doprava**| Edit.MoveControlRight |
|Přesunutí pravé mřížky ovládacího prvku|**Šipka doprava**| Edit.MoveControlRightGrid |
|Přesunutí ovládacího prvku nahoru|**Ctrl + šipka nahoru**| Edit.MoveControlUp |
|Přesunutí ovládacího prvku nahoru o mřížku|**Šipka nahoru**| Edit.MoveControlUpGrid |
|Další záložka|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Další záložka ve složce|**Ctrl+Shift+K, Ctrl+Shift+N**| Edit.NextBookmarkInFolder |
|Otevřít soubor|**Ctrl+Shift+G** (otevře název souboru pod kurzorem)| Edit.OpenFile |
|Vložit|**Ctrl+V**<br /><br /> nebo<br /><br /> **Shift+Ins**| Edit.Paste |
|Předchozí záložka|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Předchozí záložka ve složce|**Ctrl+Shift+K, Ctrl+Shift+P**| Edit.PreviousBookmarkInFolder |
|Symbol rychlého hledání|**Shift+Alt+F12**| Edit.QuickFindSymbol |
|Opakovat|**Ctrl+Y**<br /><br /> nebo<br /><br /> **Ctrl+Shift+Z**<br /><br /> nebo<br /><br /> **Shift+Alt+Backspace**| Edit.Redo |
|Aktualizace vzdálených odkazů|**Ctrl+Shift+J**| Edit.RefreshRemoteReferences |
|Nahrazení|**Ctrl+H**| Edit.Replace |
|Nahrazení v souborech|**Ctrl+Shift+H**| Edit.ReplaceinFiles |
|Vybrat vše|**Ctrl+A**| Edit.SelectAll |
|Výběr dalšího ovládacího prvku|**Tab**| Edit.SelectNextControl |
|Výběr předchozího ovládacího prvku|**Shift+Tab**| Edit.SelectPreviousControl |
|Zobrazení mřížky dlaždic|**Enter**| Edit.ShowTileGrid |
|Vypnutí ovládacího prvku Velikost|**Ctrl + Shift + šipka dolů**| Edit.SizeControlDown |
|Mřížka ovládacího prvku Velikost|**Shift + šipka dolů**| Edit.SizeControlDownGrid |
|Ovládací prvek Velikost vlevo|**Ctrl + Shift + šipka doleva**| Edit.SizeControlLeft |
|Levá mřížka ovládacího prvku Velikost|**Shift + šipka doleva**| Edit.SizeControlLeftGrid |
|Pravé řízení velikosti|**Ctrl + Shift + šipka doprava**| Edit.SizeControlRight |
|Pravá mřížka ovládacího prvku Velikost|**Shift + šipka doprava**| Edit.SizeControlRightGrid |
|Řízení velikosti nahoru|**Ctrl + Shift + šipka nahoru**| Edit.SizeControlUp |
|Ovládací prvek Velikost v mřížce nahoru|**Shift + šipka nahoru**| Edit.SizeControlUpGrid |
|Zastavení hledání|**Alt+F3, S**| Edit.StopSearch |
|Ohraničovat|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Zpět|**Ctrl+Z**<br /><br /> nebo<br /><br /> **Alt+Backspace**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Místní nabídky editoru

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Podmínky zarážek|**Alt+F9, C**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions |
|Popisky pro úpravy zarážek|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Zobrazit položku|**Ctrl+'**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Spuštěním|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Přejít k zobrazení|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Přepnutí souboru kódu záhlaví|**Ctrl+K, Ctrl+O** (písmeno 'O')| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Zobrazení hierarchie volání|**Ctrl+K, Ctrl+T**<br /><br /> nebo<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Soubor

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Ukončit|**Alt+F4**| File.Exit |
|Nový soubor|**Ctrl+N**| File.NewFile |
|Nový projekt|**Ctrl+Shift+N**| File.NewProject |
|Nový web|**Shift+Alt+N**| File.NewWebSite |
|Otevřít soubor|**Ctrl+O** (písmeno 'O')| File.OpenFile |
|Otevřený projekt|**Ctrl+Shift+O** (písmeno 'O')| File.OpenProject |
|Otevření webu|**SHIFT + ALT + O** (Letter ' O ')| File.OpenWebSite |
|Tisk|**Ctrl+P**| File.Print |
|Uložit vše|**Ctrl+Shift+S**| File.SaveAll |
|Uložit vybrané položky|**Ctrl+S**| File.SaveSelectedItems |
|Zobrazení v prohlížeči|**Ctrl+Shift+W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Pomoc

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přidat a odebrat obsah v nápovědě|**Ctrl+Alt+F1**| Help.AddandRemoveHelpContent |
|Nápověda F1|**F1**| Help.F1Help |
|Zobrazit Help|**Ctrl+F1**| Help.ViewHelp |
|Okno – nápovědě|**Shift+F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Zátěžový test

|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Přejít na podokno čítače|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Další kontextové nabídky

|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Přidat nový diagram|**Insert**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Projekt

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přidat existující položku|**Shift+Alt+A**| Project.AddExistingItem |
|Přidat novou položku|**Ctrl+Shift+A**| Project.AddNewItem |
|Průvodce třídami|**Ctrl+Shift+X**| Project.ClassWizard |
|Přepis|**Ctrl+Alt+Ins**| Project.Override |
|Zobrazit náhled změn|**ALT +;** pak **ALT + C**| Project.Previewchanges |
|Publikovat vybrané soubory|**ALT +;** pak **ALT + P**| Project.Publishselectedfiles |
|Nahradit vybrané soubory ze serveru|**ALT +;** pak **ALT + R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a>místní nabídky Project a řešení

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přesunout dolů|**Alt + šipka dolů**| ProjectandSolutionContextMenus.Item.MoveDown |
|Přesunout nahoru|**Alt + šipka nahoru**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Refaktorovat

|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zapouzdření pole|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Extrahování rozhraní|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Extrahování metody|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Odebrat parametry|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|přejmenování|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Změna pořadí parametrů|**CTRL + R, CTRL + O** (Letter ' O ')| Refactor.ReorderParameters |

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
|Seznam chyb|**Ctrl+ \\ , E**<br /><br /> nebo<br /><br /> **Ctrl+ \\ , Ctrl+E**| View.ErrorList |
|interaktivní pro jazyk F#|**Ctrl+Alt+F**| View.F#Interactive |
|Vyhledání výsledků symbolu|**Ctrl+Alt+F12**| View.FindSymbolResults |
|Forward|**Alt + šipka doprava**  (funkce se liší od View.NavigateForward v textovém editoru)| View.Forward |
|Přeposlání kontextu procházení|**Ctrl+Shift+7**| View.ForwardBrowseContext |
|Celá obrazovka|**Shift+Alt+Enter**| View.FullScreen |
|Přejít zpět|**Ctrl+-**| View.NavigateBackward |
|Přejít vpřed|**Ctrl+Shift+-**| View.NavigateForward |
|Další chyba|**Ctrl+Shift+F12**| View.NextError |
|Oznámení|**Ctrl+W, N**<br /><br /> nebo<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Prohlížeč objektů|**Ctrl+Alt+J**| View.ObjectBrowser |
|Prohlížeč objektů – Přejít na hledaný seznam|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Výstup|**Ctrl+Alt+O** (písmeno 'O')| View.Output |
|Kontext procházení pop|**Ctrl+Shift+8** (jenom C++)| View.PopBrowseContext |
|Vlastnosti – okno|**F4**| View.PropertiesWindow |
|Stránky vlastností|**Shift+F4**| View.PropertyPages |
|Zobrazení prostředků|**Ctrl+Shift+E**| View.ResourceView |
|Průzkumník serveru|**Ctrl+Alt+S**| View.ServerExplorer |
|Zobrazení inteligentní značky|**Shift+Alt+F10**<br /><br /> nebo<br /><br /> **Ctrl+.**| View.ShowSmartTag |
|Průzkumník řešení|**Ctrl+Alt+L**| View.SolutionExplorer |
|SQL Průzkumník objektů serveru|**Ctrl+ \\ , Ctrl+S**| View.SQLServerObjectExplorer |
|Seznam úkolů|**Ctrl+ \\ , T**<br /><br /> nebo<br /><br /> **Ctrl+ \\ , Ctrl+T**| View.TaskList |
|Team Explorer pro TFS|**Ctrl+ \\ , Ctrl+M**| View.TfsTeamExplorer |
|Sada nástrojů|**Ctrl+Alt+X**| View.Toolbox |
|Průzkumník modelů UML|**Ctrl+ \\ , Ctrl+U**| View.UMLModelExplorer |
|Zobrazení kódu|**F7**| View.ViewCode |
|Návrhář zobrazení|**Shift+F7**| View.ViewDesigner |
|Webový prohlížeč|**Ctrl+Alt+R**| View.WebBrowser |
|Přiblížit|**Ctrl+Shift+.**| View.ZoomIn |
|Oddálit|**Ctrl+Shift+,**| View.ZoomOut |
|Zobrazení Průzkumníka testů|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |

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
|5. až|**Alt+PgUp**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|přejmenování|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Odebrat z diagramu|**Shift+Del**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Prohlížeč entity data model|**Ctrl+1**| View.EntityDataModelBrowser |
|Podrobnosti mapování datového modelu entity|**Ctrl+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Diagram tříd

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Sbalit|**Num -**| ClassDiagram.Collapse |
|Rozbalit|**NUM +**| ClassDiagram.Expand |
|Odstranit|**Ctrl+Del**| Edit.Delete |
|Rozbalit seznam sbalení základního typu|**Shift+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Přejít na Lupa|**Shift+Alt+L**| Edit.NavigateToLollipop |
|Odebrat z diagramu|**Odstranit**| Edit.RemovefromDiagram |
|Zobrazit kód|**Enter**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Editor programového testu UI

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Kopírovat odkaz do schránky|**Ctrl+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Vložit zpoždění před|**Ctrl+Alt+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Najít vše|**Shift+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Vyhledání ovládacího prvku uživatelského rozhraní|**Ctrl+Shift+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Přesunout kód|**Ctrl+Alt+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Rozdělit na novou metodu|**Ctrl+Shift+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Editor DataSet

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Vložit sloupec|**Insert**| OtherContextMenus.ColumnContext.InsertColumn |
|Sloupec|**Ctrl+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Prohlížeč rozdílů

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Ignorovat řezací prázdné znaky|**CTRL + \\ , CTRL + MEZERNÍK**| Diff.IgnoreTrimWhitespace |
|Vložené zobrazení|**CTRL + \\ , CTRL + 1**| Diff.InlineView |
|Jenom levé zobrazení|**CTRL + \\ , CTRL + 3**| Diff.LeftOnlyView |
|Další rozdíl|**F8**| Diff.NextDifference |
|Předchozí rozdíl|**Shift+F8**| Diff.PreviousDifference |
|Jenom pravé zobrazení|**CTRL + \\ , CTRL + 4**| Diff.RightOnlyView |
|Zobrazení vedle sebe|**CTRL + \\ , CTRL + 2**| Diff.SideBySideView |
|Přepnout mezi levým a pravým tlačítkem|**CTRL + \\ , CTRL + TAB**| Diff.SwitchBetweenLeftAndRight |
|Přepínač synchronizace zobrazení|**CTRL + \\ , Ctrl + šipka dolů**| Diff.SynchronizeViewToggle |
|Přidat komentář|**Ctrl+Shift+K**| EditorContextMenus.CodeWindow.AddComment |
|Upravit místní soubor|**CTRL + SHIFT + P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>Průzkumník modelu DOM

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Aktualizovat|**F5**| DOMExplorer.Refresh |
|Vybrat element|**Ctrl+B**| DOMExplorer.SelectElement |
|Zobrazit rozložení|**Ctrl+Shift+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>interaktivní pro jazyk F#

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Zrušit interaktivní vyhodnocení|**Ctrl+Break**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Editor dokumentu grafu

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přidat uzel|**Insert**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Obě závislosti|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Příchozí závislosti|**Došlo**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Odchozí závislosti|**Zápis**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Nový komentář|**Ctrl+Shift+K**<br /><br /> nebo<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Odebrat|**Odstranit**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|přejmenování|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Diagnostika grafiky

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zachytit snímek|Žádná| Debug.Graphics.CaptureFrame |
|Posunout výběr pixelů dolů|**Shift +Alt + šipka dolů**| Graphics. MovePixelSelectionDown |
|Posunout výběr pixelů vlevo|**Shift + Alt + šipka doleva**| Graphics. MovePixelSelectionLeft |
|Posunout výběr pixelů vpravo|**Shift + Alt + šipka doprava**| Graphics. MovePixelSelectionRight |
|Posunout výběr pixelů nahoru|**Shift + Alt + šipka nahoru**| Graphics. MovePixelSelectionUp |
|Zvětšit na skutečnou velikost|**Shift+Alt+0** (nula)| Graphics.ZoomToActualSize |
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

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Upravit buňku|**F2**| Edit.EditCell |
|Odebrat|**Odstranit**| Edit.Remove |
|Odebrat řádek|**Ctrl+Delete**| Edit.RemoveRow |
|Zrušit výběr|**Escape**| Edit.SelectionCancel |
|Zvuk|**Ctrl+4**| Resources.Audio |
|Soubory|**Ctrl+5**| Resources.Files |
|Ikony|**Ctrl+3**| Resources.Icons |
|Obrázky|**Ctrl+2**| Resources.Images |
|Jiné|**Ctrl+6**| Resources.Other |
|Řetězce|**Ctrl+1**| Resources.Strings |

### <a name="merge-editor-window"></a>Okno editoru sloučení

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nastavit fokus v levém okně|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Nastavit fokus na okně výsledků|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Nastavit fokus v pravém okně|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Datové nástroje Microsoft SQL Server, porovnání schématu

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Porovnání schématu SSDT porovnání|**Shift+Alt+C**| SQL.SSDTSchemaCompareCompare |
|Skript pro vygenerování porovnání schématu SSDT|**Shift+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|Porovnání schématu SSDT další změna|**Shift + Alt +.**| SQL.SSDTSchemaCompareNextChange |
|Předchozí Změna schématu SSDT porovnání|**SHIFT + ALT +,**| SQL.SSDTSchemaComparePreviousChange |
|Zastavení porovnání schématu SSDT|**Alt+Break**| SQL.SSDTSchemaCompareStop |
|SSDT schémat – porovnat aktualizace zápisu|**Shift+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Datové nástroje Microsoft SQL Server, návrhář tabulky

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Rozbalení zástupných znaků|**Ctrl+R, E**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Plně kvalifikované názvy|**Ctrl+R, Q**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Přesunout do schématu|**Ctrl+R, M**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|přejmenování|**F2**<br /><br /> nebo<br /><br /> **Ctrl+R, R**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Shift+Alt+PgDn**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Datové nástroje Microsoft SQL Server, editor T-SQL

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Spustit s ladicím programem|**Alt+F5**| SQL.ExecuteWithDebugger |
|Rozbalení zástupných znaků|**Ctrl+R, E**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Plně kvalifikované názvy|**Ctrl+R, Q**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Přesunout do schématu|**Ctrl+R, M**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|přejmenování|**F2**<br /><br /> nebo<br /><br /> **Ctrl+R, R**<br /><br /> nebo<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|T SQL editor zrušit dotaz|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL spustit dotaz z editoru|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|T & SQL editor výsledků jako soubor|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|T SQL editor výsledků jako grid|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|T SQL editor výsledků jako text|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL editor zobrazit odhadovaný plán|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL – přepnout plán spouštění|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|editor T SQL – přepnout podokno výsledků|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL – klonovaný dotaz editoru|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|T SQL – kombinovaná databáze editoru|**Shift+Alt+PgDn**|SQL. TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Datové nástroje Microsoft SQL Server, editor T-SQL PDW

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|T SQL editor zrušit dotaz|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL spustit dotaz z editoru|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|T & SQL editor výsledků jako soubor|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|T SQL editor výsledků jako grid|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|T SQL editor výsledků jako text|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL editor zobrazit odhadovaný plán|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL – přepnout plán spouštění|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|editor T SQL – přepnout podokno výsledků|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL – klonovaný dotaz editoru|**Ctrl+Alt+N**|SQL. TSqlEditorCloneQuery |
|T SQL – klonovaný dotaz editoru|**Shift+Alt+PgDn**|SQL. TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Inspektor stránek

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Minimalizovat|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Návrhář dotazu

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

### <a name="query-results"></a>Výsledky dotazu

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nový řádek výsledků dotazu|**Alt+End**| SQL.QueryResultsNewRow |
|Aktualizace výsledků dotazu|**Shift+Alt+R**| SQL.QueryResultsRefresh |
|Zastavení výsledků dotazu|**Alt+Break**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Návrhář sestav

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Oddělovací čára|**Enter**| Edit.BreakLine |
|Znak doleva|**Šipka doleva**| Edit.CharLeft |
|Znak – doleva – zvětšit|**Shift + šipka doleva**| Edit.CharLeftExtend |
|Znak doprava|**Šipka doprava**| Edit.CharRight |
|Znak doprava – zvětšit|**Shift + šipka doprava**| Edit.CharRightExtend |
|Karta Vložit|**Tab**| Edit.InsertTab |
|Řádek dolů|**Šipka dolů**| Edit.LineDown |
|Řádek dolů – zvětšit|**Shift + šipka dolů**| Edit.LineDownExtend |
|Řádek nahoru|**Šipka nahoru**| Edit.LineUp |
|Řádek-nahoru – zvětšit|**Shift + šipka nahoru**| Edit.LineUpExtend |
|Přesunout ovládání dolů|**Ctrl + šipka dolů**| Edit.MoveControlDown |
|Přesunout ovládání doleva|**Ctrl + šipka doleva**| Edit.MoveControlLeft |
|Přesunout ovládání Doprava|**Ctrl + šipka doprava**| Edit.MoveControlRight |
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
|Přejděte na obsah části 7 Team Exploreru.|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Přejděte na obsah v části 8 Team Exploreru.|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Přejděte na obsah části 9 Team Exploreru.|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Team Explorer – navigace zpět|**Alt + šipka doleva**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Team Explorer – navigace vpřed|**Alt + šipka doprava**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Kontext TFS: Moje pracovní stránka vytvoří kopii wi|**Shift+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Kontext TFS má pracovní stránka nová propojená wi|**Shift+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Aktualizovat|**F5**| View.Refresh |

### <a name="test-explorer"></a>Průzkumník testů

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Otevřený test|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Textový editor

Klávesové zkratky specifické pro tento kontext jsou následující:


| Příkazy | Klávesové zkratky |ID příkazu|
|-|-|-|
|Zalomení řádku| **Enter**<br /><br /> nebo<br /><br /> **Shift+Enter** | Edit.BreakLine |
|Znak vlevo| **Šipka doleva** | Edit.CharLeft |
|Znak s levým rozšířením| **Shift + šipka doleva** | Edit.CharLeftExtend |
|Znak levého rozšiřujícího sloupce| **Shift + Alt + šipka doleva** | Edit.CharLeftExtendColumn |
|Znak vpravo| **Šipka doprava** | Edit.CharRight |
|Rozšíření zprava znaků| **Shift + šipka doprava** | Edit.CharRightExtend |
|Rozšíření sloupce doprava znakem| **Shift + Alt + šipka doprava** | Edit.CharRightExtendColumn |
|Vymazání záložek| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Sbalení všech sbalení| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Sbalení aktuální oblasti| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Sbalení značky| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Sbalení na definice| **Ctrl+M, Ctrl+O** (písmeno O) | Edit.CollapseToDefinitions |
|Výběr kontraktu| **Shift+Alt+-** | Edit.ContractSelection |
|Výběr komentáře| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Dokončení slova| **Ctrl + mezerník**<br /><br /> nebo<br /><br /> **Alt + šipka doprava** | Edit.CompleteWord |
|Tip pro kopírování parametru| **Ctrl+Shift+Alt+C** | Edit.CopyParameterTip |
|Snížení úrovně filtru| **Alt+,** | Edit.DecreaseFilterLevel |
|Odstranění zpět| **Backspace**<br /><br /> nebo<br /><br /> **Shift+Bkspce** | Edit.DeleteBackwards |
|Odstranění vodorovných mezer| **CTRL + K, CTRL +\\** | Edit.DeleteHorizontalWhiteSpace |
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

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>Diagram případu použití UML

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Odstranit z modelu|**Shift+Del**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>Editor akcelerátorů VC

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Nový akcelerátor|**Insert**| Edit.NewAccelerator |
|Další zadaný klíč|**Ctrl+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>Editor dialogových oken VC

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přesunout ovládání dolů|**Šipka dolů**| Edit.MoveControlDown |
|Přesunout ovládání doleva|**Šipka doleva**| Edit.MoveControlLeft |
|Přesunout ovládání Doprava|**Šipka doprava**| Edit.MoveControlRight |
|Přesunout ovládání nahoru|**Šipka nahoru**| Edit.MoveControlUp |
|Posunout sloupec vlevo|**Ctrl + šipka doleva**| Edit.ScrollColumnLeft |
|Posunout sloupec vpravo|**Ctrl + šipka doprava**| Edit.ScrollColumnRight |
|Posunout o řádek dolů|**Ctrl + šipka dolů**| Edit.ScrollLineDown |
|Posunout řádek nahoru|**Ctrl + šipka nahoru**| Edit.ScrollLineUp |
|Velikost ovládání dolů|**Shift + šipka dolů**| Edit.SizeControlDown |
|Velikost ovládání doleva|**Shift + šipka doleva**| Edit.SizeControlLeft |
|Velikost ovládacího prvku vpravo|**Shift + šipka doprava**| Edit.SizeControlRight |
|Velikost ovládání nahoru|**Shift + šipka nahoru**| Edit.SizeControlUp |
|Zarovnat dolů|**Ctrl + Shift + šipka dolů**| Format.AlignBottoms |
|Zarovnat na střed|**Shift+F9**| Format.AlignCenters |
|Zarovnat doleva|**Ctrl + Shift + šipka doleva**| Format.AlignLefts |
|Zarovnat doprostřed|**F9**| Format.AlignMiddles |
|Zarovnat práva|**Ctrl + Shift + šipka doprava**| Format.AlignRights |
|Zarovnat nahoru|**Ctrl + Shift + šipka nahoru**| Format.AlignTops |
|Tlačítko dolů|**Ctrl+B**| Format.ButtonBottom |
|Tlačítko doprava|**Ctrl+R**| Format.ButtonRight |
|Vycentrovat vodorovně|**CTRL + SHIFT + F9**| Format.CenterHorizontal |
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
|Nástroj pro zaoblené obdélníky s obrysem|**Shift+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Tužka|**Ctrl+I**| Image.PencilTool |
|Předchozí barva|**Ctrl+[**<br /><br /> nebo<br /><br /> **Ctrl + šipka doleva**| Image.PreviousColor |
|Předchozí pravá barva|**Ctrl+Shift+[**<br /><br /> nebo<br /><br /> **Ctrl + Shift + šipka doleva**| Image.PreviousRightColor |
|Nástroj pro výběr obdélníků|**Shift+Alt+S**| Image.RectangleSelectionTool |
|Nástroj Obdélník|**Alt+R**| Image.RectangleTool |
|Otočit o 90 stupňů stupňů|**Ctrl+Shift+H**| Image.Rotate90Degrees |
|Nástroj pro zaoblené obdélníky|**Alt+W**| Image.RoundedRectangleTool |
|Zobrazit mřížku|**Ctrl+Alt+S**| Image.ShowGrid |
|Zobrazení mřížky dlaždic|**Ctrl+Shift+Alt+S**| Image.ShowTileGrid |
|Malý štětec|**Ctrl+.**| Image.SmallBrush |
|Menší štětec|**Ctrl+-**| Image.SmallerBrush |
|Textový nástroj|**Ctrl+T**| Image.TextTool |
|Použití výběru jako štětce|**Ctrl+U**| Image.UseSelectionasBrush |
|Přiblížit|**Ctrl+Shift+.**<br /><br /> nebo<br /><br /> **Ctrl + šipka nahoru**| Image.ZoomIn |
|Oddálit|**Ctrl+Shift+,**<br /><br /> nebo<br /><br /> **Ctrl + šipka dolů**| Image.ZoomOut |

### <a name="vc-string-editor"></a>Editor řetězců VC

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Nový řetězec|**Insert**| Edit.NewString |

### <a name="view-designer"></a>Návrhář zobrazení

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

### <a name="visual-studio"></a>Visual Studio

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkaz|Klávesová zkratka|ID příkazu|
|-|-|-|
|Podokno Skrýt metody|**Ctrl+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

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
|Rozšíření na místě|**Ctrl+E, Ctrl+E**<br /><br /> nebo<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Přejít k nadřazenému objektu|**Ctrl+E, Ctrl+P**<br /><br /> nebo<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Přesunutí fokusu|**Ctrl+E, Ctrl+M**<br /><br /> nebo<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Procházení návrháře|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Obnovení|**Ctrl+E, Ctrl+R**<br /><br /> nebo<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Zobrazení návrháře argumentů pro skrytí|**Ctrl+E, Ctrl+A**<br /><br /> nebo<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Zobrazení návrháře pro skrytí importů|**Ctrl+E, Ctrl+I**<br /><br /> nebo<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Zobrazení mapy s přehledem pro skrytí|**Ctrl+E, Ctrl+O** (písmeno 'O')<br /><br /> nebo<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Zobrazení návrháře skrytí proměnných|**Ctrl+E, Ctrl+V**<br /><br /> nebo<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Přepnutí výběru|**Ctrl+E, Ctrl+S**<br /><br /> nebo<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Přiblížit|**Ctrl+Num +**| WorkflowDesigner.ZoomIn |
|Oddálit|**Ctrl+Num -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>Návrhář v jazyce XAML

Klávesové zkratky specifické pro tento kontext jsou následující:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Přizpůsobit všem|**Ctrl+0** (nula)| Design.FitAll |
|Zobrazení popisovačů|**F9**| Design.ShowHandles |
|Přiblížit|**Ctrl+Alt+=**| Design.ZoomIn |
|Oddálit|**Ctrl+Alt+-**| Design.ZoomOut |
|Možnosti návrháře|**Ctrl+Shift+;**|
|Úprava textu|**F2**| Format.EditText |
|Vše|**Ctrl+Shift+R**| Format.ResetLayout.All |
|Spuštění kódu projektu|**Ctrl+F9**|
|Skrýt (jenom Blend)|**Ctrl+H**| Timeline.Hide (pouze Blend) |
|Zamknout (jenom Blend)|**Ctrl+L**| Timeline.Lock (pouze Blend) |
|Zobrazit (jenom Blend)|**Ctrl+Shift+H**| Timeline.Show (pouze Blend) |
|Odemknutí (jenom Blend)|**Ctrl+Shift+L**| Timeline.Unlock (pouze Blend) |
|Levý přesun hraničních zařízení doleva|**CTRL + SHIFT +,**| View.EdgeLeftMoveLeft |
|Přesunutí doleva doprava|**CTRL + SHIFT +.**| View.EdgeLeftMoveRight |
|Posun doprava doleva|**Ctrl+Shift+Alt+,**| View.EdgeRightMoveLeft |
|Pravé přesunutí doprava|**CTRL + SHIFT + ALT +.**| View.EdgeRightMoveRight |
|Zobrazit nabídku značek vlastnosti|**Ctrl + mezerník**| Zobrazit. ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>Editor XML (textový)

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Spustit ladění XSLT|**Alt+F5**| XML.StartXSLTDebugging |
|Spustit XSLT bez ladění|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>Návrhář schématu XML

Klávesové zkratky, které jsou specifické pro tento kontext:


|Příkazy|Klávesové zkratky|ID příkazu|
|-|-|-|
|Zdola nahoru|**Alt + šipka nahoru**| GraphView.BottomtoTop |
|Zleva doprava|**Alt + šipka doprava**| GraphView.LefttoRight |
|Zprava doleva|**Alt + šipka doleva**| GraphView.RighttoLeft |
|Shora dolů|**Alt + šipka dolů**| GraphView.ToptoBottom |
|Odebrat z pracovního prostoru|**Odstranit**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Zobrazit zobrazení modelu obsahu|**Ctrl+2**| XsdDesigner.ShowContentModelView |
|Zobrazit zobrazení grafu|**Ctrl+3**| XsdDesigner.ShowGraphView |
|Zobrazit úvodní zobrazení|**Ctrl+1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](reference/visual-studio-commands.md)
