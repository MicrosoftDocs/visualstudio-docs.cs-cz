---
title: Identifikátory GUID a ID panelů nástrojů sady Visual Studio | Dokumenty společnosti Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708232"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identifikátory GUID a ID panelů nástrojů sady Visual Studio
Toto téma obsahuje výčet hodnoty GUID a ID panelů nástrojů, které jsou zahrnuty v integrovaném vývojovém prostředí sady Visual Studio (IDE) a skupin, které obsahují. Tyto hodnoty jsou definovány v *souborech .vsct,* které jsou nainstalovány jako součást sady Visual Studio SDK. Další informace naleznete v tématu [Příkazy, nabídky a skupiny definované ide](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Mnoho panelů nástrojů, které jsou k dispozici pro sadu Visual Studio, není definováno sadou Visual Studio a jejich hodnoty GUID a ID nejsou veřejné. V tomto tématu jsou uvedeny pouze panely nástrojů, které jsou definovány v souborech sady Visual Studio SDK *.vsct.*

 Další informace o práci s objekty IDE, které jsou definovány v souborech *.vsct,* naleznete [v tématu Rozšíření nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Výchozí panely nástrojů poskytované rozhraním IDE sady `guidSHLMainMenu`Visual Studio používají identifikátor `GUID:ID` GUID , s výjimkou případů, kdy je pomocí syntaxe zadáno jinak.

## <a name="ide-toolbars"></a>Panely nástrojů IDE
 Následující panely nástrojů jsou poskytovány ide sady Visual Studio. Panely nástrojů lze zobrazit tak, že je vyberete v podnabídce **Panely nástrojů** v nabídce **Nástroje.** Panely nástrojů v oknech nástrojů nejsou v této části zahrnuty.

 Z panelů nástrojů mohou sestoupit pouze skupiny. Chcete-li přidat skupinu, nastavte její nadřazenou položku na identifikátor GUID a ID panelu nástrojů. Chcete-li přidat tlačítko na panel nástrojů, nastavte jeho nadřazený objekt na skupinu na panelu nástrojů.

|Panel nástrojů|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Sestavení|IDM_VS_TOOL_BUILD|
|Textový editor|IDM_VS_TOOL_TEXTEDITOR|
|Ladit|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Umístění ladění|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Speciální panely nástrojů
 Tyto panely nástrojů jsou definovány ide sady Visual Studio, ale slouží specializované funkce a nejsou hostitelem skupin příkazů.

|Panel nástrojů|ID|
|-------------|--------|
|Přidat – příkaz|IDM_VS_TOOL_ADDCOMMAND|
|Nedefinované|IDM_VS_TOOL_UNDEFINED|
|Schéma XML|IDM_VS_TOOL_SCHEMA|
|data XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Skupiny na panelech nástrojů ide
 Chcete-li přidat tlačítko na standardní panel nástrojů, nastavte jednu z následujících skupin jako nadřazenou položku. Skupiny jsou seřazeny podle nadřazeného panelu nástrojů.

### <a name="standard-toolbar-groups"></a>Standardní skupiny panelů nástrojů

|Name (Název)|ID|
|----------|--------|
|Uložit/otevřít|IDG_VS_TOOLSB_SAVEOPEN|
|Vyjmout/kopírovat|IDG_VS_TOOLSB_CUTCOPY|
|Vrátit a vrátit znovu|IDG_VS_TOOLSB_UNDOREDO|
|Spustit/sestavit|IDG_VS_TOOLSB_RUNBUILD|
|Search|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nová okna|IDG_VS_TOOLSB_NEWWINDOWS|
|Načíst nebo uložit|IDG_VS_WINDOWUI_LOADSAVE|
|Měřidlo|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Vytváření skupin panelů nástrojů

|Name (Název)|ID|
|----------|--------|
|Panel sestavení|IDG_VS_BUILDBAR|
|Zrušit|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Skupiny panelů nástrojů textového editoru

|Name (Název)|ID|
|----------|--------|
|Dokončení|IDM_VS_TOOL_TEXTEDITOR|
|Odrážka|IDG_VS_EDITTOOLBAR_INDENT|
|Poznámka|IDG_VS_EDITTOOLBAR_COMMENT|
|Záložky|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Ladění skupin panelů nástrojů

|Name (Název)|ID|
|----------|--------|
|Spouštěcí|IDM_DEBUG_TOOLBAR|
|Krokování|IDG_DEBUG_TOOLBAR_STEPPING|
|Watch|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Ladění skupin panelu nástrojů umístění

|Name (Název)|ID|
|----------|--------|
|Umístění ladění|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Panely nástrojů okna nástrojů
 Panely nástrojů se mohou zobrazit přímo v rozhraní IDE nebo v oknech nástrojů, například **Průzkumníkřešení**. Vzhledem k tomu, že okna nástrojů nejsou v *souborech .vsct definována,* panely nástrojů okna nástrojů nemají definované rodiče. Místo toho jsou umístěny v kódu. V následující tabulce jsou uvedeny panely nástrojů, které se zobrazují v oknech nástrojů v prostředí IDE, a skupiny příkazů, které obsahují.

> [!NOTE]
> Panely nástrojů a skupiny `guidSHLMainMenu`používají identifikátor GUID , s výjimkou případů, kdy je pomocí syntaxe GUID:ID zadáno jinak. Pokud je pro panel nástrojů určen identifikátor GUID, vztahuje se také na skupiny, které pocházejí z tohoto panelu nástrojů.

|Okno nástroje|Panel nástrojů|Skupiny|
|-----------------|-------------|------------|
|Průzkumník řešení|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1. 5|
|Průzkumník serveru|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Vlastnosti|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|zobrazení tříd|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|zobrazení tříd|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|prohlížeč objektů|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|prohlížeč objektů|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Výstup|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|hledání a nahrazování|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Najít výsledky 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Najít výsledky 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Fragment kódu|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Záložky|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Seznam úkolů|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Uživatelské úkoly|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Seznam chyb|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Prohlížeč volání|IDM_VS_TOOL_CALLBROWSER1. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Zarážky|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Demontáž|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Paměť 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1. 4<br /><br /> IDG_MEMORY_COLUMNS1. 4|
|Procesy|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Viz také
- [Přidání ovladače nabídky na panel nástrojů](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Přidání panelu nástrojů do okna nástroje](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
