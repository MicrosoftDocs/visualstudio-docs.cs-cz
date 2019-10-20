---
title: Nahradit dočasnou proměnnou její hodnotou
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8b758407dc5500630157050c10f881a6515e1216
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661016"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Vložené dočasné refaktoring proměnných

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje odebrat dočasnou proměnnou a nahradit ji hodnotou místo ní.

**Když:** Použití dočasné proměnné usnadňuje pochopení kódu.

**Proč:** Odebrání dočasné proměnné může usnadnit čtení kódu.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do dočasné proměnné, která bude vložena:

   - C#:

       ![Zvýrazněný kód –C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/inline-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Stisknut**
      - Klikněte pravým tlačítkem na kód a vyberte nabídku **rychlé akce a refaktoring** .

3. V překryvném okně náhledu vyberte možnost **vložená dočasná proměnná** .

   Proměnná je odebrána a její použití nahrazeno hodnotou proměnné.

   - C#:

      ![Vložený výsledek –C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Vložený výsledek – Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)