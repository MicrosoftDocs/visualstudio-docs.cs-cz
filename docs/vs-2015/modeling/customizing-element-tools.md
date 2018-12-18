---
title: Přizpůsobení nástrojů elementu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cf2d48ee0ec4c8f2f9986f4655eb98b44583beef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220503"
---
# <a name="customizing-element-tools"></a>Přizpůsobení nástrojů elementu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V definice DSL představují jeden koncept jako skupiny prvků. Pokud jste vytvořili model, ve kterém má součást fixní sadu porty, je vždy třeba porty, které chcete vytvořit ve stejnou dobu jako jejich nadřazené komponenty. Proto budete muset přizpůsobit nástroj pro vytváření element tak, aby, vytvoří se skupina elementů nikoli jen jeden. Za tím účelem můžete přizpůsobit, jak inicializovat nástroj pro vytváření elementu.  
  
 Můžete také přepsat, co se stane, když nástroj je přetáhnout do diagramu nebo prvku.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Přizpůsobení obsahu nástroj – Element  
 Každý prvek nástroj ukládá instance <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), který obsahuje serializovaná verze jednoho nebo více prvků modelu a odkazy. Ve výchozím nastavení EGP nástroj element obsahuje jednu instanci třídy, která zadáte pro nástroj. Toto můžete změnit tak, že přepíšete *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Tato metoda je volána při načtení balíčku DSL.  
  
 Parametr metody je ID třídy, která jste zadali v definici DSL. Při volání metody s třídou, která vás zajímají, můžete přidat další prvky do EGP.  
  
 EGP musí obsahovat, vkládání odkazů z jeden hlavní prvek na pobočkách elementy. Může také obsahovat referenční odkazy.  
  
 Následující příklad vytvoří hlavní prvek a dva prvky vložené. Hlavní třída se nazývá odpor a obsahuje dvě relace vkládání elementů s názvem terminálu. Vkládání vlastnosti role jsou pojmenovány Terminal1 a Terminal2 a mít násobnost 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení vytvoření a přesunutí elementu](../modeling/customizing-element-creation-and-movement.md)



