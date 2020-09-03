---
title: Podpora průvodce pro vnořené projekty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 206fd12ea8f198e1659a49ed566e726e49878c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180343"
---
# <a name="wizard-support-for-nested-projects"></a>Podpora průvodce pro vnořené projekty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozhraní IDE spustí dva průvodce, které může nadřazený projekt pro vnořené projekty implementovat: průvodce **vytvořením nového projektu** a průvodce **přidáním položky** .  
  
 Pokud uživatel spustí průvodce **vytvořením** projektu výběrem možnosti **Přidat projekt** a kliknutím na **položku Nový projekt** v nabídce soubor nebo výběrem možnosti **Přidat** a kliknutím pravým tlačítkem myši na **Nový projekt** v Průzkumník řešení, rozhraní IDE spustí příkaz **AddProject** a implementace nadřazeného projektu příkazu **AddProject** vrátí buď soubor šablony projektu, nebo soubor průvodce (. vsz), který má sadu kontextových parametrů.  
  
 Podobně implementace průvodců **AddItem** nadřazeného projektu vrátí soubor. vsz, který má jinou sadu kontextových parametrů.  
  
 Další informace o průvodcích najdete v tématu [Průvodce (. Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [kontextové parametry](../../extensibility/internals/context-parameters.md) a [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
