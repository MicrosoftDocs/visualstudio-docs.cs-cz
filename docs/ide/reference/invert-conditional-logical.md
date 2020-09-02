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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531679"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertovat podmíněné výrazy a podmíněné operátory AND/OR

Tento refaktoring platí pro:

- C#
- Visual Basic

**Co:** Umožňuje invertovat podmíněný výraz nebo podmíněný operátor AND/OR.

**Když:** Máte podmíněný výraz nebo podmíněný operátor AND/OR, který by měl být lépe srozumitelný, pokud se obrátí.

**Proč:** Obrácení výrazu nebo podmíněného operátoru OR ručně může trvat mnohem delší dobu a může způsobit chyby. Tato oprava kódu vám pomůže tento Refaktorovat automaticky.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Invertování podmíněných výrazů a podmíněného refaktoringu a/nebo operátorů

1. Umístěte kurzor do podmíněného výrazu nebo podmíněného operátoru OR.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte **Invertovat podmíněné** nebo **nahraďte ' && ' znakem ' | | '**

    ![Invertovat podmíněný](media/invert-conditional.png)

    ![Invertovat podmíněný](media/invert-logical-operator.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
