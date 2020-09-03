---
title: Nahradit dočasnou proměnnou její hodnotou
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8f0199436f5f9b1013a4c49cfb5909e760c73dcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568864"
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
