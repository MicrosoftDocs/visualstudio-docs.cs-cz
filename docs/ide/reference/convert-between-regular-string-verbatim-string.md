---
title: Převod mezi literály běžných řetězců a literály doslovných řetězců
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 7e8e239f53f92727072a2fcd6573d6957b7cd3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290333"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Převod mezi regulárním řetězcem a doslovném přefaktoringem řetězcových literálů

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje převádět mezi regulárním řetězcem a doslovnémi textovými literály.

**Když:** Buď chcete ušetřit místo nebo poskytnout větší přehlednost kódu.

**Proč:** Převod doslovného řetězcového literálu na regulární řetězcový literál může přispět k úspory místa. Převádění regulárního řetězcového literálu na doslovné řetězcový literál může poskytovat větší přehlednost.

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor buď na běžný řetězec, nebo na doslovné řetězcový literál:

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vyberte jednu z následujících možností: 

    Vyberte **Převést na běžný řetězec**.

    ![Převést na běžný řetězec](media/convert-to-regular-string.png)

    Vyberte **Převést na doslovný řetězec**.

    ![Převést na doslovné řetězec](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)