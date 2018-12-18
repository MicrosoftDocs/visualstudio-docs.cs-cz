---
title: Otevření modelu UML pomocí rozhraní API sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62b8700e85ccab271dbfdc4f9bac504ee64197a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779616"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Otevření modelu UML pomocí rozhraní API sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí rozhraní API můžete také otevřít modelů a diagramů v uživatelském rozhraní sady Visual Studio.  
  
 Pokud chcete pouze přečíst model v kódu programu bez zviditelnění pro uživatele, můžete použít následující metody:  
  
-   Sběrnice modelu Visual Studio umožňuje přístup k modelů a prvkům v sobě a poskytuje standardní metodu vytváření vazeb mezi jednotlivými. Další informace najdete v tématu [modely UML integrovat s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Model lze otevřít v režimu jen pro čtení. Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Showing"></a> Otevírání modelů a diagramů v sadě Visual Studio  
 K otevření modelu v uživatelském rozhraní, použijte standardní rozhraní API Visual Studio `EnvDTE.DTE`. Existují dvě užitečná přetypování, které můžete provést na položkách projektu modelování:  
  
- `EnvDTE.Project` může být převeden do a z `IModelingProject`, pokud je projekt projektem modelování a projekt je načten do aktuální domény aplikace.  
  
- `EnvDTE.ProjectItem` může být převeden do a z `IDiagramContext`, pokud je položka diagramu UML.  
  
  Následující příklad váš projekt musí importovat tyto odkazy:  
  
- EnvDTE  
  
- Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
- Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
- Microsoft.VisualStudio.Shell.Immutable. [verze]  
  
- Microsoft.VisualStudio.Uml.Interfaces  
  
- System.ComponentModel.Composition  
  
  Tento příklad otevře UML model v sadě Visual Studio:  
  
```  
using EnvDTE; // Visual Studio API for loading diagrams  
using   
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;    
   // for ICommandExtension and other handler types  
using Microsoft.VisualStudio.Uml.Classes;   
   // for basic UML types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // for model construction methods  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram   
...  
```  
  
 V rozšíření sady Visual Studio můžete provést toto prohlášení k získání přístupu k poskytovateli služby hostitele:  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 V metodě je možné otevřít projekt, například aktuální projekt:  
  
```  
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
IModelingProject modelingProject = project as IModelingProject;  
if (modelingProject == null) return; // not a modeling project  
  
// Access the model's store and contents.  
IModelStore store = modelingProject.Store;  
foreach (IElement element in store.Root.OwnedElements) {...}  
  
// Open all the project's diagrams.  
foreach (ProjectItem item in project.ProjectItems)  
{   
     IDiagramContext modelingItem = item as IDiagramContext;  
     if (modelingItem == null)  
         continue; // not a model diagram  
     IDiagram diagram = modelingItem.CurrentDiagram;  
     if (diagram == null)  
     {  
        // Diagram is closed. Open it.  
        item.Open().Activate();  
        diagram = modelingItem.CurrentDiagram;  
     }  
     // Access the shapes.  
     foreach (IShape<IElement> shape   
               in diagram.GetChildShapes<IElement>())  
     {  
       IElement displayedElement = shape.Element;  
       ...  
     }  
   }  
}   
```  
  
## <a name="see-also"></a>Viz také  
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md)   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)



