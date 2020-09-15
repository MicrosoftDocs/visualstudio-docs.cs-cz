---
title: Řízení barvy, stylu čáry a dalších vlastností obrazce
description: Poskytuje informace o řízení vlastností obrazce, jako je barva a styl čáry.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 759c7def23cf8ac0df33a75d25eb5bcbcf44b209
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100424"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Řízení barvy, stylu čáry a ostatních vlastností obrazce

Některé vlastnosti obrazce, jako je například Color, můžou být vystavené. To znamená, že vlastnosti mohou být propojeny s doménovou vlastností obrazce. Ostatní musí být řízeny přímo.

## <a name="exposing-a-property"></a>Vystavení vlastnosti
 Některé vlastnosti obrazce, jako je například barva, mohou být propojeny s hodnotou doménové vlastnosti.

 V definici DSL vyberte třídu Shape, spojnice nebo diagram. V nabídce klepněte pravým tlačítkem myši na možnost **Přidat vystavené**a zvolte požadovanou vlastnost, například barva výplně.

 Tvar má nyní doménovou vlastnost, kterou můžete nastavit v programovém kódu nebo jako uživatel.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamická aktualizace vystavené vlastnosti
 Obvykle chcete, aby vystavená vlastnost byla závislá na jiné vlastnosti. Například můžete chtít, aby se v případě, že je určitá doménová vlastnost menší než nula, tvar popnul. Chcete-li tuto závislost provést, vytvořte [pravidlo](../modeling/rules-propagate-changes-within-the-model.md). Příklad:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```