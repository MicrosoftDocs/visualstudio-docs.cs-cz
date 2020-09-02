---
title: Příkazy, nabídky a skupiny definované rozhraním IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192738"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mnoho nabídek, příkazů a skupin příkazů je již definováno pro použití [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rozhraním IDE. Tyto příkazy jsou k dispozici také pro vaše použití při rozšiřování [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Hledání příkazů definovaných prostředím  
 Příkazy prostředí jsou definované v sadě čtyř souborů. vsct:  
  
- SharedCmdDef. vsct  
  
- SharedCmdPlace. vsct  
  
- ShellCmdDef. vsct  
  
- ShellCmdPlace. vsct  
  
  Tyto soubory jsou umístěny v *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Tyto soubory obsahují definice a identifikátory GUID nabídek a skupin, které můžete použít v souboru konfigurace příkazového řádku (. vsct) své sady VSPackage jako kontejnery pro vlastní nabídky, skupiny a příkazy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Poskytuje hodnoty identifikátoru GUID a ID pro nabídky na řádku nabídek sady Visual Studio a ve skupinách, které obsahují.  
  
 [Identifikátory GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Poskytuje hodnoty identifikátoru GUID a ID pro panely nástrojů v integrovaném vývojovém prostředí sady Visual Studio a skupiny, které obsahují.  
  
 [Identifikátory GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Poskytuje identifikátory GUID a ID příkazů, které jsou definovány v integrovaném vývojovém prostředí sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Příkazová tabulka sady Visual Studio (. Soubory vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Příkazy definované rozhraním IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
