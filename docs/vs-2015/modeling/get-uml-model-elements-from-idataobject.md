---
title: Získávání elementů modelu UML z objektu IDataObject | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a560ce5116c52b8c2e83ce9b28252f060e2485f1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782073"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Získávání elementů modelu UML z objektu IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když uživatel přetáhne prvky z libovolného zdroje do diagramu, přetažené prvky jsou zakódovány `System.Windows.Forms.IDataObject`. Kódování závisí na typu zdrojového objektu. Následující fragment ukazuje, jak načíst prvky, pokud je zdroj UML diagram.  
  
> [!NOTE]
>  Většinu operací, které je třeba provést v modelech UML lze provést pomocí typů definovaných v sestavení **Microsoft.VisualStudio.Uml.Interfaces** a  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Ale k tomuto účelu, budete muset použít některé třídy, které jsou součástí implementace nástroje modelu UML. Například `ShapeElement` v tomto fragmentu není stejný jako UML `IShape`. Aby se snížilo riziko uvedení modelu a diagramů do nekonzistentního stavu, je lepší vyhýbat se použití metod na tyto třídy implementace, jedině pokud neexistuje žádná alternativa.  
  
## <a name="code-sample"></a>Ukázka kódu  
 Váš projekt musí odkazovat na následující [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] sestavení:  
  
 **Microsoft.VisualStudio.Modeling.Sdk. [verze]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [verze]**  
  
 **System.Windows.Forms**  
  
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
  
 Další informace o `ElementGroupPrototype` a `Store` ve které jsou implementovány nástroje modelování UML, naleznete v tématu [sada Modeling SDK for Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="see-also"></a>Viz také  
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



