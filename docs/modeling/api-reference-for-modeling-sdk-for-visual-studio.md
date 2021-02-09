---
title: Reference k rozhraní API pro modelování sady SDK
description: Přečtěte si, jak sada Visual Studio pro vizualizaci a modelování nabízí platformu, na které jsou sestavené nástroje DSL (Domain Specific Language).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b9393c8e01cb304b6a89ac9b400f3efc29d8c056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861907"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referenční dokumentace rozhraní API k sadě Modeling SDK pro sadu Visual Studio

Sada Visual Studio pro vizualizaci a modelování nabízí platformu, na které jsou sestavené nástroje pro jazyky specifické pro doménu (DSL).

Tato část obsahuje referenční materiály pro obory názvů, které mají názvy začínající na Microsoft. VisualStudio. Modeling.

|Obor názvů|Content|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Třídy jako ModelElement, což je základní třída všech tříd domény, které definujete v DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Třídy, které tvoří součást definice DSL|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Nástroje pro ukládání modelů a nástroje pro měření výkonu.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Třídy jako ShapeElement, což je základní třída všech tvarů definovaných v DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metody gesta a výběru.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Rozhraní API návrháře definice DSL|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Interní třídy návrháře definice DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributy, které umožňují rozšiřování návrháře DSL pomocí příkazů, gest a ověřování.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozšíření pro ModelElement, které implementují rozšiřitelnost DSL|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributy rozšiřitelnosti|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umožňuje nastavit části modelu jen pro čtení.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Rozhraní ModelBus API, které pomáhá integrovat různé modely.|
|[Microsoft. VisualStudio. Modeling. Integration. výběr](/previous-versions/ee904394(v=vs.140))|Dialogové okno umožňující uživatelům přejít na modely a elementy a vytvořit odkazy na ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Služba výběru.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|ModelBus Adapter Framework pro Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. výběr](/previous-versions/ee886769(v=vs.140))|Dialogové okno pro výběr, které umožňuje uživatelům přejít na modely a elementy a vytvořit odkazy na ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Rozhraní mezi DSL a Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umožňuje definovat místní (kontextové) příkazy nabídky.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umožňuje definovat omezení ověřování.|

## <a name="see-also"></a>Viz také

- [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)
