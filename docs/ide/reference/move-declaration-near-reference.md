---
title: Přesunout deklaraci proměnné poblíž odkazu
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c0a82b48a556e26866393661d4b87836db765abb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666502"
---
# <a name="move-declaration-near-reference-refactoring"></a>Přesunout deklaraci do blízkosti referenčního faktoru

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje přesunout deklarace proměnných blíž na jejich použití.

**Když:** Máte deklarace proměnných, které mohou být v užším oboru.

**Proč:** Můžete ponechat, jak je, ale to může způsobit problémy s čitelností nebo skrývání informací. Je to možnost Refaktorovat, aby se zlepšila čitelnost.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do deklarace proměnné.

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte **přesunout deklaraci deklarace v blízkosti odkazu** .
   - **Stisknut**
      - Klikněte na kód pravým tlačítkem, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce okna Náhled vyberte **přesunout deklaraci deklarace v blízkosti odkazu** .

1. Až budete s změnou spokojeni, stiskněte klávesu **ENTER** nebo klikněte na opravit v nabídce a změny se potvrdí.

Příklad:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)