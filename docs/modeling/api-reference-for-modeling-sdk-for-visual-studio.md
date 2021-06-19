---
title: Referenční informace k rozhraní API pro sadu Modeling SDK
description: Zjistěte, jak Visual Studio Visualization and Modeling SDK poskytuje platformu, na které jsou vytvořené nástroje jazyků (DLS) pro konkrétní doménu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9603ace5751443c04d0a7503a43e08c044269817
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385458"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referenční dokumentace rozhraní API k sadě Modeling SDK pro sadu Visual Studio

Sada Visual Studio Visualization and Modeling SDK poskytuje platformu, na které jsou vytvořené nástroje jazyků pro konkrétní doménu (DSL).

Tato část obsahuje referenční materiál pro obory názvů, které mají názvy, které začínají na Microsoft.VisualStudio.Modeling.

|Obor názvů|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Třídy, jako je ModelElement, což je základní třída všech tříd domény, které definujete v DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Třídy, které jsou součástí definice DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Prohlížeč úložiště modelů a nástroje pro měření výkonu.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Třídy jako ShapeElement, což je základní třída všech tvarů, které definujete v DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metody gest a výběru.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Rozhraní API návrháře definic DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interní třídy návrháře definice DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributy, které umožňují rozšířit návrhář DSL o příkazy, gesta a ověřování.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozšíření pro ModelElement, které implementují rozšíření DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributy rozšiřitelnosti|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umožňuje vytvářet části modelu jen pro čtení.|
|[Microsoft.VisualStudio.Modeling.Integration](/previous-versions/ee904412(v=vs.140))|Rozhraní API Služby Modelbus, které pomáhá integrovat různé modely.|
|[Microsoft.VisualStudio.Modeling.Integration.Picker](/previous-versions/ee904394(v=vs.140))|Dialogové okno, které uživatelům umožňuje přejít na modely a prvky a vytvořit odkazy Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Služba výběr.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell](/previous-versions/ee869435(v=vs.140))|Rozhraní adaptéru Modelbus pro Visual Studio.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell.Picker](/previous-versions/ee886769(v=vs.140))|Dialogové okno Výběr, které uživatelům umožňuje přejít k modelům a prvkům a vytvořit odkazy modelbusu.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Rozhraní mezi adresáři DSL a Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umožňuje definovat příkazy místní nabídky.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umožňuje definovat ověřovací omezení.|

## <a name="see-also"></a>Viz také

- [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)
