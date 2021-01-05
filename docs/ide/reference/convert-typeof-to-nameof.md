---
title: Převedení typeof na nameof
description: Naučte se, jak pomocí nabídky rychlé akce a Refaktoring v aplikaci Visual Studio převést typeof na nameof v jazyce C# a GetType na NameOf v Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761196"
---
# <a name="convert-typeof-to-nameof"></a>Převést `typeof` na `nameof`

Tento refaktoring platí pro:

- C#
- Visual Basic

**Co:** Umožňuje převést instanci typu `typeof(<QualifiedType>).Name` na `nameof(<QualifiedType>)` v jazyce C# a instanci `GetType(<QualifiedType>).Name` na do `NameOf(<QualifiedType>)` v Visual Basic.

**Když:**  Všechny instance, `typeof(<QualifiedType>).Name` kde `someType` není obecný typ. Toto vyloučení je nezbytné, protože tento případ nevrací stejnou řetězcovou hodnotu jako `nameof(<QualifiedType>)` . Totéž platí pro instanci Visual Basic.

**Proč:** Použití `nameof` namísto názvu `type` zabraňuje odrazu při načítání `type` objektu a je výkonnějším způsobem jeho zápisu.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do `typeof(<QualifiedType>).Name` instance pro C# nebo `GetType(<QualifiedType>).Name` v Visual Basic.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vyberte jednu z následujících možností:

    - C#
      <br>Vyberte **převést typeof na nameof**: ![ snímek nabídky rychlé akce a nabídka refaktoringu v aplikaci Visual Studio s vybranou možnost převést typeof na ' nameof ' a zobrazí se změny kódu C#.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Vyberte **převést GetType na nameof**: ![ snímek nabídky rychlé akce a nabídka refaktoringu v aplikaci Visual Studio s vybranou rutinou "GetType" na "NameOf" a Visual Basic zobrazené změny kódu.](media/convert-get-type.PNG)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
