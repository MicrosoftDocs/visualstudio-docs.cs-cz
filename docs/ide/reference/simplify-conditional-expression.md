---
title: Zjednodušení logických výrazů
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring zjednodušit podmíněný výraz.
ms.custom: SEO-VS-2020
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: dd7b3f29e804ec5e925c34f7994164d5a8465a50
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480210"
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