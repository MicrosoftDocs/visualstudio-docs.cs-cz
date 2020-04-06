---
title: Příkazy, nabídky a skupiny definované ide | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707720"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím
Mnoho nabídek, příkazů a skupin příkazů jsou již [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definovány pro použití ide. Tyto příkazy jsou také k dispozici [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pro použití při rozšíření .

## <a name="finding-environment-defined-commands"></a>Hledání příkazů definovaných prostředím
 Příkazy prostředí jsou definovány v sadě čtyř souborů .vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Tyto soubory jsou umístěny v\\ * \<instalační cestě sady Visual Studio SDK>\VisualStudioIntegration\Common\Inc *. Tyto soubory poskytují definice a identifikátory GUID nabídek a skupin, které můžete použít v souboru konfigurace příkazové tabulky (.vsct) vašeho balíčku VSPackage jako kontejnery pro vlastní nabídky, skupiny a příkazy.

## <a name="in-this-section"></a>V tomto oddílu
- [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Poskytuje hodnoty GUID a ID nabídek na panelu nabídek sady Visual Studio a skupin, které obsahují.

- [Identifikátory GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Poskytuje hodnoty GUID a ID panelů nástrojů v rozhraní IDE sady Visual Studio a skupin, které obsahují.

- [Identifikátory GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Poskytuje hodnoty GUID a ID příkazů definovaných rozhraním IDE sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
