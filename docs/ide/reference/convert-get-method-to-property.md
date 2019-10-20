---
title: Převést metodu GET na vlastnost; převést vlastnost na metodu Get
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ac33db013a8cea11b373e4104bf2d58a1b22cef4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654528"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Převést metodu GET na vlastnost Property/Convert pro získání refaktoringu metod

Tyto refaktoringy se vztahují na:

- C#

## <a name="convert-get-method-to-property"></a>Převést metodu GET na vlastnost

**Co:** Umožňuje převést metodu GET na vlastnost (a volitelně i metodu set).

**Když:** Máte metodu GET, která neobsahuje žádnou logiku.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do názvu metody Get.

1. Dále proveďte jednu z následujících akcí:

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v překryvném okně náhledu vyberte možnost **nahradit metodu vlastností** .
   - **Stisknut**
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

   - **Kombinace**
      - Stiskněte klávesu **Ctrl** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte možnost **nahradit vlastnost pomocí metody** .
   - **Stisknut**
      - Klikněte na kód pravým tlačítkem, vyberte nabídku **rychlé akce a refaktoring** a v místní nabídce okna náhledu vyberte **nahradit vlastnost pomocí metody** .

1. Pokud jste spokojeni se změnou ve verzi Preview kódu, stiskněte klávesu **ENTER** nebo klikněte na opravu z nabídky a změny se potvrdí.

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)