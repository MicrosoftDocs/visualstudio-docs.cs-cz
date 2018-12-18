---
title: Identifikátory GUID a ID panelů nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 183baec1e0170f9c34a100cbf64257a3e7fa45e7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061857"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Identifikátory GUID a ID panelů nástrojů sady Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto téma uvádí hodnoty GUID a ID panelů nástrojů, které jsou součástí integrovaného vývojového prostředí (IDE) sady Visual Studio a skupin, které obsahují. Tyto hodnoty jsou definovány v souborech .vsct, které se instalují jako součást sady Visual Studio SDK. Další informace najdete v tématu [IDE-Defined příkazy, nabídky a skupiny](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
>  Mnohé z panelů nástrojů sady Visual Studio nejsou definovány tak, že Visual Studio a jejich identifikátoru GUID a ID hodnoty nejsou veřejné. Toto téma obsahuje seznam pouze panely nástrojů, které jsou definovány v souborech .vsct Visual Studio SDK.

 Další informace o tom, jak pracovat s objekty integrovaného vývojového prostředí, které jsou definovány v souborech .vsct najdete v tématu [rozšiřování nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).

 Výchozí panely nástrojů poskytuje integrované vývojové prostředí sady Visual Studio použijte identifikátor GUID `guidSHLMainMenu`, s výjimkou pomocí syntaxe GUID:ID uvedeno jinak.

## <a name="ide-toolbars"></a>Panely nástrojů rozhraní IDE
 Následující panely nástrojů jsou k dispozici v integrovaném vývojovém prostředí sady Visual Studio. Panely nástrojů lze zobrazit tak, že je vyberete na **panely nástrojů** podnabídce **nástroje** nabídky. Panely nástrojů v oknech nástrojů nejsou zahrnuté v této části.

 Pouze skupiny můžete sestup přímo z panelů nástrojů. Přidat skupinu, nastavte jeho nadřazený objekt na identifikátor GUID a ID panelu nástrojů. Přidáte tlačítko na panelu nástrojů, nastavte jeho nadřazený objekt do skupiny na panelu nástrojů.

|Panel nástrojů|ID|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Sestavení|IDM_VS_TOOL_BUILD|
|Textový editor|IDM_VS_TOOL_TEXTEDITOR|
|Ladit|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Ladit umístění|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Speciální panelů nástrojů
 Panely nástrojů, které jsou definovány pomocí integrovaného vývojového prostředí sady Visual Studio, ale sloužit specializované funkce a není hostitelem pro skupinu příkazů.

|Panel nástrojů|ID|
|-------------|--------|
|Příkaz Přidat|IDM_VS_TOOL_ADDCOMMAND|
|Nedefinovaný|IDM_VS_TOOL_UNDEFINED|
|XML schéma|IDM_VS_TOOL_SCHEMA|
|XML Data|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Skupiny na panely nástrojů rozhraní IDE
 Na standardním panelu nástrojů přidejte tlačítko, nastavte jednu z následujících skupin jako jeho nadřazený objekt. Skupiny jsou seřazeny podle nadřazeného panelu nástrojů.

### <a name="standard-toolbar-groups"></a>Skupiny na standardním panelu nástrojů

|Název|ID|
|----------|--------|
|Uložit a otevřít|IDG_VS_TOOLSB_SAVEOPEN|
|Vyjmout/Kopírovat|IDG_VS_TOOLSB_CUTCOPY|
|Zpět/znovu|IDG_VS_TOOLSB_UNDOREDO|
|Spuštění/sestavení|IDG_VS_TOOLSB_RUNBUILD|
|Hledat|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nové Windows|IDG_VS_TOOLSB_NEWWINDOWS|
|Načtení a uložení|IDG_VS_WINDOWUI_LOADSAVE|
|Měřidla|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Vytvořit skupiny pro panel nástrojů

|Název|ID|
|----------|--------|
|Panelu sestavení|IDG_VS_BUILDBAR|
|Zrušit|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Panel nástrojů textového editoru skupiny

|Název|ID|
|----------|--------|
|Dokončení|IDM_VS_TOOL_TEXTEDITOR|
|Odsazení|IDG_VS_EDITTOOLBAR_INDENT|
|Komentář|IDG_VS_EDITTOOLBAR_COMMENT|
|Záložky|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Ladění nástrojů skupiny

|Název|ID|
|----------|--------|
|Spuštění|IDM_DEBUG_TOOLBAR|
|Krokování|IDG_DEBUG_TOOLBAR_STEPPING|
|Sledování|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Skupiny nástrojů umístění ladění

|Název|ID|
|----------|--------|
|Ladit umístění|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Panelech nástrojů
 Panely nástrojů lze zobrazit přímo v integrovaném vývojovém prostředí nebo v oknech nástrojů třeba **Průzkumníka řešení**. Protože nástroj windows nejsou definovány v souborech .vsct, panelech nástrojů nemají definované nadřazené položky. Místo toho jsou umístěny v kódu. V následující tabulce jsou uvedeny panely nástrojů, které se zobrazují na okna nástrojů v prostředí IDE a příkaz skupiny, které obsahují.

> [!NOTE]
>  Panely nástrojů a skupiny použijte identifikátor GUID `guidSHLMainMenu`, s výjimkou pomocí syntaxe GUID:ID uvedeno jinak. Kde GUID je zadaný pro panel nástrojů, platí i pro skupiny, ke kterým sestup z panelu nástrojů.

|Panel nástrojů|Panel nástrojů|Skupiny|
|-----------------|-------------|------------|
|Průzkumník řešení|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|
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
|Seznam úloh|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Uživatelské úkoly|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Seznam chyb|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Prohlížeč volání|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Zarážky|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Převod do strojového jazyka|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Paměť 1 – 4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|
|Procesy|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Viz také
 [Přidání Kontroleru nabídky do panelu nástrojů](../../extensibility/adding-a-menu-controller-to-a-toolbar.md) [přidání panelu nástrojů do panelu nástrojů](../../extensibility/adding-a-toolbar-to-a-tool-window.md) [identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
