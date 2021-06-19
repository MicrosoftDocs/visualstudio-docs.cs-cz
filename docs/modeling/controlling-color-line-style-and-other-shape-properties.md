---
title: Řízení barvy, stylu čáry a dalších vlastností obrazce
description: Poskytuje informace o řízení vlastností obrazce, jako je barva a styl čáry.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 836c77f3651b7686e9366fe75ea7922a248fd28f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389628"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Řízení barvy, stylu čáry a ostatních vlastností obrazce

Některé vlastnosti obrazce, například barva, mohou být zveřejněné. To znamená, že vlastnosti mohou být propojeny s vlastností domény obrazce. Jiné je třeba řídit přímo.

## <a name="exposing-a-property"></a>Vystavení vlastnosti
 Některé vlastnosti obrazce, jako je barva, mohou být propojeny s hodnotou vlastnosti domény.

 V definici DSL vyberte tvar, konektor nebo třídu diagramu. V místní nabídce klikněte pravým tlačítkem na **Přidat** vystavené a pak zvolte požadovanou vlastnost, například Barva výplně.

 Tvar teď má vlastnost domény, kterou můžete nastavit v kódu programu nebo jako uživatel.

## <a name="dynamically-updating-an-exposed-property"></a>Dynamická aktualizace zveřejněné vlastnosti
 Obvykle chcete, aby vystavená vlastnost byla závislá na jiné vlastnosti. Můžete například chtít, aby se tvar zčervenl vždy, když je konkrétní vlastnost domény menší než nula. Pokud chcete vytvořit tuto závislost, vytvořte [pravidlo](../modeling/rules-propagate-changes-within-the-model.md). Příklad:

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