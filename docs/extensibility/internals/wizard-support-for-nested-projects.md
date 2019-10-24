---
title: Podpora průvodce pro vnořené projekty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721425"
---
# <a name="wizard-support-for-nested-projects"></a>Podpora průvodce pro vnořené projekty
Rozhraní IDE spustí dva průvodce, které může nadřazený projekt pro vnořené projekty implementovat: průvodce **vytvořením nového projektu** a průvodce **přidáním položky** .

 Pokud uživatel spustí průvodce **vytvořením** projektu výběrem možnosti **Přidat projekt** a kliknutím na **položku Nový projekt** v nabídce soubor nebo výběrem možnosti **Přidat** a kliknutím pravým tlačítkem myši na **Nový projekt** v Průzkumník řešení, rozhraní IDE spustí **AddProject** příkaz a implementace nadřazeného projektu **AddProject** příkazu vrátí buď soubor šablony projektu, nebo soubor průvodce (. vsz), který má sadu kontextových parametrů.

 Podobně implementace průvodců **AddItem** nadřazeného projektu vrátí soubor. vsz, který má jinou sadu kontextových parametrů.

 Další informace o průvodcích najdete v tématu [Průvodce (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [kontextové parametry](../../extensibility/internals/context-parameters.md) a [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)