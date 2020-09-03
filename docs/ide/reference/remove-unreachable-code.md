---
title: Odebrání nedosažitelného refaktoringu kódu
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd827870f07fb3161674d287d20f266942e61afe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093984"
---
# <a name="remove-unreachable-code-refactoring"></a>Odebrání nedosažitelného refaktoringu kódu

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Odebere kód, který nebude nikdy proveden.

**Když:** Váš program nemá žádnou cestu k fragmentu kódu, takže fragment kódu není potřebný.

**Proč:** Vylepšit čitelnost a udržovatelnost odebráním kódu, který je nadbytečný a nebude nikdy proveden.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na libovolné místo v nedosažitelném kódu.

![Vybledlý nedosažitelný kód](media/unreachablecode-faded-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v okně Náhled vyberte možnost **Odebrat nedosažitelný kód** .
   - **Myš**
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

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
