---
title: Odebrání nedosažitelného refaktoringu kódu
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1e5bdab773cf70963e1d0f485a7779e57084c8a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655607"
---
# <a name="remove-unreachable-code-refactoring"></a>Odebrání nedosažitelného refaktoringu kódu

Tento refaktoring platí pro:

- C#

**Co:** Odebere kód, který nebude nikdy proveden.

**Když:** Váš program nemá žádnou cestu k fragmentu kódu, takže fragment kódu není potřebný.

**Proč:** Vylepšit čitelnost a udržovatelnost odebráním kódu, který je nadbytečný a nebude nikdy proveden.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na libovolné místo v nedosažitelném kódu.

![Vybledlý nedosažitelný kód](media/unreachablecode-faded-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v okně Náhled vyberte možnost **Odebrat nedosažitelný kód** .
   - **Stisknut**
      - Klikněte na kód pravým tlačítkem, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte **Odebrat nedosažitelný kód** .

1. Až budete s změnou spokojeni, stiskněte klávesu **ENTER** nebo klikněte na opravit v nabídce a změny se potvrdí.

Příklad:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)