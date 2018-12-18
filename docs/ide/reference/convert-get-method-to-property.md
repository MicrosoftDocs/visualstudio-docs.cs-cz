---
title: Převedení metody Get na vlastnost a převod vlastnosti na metodu Get
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c5e7cc7be759991647a9bd40415639ab3b08fa1d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056344"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Převedení metody Get na vlastnost / vlastnost převést na refaktoringy Get – metoda

Tyto refaktoringy platí pro:

- C#

## <a name="convert-get-method-to-property"></a>Převedení metody Get na vlastnost

**Co:** umožňuje převést metody Get na vlastnosti (a volitelně metodu Set).

**Kdy:** měl odpovídající metodu Get, který neobsahuje žádnou logiku.

### <a name="how-to"></a>Postupy

1. Umístěte ukazatel myši v názvu metody Get.

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **nahraďte metodu pomocí vlastnosti** z automaticky otevíraného okna okno náhledu.
   - **Myši**
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **nahraďte metodu vlastnost** z automaticky otevíraného okna okno náhledu.

1. (Volitelné) Pokud máte metodu Set, můžete také metodu Set v tuto chvíli převést tak, že vyberete **metoda nahradit Get a Set – metoda s vlastností**.

1. Pokud jste spokojení se změnou ve verzi preview kód, stiskněte **Enter** nebo klikněte na opravu z nabídky a změny budou potvrzeny.

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

## <a name="convert-property-to-get-method"></a>Převod vlastnosti na metodu Get

**Co:** umožňuje převod vlastnosti na metodu Get

**Kdy:** mít zadanou vlastnost, která zahrnuje více než okamžitě nastavení a získání hodnoty

### <a name="how-to"></a>Postupy

1. Umístěte ukazatel myši v názvu metody Get.

1. Dále proveďte jednu z následujících akcí:

   - **Klávesnice**
      - Stisknutím klávesy **Ctrl**+**.** aktivační událost **rychlé akce a Refaktoringy** nabídky a vybereme **vlastnost nahraďte metody** z automaticky otevíraného okna okno náhledu.
   - **Myši**
      - Klikněte pravým tlačítkem na kód, vyberte **rychlé akce a Refaktoringy** nabídky a vybereme **vlastnost nahraďte metody** z automaticky otevíraného okna okno náhledu.

1. Pokud jste spokojení se změnou ve verzi preview kód, stiskněte **Enter** nebo klikněte na opravu z nabídky a změny budou potvrzeny.

## <a name="see-also"></a>Viz také:

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)