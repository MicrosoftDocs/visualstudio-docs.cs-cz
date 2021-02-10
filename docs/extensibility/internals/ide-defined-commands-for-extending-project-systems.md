---
title: IDE-Defined příkazy pro rozšíření systémů projektů | Microsoft Docs
description: Přečtěte si o příkazech a skupinách příkazů definovaných v integrovaném vývojovém prostředí (IDE) sady Visual Studio, které se používá pro rozšiřování systémů projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a08d60a52ed970781ceafdb15d0d5c64440f0cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968070"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Příkazy definované prostředím IDE pro rozšíření systémů projektů
Chcete-li zvětšit systémy projektu, můžete použít příkazy a skupiny příkazů poskytované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraním IDE.

 V následujících oddílech jsou uvedeny položky příkazů, které jsou zvláště užitečné pro rozšiřování systémů projektů.

## <a name="command-menus"></a>Nabídky příkazů
 V následující tabulce jsou uvedeny nabídky příkazů, které jsou užitečným umístěním, kde můžete umístit příkazy vysoké úrovně, které vyvolají zařízení s podporou projektu.

|Nabídka příkazů|Description|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Nabídka na nejvyšší úrovni **projektu** .|
|IDM_VS_TOOL_PROJWIN|Panel nástrojů **Průzkumník řešení** .|

## <a name="shortcut-menus"></a>Místní nabídky
 V následující tabulce jsou uvedeny místní nabídky, které se použijí, když je vybrán jeden uzel v **Průzkumník řešení**, nebo když v **Průzkumník řešení** existuje více homogenních výběrů, což znamená, že všechny vybrané uzly mají stejný typ.

|Místní nabídka|Description|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Platí v případě, že je vybrán uzel projektu.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Použije se při výběru souboru.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Použije se, když je vybraná složka.|
|IDM_VS_CTXT_WEBREFFOLDER|Platí, pokud je vybrána složka webové odkazy.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Platí v případě, že je vybrána možnost kořenový uzel odkazů s názvem odkazy.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Platí, pokud jsou vybrány referenční uzly; mezi ně patří pouze sestavení, COM a odkazy na projekt. Nezahrnuje webové odkazy.|

 V následující tabulce jsou uvedeny místní nabídky, které se použijí, pokud výběr v **Průzkumník řešení** zahrnuje více hierarchií,

|Místní nabídka|Description|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Platí v případě, že aktuální výběr obsahuje uzel řešení a uzly kořenového projektu.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Platí, pokud aktuální výběr obsahuje uzel řešení a položky projektu.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Platí v případě, že aktuální výběr se skládá pouze z více kořenových uzlů projektu.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Platí, pokud aktuální výběr obsahuje kombinaci kořenových uzlů projektu a položek projektu. Kromě toho výběr může obsahovat uzel řešení.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Platí v případě, že aktuální výběr obsahuje položky projektu z více projektů v řešení nebo když jsou v rámci stejného projektu vybrány položky různých typů.|

## <a name="command-groups"></a>Skupiny příkazů
 V následující tabulce jsou uvedeny skupiny příkazů, které lze použít při rozšiřování projektů a k přístupu prostřednictvím <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> místní nabídky.

|Skupina příkazů|Description|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Příkazy pro sestavování, resestavení a nasazení projektu.|
|IDG_VS_CTXT_COMPILELINK|Příkazy pro kompilaci a propojení projektu.|
|IDG_VS_CTXT_PROJECT_CONFIG|Příkazy, které nastavují konfiguraci projektu a pořadí sestavení.|
|IDG_VS_CTXT_PROJECT_ADD|Příkazy, které přidávají položky do projektu.|
|IDG_VS_CTXT_PROJECT_START|Příkazy, které nastaví spouštěný projekt přidružený k klávesě F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Příkazy pro ukládání položek projektu.|
|IDG_VS_CTXT_PROJECT_DEBUG|Příkazy pro ladění.|
|IDG_VS_CTXT_PROJECT_SCC|Příkazy pro správu zdrojového kódu|
|IDG_VS_CTXT_PROJECT_TRANSFER|Příkazy pro operace vyjmutí, kopírování a vložení.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Příkazy, které poskytují přístup k dialogovému oknu **Vlastnosti projektu** .|

## <a name="see-also"></a>Viz také

- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vytváření znovu použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md)
