---
title: Reference k rozhraní API pro modelování sady SDK
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65f8703597d6297afde6e2685594784fdd1d755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672848"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referenční dokumentace rozhraní API k sadě Modeling SDK pro sadu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sada Visual Studio pro vizualizaci a modelování nabízí platformu, na které jsou sestavené jazyky (DSL) a nástroje UML pro konkrétní domény.

> [!NOTE]
> Informace o rozhraní API pro modelování UML najdete v tématu [Reference k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Informace o transformaci textu najdete v tématu [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md).

 Tato část obsahuje referenční materiály pro obory názvů, které mají názvy začínající na Microsoft. VisualStudio. Modeling.

|Obor názvů|Content|
|---------------|-------------|
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
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Rozhraní ModelBus Adapter pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. výběr](/previous-versions/ee886769(v=vs.140))|Dialogové okno pro výběr, které umožňuje uživatelům přejít na modely a elementy a vytvořit odkazy na ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Rozhraní mezi DSL a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umožňuje definovat místní (kontextové) příkazy nabídky.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umožňuje definovat omezení ověřování.|

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md)
