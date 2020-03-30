---
title: Převod mezi vlastností auto a úplnou vlastností
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395410"
---
# <a name="convert-between-auto-property-and-full-property"></a>Převod mezi vlastností auto a úplnou vlastností

Toto refaktoring se vztahuje na:

- C#

**Co:** Převést mezi automaticky implementované vlastnosti na úplnou vlastnost.

**Kdy:** Logika vlastnosti se změnila.

**Proč:** Můžete převést mezi automaticky implementované vlastnosti na úplnou vlastnost ručně, ale tato funkce bude automaticky dělat práci za vás. 

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na název vlastnosti.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
3. Vyberte z následujících dvou možností: 

    Vyberte **Převést na úplnou vlastnost**.

   ![Převést vlastnost auto na úplnou vlastnost](media/convert-auto-property-to-full-property.png) 

    Vyberte **Použít vlastnost auto**. 

    ![Převést úplnou vlastnost na automatickou vlastnost](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
