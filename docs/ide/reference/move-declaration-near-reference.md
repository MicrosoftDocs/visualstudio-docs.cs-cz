---
title: Přesunout deklaraci proměnné poblíž odkazu
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring přesunout deklarace proměnných blíž na jejich použití.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce731da61c0c119869c1c1b85a87ebe44fabf273
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927922"
---
# <a name="move-declaration-near-reference-refactoring"></a>Přesunout deklaraci do blízkosti referenčního faktoru

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje přesunout deklarace proměnných blíž na jejich použití.

**Když:** Máte deklarace proměnných, které mohou být v užším oboru.

**Proč:** Můžete ponechat, jak je, ale to může způsobit problémy s čitelností nebo skrývání informací. Je to možnost Refaktorovat, aby se zlepšila čitelnost.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do deklarace proměnné.

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte **přesunout deklaraci deklarace v blízkosti odkazu** .
   - **Myš**
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

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
