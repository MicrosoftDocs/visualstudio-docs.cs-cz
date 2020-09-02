---
title: Dokončování DateTime a TimeSpan pomocí nabídky IntelliSense
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471548"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Dokončování DateTime a TimeSpan pomocí nabídky IntelliSense

Tento refaktoring platí pro:

- C#

**Co:** Literál řetězce DateTime a TimeSpan a formátování řetězce formátu v nabídce technologie IntelliSense.

**Když:** Chcete zapsat literál řetězce DateTime a TimeSpan a řetězec formátu. Technologie IntelliSense poskytuje základní dokončování a vysvětlení, co každý ze znaků znamená. 

**Proč:** Formátování formátu data a času je obtížné a technologie IntelliSense vám může usnadnit psaní.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do řetězce formátu DateTime nebo TimeSpan.
2. Stisknutím **klávesové zkratky CTRL** + **Space** aktivujte nabídku **IntelliSense** .
3. Vyberte znak, který chcete přidat.

   ![IntelliSense dokončování hodnoty DateTime](media/datetime-completion.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
