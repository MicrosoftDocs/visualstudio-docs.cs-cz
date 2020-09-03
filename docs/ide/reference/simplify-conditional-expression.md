---
title: Zjednodušení logických výrazů
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
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

    ![Zjednodušení logických výrazů](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)