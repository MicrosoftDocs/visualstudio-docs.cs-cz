---
title: Převést metodu GET na nebo z vlastnosti
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring převést metodu get (a volitelně také metodu set) na vlastnost.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3aa7831c56068c826c9bbecf97d7115331243251
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039820"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Převést metodu GET na vlastnost Property/Convert pro získání refaktoringu metod

Tyto refaktoringy se vztahují na:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Převedení metody Get na vlastnost

**Co:** Umožňuje převést metodu GET na vlastnost (a volitelně i metodu set).

**Když:** Máte metodu GET, která neobsahuje žádnou logiku.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu metody Get.

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v překryvném okně náhledu vyberte možnost **nahradit metodu vlastností** .
   - **Myš**
      - Klikněte pravým tlačítkem na kód, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte **nahradit metodu vlastností** .

1. Volitelné Máte-li metodu set, můžete také v tuto chvíli převést metodu set, a to tak, že vyberete možnost **nahradit metodu get a nastavíte metodu s vlastností**.

1. Pokud jste spokojeni se změnou ve verzi Preview kódu, stiskněte klávesu **ENTER** nebo klikněte na opravu z nabídky a změny se potvrdí.

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

**Co:** Umožňuje převést vlastnost na metodu get.

**Když:** Máte vlastnost, která zahrnuje více než bezprostředně nastavování a získávání hodnoty.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu metody Get.

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte možnost **nahradit vlastnost pomocí metody** .
   - **Myš**
      - Klikněte na kód pravým tlačítkem, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte **nahradit vlastnost pomocí metody** .

1. Pokud jste spokojeni se změnou ve verzi Preview kódu, stiskněte klávesu **ENTER** nebo klikněte na opravu z nabídky a změny se potvrdí.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
