---
title: Identifikátory GUID a ID nabídek sady Visual Studio | Microsoft Docs
description: Zobrazte seznam hodnot identifikátoru GUID a ID pro nabídky a skupiny v řádku nabídek sady Visual Studio, který je součástí integrovaného vývojového prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bceee5fce8a77ad5169020bd3d21896bdbc71443
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898068"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Identifikátory GUID a ID nabídek sady Visual Studio
V tomto článku jsou vyčteny hodnoty identifikátoru GUID a ID nabídek a skupin na řádku nabídek sady Visual Studio. Tyto hodnoty jsou definovány v souborech *. vsct* , které jsou nainstalovány jako součást sady Visual Studio SDK. Další informace naleznete v tématu [příkazy, nabídky a skupiny definované rozhraním IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Další informace o tom, jak pracovat s objekty integrovaného vývojového prostředí (IDE), které jsou definovány v souborech *. vsct* , najdete v tématu [rozšiřuje nabídky a příkazy](../../extensibility/extending-menus-and-commands.md).

 Nabídky a skupiny v řádku nabídek sady Visual Studio používají identifikátor GUID `guidSHLMainMenu` . Řádek nabídek má ID `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Skupiny na řádku nabídek sady Visual Studio
 Chcete-li přidat nabídku do řádku nabídek, nastavte jednu z těchto skupin jako nadřazenou.

|Group (Skupina)|ID|
|-----------|--------|
|Soubor/upravit/zobrazit|IDG_VS_MM_FILEEDITVIEW|
|Refaktoring|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Sestavení|IDG_VS_MM_BUILDDEBUGRUN|
|Formát/nástroje|IDG_VS_MM_TOOLSADDINS|
|Okno/Help/komunita|IDG_VS_MM_WINDOWHELP|
|Addins|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Nabídky na řádku nabídek sady Visual Studio
 Chcete-li přidat skupinu do existující nabídky sady Visual Studio, nastavte jednu z následujících nabídek jako její nadřazenou položku. Podnabídky nejsou zahrnuté v tomto seznamu.

|Nabídka|ID|
|----------|--------|
|Soubor|IDM_VS_MENU_FILE|
|Upravit|IDM_VS_MENU_EDIT|
|Zobrazení|IDM_VS_MENU_VIEW|
|Refaktoring|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Sestavení|IDM_VS_MENU_BUILD|
|Formát|IDM_VS_MENU_FORMAT|
|nástroje|IDM_VS_MENU_TOOLS|
|Rozšíření|IDM_VS_MENU_EXTENSIONS|
|Okno|IDM_VS_MENU_WINDOW|
|Addins|IDM_VS_MENU_ADDINS|
|Komunita|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Skupiny v nabídkách sady Visual Studio
 V následujících seznamech jsou uvedeny skupiny, které se doplňují přímo z nabídek na řádku nabídek sady Visual Studio. Nejrychlejší způsob, jak přidat příkaz do nabídky aplikace Visual Studio, je nastavit jednu z těchto skupin jako nadřazenou. Skupiny, které se doplní podnabídkami, se v této části nezobrazí.

### <a name="file-menu-groups"></a>Skupiny nabídek souborů

|Group (Skupina)|ID|
|-----------|--------|
|Nové/otevřené|IDG_VS_FILE_FILE|
|Přidání|IDG_VS_FILE_ADD|
|Řešení|IDG_VS_FILE_SOLUTION|
|Různé|IDG_VS_FILE_MISC|
|Uložit|IDG_VS_FILE_SAVE|
|přejmenování|IDG_VS_FILE_RENAME|
|Prohlížeč|IDG_VS_FILE_BROWSER|
|Tisk|IDG_VS_FILE_PRINT|
|Naposledy použité|IDG_VS_FILE_MRU|
|Přesunout|IDG_VS_FILE_MOVE|
|Ukončit|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Upravit skupiny nabídek

|Group (Skupina)|ID|
|-----------|--------|
|Vrátit zpět/znovu|IDG_VS_EDIT_UNDOREDO|
|Vyjmout/kopírovat/vložit|IDG_VS_EDIT_CUTCOPY|
|Vyberte|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Vyhledávání|IDG_VS_EDIT_FIND|
|Objekty|IDG_VS_EDIT_OBJECTS|
|OLE – příkazy|IDG_VS_EDIT_OLEVERBS|
|Dobře příkazů|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Refaktoring skupin nabídek

|Group (Skupina)|ID|
|-----------|--------|
|Společné|IDG_REFACTORING_COMMON|
|Pokročilý|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Zobrazení skupin nabídek

|Group (Skupina)|ID|
|-----------|--------|
|Kód formuláře|IDG_VS_VIEW_FORMCODE|
|Prohlížeč|IDG_VS_VIEW_BROWSER|
|Definování zobrazení|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architekt Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Okna organizace|IDG_VS_VIEW_ORG_WINDOWS|
|Prohlížeč kódu|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Vývoj pro Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Panely nástrojů|IDG_VS_VIEW_TOOLBARS|
|Symboly|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navigace|IDG_VS_VIEW_NAVIGATE|
|Small Navigate|IDG_VS_VIEW_SMALLNAVIGATE|
|prohlížeč objektů|IDG_VS_VIEW_OBJBRWSR|
|Dobře příkazů|IDG_VS_VIEW_COMMANDWELL|
|Stránky vlastností|IDG_VS_VIEW_PROPPAGES|
|Aktualizovat|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Skupiny nabídek projektu

|Group (Skupina)|ID|
|-----------|--------|
|Různé přidání|IDG_VS_PROJ_MISCADD|
|Přidání|IDG_VS_PROJ_ADD|
|Složka|IDG_VS_PROJ_FOLDER|
|Uvolnění nebo opětovné načtení|IDG_VS_PROJ_UNLOADRELOAD|
|Reference|IDG_VS_PROJ_REFERENCE|
|Možnosti|IDG_VS_PROJ_OPTIONS|
|Nastavení|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Skupiny nabídek sestavení

|Group (Skupina)|ID|
|-----------|--------|
|Řešení|IDG_VS_BUILD_SOLUTION|
|Výběr|IDG_VS_BUILD_SELECTION|
|Optimalizace na základě profilu|IDG_VS_PGO_SELECTION|
|Různé|IDG_VS_BUILD_MISC|
|Zrušit|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Skupiny nabídek Nástroje

|Group (Skupina)|ID|
|-----------|--------|
|Příkazový řádek|IDG_VS_TOOLS_CMDLINE|
|Fragmenty kódu|IDG_VS_TOOLS_SNIPPETS|
|Podmnožina objektu|IDG_VS_TOOLS_OBJSUBSET|
|Možnosti|IDG_VS_TOOLS_OPTIONS|
|Další 2|IDG_VS_TOOLS_OTHER2|
|Externí nástroje|IDG_VS_TOOLS_EXT_TOOLS|
|Externí přizpůsobení|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Skupiny nabídek oken

|Group (Skupina)|ID|
|-----------|--------|
|Nová|IDG_VS_WINDOW_NEW|
|Ukotvit/zavřít|IDG_VS_DOCKCLOSE|
|Ukotvit/skrýt|IDG_VS_DOCKHIDE|
|Uspořádat|IDG_VS_WINDOW_ARRANGE|
|Navigace|IDG_VS_WINDOW_NAVIGATION|
|Seznam|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Skupiny nabídek Help

|Group (Skupina)|ID|
|-----------|--------|
|ukázky|IDG_VS_HELP_SAMPLES|
|Podpora|IDG_VS_HELP_SUPPORT|
|Informace|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Podnabídky nabídek sady Visual Studio
 Následující hierarchie znázorňuje podnabídky, které jsou spojeny s nabídkami na řádku nabídek sady Visual Studio. Vzhledem k tomu, že jako nadřazenou položku může mít nabídka pouze skupina, musí být každá podnabídka ze skupiny v nabídce ze skupiny, nikoli přímo z nabídky. Další informace o vztahu mezi nabídkami, skupinami a podnabídkami najdete v tématu [Přidání podnabídky do nabídky](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Názvy nabídek v řádku nabídek sady Visual Studio nejsou samostatně zobrazeny v této hierarchii, protože je možné je odvodit z konvence pojmenování pro skupiny v rozhraní IDE, a to takto: *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

|Nadřazená skupina|Nabídk|Podřízené skupiny|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1... 6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Viz také
- [Identifikátory GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Identifikátory GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
