---
title: Příkazy, nabídky a skupiny definované rozhraním IDE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707720"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím
Mnoho nabídek, příkazů a skupin příkazů je již definováno pro použití [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraním IDE. Tyto příkazy jsou k dispozici také pro vaše použití při rozšiřování [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Hledání příkazů definovaných prostředím
 Příkazy prostředí jsou definované v sadě čtyř souborů. vsct:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Tyto soubory jsou umístěny v *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc \\ . Tyto soubory obsahují definice a identifikátory GUID nabídek a skupin, které můžete použít v souboru konfigurace příkazového řádku (. vsct) své sady VSPackage jako kontejnery pro vlastní nabídky, skupiny a příkazy.

## <a name="in-this-section"></a>V tomto oddílu
- [Identifikátory GUID a ID nabídek sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Poskytuje hodnoty identifikátoru GUID a ID pro nabídky na řádku nabídek sady Visual Studio a ve skupinách, které obsahují.

- [Identifikátory GUID a ID panelů nástrojů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Poskytuje hodnoty identifikátoru GUID a ID pro panely nástrojů v integrovaném vývojovém prostředí sady Visual Studio a skupiny, které obsahují.

- [Identifikátory GUID a ID příkazů sady Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Poskytuje identifikátory GUID a ID příkazů, které jsou definovány v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
