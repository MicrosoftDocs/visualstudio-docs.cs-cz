---
title: Převod mezi automatickou a celou vlastností
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převádět mezi automaticky implementovanou vlastností a plnou vlastností.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3680444c07658da8e77b6058f5a71b9dcf119193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907603"
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
