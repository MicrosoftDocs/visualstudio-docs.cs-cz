---
title: Označit člen jako statický
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
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515300"
---
# <a name="make-member-static"></a>Označit člen jako statický

Tento refaktoring platí pro:

- C#

**Co:** Vytvořte člen jako statický.

**Když:** Chcete, aby byl nestatický člen statický.

**Proč:** Statické členy zlepšují čitelnost: s vědomím, že konkrétní kód je izolovaný, usnadňuje pochopení, opětovné čtení a opakované použití. 

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na název člena.

2. Stiskněte klávesu **Ctrl**+ **.** (tečka) pro aktivaci nabídky **rychlé akce a refaktoringu** .

   ![Označit člen jako statický](media/make-member-static.png)

3. Vyberte **Nastavit jako statickou**.

## <a name="see-also"></a>Viz také

- [Refaktoring](../refactoring-in-visual-studio.md)
