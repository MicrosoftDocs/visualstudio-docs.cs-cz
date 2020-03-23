---
title: Vytvořit člen statický
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515300"
---
# <a name="make-member-static"></a>Vytvořit člen statický

Toto refaktoring se vztahuje na:

- C#

**Co:** Vytvořte člen statický.

**Kdy:** Chcete, aby nestatický člen byl statický.

**Proč:** Statické členy zlepšit čitelnost: s vědomím, že konkrétní kód je izolován usnadňuje pochopení, opětovné čtení a opětovné použití. 

## <a name="how-to"></a>Postupy

1. Umístěte stříšku na jméno člena.

2. Stiskněte **klávesu Ctrl**+**.** (tečka) pro spuštění nabídky **Rychlé akce a Refaktorings.**

   ![Vytvořit člen statický](media/make-member-static.png)

3. Vyberte **Nastavit jako statickou**.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
