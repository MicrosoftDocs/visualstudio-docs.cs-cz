---
title: Generovat přepsání metody C# Equals a GetHashCode
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569280"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generovat přepsání metody Rovná se a GetHashCode v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

**Co:** Umožňuje generovat **metody Equals** a **GetHashCode.**

**Kdy:** Generovat tyto přepsání, pokud máte typ, který by měl být porovnán s jedním nebo více polí, nikoli podle umístění objektu v paměti.

**Proč:**

- Pokud implementujete typ hodnoty, měli byste zvážit přepsání **metody Equals,** abyste získali vyšší výkon oproti výchozí implementaci metody Equals na ValueType.

- Pokud implementujete typ odkazu, měli byste zvážit přepsání **metody Equals,** pokud váš typ vypadá jako základní typ, například Point, String, BigNumber a tak dále.

- Přepište **GetHashCode** metoda povolit typ pracovat správně v tabulce hash. Přečtěte si další pokyny k [operátorům rovnosti](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Postupy

1. Umístěte kurzor někde na řádek deklarace typu.

   ![Zvýrazněný kód](media/overrides-highlight-cs.png)

   > [!TIP]
   > Nepoklepejte na něj, nebo nebude k dispozici možnost nabídky. Stačí umístit kurzor někde na linku.

1. Dále proveďte jeden z následujících akcí:

   - Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

   - Klikněte pravým tlačítkem myši a vyberte nabídku **Rychlé akce a Refaktoringy.**

   - Klikněte na ![Šroubovák](../media/screwdriver-icon.png) se zobrazí na levém okraji.

   ![Generovat náhled přepsání](media/overrides-preview-cs.png)

1. V rozevírací nabídce vyberte **Generovat rovná se(objekt)** nebo **Generovat rovná se a GetHashCode.**

1. V dialogovém okně **Vybrat členy** vyberte členy, pro které chcete vygenerovat metody:

    ![Dialogové okno Generovat přepsání](media/overrides-dialog-cs.png)

    > [!TIP]
    > Můžete také vygenerovat operátory z tohoto dialogového okna pomocí zaškrtávacího políčka v dolní části dialogového okna.

   Metody `Equals` `GetHashCode` a jsou generovány s výchozí implementace.

   ![Generovat výsledek metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
