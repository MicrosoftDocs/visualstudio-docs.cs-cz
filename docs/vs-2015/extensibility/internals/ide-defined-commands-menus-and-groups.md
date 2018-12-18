---
title: Příkazy definované prostředím IDE, nabídky a skupiny | Dokumentace Microsoftu
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
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20fc9e69224f45a5e50462d38b4b2001e3122b49
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776756"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Počet nabídek, příkazy a skupinu příkazů jsou již definovány pro použití [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Tyto příkazy jsou také k dispozici pro použití při rozšíření [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Hledání příkazů prostředí definované  
 Příkazy prostředí jsou definovány v sadě čtyři soubory .vsct:  
  
- SharedCmdDef.vsct  
  
- SharedCmdPlace.vsct  
  
- ShellCmdDef.vsct  
  
- ShellCmdPlace.vsct  
  
  Tyto soubory jsou umístěny v  *\<Visual Studio SDK instalační_cesta >* \VisualStudioIntegration\Common\Inc\\. Tyto soubory poskytují definice a identifikátory GUID nabídek a skupiny, které můžete použít v souboru konfigurace (.vsct) tabulky příkazů z vašeho balíčku VSPackage jako kontejnery pro nabídky, skupiny a příkazy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Poskytuje hodnoty GUID a ID nabídky na řádku nabídek sady Visual Studio a skupin, které obsahují.  
  
 [Identifikátory GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Poskytuje hodnoty GUID a ID panelů nástrojů v sadě Visual Studio IDE a skupin, které obsahují.  
  
 [Identifikátory GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Poskytuje hodnoty GUID a ID příkazy definované v integrovaném vývojovém prostředí sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Tabulky příkazů sady Visual Studio (. Soubory Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

