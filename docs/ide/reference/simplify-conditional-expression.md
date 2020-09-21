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
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810347"
---
# <a name="simplify-conditional-expression-refactoring"></a>Zjednodušení refaktoringu podmíněného výrazu

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zjednodušit [podmíněný výraz](/dotnet/csharp/language-reference/operators/conditional-operator).

**Když:** Chcete odstranit zbytečný kód, který by poskytoval větší přehlednost.

**Proč:** Zjednodušení podmíněného výrazu může poskytovat větší srozumitelnou a stručnou syntaxi. Tento nástroj refaktoringu provede úlohu automaticky namísto ručního provedení.

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na podmíněný výraz:

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vybrat **zjednodušit podmíněný výraz**

    ![Zjednodušení logických výrazů](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)