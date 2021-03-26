---
title: IDE-Defined příkazy, nabídky a skupiny | Microsoft Docs
description: Seznamte se s nabídkami, příkazy a skupinami příkazů, které jsou definovány v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b88bbab9c92cdd8627521eaa58284fd33964b7e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085946"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Příkazy, nabídky a skupiny definované integrovaným vývojovým prostředím
Mnoho nabídek, příkazů a skupin příkazů je již definováno pro použití [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraním IDE. Tyto příkazy jsou k dispozici také pro vaše použití při rozšiřování [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Hledání příkazů Environment-Defined
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
