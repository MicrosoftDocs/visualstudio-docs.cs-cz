---
title: Odebrání refaktoringu nedosažitelného kódu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093984"
---
# <a name="remove-unreachable-code-refactoring"></a>Odebrání refaktoringu nedosažitelného kódu

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Odebere kód, který nikdy nebude proveden.

**Kdy:** Program nemá žádnou cestu k fragmentu kódu, takže tento fragment kódu není zbytečný.

**Proč:** Zlepšit čitelnost a udržovatelnost odebráním kódu, který je nadbytečný a nikdy nebude proveden.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor kamkoli v nevyblednutém kódu, který je nedostupný:

![Vybledlý nedostupný kód](media/unreachablecode-faded-cs.png)

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** aktivujte nabídku **Rychlé akce a Refaktoringy** a v yberte **Odebrat nedostupný kód** z vyskakovacího okna Náhled.
   - **Myš**
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Odebrat nedostupný kód.**

1. Až budete se změnou spokojeni, stiskněte **Enter** nebo klikněte na opravu v nabídce a změny budou potvrzeny.

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
