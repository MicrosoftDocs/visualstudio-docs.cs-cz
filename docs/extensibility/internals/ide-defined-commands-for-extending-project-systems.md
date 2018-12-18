---
title: Příkazy definované IDE pro rozšíření projektu systémy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4941f5d842f311f078594ee9a9deef02219ea05d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132012"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Příkazy definované IDE pro rozšíření projektu systémy
Pokud chcete rozšířit projektu systémů, můžete použít příkazy a příkaz skupiny poskytované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Následující části uvádějí příkaz položky, které jsou užitečné zejména pro rozšíření projektu systémy.  
  
## <a name="command-menus"></a>Příkaz nabídky  
 V následující tabulce jsou uvedeny příkaz nabídky, které jsou užitečné umístění můžete uvést vysoké úrovně příkazy, které vyvolání rozšiřujícího objektu projektu.  
  
|Příkaz nabídky|Popis|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Projektu** nabídek nejvyšší úrovně.|  
|IDM_VS_TOOL_PROJWIN|**Průzkumníku řešení** panelu nástrojů.|  
  
## <a name="shortcut-menus"></a>Místní nabídky  
 V následující tabulce jsou uvedeny místní nabídky, které se vztahují, když je vybraný jeden uzel v **Průzkumníku řešení**, nebo když se více homogenního výběrů v **Průzkumníku**, který je při všechny vybrané uzly jsou stejného typu.  
  
|Místní nabídky|Popis|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Platí, když je vybrán uzel projektu.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Platí, když je vybrán soubor.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Použije, pokud je vybrána složka.|  
|IDM_VS_CTXT_WEBREFFOLDER|Použije, pokud je vybrána složka webový odkaz.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Platí, pokud je vybrána odkazů na kořenový uzel nazývají "Odkazy".|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Platí, pokud jsou vybrané uzly odkaz; mezi ně patří sestavení modelu COM a pouze odkazy na projekt. Nezahrnuje webové odkazy.|  
  
 V následující tabulce jsou uvedeny místní nabídky, které platí při výběru v **Průzkumníku řešení** zahrnuje více hierarchií,  
  
|Místní nabídky|Popis|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Použije, pokud aktuální výběr obsahuje uzel řešení a kořenové uzly projektu.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Použije, pokud aktuální výběr obsahuje položky uzel a projekt řešení.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Platí, když se skládá z několika kořenové uzly projektu pouze aktuální výběr.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Použije, pokud aktuální výběr obsahuje kombinaci kořenových uzlů projektu a položky projektu. Výběr kromě toho může obsahovat uzel řešení.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Použije, když aktuální výběr obsahuje položky projektu z více projekty v řešení, nebo když je vybraných položek různých typů v rámci jednoho projektu.|  
  
## <a name="command-groups"></a>Příkaz skupiny  
 V následující tabulce jsou uvedeny příkaz skupiny, které můžete použít, když rozšíříte projekty a který je k dispozici prostřednictvím <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> místní nabídky.  
  
|Skupina příkazu|Popis|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Příkazy pro vytváření, opětovné sestavení a nasazení projektu.|  
|IDG_VS_CTXT_COMPILELINK|Příkazy pro kompilaci a propojení projektu.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Příkazy, které nastavit konfiguraci projektu a pořadí sestavení.|  
|IDG_VS_CTXT_PROJECT_ADD|Příkazy, které přidání položek do projektu.|  
|IDG_VS_CTXT_PROJECT_START|Příkazy, které nastavit přidružené klávesy F5 projekt po spuštění.|  
|IDG_VS_CTXT_PROJECT_SAVE|Příkazy pro uložení položky projektu.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Příkazy pro ladění.|  
|IDG_VS_CTXT_PROJECT_SCC|Příkazy pro řízení zdrojů.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Příkazy pro vyjmutí, operace kopírování a vkládání.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Příkazy, které poskytují přístup k **vlastnosti projektu** dialogové okno.|  
  
## <a name="see-also"></a>Viz také  
 [Jak přidat VSPackages prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Vytváření znovu použitelných skupin tlačítek](../../extensibility/creating-reusable-groups-of-buttons.md)