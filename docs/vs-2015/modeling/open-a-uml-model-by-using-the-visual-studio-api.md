---
title: Otevření modelu UML pomocí rozhraní API sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668511"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Otevření modelu UML pomocí rozhraní API sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modely a diagramy můžete také otevřít v uživatelském rozhraní sady Visual Studio pomocí rozhraní API.

 Pokud chcete pouze číst model v programovém kódu, aniž by byl viditelný pro uživatele, můžete použít následující metody:

- Sběrnice modelů sady Visual Studio umožňuje přístup k modelům a prvkům v rámci nich a poskytuje standardní způsob, jak vytvořit propojení mezi jedním modelem a druhým. Další informace najdete v tématu [Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Model můžete otevřít v režimu jen pro čtení. Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="opening-models-and-diagrams-in-visual-studio"></a><a name="Showing"></a> Otevírání modelů a diagramů v aplikaci Visual Studio
 Chcete-li otevřít model v uživatelském rozhraní, použijte standardní rozhraní API sady Visual Studio `EnvDTE.DTE` . Existují dva užitečné přetypování, které lze provést při modelování položek projektu:

- `EnvDTE.Project` lze přetypovat na a z `IModelingProject` , pokud se jedná o projekt modelování, a pokud je projekt načten v aktuální doméně AppDomain.

- `EnvDTE.ProjectItem` lze přetypovat na a z `IDiagramContext` , pokud je položka diagram UML.

  V následujícím příkladu by váš projekt měl importovat tyto odkazy:

- EnvDTE

- Microsoft. VisualStudio. ArchitectureTools. rozšiřitelnost

- Microsoft. VisualStudio. Modeling. SDK. znění

- Microsoft. VisualStudio. Modeling. SDK. Diagrams. znění

- Microsoft. VisualStudio. Shell. unmutable. znění

- Microsoft. VisualStudio. Uml. Interfaces

- System. ComponentModel. složení

  Tento příklad otevře model UML v aplikaci Visual Studio:

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

 V rozšíření sady Visual Studio můžete učinit tuto deklaraci k získání přístupu k poskytovateli hostitelských služeb:

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 V metodě máte přístup k projektu, například k aktuálnímu projektu:

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
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md) [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)
