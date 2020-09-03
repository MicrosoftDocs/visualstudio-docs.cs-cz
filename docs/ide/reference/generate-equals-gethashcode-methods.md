---
title: Vygenerovat GetHashCode přepsání metody se rovná a
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569280"
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

   - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .

   - Klikněte na ![screwdriver](../media/screwdriver-icon.png) ikona, která se zobrazí na levém okraji

   ![Vygenerovat náhled přepsání](media/overrides-preview-cs.png)

1. V rozevírací nabídce vyberte **Generovat Equals (objekt)** nebo **Generovat Equals a GetHashCode** .

1. V dialogovém okně **Vybrat členy** vyberte členy, pro které chcete generovat metody:

    ![Dialogové okno generovat potlačení](media/overrides-dialog-cs.png)

    > [!TIP]
    > Pomocí zaškrtávacího políčka v dolní části dialogového okna můžete také zvolit generování operátorů z tohoto dialogového okna.

   `Equals`Metody a `GetHashCode` jsou generovány s výchozími implementacemi.

   ![Generovat výsledek metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
