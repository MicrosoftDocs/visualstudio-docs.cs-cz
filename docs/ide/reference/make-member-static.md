---
title: Označení členů jako statických
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring učinit člena statickou.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e663d59f47728bc4a7c84290ee0e89ae453f23ae
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561016"
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

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
