---
title: Vygenerovat GetHashCode přepsání metody se rovná a
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoringu generovat metody Equals a GetHashCode.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 6a9d0ea6f6cb0aedc4fa13a8014b1a8bd66ccca0
ms.sourcegitcommit: 6ed6ae5a1693607dce57923a78d01eea3d88b29a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514940"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generování přepisů metod Equals a GetHashCode v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje generovat metody **Equals** a **GetHashCode** .

**Když:** Vygenerujte tato přepsání, pokud máte typ, který by měl být porovnán jedním nebo více poli namísto umístění objektu v paměti.

**Proč:**

- Pokud implementujete typ hodnoty, měli byste zvážit přepsání metody **Equals** . Pokud to uděláte, můžete získat vyšší výkon při výchozí implementaci metody Equals na ValueType.

- Pokud implementujete typ odkazu, měli byste zvážit přepsání metody **Equals** , pokud váš typ vypadá jako základní typ, například Point, String, BigNumber a tak dále.

- Přepsat metodu **GetHashCode** a umožnit tak správné fungování typu v zatřiďovací tabulce. Přečtěte si další pokyny pro [operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Postupy

1. Umístěte kurzor někam na řádek deklarace typu.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   Váš kód by měl vypadat podobně jako na následujícím snímku obrazovky:

   ![Snímek obrazovky se zvýrazněným kódem, na kterém se má použít vygenerovanou metodu](media/overrides-highlight-cs.png)

   > [!TIP]
   > Neklepejte na možnost vybrat název typu, jinak nebude k dispozici možnost nabídky. Stačí umístit kurzor někam na řádek.

1. Dále vyberte jednu z následujících akcí:

   - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .

   - Klikněte na ![Snímek obrazovky s ikonou Screwdriver rychlých akcí v aplikaci Visual Studio](../media/screwdriver-icon.png) ikona, která se zobrazí na levém okraji

1. V rozevírací nabídce vyberte **Generovat Equals (objekt)** nebo **Generovat Equals a GetHashCode** .

   ![Snímek obrazovky s rozevírací nabídkou generovat přepsání](media/overrides-preview-cs.png)

1. V dialogovém okně **Vybrat členy** vyberte členy, pro které chcete generovat metody:

    ![Dialogové okno generovat potlačení](media/overrides-dialog-cs.png)

    > [!TIP]
    > Pomocí zaškrtávacího políčka v dolní části dialogového okna můžete také zvolit generování operátorů z tohoto dialogového okna.

   `Equals`Metody a `GetHashCode` jsou generovány s výchozími implementacemi, jak je znázorněno v následujícím kódu:

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   Váš kód by měl vypadat podobně jako na následujícím snímku obrazovky:

   ![Snímek obrazovky s výsledkem vygenerované metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
