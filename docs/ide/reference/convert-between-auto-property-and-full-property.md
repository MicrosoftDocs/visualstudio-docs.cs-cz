---
title: Převod mezi automatickou a celou vlastností
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395410"
---
# <a name="convert-between-auto-property-and-full-property"></a>Převod mezi automatickou a celou vlastností

Tento refaktoring platí pro:

- C#

**Co:** Převeďte mezi automaticky implementovanou vlastností na vlastnost Full.

**Když:** Logika vlastnosti se změnila.

**Proč:** Automaticky implementovanou vlastnost můžete převést na úplnou vlastnost ručně, ale tato funkce automaticky provede práci za vás. 

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na název vlastnosti.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte z následujících dvou možností: 

    Vyberte **převést na celou vlastnost**.

   ![Převést vlastnost auto na vlastnost Full](media/convert-auto-property-to-full-property.png) 

    Vyberte **použít automatickou vlastnost**. 

    ![Převést vlastnost Full na vlastnost auto](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
