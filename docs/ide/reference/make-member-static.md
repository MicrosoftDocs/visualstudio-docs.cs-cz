---
title: Označení členů jako statických
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77515300"
---
# <a name="make-member-static"></a>Označení členů jako statických

Tento refaktoring platí pro:

- C#

**Co:** Vytvořte člen jako statický.

**Když:** Chcete, aby byl nestatický člen statický.

**Proč:** Statické členy zlepšují čitelnost: s vědomím, že konkrétní kód je izolovaný, usnadňuje pochopení, opětovné čtení a opakované použití. 

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na název člena.

2. Stiskněte klávesu **CTRL** + **.** (tečka) pro aktivaci nabídky **rychlé akce a refaktoringu** .

   ![Označení členů jako statických](media/make-member-static.png)

3. Vyberte **Nastavit jako statickou**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
