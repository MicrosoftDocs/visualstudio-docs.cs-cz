---
title: Aktualizace obrazců a konektorů k vyjádření modelu
description: Seznamte se s tím, že v jazyce specifickém pro doménu v aplikaci Visual Studio můžete nastavit vzhled tvaru, který odráží stav podkladového modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57f3785fe232b20123475bd85be2be7148e5b87e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924342"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Aktualizace obrazců a konektorů k vyjádření modelu

V jazyce specifickém pro doménu v aplikaci Visual Studio můžete nastavit vzhled tvaru tak, aby odrážel stav podkladového modelu.

Příklady kódu v tomto tématu by měly být přidány do `.cs` souboru v `Dsl` projektu. V každém souboru budete potřebovat tyto direktivy:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Nastavení vlastností mapy obrazců pro řízení viditelnosti dekoratér

Můžete ovládat viditelnost dekoratér bez psaní programového kódu tak, že nakonfigurujete mapování mezi obrazcem a doménovou třídou v definici DSL. Další informace najdete v tématu [definování Domain-Specificho jazyka](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Vystavení barvy a stylu tvaru jako vlastností

V definici DSL klikněte pravým tlačítkem myši na třídu Shape, přejděte na **Přidat vystavené** a potom klikněte na jednu z položek, jako je **Barva výplně**.

Tvar má nyní doménovou vlastnost, kterou můžete nastavit v programovém kódu nebo jako uživatel. Například pro nastavení v kódu programu příkazu nebo pravidla můžete napsat:

`shape.FillColor = System.Drawing.Color.Red;`

Chcete-li nastavit proměnnou vlastnosti pouze v rámci řízení programu a nikoli podle uživatele, vyberte v diagramu definice DSL vlastnost Nová doména, jako je **Barva výplně** . Potom můžete v **okno Vlastnosti nastavit procházení** do `false` nebo nastavit na **hodnotu jen pro čtení uživatelského rozhraní** `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definování pravidel změny pro barvu, styl nebo umístění závisí na vlastnostech elementu modelu.
 Můžete definovat pravidla, která aktualizují vzhled obrazce závislého na jiných částech modelu. Můžete například definovat pravidlo změny u prvku modelu, který aktualizuje barvu jeho tvaru závislých na vlastnostech elementu modelu. Další informace o pravidlech změn najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

 Pravidla byste měli použít pouze k aktualizaci vlastností, které jsou udržovány v rámci úložiště, protože pravidla nejsou vyvolána, když je proveden příkaz k vrácení zpět. To nezahrnuje některé grafické funkce, jako je například velikost a viditelnost tvaru. Chcete-li aktualizovat tyto funkce tvaru, přečtěte si téma [aktualizace grafických funkcí bez možnosti ukládání](#OnAssociatedProperty).

 Následující příklad předpokládá, že jste byli vystaveni `FillColor` jako doménová vlastnost, jak je popsáno v předchozí části.

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

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Použití OnChildConfigured k inicializaci vlastností obrazce

Chcete-li nastavit vlastnosti obrazce při jeho prvním vytvoření, přepsání `OnChildConfigured()` v částečné definici vaší třídy diagramu. Třída diagramu je určena v definici DSL a vygenerovaný kód je v **Dsl\Generated Code\Diagram.cs**. Příklad:

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

Tuto metodu lze použít pro vlastnosti domény i pro funkce, které nejsou uloženy, jako je například velikost obrazce.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Použití AssociateValueWith () k aktualizaci dalších funkcí obrazce

U některých funkcí tvaru, jako je například, zda má stín nebo styl šipky spojnice, neexistuje žádná předdefinovaná metoda, jak tuto funkci vystavit jako doménovou vlastnost.  Změny těchto funkcí nejsou pod kontrolou transakčního systému. Proto není vhodné je aktualizovat pomocí pravidel, protože pravidla nejsou vyvolána, když uživatel provede příkaz k vrácení zpět.

Místo toho můžete tyto funkce aktualizovat pomocí <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . V následujícím příkladu je styl šipky spojnice řízený hodnotou vlastnosti doména v relaci, kterou konektor zobrazuje:

```csharp
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
        { // Update the shape's built-in Decorator feature:
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

`AssociateValueWith()` má být volána jednou pro každou vlastnost domény, kterou chcete zaregistrovat. Po jeho volání budou všechny změny zadané vlastnosti volat `OnAssociatedPropertyChanged()` do všech tvarů, které prezentují prvek modelu vlastnosti.

Pro každou instanci není nutné volat `AssociateValueWith()` . I když je InitializeResources metodou instance, je vyvolána pouze jednou pro každou třídu Shape.
