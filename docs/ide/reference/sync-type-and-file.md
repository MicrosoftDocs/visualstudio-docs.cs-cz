---
title: Přejmenování názvu souboru tak, aby odpovídal typu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5b7a42a174fecd078e804f2ab3c35fbe442364a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594393"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Synchronizace typu s názvem souboru nebo název souboru s refaktoringem typu

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje přejmenovat typ tak, aby odpovídal názvu souboru, nebo přejmenovat název souboru tak, aby odpovídal typu, který obsahuje.

**Kdy:** Přejmenovali jste soubor nebo typ a ještě jste neaktualizovali odpovídající soubor nebo typ tak, aby odpovídaly.

**Proč:** Umístění typu do souboru s jiným názvem nebo naopak je obtížné najít to, co hledáte. Přejmenováním typu nebo názvu souboru se kód stane čitelnějším a snadněji se naviguje.

> [!NOTE]
> Toto refaktoring ještě není k dispozici pro projekty .NET Standard a .NET Core.

## <a name="how-to"></a>Postupy

1. Zvýrazněte nebo umístěte textový kurzor do názvu typu, který chcete synchronizovat:

   - C#:

       ![Zvýrazněný kód - C #](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Zvýrazněný kód – Visual Basic](media/synctype-highlight-vb.png)

2. Dále proveďte jeden z následujících akcí:

   - **Klávesnice**
      - Stiskněte **klávesu Ctrl**+**.** chcete-li aktivovat nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vybrat **Přejmenovat soubor na *TypeName*.cs,** kde *typename* je název vybraného typu.
      - Stiskněte **klávesu Ctrl**+**.** chcete-li aktivovat nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Přejmenovat typ na Název _souboru,_ ** kde *název souboru* je název aktuálního souboru.
   - **Myš**
      - Klepněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z vyskakovacího okna Náhled vyberte **Přejmenovat soubor na *TypeName*.cs,** kde *typename* je název vybraného typu.
      - Klikněte pravým tlačítkem myši na kód, vyberte nabídku **Rychlé akce a Refaktoringy** a z místního okna Náhled vyberte **Přejmenovat typ na Název _souboru,_ ** kde *název souboru* je název aktuálního souboru.

   Typ nebo soubor je přejmenován.

   - C#: V níže uvedeném příkladu byl soubor **MyClass.cs** přejmenován na **MyNewClass.cs** tak, aby odpovídal názvu typu.

       ![Inline výsledek C #](media/synctype-result-cs.png)

   - Visual Basic: V níže uvedeném příkladu byl soubor **Employee.vb** přejmenován na **Person.vb** tak, aby odpovídal názvu typu.

       ![Vsazená výsledková položka Jazyka](media/synctype-result-vb.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
