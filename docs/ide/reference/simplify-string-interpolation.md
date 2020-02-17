---
title: Zjednodušit interpolaci řetězců
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 15f034b0ecf46e19681f3b74e4137a2de9e9d950
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280752"
---
# <a name="simplify-string-interpolation-refactoring"></a>Zjednodušit refaktoring řetězcové interpolace

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zjednodušit [interpolaci řetězce](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Když:** Máte interpolaci řetězců, kterou lze zjednodušit.

**Proč:** Zjednodušení řetězcové interpolace může poskytnout větší srozumitelnou a stručnou syntaxi. Tento nástroj refaktoringu provede úlohu automaticky namísto ručního provedení.

## <a name="how-to"></a>Postupy

1. Umístit blikající kurzor na řetězcovou interpolaci:

2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vybrat **zjednodušit interpolaci**

    ![Zjednodušit interpolaci řetězců](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Viz také

- [Refaktoring](../refactoring-in-visual-studio.md)