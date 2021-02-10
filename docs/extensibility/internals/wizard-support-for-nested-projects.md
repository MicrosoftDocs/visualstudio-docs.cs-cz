---
title: Podpora průvodce pro vnořené projekty | Microsoft Docs
description: Přečtěte si o dvou průvodcích, které může nadřazený projekt implementovat pro vnořené projekty ve VSPackage v sadě Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f2cd84379ead1cd45296ae370aab215a37cf4b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935868"
---
# <a name="wizard-support-for-nested-projects"></a>Podpora průvodce pro vnořené projekty
Rozhraní IDE spustí dva průvodce, které může nadřazený projekt pro vnořené projekty implementovat: průvodce **vytvořením nového projektu** a průvodce **přidáním položky** .

 Pokud uživatel spustí průvodce **vytvořením** projektu výběrem možnosti **Přidat projekt** a kliknutím na **položku Nový projekt** v nabídce soubor nebo výběrem možnosti **Přidat** a kliknutím pravým tlačítkem myši na **Nový projekt** v Průzkumník řešení, rozhraní IDE spustí příkaz **AddProject** a implementace nadřazeného projektu příkazu **AddProject** vrátí buď soubor šablony projektu, nebo soubor průvodce (. vsz), který má sadu kontextových parametrů.

 Podobně implementace průvodců **AddItem** nadřazeného projektu vrátí soubor. vsz, který má jinou sadu kontextových parametrů.

 Další informace o průvodcích najdete v tématu [Průvodce (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [kontextové parametry](../../extensibility/internals/context-parameters.md) a [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
