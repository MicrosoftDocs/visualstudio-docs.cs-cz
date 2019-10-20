---
title: Vygenerovat C# přepsání metod Equals a GetHashCode
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e70593bc04b576237a7f9f0f51ae6c3d37e40a88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660029"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generování přepisů metod Equals a GetHashCode v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje generovat metody **Equals** a **GetHashCode** .

**Když:** Vygenerujte tato přepsání, pokud máte typ, který by měl být porovnán jedním nebo více poli namísto umístění objektu v paměti.

**Proč:**

- Pokud implementujete typ hodnoty, měli byste zvážit přepsání metody **Equals** , aby se zvýšil výkon při výchozí implementaci metody Equals na ValueType.

- Pokud implementujete typ odkazu, měli byste zvážit přepsání metody **Equals** , pokud váš typ vypadá jako základní typ, například Point, String, BigNumber a tak dále.

- Přepsat metodu **GetHashCode** a umožnit tak správné fungování typu v zatřiďovací tabulce. Přečtěte si další pokyny pro [operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Postupy

1. Umístěte kurzor někam na řádek deklarace typu.

   ![Zvýrazněný kód](media/overrides-highlight-cs.png)

   > [!TIP]
   > Neklepejte na možnost vybrat název typu, jinak nebude k dispozici možnost nabídky. Stačí umístit kurzor někam na řádek.

1. Dále proveďte jednu z následujících akcí:

   - Stiskněte klávesu **Ctrl** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .

   - Klikněte na ![screwdriver](../media/screwdriver-icon.png) ikona, která se zobrazí na levém okraji

   ![Vygenerovat náhled přepsání](media/overrides-preview-cs.png)

1. V rozevírací nabídce vyberte **Generovat Equals (objekt)** nebo **Generovat Equals a GetHashCode** .

1. V dialogovém okně **Vybrat členy** vyberte členy, pro které chcete generovat metody:

    ![Dialogové okno generovat potlačení](media/overrides-dialog-cs.png)

    > [!TIP]
    > Pomocí zaškrtávacího políčka v dolní části dialogového okna můžete také zvolit generování operátorů z tohoto dialogového okna.

   Metody `Equals` a `GetHashCode` jsou generovány s výchozími implementacemi.

   ![Generovat výsledek metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)