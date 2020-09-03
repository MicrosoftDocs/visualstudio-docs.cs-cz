---
title: Přesunout deklaraci proměnné poblíž odkazu
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
ms.openlocfilehash: 1339f4a9d151ef41d9a35c5aac0a96f220a297b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093995"
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
