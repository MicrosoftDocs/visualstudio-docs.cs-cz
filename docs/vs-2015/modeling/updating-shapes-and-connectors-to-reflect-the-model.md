---
title: Aktualizace obrazců a konektorů k vyjádření modelu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 93c079a5dc80b0a26e133258328fb7b5b9fb8d41
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192449"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aktualizace obrazců a konektorů k vyjádření modelu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V jazyka specifického pro doménu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], provedete vzhledu tvar odráží stav základní model.  
  
 Příklady kódu v tomto tématu by se měl přidat k `.cs` ve vašich `Dsl` projektu. Budete potřebovat tyto příkazy do každého souboru:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Nastavit vlastnosti Mapa obrazce pro řízení viditelnosti dekorátoru  
 Můžete řídit viditelnosti dekorátoru bez psaní kódu programu, tím, že nakonfigurujete mapování mezi obrazcem a doménová třída v definici DSL. Další informace naleznete v následujících tématech:  
  
-   [Postupy: řízení viditelnosti dekorátoru – přesměrování](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)  
  
-   [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)  
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Zpřístupnění barvu a styl v tvaru formě vlastnosti  
 V definici DSL, klikněte pravým tlačítkem na třídu tvar, přejděte na **přidat vystavený**a potom klikněte na jednu z položek, jako **Barva výplně**.  
  
 Doménová vlastnost, kterou můžete nastavit v kódu programu nebo jako uživatel nyní má obrazec. Například chcete-li nastavit v kódu programu, příkazu nebo pravidlo, můžete napsat:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Pokud chcete vlastnost proměnné pouze v rámci řízení programu a ne uživatele, vyberte novou vlastnost domény jako je například **Barva výplně** v diagramem definice DSL. Potom v okně Vlastnosti nastavte **je Prohlížitelná** k `false` nebo nastavte **je jen pro čtení uživatelského rozhraní** k `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definovat pravidla změnit barvu, styl nebo umístění závisí na vlastnosti prvku modelu  
 Můžete definovat pravidla, které aktualizují vzhledu tvar závisí na dalších součástí modelu. Například můžete definovat pravidla změnit na prvek modelu, který aktualizuje barva jeho tvar závisí na vlastnostech prvku modelu. Další informace o pravidlech změnu, naleznete v tématu [pravidla šíření změn v rámci the Model](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Pravidla by měla používat jenom k aktualizaci vlastností, které jsou zachovány v rámci Store, protože pravidla nejsou vyvolány při provádění příkazu zpět. To nezahrnuje některé grafické funkce, třeba velikost a zda se tvar. K aktualizaci těchto funkcí tvaru, naleznete v tématu [aktualizace Non-Store grafické funkce](#OnAssociatedProperty).  
  
 V následujícím příkladu se předpokládá, že mají přístup `FillColor` jako doménová vlastnost, jak je popsáno v předchozí části.  
  
```csharp  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Použít OnChildConfigured k inicializaci vlastností obrazce  
 Chcete-li nastavit vlastnosti obrazec při prvním vytvoření přepsání `OnChildConfigured()` v částečnou definici třídy diagramu. Diagram tříd je zadán v definici DSL a generovaného kódu je v **Dsl\Generated Code\Diagram.cs**. Příklad:  
  
```csharp  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 Tuto metodu lze pro vlastnosti domény i bez úložiště funkcí, jako je například velikost tvaru.  
  
##  <a name="OnAssociatedProperty"></a> Použití AssociateValueWith() k aktualizaci další funkce obrazec  
 Pro některé funkce obrazce, jako je například, zda má stín nebo styl šipky konektoru neexistuje žádná integrovaná metoda vystavení funkce jako doménovou vlastnost.  Změny těchto funkcí nejsou pod kontrolou transakcí systému. Proto není třeba je aktualizovat pomocí pravidel, protože pravidla nejsou vyvolány, když uživatel provádí příkaz zpět.  
  
 Místo toho můžete aktualizovat tyto funkce pomocí <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. V následujícím příkladu se provádí styl šipky konektoru podle hodnoty vlastnosti domény ve vztahu, který zobrazuje konektoru:  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape’s built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()` by měla být volána jednou pro každou doménovou vlastnost, kterou chcete zaregistrovat. Poté, co byla volána, bude volat jakékoli změny pro zadanou vlastnost `OnAssociatedPropertyChanged()` v obrazce, které se prvek vlastnosti modelu.  
  
 Není nutné volat `AssociateValueWith()` pro každou instanci. I když InitializeResources je metoda instance, je vyvolána pouze jednou pro každou třídu tvaru.



