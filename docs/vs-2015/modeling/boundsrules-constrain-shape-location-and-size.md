---
title: Umístění a velikost obrazce omezení BoundsRules | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672732"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Umístění a velikost obrazce omezení BoundsRules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Pravidlo vázané na hranice* je třída, která definuje omezení velikosti a umístění tvaru. Poskytuje metodu, která se volá opakovaně, když uživatel přetáhne tvar nebo rohy nebo strany obrazce.

 Následující příklad omezuje obdélníkový tvar tak, aby byl pruhem pevné velikosti, buď vodorovně nebo svisle. Když uživatel přetáhne rohy nebo strany, obrys se Překlopí mezi dvě povolené Konfigurace výšky a šířky.

 Pravidlo Bounds je třída odvozená z <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> . Instance pravidla se vytvoří v obrazci:

```
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

 Všimněte si, že umístění i velikost mohou být omezeny, pokud chcete.

## <a name="see-also"></a>Viz také
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>[Reagování na změny a šíření změn](../modeling/responding-to-and-propagating-changes.md)
