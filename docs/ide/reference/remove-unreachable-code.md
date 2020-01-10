---
title: Odebrání nedosažitelného kódu refaktoringu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 62002e78513ecb6ebaefd8130255471d6ba93d0c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565484"
---
# <a name="remove-unreachable-code-refactoring"></a>Odebrání nedosažitelného kódu refaktoringu

Tento refaktoring platí pro:

- C#

**Co:** Odebere kód, který nebude nikdy proveden.

**Když:** Váš program nemá žádnou cestu k fragmentu kódu, takže fragment kódu není potřebný.

**Proč:** Vylepšit čitelnost a udržovatelnost odebráním kódu, který je nadbytečný a nebude nikdy proveden.

## <a name="how-to"></a>Postupy

1. Umístíte kurzor kamkoliv v vyblednout si kód, který nedostupný:

![Vyblednout nedosažitelný kód](media/unreachablecode-faded-cs.png)

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl**+ **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v okně Náhled vyberte možnost **Odebrat nedosažitelný kód** .
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

- [Refaktoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
