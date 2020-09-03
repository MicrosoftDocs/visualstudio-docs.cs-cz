---
title: Čtení modelu UML v programovém kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbc55204987f4b6ea0d45c4228f6c194f1ebaf64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671313"
---
# <a name="read-a-uml-model-in-program-code"></a>Čtení modelu UML v programovém kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model UML a jeho diagramy můžete načíst pomocí rozhraní API UML.

## <a name="reading-a-model-in-program-code"></a><a name="Reading"></a> Čtení modelu v programovém kódu
 Pro přístup k obsahu modelu bez zobrazení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okně použijte `ModelingProject.LoadReadOnly()` .

 Příklad:

```
using Microsoft.VisualStudio.Uml.Classes;
               // for IElement
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
               // for ModelingProject
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
               // for IModelStore
...
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";
using (IModelingProjectReader projectReader =
           ModelingProject.LoadReadOnly(projectPath))
{
   IModelStore store = projectReader.Store;
   foreach (IClass umlClass in store.AllInstances<IClass>())
   {
       ...
   }
}
```

 Pokud chcete načíst tvary v diagramu, je nutné si přečíst projekt a pak diagram.

 Příklad:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
foreach (string diagramFile in projectReader. DiagramFileNames)
{
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);
  foreach (IShape<IElement> shape
         in diagram.GetChildShapes<IElement>())
  { ... }
}
```

## <a name="alternative-methods"></a>Alternativní metody
 Pro mnoho aplikací [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vám Modelbus umožňuje odkazovat na modely a prvky v nich s větší odolností a flexibilitou než u metod popsaných v tomto tématu. Poskytuje standardní způsob, jak vytvořit propojení mezi libovolnými prvky ve stejném nebo různých modelech. Další informace najdete v tématu [Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 Modely a diagramy můžete také otevřít v uživatelském rozhraní pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní API. Další informace najdete v tématu [otevření modelu UML pomocí rozhraní API sady Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="stand-alone-applications"></a><a name="Standalone"></a> Samostatné aplikace
 Příklad v předchozí části bude fungovat v rozšířeních sady Visual Studio. Je možné číst model v samostatné aplikaci, ale je nutné přidat do projektu některé odkazy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

> [!NOTE]
> Podrobnosti o tom, jak číst model v samostatné aplikaci, se v budoucích verzích produktu budou nejspíš měnit. Některé funkce, které jsou dostupné v aktuální verzi, nemusí být k dispozici v budoucích verzích.

#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Chcete-li přidat odkazy pro čtení modelu v samostatné aplikaci.

1. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt, ve kterém vytváříte aplikaci, a pak klikněte na **vlastnosti**. V editoru vlastností na kartě **aplikace** nastavte **cílovou architekturu** na požadovanou verzi .NET Framework.

2. Přidejte [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] odkazy, které potřebujete pro přístup k modelům UML, obvykle:

   - Microsoft.VisualStudio.Uml.Interfaces.dll

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

3. Kromě odkazů uvedených v předchozích částech přidejte následující odkazy projektu z **\Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies**:

   - Microsoft.VisualStudio.Uml.dll

   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll

     Pokud chcete ve své aplikaci číst diagramy, můžete také vyžadovat tyto odkazy:

   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll

## <a name="see-also"></a>Viz také
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md) [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)
