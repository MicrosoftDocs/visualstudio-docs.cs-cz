---
title: Umístění a velikost obrazce omezení BoundsRules
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 104a74a38099286675a742ce9eea367d9eeabe84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944385"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Umístění a velikost obrazce omezení BoundsRules

A *hranice pravidlo* je třída, která definuje omezení na velikost a umístění obrazce. Poskytuje metodu, která je volána opakovaně, když uživatel je přetáhnete obrazce nebo rozích nebo stranách obrazce.

Následující příklad omezí pravoúhlému tvaru jako panel s pevnou velikostí, vodorovně nebo svisle. Když uživatel nastavuje tažením rozích nebo stranách, obrys převrátí mezi dvě konfigurace povolených výšky a šířky.

Rozsah pravidla je třída odvozená z <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Instance pravidla je vytvořen ve tvaru:

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

Všimněte si, že umístění a velikost můžete omezené, pokud chcete.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Odpovědi na změny a jejich šíření](../modeling/responding-to-and-propagating-changes.md)