---
title: Označení členů jako statických
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring učinit člena statickou.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5478e85d89d4ea44d34e0a5ae9170aaffb3836f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919445"
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
