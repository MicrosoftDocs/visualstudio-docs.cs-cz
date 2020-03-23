---
title: Nahrazení dočasné proměnné její hodnotou
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568864"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Inline dočasné proměnné refaktoring

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje odebrat dočasnou proměnnou a nahradit ji její hodnotou.

**Kdy:** Použití dočasné proměnné ztěžuje pochopení kódu.

**Proč:** Odebrání dočasné proměnné může usnadnit čtení kódu.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor uvnitř dočasné proměnné, která má být vložena:

   - C#:

       ![Zvýrazněný kód - C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – visual basic](media/inline-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
   - **Myš**
      - Klikněte pravým tlačítkem myši na kód a vyberte nabídku **Rychlé akce a Refaktoringy.**

3. V rozbalovacím okně Náhled vyberte **Vložkovou dočasnou proměnnou.**

   Proměnná je odebrána a její použití nahrazeno hodnotou proměnné.

   - C#:

      ![Inline výsledek - C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Vsazený výsledek – Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
