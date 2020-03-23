---
title: Přesunout deklaraci proměnné v blízkosti odkazu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093995"
---
# <a name="move-declaration-near-reference-refactoring"></a>Přesunout deklaraci v blízkosti refaktoringu odkazu

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje přesunout deklarace proměnných blíže k jejich použití.

**Kdy:** Máte deklarace proměnných, které mohou být v užším oboru.

**Proč:** Můžete to nechat tak, jak je, ale to může způsobit problémy se čitelností nebo skrytí informací. Toto je šance na refaktoring ke zlepšení čitelnosti.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do deklarace proměnné.

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** aktivujete nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Přesunout deklaraci v blízkosti odkazu.**
   - **Myš**
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Přesunout deklaraci v blízkosti odkazu.**

1. Až budete se změnou spokojeni, stiskněte **Enter** nebo klikněte na opravu v nabídce a změny budou potvrzeny.

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
