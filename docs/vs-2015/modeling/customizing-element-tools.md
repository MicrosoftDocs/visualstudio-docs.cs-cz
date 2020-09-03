---
title: Přizpůsobení nástrojů prvku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655014"
---
# <a name="customizing-element-tools"></a>Přizpůsobení nástrojů elementu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V některých definicích DSL představujete jeden koncept jako skupinu prvků. Například pokud vytvoříte model, ve kterém má součást pevnou sadu portů, vždy chcete, aby byly porty vytvořeny ve stejnou dobu jako jejich nadřazená komponenta. Proto je nutné přizpůsobit Nástroj pro vytváření elementů, aby místo jednoho vytvořil skupinu prvků. Chcete-li to dosáhnout, můžete přizpůsobit, jak je nástroj pro vytváření prvků inicializován.

 Můžete také přepsat to, co se stane, když je nástroj přetažen do diagramu nebo prvku.

## <a name="customizing-the-content-of-an-element-tool"></a>Přizpůsobení obsahu nástroje prvku
 Každý nástroj elementu ukládá instanci třídy <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), která obsahuje serializovanou verzi jednoho nebo více prvků modelu a propojení. Ve výchozím nastavení obsahuje EGP nástroje elementu jednu instanci třídy, kterou pro nástroj zadáte. To můžete změnit přepsáním *YourLanguage* `ToolboxHelper.CreateElementToolPrototype` . Tato metoda se volá při načtení balíčku DSL.

 Parametr metody je ID třídy, kterou jste zadali v definici DSL. Když je metoda volána se třídou, kterou zajímáte, můžete přidat další prvky do EGP.

 EGP musí zahrnovat odkazy na vložení z jednoho hlavního prvku na prvky dceřiné společnosti. Může také zahrnovat odkazy na odkazy.

 Následující příklad vytvoří hlavní prvek a dva vložené prvky. Hlavní třída se nazývá odpor a má dva vztahy vložení k prvkům s názvem terminál. Vlastnosti role vložení jsou pojmenované Terminal1 a Terminal2 a obě mají násobnost 1.. 1.

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
