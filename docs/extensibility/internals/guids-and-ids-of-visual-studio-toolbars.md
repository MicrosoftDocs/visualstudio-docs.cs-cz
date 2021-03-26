---
title: Identifikátory GUID a ID panelů nástrojů sady Visual Studio | Microsoft Docs
description: Zobrazí seznam hodnot identifikátoru GUID a ID pro panely nástrojů a skupiny, které obsahují, které jsou součástí integrovaného vývojového prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ca3a2ec0b9d0eef7821641eaf05e93f83f94f40
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082072"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identifikátory GUID a ID panelů nástrojů sady Visual Studio
Toto téma obsahuje výčet hodnot identifikátoru GUID a ID panelů nástrojů, které jsou součástí integrovaného vývojového prostředí (IDE) sady Visual Studio, a skupin, které obsahují. Tyto hodnoty jsou definovány v souborech *. vsct* , které jsou nainstalovány jako součást sady Visual Studio SDK. Další informace naleznete v tématu [příkazy, nabídky a skupiny definované rozhraním IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Mnoho panelů nástrojů dostupných pro sadu Visual Studio není definováno aplikací Visual Studio a hodnoty identifikátoru GUID a ID nejsou veřejné. V tomto tématu jsou uvedeny pouze panely nástrojů, které jsou definovány v souborech sady Visual Studio SDK *. vsct* .

 Další informace o tom, jak pracovat s objekty IDE, které jsou definovány v souborech *. vsct* , naleznete v tématu [extend menu and Commands](../../extensibility/extending-menus-and-commands.md).

 Výchozí panely nástrojů poskytované rozhraním IDE sady Visual Studio používají identifikátor GUID `guidSHLMainMenu` , s výjimkou případů, kdy je uvedeno jinak pomocí `GUID:ID` syntaxe.

## <a name="ide-toolbars"></a>Panely nástrojů IDE
 Následující panely nástrojů jsou k dispozici v integrovaném vývojovém prostředí sady Visual Studio. Panely nástrojů lze zobrazit jejich výběrem v podnabídce **panelů nástrojů** v nabídce **nástroje** . V této části nejsou zahrnuty panely nástrojů v oknech nástrojů.

 Pouze skupiny mohou být přímo z panelů nástrojů. Chcete-li přidat skupinu, nastavte její nadřazený prvek na identifikátor GUID a ID panelu nástrojů. Chcete-li přidat tlačítko na panel nástrojů, nastavte jeho nadřazený prvek na skupinu na panelu nástrojů.

|Panel nástrojů|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Sestavení|IDM_VS_TOOL_BUILD|
|Textový editor|IDM_VS_TOOL_TEXTEDITOR|
|Ladění|guidVSDebugGroup: IDM_DEBUG_TOOLBAR|
|Umístění ladění|guidVSDebugGroup: IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Speciální panely nástrojů
 Tyto panely nástrojů jsou definovány v integrovaném vývojovém prostředí sady Visual Studio, ale obsluhují specializované funkce a nehostují skupiny příkazů.

|Panel nástrojů|ID|
|-------------|--------|
|Přidat – příkaz|IDM_VS_TOOL_ADDCOMMAND|
|Nedefinované|IDM_VS_TOOL_UNDEFINED|
|Schéma XML|IDM_VS_TOOL_SCHEMA|
|Data XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Skupiny na panelech nástrojů IDE
 Chcete-li přidat tlačítko na standardní panel nástrojů, nastavte jednu z následujících skupin jako své nadřazené položky. Skupiny jsou seřazené podle nadřazeného panelu nástrojů.

### <a name="standard-toolbar-groups"></a>Skupiny standardních panelů nástrojů

|Name|ID|
|----------|--------|
|Uložit/otevřít|IDG_VS_TOOLSB_SAVEOPEN|
|Vyjmout/kopírovat|IDG_VS_TOOLSB_CUTCOPY|
|Vrátit zpět/znovu|IDG_VS_TOOLSB_UNDOREDO|
|Spustit/sestavit|IDG_VS_TOOLSB_RUNBUILD|
|Hledat|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nová okna|IDG_VS_TOOLSB_NEWWINDOWS|
|Načíst/Uložit|IDG_VS_WINDOWUI_LOADSAVE|
|Měřidlo|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Sestavení skupin panelů nástrojů

|Name|ID|
|----------|--------|
|Panel sestavení|IDG_VS_BUILDBAR|
|Zrušit|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Skupiny panelů nástrojů textový editor

|Name|ID|
|----------|--------|
|Dokončení|IDM_VS_TOOL_TEXTEDITOR|
|Rážce|IDG_VS_EDITTOOLBAR_INDENT|
|Komentář|IDG_VS_EDITTOOLBAR_COMMENT|
|Záložky|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Ladit skupiny panelů nástrojů

|Name|ID|
|----------|--------|
|Spuštění|IDM_DEBUG_TOOLBAR|
|Pokusný|IDG_DEBUG_TOOLBAR_STEPPING|
|Watch|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Skupiny panelů nástrojů umístění ladění

|Name|ID|
|----------|--------|
|Umístění ladění|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Panely nástrojů okna nástrojů
 Panely nástrojů se mohou zobrazit přímo v integrovaném vývojovém prostředí nebo v oknech nástrojů, jako je například **Průzkumník řešení**. Vzhledem k tomu, že okna nástrojů nejsou definována v souborech *. vsct* , panely nástrojů okna nástroje nemají definované nadřazené položky. Místo toho jsou vloženy do kódu. V následující tabulce jsou uvedeny panely nástrojů, které se zobrazují v oknech nástrojů v integrovaném vývojovém prostředí (IDE), a skupiny příkazů, které obsahují.

> [!NOTE]
> Pomocí panelů nástrojů a skupin se používá identifikátor GUID `guidSHLMainMenu` , s výjimkou případů, kdy je jinak určen pomocí syntaxe GUID: ID. Pokud je pro panel nástrojů zadán identifikátor GUID, vztahuje se také na skupiny, které jsou na panelu nástrojů.

|Okno nástroje|Panel nástrojů|Skupiny|
|-----------------|-------------|------------|
|Průzkumník řešení|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. čl|
|Průzkumník serveru|guid_SE_MenuGroup: IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Vlastnosti|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|zobrazení tříd|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|zobrazení tříd|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|prohlížeč objektů|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|prohlížeč objektů|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Výstup|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|hledání a nahrazování|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Výsledky hledání 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Výsledky hledání 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Fragment kódu|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Záložky|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Seznam úkolů|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Uživatelské úkoly|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Seznam chyb|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Prohlížeč volání|IDM_VS_TOOL_CALLBROWSER1.. 16bitovém|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Zarážky|guidVSDebugGroup: IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Zpětný překlad|guidVSDebugGroup: IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Paměť 1-4|guidVSDebugGroup: IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1.. 4<br /><br /> IDG_MEMORY_COLUMNS1.. 4|
|Procesy|guidVSDebugGroup: IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Viz také
- [Přidání řadiče nabídky na panel nástrojů](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Přidání panelu nástrojů do okna nástrojů](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
