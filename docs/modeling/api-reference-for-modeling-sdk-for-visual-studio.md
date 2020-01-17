---
title: Reference k rozhraní API k sadě Modeling SDK
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e4be65a94892aa87dbc7f146ce3671336a37558
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113730"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referenční dokumentace rozhraní API k sadě Modeling SDK pro sadu Visual Studio

Visual Studio Visualization and Modeling SDK poskytuje platformu, na kterém jsou integrované nástroje pro jazyky specifické pro doménu (DSL).

Tato část obsahuje referenční materiál pro obory názvů, které mají názvy, které začínají řetězcem "Microsoft.VisualStudio.Modeling".

|Názvový prostor|Obsah|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Třídy, jako je například ModelElement, což je základní třídou třídy domény, které definujete v DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Třídy, které tvoří část definice DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Model Store prohlížeč výkonu měření nástroje a.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Třídy, jako je například ShapeElement, což je základní třída všech tvarů, které definujete v DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gesta a výběr metody.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Rozhraní API pro návrháře definici DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interní třídy návrháře definici DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributy, které vám umožní rozšířit Návrhář DSL s příkazy, gesta a ověřování.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Rozšiřující metody pro ModelElement, které implementují rozšíření DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributy rozšíření|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umožňuje vytvořit části model jen pro čtení.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Rozhraní API Modelbus, které vám pomůže integrovat různých modelů.|
|[Microsoft. VisualStudio. Modeling. Integration. výběr](/previous-versions/ee904394(v=vs.140))|Dialogové okno, které mohou uživatelé přejít na modely a prvky k vytvoření odkazů Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Výběr služby.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Modelbus adaptéru rozhraní pro sadu Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. výběr](/previous-versions/ee886769(v=vs.140))|Dialogové okno Výběr, který mohou uživatelé přejít na modely a prvky k vytvoření odkazů Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Rozhraní mezi DSL a sady Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umožňuje definovat příkazy nabídky zástupců (objektu context).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umožňuje definovat omezení ověření.|

## <a name="see-also"></a>Viz také:

- [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)
