---
title: Podpora průvodce pro vnořené projekty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e8a32db2542ae1729a7fdc87cc2ab32845f8ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137492"
---
# <a name="wizard-support-for-nested-projects"></a>Podpora průvodce pro vnořené projekty
Rozhraní IDE spustí dvou průvodců, které můžete implementovat nadřazený projekt pro vnořené projekty: **nový projekt** průvodce a **přidat položku** průvodce.  
  
 Pokud uživatel spustí **nový projekt** Průvodce výběrem **přidat projekt** a kliknutím na **nový projekt** v nabídce Soubor nebo výběrem **přidat** a kliknete pravým tlačítkem **nový projekt** v Průzkumníku řešení rozhraní IDE spustí **AddProject** příkaz a provádění nadřazený projekt **AddProject**příkaz buď vrátí soubor šablony projektu, nebo soubor průvodce (.vsz), který obsahuje sadu kontextové parametry.  
  
 Podobně nadřazený projekt implementace **AddItem** průvodců vrátí .vsz Soubor, který má jinou sadu kontextové parametry.  
  
 Další informace o Průvodci najdete v tématu [průvodce (. Soubor vsz)](../../extensibility/internals/wizard-dot-vsz-file.md), [kontextové parametry](../../extensibility/internals/context-parameters.md) a [registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Vnoření projektů](../../extensibility/internals/nesting-projects.md)