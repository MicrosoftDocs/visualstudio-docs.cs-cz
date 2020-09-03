---
title: Zjednodušení interpolace řetězců
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a8b0fd53164cb98921b111d49fa04a76c9d0d8a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094305"
---
# <a name="simplify-string-interpolation-refactoring"></a>Zjednodušit refaktoring řetězcové interpolace

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje zjednodušit [interpolaci řetězce](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation).

**Když:** Máte interpolaci řetězců, kterou lze zjednodušit.

**Proč:** Zjednodušení řetězcové interpolace může poskytnout větší srozumitelnou a stručnou syntaxi. Tento nástroj refaktoringu provede úlohu automaticky namísto ručního provedení.

## <a name="how-to"></a>Postupy

1. Umístit blikající kurzor na řetězcovou interpolaci:

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vybrat **zjednodušit interpolaci**

    ![Zjednodušení interpolace řetězců](media/simplify-string-interpolation.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)