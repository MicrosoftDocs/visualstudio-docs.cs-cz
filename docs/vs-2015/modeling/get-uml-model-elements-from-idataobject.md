---
title: Získat prvky modelu UML z IDataObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666080"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Získávání elementů modelu UML z objektu IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když uživatel přetáhne prvky z libovolného zdroje do diagramu, přetažené prvky jsou zakódovány v `System.Windows.Forms.IDataObject` . Kódování závisí na typu zdrojového objektu. Následující fragment kódu ukazuje, jak načíst prvky, pokud je zdrojem diagram UML.

> [!NOTE]
> Většinu operací, které je třeba provést v modelech UML, lze provádět pomocí typů definovaných v sestaveních **Microsoft. VisualStudio. Uml. Interfaces** a **Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost**. Pro tento účel ale musíte použít některé třídy, které jsou součástí implementace nástrojů modelování UML. Například `ShapeElement` v tomto fragmentu není stejný jako v UML `IShape` . Aby se snížilo riziko uvedení modelu a diagramů UML do nekonzistentního stavu, je lepší vyhnout se použití metod u těchto tříd implementace, s výjimkou případů, kdy neexistuje žádná alternativa.

## <a name="code-sample"></a>Ukázka kódu
 Projekt musí odkazovat na následující [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] sestavení:

 **Microsoft. VisualStudio. Modeling. SDK. znění**

 **Microsoft. VisualStudio. Modeling. SDK. Diagrams. znění**

 **System. Windows. Forms**

```
using Microsoft.VisualStudio.Modeling;
  // for ElementGroupPrototype
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs
… 
  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
                  (DiagramDragEventArgs dragEvent)
  {
     //ElementGroupPrototype is the container for
     //dragged and copied elements and toolbox items.
     ElementGroupPrototype prototype =
        dragEvent.Data.
        GetData(typeof(ElementGroupPrototype))
                     as ElementGroupPrototype;
     // Locate the originals in the implementation store.
     IElementDirectory implementationDirectory =
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

     return  prototype.ProtoElements.Select(
       prototypeElement =>
       {
          ModelElement element = implementationDirectory
                .FindElement(prototypeElement.ElementId);
          ShapeElement shapeElement = element as ShapeElement;
          if (shapeElement != null)
          {
            // Dragged from a diagram.
            return shapeElement.ModelElement as IElement;
          }
          else
          {
            // Dragged from UML Model Explorer.
            return element as IElement;
          }
        });
    }
```

 Další informace o `ElementGroupPrototype` nástroji a o `Store` tom, kde jsou implementovány nástroje pro modelování UML, naleznete v tématu [Modeling SDK for Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Viz také
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md) [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
