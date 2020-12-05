---
title: Odebrání nedosažitelného refaktoringu kódu
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring odebrat kód, který se nikdy nespustí.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3af9d0a14b600773c5025fcaad68380c7bb82b29
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616704"
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
