---
title: Příkazy, nabídky a skupiny definované rozhraním IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727287"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím
Mnoho nabídek, příkazů a skupin příkazů je již definováno pro použití rozhraním IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Tyto příkazy jsou k dispozici také pro vaše použití při rozšiřování [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Hledání příkazů definovaných prostředím
 Příkazy prostředí jsou definované v sadě čtyř souborů. vsct:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Tyto soubory jsou umístěny v *instalační cestě sady \<Visual Studio SDK >* \VisualStudioIntegration\Common\Inc \\. Tyto soubory obsahují definice a identifikátory GUID nabídek a skupin, které můžete použít v souboru konfigurace příkazového řádku (. vsct) své sady VSPackage jako kontejnery pro vlastní nabídky, skupiny a příkazy.

## <a name="in-this-section"></a>V tomto oddílu
- [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Poskytuje hodnoty identifikátoru GUID a ID pro nabídky na řádku nabídek sady Visual Studio a ve skupinách, které obsahují.

- [Identifikátory GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Poskytuje hodnoty identifikátoru GUID a ID pro panely nástrojů v integrovaném vývojovém prostředí sady Visual Studio a skupiny, které obsahují.

- [Identifikátory GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Poskytuje identifikátory GUID a ID příkazů, které jsou definovány v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také:
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)