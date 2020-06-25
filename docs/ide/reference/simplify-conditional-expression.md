---
title: Zjednodušit podmíněný výraz
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d0571c01217441d4a39fbfe6fb58ccfe95fd0c5a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290385"
---
# <a name="simplify-conditional-expression-refactoring"></a>Zjednodušení refaktoringu podmíněného výrazu

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zjednodušit [podmíněný výraz](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

**Když:** Chcete odstranit zbytečný kód, který by poskytoval větší přehlednost.

**Proč:** Zjednodušení podmíněného výrazu může poskytovat větší srozumitelnou a stručnou syntaxi. Tento nástroj refaktoringu provede úlohu automaticky namísto ručního provedení.

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na podmíněný výraz:

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vybrat **zjednodušit podmíněný výraz**

    ![Zjednodušit podmíněný výraz](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)