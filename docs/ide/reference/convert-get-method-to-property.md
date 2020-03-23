---
title: Převést metodu Get na vlastnost; convert vlastnost na Get metoda
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: af507a8b437a20e3d4f4807d582abab6f9a12e27
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094212"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Převést metodu Get na vlastnost / Převést vlastnost na refaktoring metody Get

Tyto refaktoringy se vztahují na:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Převedení metody Get na vlastnost

**Co:** Umožňuje převést Get metoda do vlastnosti (a volitelně Set metoda).

**Kdy:** Máte Get metoda, která neobsahuje žádnou logiku.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu metody Get.

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** aktivujete nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Metodu Nahradit vlastností.**
   - **Myš**
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Metodu Nahradit vlastností.**

1. (Nepovinné) Pokud máte Set metoda, můžete také převést Set metoda v tomto okamžiku výběrem **Nahradit Get metoda a Set metoda s vlastností**.

1. Pokud jste se změnou náhledu kódu spokojeni, stiskněte **Enter** nebo klikněte na opravu z nabídky a změny budou potvrzeny.

Příklad:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Převést vlastnost na metodu Get

**Co:** Umožňuje převést vlastnost na metodu Get.

**Kdy:** Máte vlastnost, která zahrnuje více než okamžitě nastavení a získání hodnoty

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu metody Get.

1. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** aktivujete nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Nahradit vlastnost metodami.**
   - **Myš**
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Nahradit vlastnost metodami.**

1. Pokud jste se změnou náhledu kódu spokojeni, stiskněte **Enter** nebo klikněte na opravu z nabídky a změny budou potvrzeny.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
