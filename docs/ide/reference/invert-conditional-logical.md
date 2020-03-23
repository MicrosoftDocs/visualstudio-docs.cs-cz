---
title: Invertování podmíněných výrazů a logických operací
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531679"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertovat podmíněné výrazy a podmíněné operátory AND/OR

Toto refaktoring se vztahuje na:

- C#
- Visual Basic

**Co:** Umožňuje invertovat podmíněný výraz nebo podmíněný operátor AND/OR.

**Kdy:** Máte podmíněný výraz nebo podmíněný operátor AND/OR, který by byl lépe pochopen, pokud by byl invertován.

**Proč:** Ruční obrácení výrazu nebo podmíněného operátoru AND/OR může trvat mnohem déle a případně může zavést chyby. Tato oprava kódu vám pomůže provést tento refaktoring automaticky.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Invertovat podmíněné výrazy a podmíněné operátory AND/OR refaktoring

1. Umístěte kurzor do podmíněného výrazu nebo podmíněného operátoru AND/OR.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
3. Vyberte **Invertovat podmíněné** nebo **Nahradit && s '||'**

    ![Invertovat podmíněné](media/invert-conditional.png)

    ![Invertovat podmíněné](media/invert-logical-operator.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)
