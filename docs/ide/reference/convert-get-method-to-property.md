---
title: Převést metodu GET na vlastnost; převést vlastnost na metodu Get
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094212"
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
