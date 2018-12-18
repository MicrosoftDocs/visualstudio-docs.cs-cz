---
title: Identifikátory GUID a ID nabídek sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b7c8af93604a7e8e33d7d21d26b85c59985b878
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499936"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Identifikátory GUID a ID sady Visual Studio nabídky
Tento článek uvádí hodnoty GUID a ID nabídek a skupin v řádku nabídek sady Visual Studio. Tyto hodnoty jsou definovány v *.vsct* soubory, které se instalují jako součást sady Visual Studio SDK. Další informace najdete v tématu [příkazy definované prostředím IDE, nabídky a skupiny](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Další informace o tom, jak pracovat s objekty integrované vývojové prostředí (IDE), které jsou definovány v *.vsct* soubory, naleznete v tématu [rozšířit nabídek a příkazů](../../extensibility/extending-menus-and-commands.md).  
  
 Nabídky a skupiny na řádku nabídek sady Visual Studio použijte identifikátor GUID `guidSHLMainMenu`. Nabídek samotné má ID `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Skupiny v řádku nabídek sady Visual Studio  
 Přidání nabídky na řádku nabídek, nastavte jednu z těchto skupin jako jeho nadřazený objekt.  
  
|Skupina|ID|  
|-----------|--------|  
|Soubor / / zobrazení pro úpravy|IDG_VS_MM_FILEEDITVIEW|  
|Refaktoring|IDG_VS_MM_REFACTORING:|  
|Projekt|IDG_VS_MM_PROJECT|  
|Sestavení|IDG_VS_MM_BUILDDEBUGRUN|  
|Formát/Tools|IDG_VS_MM_TOOLSADDINS|  
|Okno/Help/Community|IDG_VS_MM_WINDOWHELP|  
|Doplňky|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Nabídky na řádku nabídek sady Visual Studio  
 Přidání skupiny do existující nabídky sady Visual Studio, nastavte jednu z následujících nabídek jako jeho nadřazený objekt. Podnabídek nejsou zahrnuté v tomto seznamu.  
  
|Nabídka|ID|  
|----------|--------|  
|Soubor|IDM_VS_MENU_FILE|  
|Upravit|IDM_VS_MENU_EDIT|  
|Zobrazit|IDM_VS_MENU_VIEW|  
|Refaktorovat|IDM_VS_MENU_REFACTORING|  
|Projekt|IDM_VS_MENU_PROJECT|  
|Sestavení|IDM_VS_MENU_BUILD|  
|Formát|IDM_VS_MENU_FORMAT|  
|Nástroje|IDM_VS_MENU_TOOLS|  
|Okno|IDM_VS_MENU_WINDOW|  
|Doplňky|IDM_VS_MENU_ADDINS|  
|Komunita|IDM_VS_MENU_COMMUNITY|  
|Nápověda|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Skupiny v nabídkách aplikace Visual Studio  
 Následující seznamy shrnují skupiny, ke kterým sestup přímo z nabídky na řádku nabídek sady Visual Studio. Nejrychlejší způsob, jak přidat příkaz nabídky sady Visual Studio je nastavte jednu z těchto skupin jako nadřazený. Skupiny, které sestup od podnabídek v této části nezobrazí.  
  
### <a name="file-menu-groups"></a>Soubor skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Nový/otevřít|IDG_VS_FILE_FILE|  
|Přidejte|IDG_VS_FILE_ADD|  
|Řešení|IDG_VS_FILE_SOLUTION|  
|Různé|IDG_VS_FILE_MISC|  
|Uložit|IDG_VS_FILE_SAVE|  
|přejmenování|IDG_VS_FILE_RENAME|  
|Prohlížeč|IDG_VS_FILE_BROWSER|  
|Tisk|IDG_VS_FILE_PRINT|  
|Naposledy použité|IDG_VS_FILE_MRU|  
|Přesunutí|IDG_VS_FILE_MOVE|  
|Ukončit|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Upravit skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Zpět/znovu|IDG_VS_EDIT_UNDOREDO|  
|Vyjmutí/zkopírování/vložení|IDG_VS_EDIT_CUTCOPY|  
|Vyberte|IDG_VS_EDIT_SELECT|  
|Příkaz GoTo|IDG_VS_EDIT_GOTO|  
|Najít|IDG_VS_EDIT_FIND|  
|Objekty|IDG_VS_EDIT_OBJECTS|  
|Příkazy OLE|IDG_VS_EDIT_OLEVERBS|  
|Příkaz dobře|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Refaktorovat skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Běžné|IDG_REFACTORING_COMMON|  
|Upřesnit|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Zobrazení skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Kód formuláře|IDG_VS_VIEW_FORMCODE|  
|Prohlížeč|IDG_VS_VIEW_BROWSER|  
|Definujte zobrazení|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|Návrhář Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Organizace Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Prohlížeč kódu|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Windows dev|IDG_VS_VIEW_DEV_WINDOWS|  
|Panely nástrojů|IDG_VS_VIEW_TOOLBARS|  
|Symboly|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Navigace|IDG_VS_VIEW_NAVIGATE|  
|Malý přejděte.|IDG_VS_VIEW_SMALLNAVIGATE|  
|prohlížeč objektů|IDG_VS_VIEW_OBJBRWSR|  
|Příkaz dobře|IDG_VS_VIEW_COMMANDWELL|  
|Stránky vlastností|IDG_VS_VIEW_PROPPAGES|  
|Aktualizace|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Projekt skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Různé přidat|IDG_VS_PROJ_MISCADD|  
|Přidejte|IDG_VS_PROJ_ADD|  
|Folder|IDG_VS_PROJ_FOLDER|  
|Uvolnění a opětovné načtení|IDG_VS_PROJ_UNLOADRELOAD|  
|Odkaz|IDG_VS_PROJ_REFERENCE|  
|Možnosti|IDG_VS_PROJ_OPTIONS|  
|Nastavení|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Vytvoření skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Řešení|IDG_VS_BUILD_SOLUTION|  
|Výběr|IDG_VS_BUILD_SELECTION|  
|Optimalizace na základě profilu|IDG_VS_PGO_SELECTION|  
|Různé|IDG_VS_BUILD_MISC|  
|Zrušit|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Skupina nabídky Nástroje  
  
|Skupina|ID|  
|-----------|--------|  
|Příkazový řádek|IDG_VS_TOOLS_CMDLINE|  
|Fragmenty kódu|IDG_VS_TOOLS_SNIPPETS|  
|Dílčí objekt|IDG_VS_TOOLS_OBJSUBSET|  
|Možnosti|IDG_VS_TOOLS_OPTIONS|  
|Další 2|IDG_VS_TOOLS_OTHER2|  
|Externí nástroje|IDG_VS_TOOLS_EXT_TOOLS|  
|Externí přizpůsobení|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Okno skupiny nabídek  
  
|Skupina|ID|  
|-----------|--------|  
|Nový|IDG_VS_WINDOW_NEW|  
|Ukotvit nebo zavřít.|IDG_VS_DOCKCLOSE|  
|Ukotvit nebo skrýt|IDG_VS_DOCKHIDE|  
|Uspořádat|IDG_VS_WINDOW_ARRANGE|  
|Navigace|IDG_VS_WINDOW_NAVIGATION|  
|Seznam|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Skupiny nabídek nápovědy  
  
|Skupina|ID|  
|-----------|--------|  
|Ukázky kódu|IDG_VS_HELP_SAMPLES|  
|Podpora|IDG_VS_HELP_SUPPORT|  
|O produktu|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Podnabídek nabídek sady Visual Studio  
 U následující hierarchie zobrazuje dílčích nabídek, které jsou spojeny s nabídkami v řádku nabídek sady Visual Studio. Protože nabídce jako jeho nadřazený objekt může mít pouze skupiny, každý podnabídky musí sestup ze skupiny v nabídce, namísto přímo z nabídky. Další informace o vztahu mezi nabídek, skupiny a podnabídek najdete v tématu [přidání podnabídky do nabídky](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Názvy nabídek na řádku nabídek sady Visual Studio se nezobrazují samostatně v této hierarchii vzhledem k tomu, že lze odvodit z zásady vytváření názvů skupin v integrovaném vývojovém prostředí, následujícím způsobem: *IDG_VS_\<název nabídky\>_\< Název skupiny\>*.  
  
|Nadřazená skupina|Podnabídka|Podřízené skupiny|  
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
  
## <a name="see-also"></a>Viz také:  
 [Identifikátory GUID a ID sady Visual Studio panelů nástrojů](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Příkazy identifikátory GUID a ID sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Soubory tabulky (.vsct) příkaz pro Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)