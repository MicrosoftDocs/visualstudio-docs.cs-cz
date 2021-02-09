---
title: Nahradit dočasnou proměnnou její hodnotou
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring odebrat dočasnou proměnnou a místo ní ji nahradit její hodnotou.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ebe062d5dd569ae1d2162ea7334f91d8b82decdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852372"
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

       ![Zvýrazněný kód-C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/inline-highlight-vb.png)

2. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   - **Myš**
      - Klikněte pravým tlačítkem na kód a vyberte nabídku **rychlé akce a refaktoring** .

3. V překryvném okně náhledu vyberte možnost **vložená dočasná proměnná** .

   Proměnná je odebrána a její použití nahrazeno hodnotou proměnné.

   - C#:

      ![Vložený výsledek – C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Vložený výsledek – Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
