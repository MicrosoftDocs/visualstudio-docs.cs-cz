---
title: Podpora průvodce vnořených projektů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703197"
---
# <a name="wizard-support-for-nested-projects"></a>Podpora průvodce pro vnořené projekty
Rozhraní IDE spustí dva průvodce, které může implementovat nadřazený projekt pro vnořené projekty: Průvodce **novým projektem** a Průvodce **přidáním položky.**

 Pokud uživatel spustí Průvodce **novým projektem** tak, že v nabídce Soubor **vyberete Přidat projekt** a klepnete na tlačítko **Přidat** a klepnete pravým tlačítkem myši na Nový **projekt,** spustí ide příkaz **AddProject** a implementace příkazu **AddProject** nadřazeného projektu vrátí soubor projektu šablony nebo soubor průvodce (.vsz), který má sadu kontextových parametrů. **Add**

 Podobně nadřazený projekt implementace **AddItem** průvodců vrátí soubor .vsz, který má jinou sadu parametrů kontextu.

 Další informace o čarodějích naleznete v [průvodci (. Vsz) soubor](../../extensibility/internals/wizard-dot-vsz-file.md), [kontextové parametry](../../extensibility/internals/context-parameters.md) a [registrace projektů a šablon položek](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
