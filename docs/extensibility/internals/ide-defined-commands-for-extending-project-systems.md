---
title: Příkazy definované ide pro rozšíření projektových systémů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707739"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Příkazy definované prostředím IDE pro rozšíření systémů projektů
Chcete-li rozšířit projektové systémy, můžete použít příkazy a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] skupiny příkazů poskytované ide.

 V následujících částech jsou uvedeny položky příkazů, které jsou zvláště užitečné pro rozšíření projektových systémů.

## <a name="command-menus"></a>Nabídky příkazů
 V následující tabulce jsou uvedeny nabídky příkazů, které jsou užitečné umístění pro umístění příkazů vysoké úrovně, které vyvolávají rozšíření projektu.

|Nabídka Příkaz|Popis|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Nabídka **Projekt** nejvyšší úrovně.|
|IDM_VS_TOOL_PROJWIN|Panel nástrojů **Průzkumník řešení.**|

## <a name="shortcut-menus"></a>Místní nabídky
 V následující tabulce jsou uvedeny místní nabídky, které platí při výběru jednoho uzlu v **Průzkumníku řešení**nebo pokud je v **Průzkumníku řešení**více homogenních výběrů , což je doba, kdy jsou všechny vybrané uzly stejného typu.

|Místní nabídka|Popis|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Použije se, když je vybrán uzel projektu.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Použije se, když je vybrán soubor.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Použije se při výběru složky.|
|IDM_VS_CTXT_WEBREFFOLDER|Použije se, když je vybrána složka Webový odkaz.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Platí, když je vybrán kořenový uzel odkazů s názvem "Reference".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Platí, když jsou vybrány referenční uzly; patří mezi ně pouze odkazy na sestavení, COM a projekt. Neobsahuje webové odkazy.|

 V následující tabulce jsou uvedeny místní nabídky, které se použijí, když výběr v **Průzkumníku řešení** zahrnuje více hierarchií,

|Místní nabídka|Popis|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Platí, když aktuální výběr obsahuje uzel řešení a uzly kořenového projektu.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Platí, když aktuální výběr obsahuje uzel řešení a položky projektu.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Platí, když se aktuální výběr skládá pouze z více uzly kořenového projektu.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Použije se, když aktuální výběr obsahuje kombinaci kořenových uzly projektu a položek projektu. Kromě toho výběr může obsahovat uzel řešení.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Platí, pokud aktuální výběr obsahuje položky projektu z více projektů v řešení nebo pokud jsou ve stejném projektu vybrány položky různých typů.|

## <a name="command-groups"></a>Skupiny příkazů
 V následující tabulce jsou uvedeny skupiny příkazů, které lze použít <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> při rozšiřování projektů, a ke kterým máte přístup prostřednictvím místní nabídky.

|Skupina příkazů|Popis|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Příkazy pro vytváření, opětovné sestavení a nasazení projektu.|
|IDG_VS_CTXT_COMPILELINK|Příkazy pro kompilaci a propojení projektu.|
|IDG_VS_CTXT_PROJECT_CONFIG|Příkazy, které nastavují konfiguraci projektu a pořadí sestavení.|
|IDG_VS_CTXT_PROJECT_ADD|Příkazy, které přidávají položky do projektu.|
|IDG_VS_CTXT_PROJECT_START|Příkazy, které nastavují spouštěcí projekt přidružený ke klíči F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Příkazy pro ukládání položek projektu.|
|IDG_VS_CTXT_PROJECT_DEBUG|Příkazy pro ladění.|
|IDG_VS_CTXT_PROJECT_SCC|Příkazy pro svoz zdrojového kódu.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Příkazy pro operace vyjmutí, kopírování a vkládání.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Příkazy, které poskytují přístup k dialogovému oknu **Vlastnosti projektu.**|

## <a name="see-also"></a>Viz také

- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vytváření znovu použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md)
