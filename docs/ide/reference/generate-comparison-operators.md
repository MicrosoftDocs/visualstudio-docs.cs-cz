---
title: Generovat operátory porovnání pro typy, které implementují IComparable
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290336"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Generovat operátory porovnání pro typy, které implementují IComparable

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje generovat operátory **porovnání** pro typy, které implementují IComparable.

**Když:** Máte typ, který implementuje rozhraní IComparable, automaticky přidáte operátory porovnání.

**Proč:** Pokud implementujete typ hodnoty, měli byste zvážit přepsání metody **Equals** , aby se zvýšil výkon při výchozí implementaci metody Equals na ValueType.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor buď dovnitř třídy, nebo do klíčového slova IComparable.

2. Dále proveďte jednu z následujících akcí:

   - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .

   - Klikněte na ![screwdriver](../media/screwdriver-icon.png) ikona, která se zobrazí na levém okraji

   ![Vygenerování operátorů porovnání](media/generate-comparison-operators.png)

3. V rozevírací nabídce vyberte **Generovat Equals (objekt)** .

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
