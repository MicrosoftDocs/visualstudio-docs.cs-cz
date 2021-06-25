---
title: IDE-Defined příkazy pro rozšíření projektových systémů | Microsoft Docs
description: Seznamte se s příkazy a skupinami příkazů definovanými v Visual Studio integrované vývojové prostředí (IDE), které se používají k rozšíření systémů projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4525802bf308d740ea5c468fac171e74bff2b34e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901159"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Příkazy definované prostředím IDE pro rozšíření systémů projektů
Pokud chcete rozšířit systémy projektů, můžete použít příkazy a skupiny příkazů poskytované rozhraním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Následující části obsahují seznam položek příkazů, které jsou zvláště užitečné pro rozšíření systémů projektů.

## <a name="command-menus"></a>Nabídky příkazů
 V následující tabulce jsou uvedeny nabídky příkazů, které jsou užitečnými umístěními pro zadání příkazů vysoké úrovně, které vyvolaly rozšiřující projekt.

|Příkazová nabídka|Description|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Nabídka **nejvyšší** úrovně Projektu.|
|IDM_VS_TOOL_PROJWIN|Panel **Průzkumník řešení** panelu nástrojů.|

## <a name="shortcut-menus"></a>Místní nabídky
 Následující tabulka uvádí místní nabídky, které se použijí při výběru jednoho uzlu v **Průzkumník řešení** nebo při více homogenních výběrech v **Průzkumník řešení**, což znamená, že všechny vybrané uzly jsou stejného typu.

|Místní nabídka|Description|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Platí, když je vybraný uzel projektu.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Platí, když je vybraný soubor.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Platí, když je vybraná složka.|
|IDM_VS_CTXT_WEBREFFOLDER|Platí, když je vybraná složka Webový odkaz.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Platí, když je vybraný kořenový uzel odkazy s názvem Odkazy.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Použije se, když jsou vybrané referenční uzly. Patří mezi ně pouze odkazy na sestavení, com a projekt. Nezahrnuje webové odkazy.|

 Následující tabulka uvádí místní nabídky, které se použijí, když výběr v Průzkumník řešení **více** hierarchií.

|Místní nabídka|Description|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Platí, když aktuální výběr obsahuje uzel řešení a kořenové uzly projektu.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Platí, když aktuální výběr obsahuje uzel řešení a položky projektu.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Platí pouze v případě, že se aktuální výběr skládá z několika kořenových uzlů projektu.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Platí, když aktuální výběr obsahuje kombinaci kořenových uzlů projektu a položek projektu. Kromě toho může výběr obsahovat uzel řešení.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Platí, když aktuální výběr obsahuje položky projektu z více projektů v řešení nebo když jsou položky různých typů vybrány ve stejném projektu.|

## <a name="command-groups"></a>Skupiny příkazů
 Následující tabulka uvádí skupiny příkazů, které můžete použít při rozšíření projektů a které jsou dostupné prostřednictvím <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> místní nabídky.

|Skupina příkazů|Description|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Příkazy pro sestavení, opětovné sestavení a nasazení projektu.|
|IDG_VS_CTXT_COMPILELINK|Příkazy pro kompilaci a propojení projektu.|
|IDG_VS_CTXT_PROJECT_CONFIG|Příkazy, které nastaví konfiguraci projektu a pořadí sestavení.|
|IDG_VS_CTXT_PROJECT_ADD|Příkazy, které přidávají položky do projektu.|
|IDG_VS_CTXT_PROJECT_START|Příkazy, které nastaví spouštěný projekt přidružený ke klíči F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Příkazy pro ukládání položek projektu|
|IDG_VS_CTXT_PROJECT_DEBUG|Příkazy pro ladění.|
|IDG_VS_CTXT_PROJECT_SCC|Příkazy pro řízení zdrojového kódu.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Příkazy pro operace vyjmutí, kopírování a vložení.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Příkazy, které poskytují přístup k **dialogovému oknu Vlastnosti** projektu.|

## <a name="see-also"></a>Viz také

- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vytváření znovu použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md)
