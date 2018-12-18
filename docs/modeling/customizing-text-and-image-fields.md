---
title: Přizpůsobení textových a obrazových polí
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 32bba243cd38132a4c64a0b8706f9dbdca823ad3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942371"
---
# <a name="customizing-text-and-image-fields"></a>Přizpůsobení textových a obrazových polí
Při definování dekoratér text obrazce, je reprezentována TextField. Příklady inicializace TextFields a dalších ShapeFields zkontrolujte Dsl\GeneratedCode\Shapes.cs ve vašem řešení DSL.

 Třídy TextField je objekt, který spravuje oblast uvnitř obrazce, jako je například místo přiřazené k popisku. Jedna instance třídy TextField jsou sdílena mezi mnoha tvary stejné třídy. Instance třídy TextField neukládá text popisku odděleně pro každou instanci: místo toho `GetDisplayText(ShapeElement)` metoda má tvar jako parametr a můžete vyhledat text závisí na aktuální stav tvaru a jeho element modelu.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Jak se určují vzhled textové pole
 `DoPaint()` Metoda je volána k zobrazí pole na obrazovce. Můžete buď přepsat výchozí `DoPaint(),` nebo je můžete přepsat některé metody, které volá. Následující zjednodušenou verzi metody výchozí, pomůže vám pochopit, jak změnit výchozí chování:

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Existuje několik dalších dvojic `Get` metody a `Default` vlastnosti, jako například `DefaultMultipleLine/GetMultipleLine()`. Výchozí vlastnosti chcete změnit hodnotu pro všechny výskyty pole tvaru můžete přiřadit hodnotu. Chcete-li hodnota mírně lišit od jednoho obrazce instance do jiné nebo závisí na stavu tvar nebo jeho element modelu, přepsat `Get` metody.

## <a name="static-customizations"></a>Statické přizpůsobení
 Pokud chcete, změňte každou instanci tohoto pole tvaru, nejdřív zjistěte, zda je nastavit vlastnost v definici DSL. Můžete například nastavit velikost písma a styl v okně Vlastnosti.

 Pokud ne, pak mají přednost před `InitializeShapeFields` metoda obrazec třídy a přiřadit hodnoty k odpovídající `Default...` vlastnosti textového pole.

> [!WARNING]
>  K přepsání `InitializeShapeFields()`, je nutné nastavit **Generates Double Derived** vlastnost obrazec třídy na `true` v definici DSL.

 V tomto příkladu má tvar textové pole, který se použije pro uživatele komentáře. Chceme použít standardní komentář písma. Protože je standardní písmo ze sady styl, jsme nastavili výchozí písmo id:

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Dynamické přizpůsobení
 Chcete-li vzhled lišit závisí na stavu obrazec nebo jeho element modelu, odvozovat vlastní podtřídu `TextField` a přepište jeden nebo více `Get...` metody. Musí také přepsat metodu InitializeShapeFields vaše tvar a nahraďte instance TextField instance vlastní třídy.

 Následující příklad provede písmo textového pole závisí na stavu logická doménovou vlastnost elementu obrazce modelu.

 Pokud chcete spustit tento příklad kódu, vytvořte nové řešení DSL pomocí minimální jazykový šablony. Přidat logickou doménová vlastnost, která `AlternateState` do ExampleElement doménové třídy. Přidejte do třídy ExampleShape dekoratér ikony a vytvořit obrazovou k souboru rastrového obrázku. Klikněte na tlačítko **Transformovat všechny šablony**. Přidejte nový soubor kódu v projektu DSL a vložte následující kód.

 Pro otestování kódu, stiskněte klávesu F5 a ladění řešení, otevřete diagram vzorku. Výchozí stav ikony by se zobrazit. Vyberte obrazec a v okně Vlastnosti změňte hodnotu **AlternateState** vlastnost. Měli změnit písmo názvu elementu.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Nastaví styl
 Předchozí příklad ukazuje, jak změnit pole text písmu, která je k dispozici. Ale je však změnit na jednu sadu stylů, který je spojen s obrazci nebo s aplikací. K tomuto účelu můžete přepsat <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> nebo GetTextBrushId().

 Případně, zvažte možnost změnit sadu stylů tvaru tak, že přepíšete <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. To má za následek Změna písma a štětce pro všechna pole tvaru.

## <a name="customizing-image-fields"></a>Přizpůsobení obrazových polí
 Při definování dekoratéru obrázku ve tvaru a při definování obrazce obrázku, oblast, ve kterém se zobrazí obrazec se spravuje přes ImageField. Příklady inicializace ImageFields a dalších ShapeFields zkontrolujte Dsl\GeneratedCode\Shapes.cs ve vašem řešení DSL.

 ImageField je objekt, který spravuje oblast uvnitř obrazce, jako je například pole Přiřazeno dekoratér. Jedna instance třídy ImageField jsou sdílena mezi mnoha tvary stejné třídy obrazce. Instance třídy ImageField neukládá samostatnou image pro všechny obrazce: místo toho `GetDisplayImage(ShapeElement)` metoda má tvar jako parametr a můžete vyhledat bitovou kopii závisí na aktuální stav tvaru a jeho prvek modelu.

 Pokud chcete zvláštní chování, například bitové kopie proměnné, můžete vytvořit vlastní třídu odvozenou ze třídy ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Chcete-li vytvořit podtřídu třídy ImageField

1.  Nastavte **Generates Double Derived** vlastnost nadřazené třídy tvar v definici DSL.

2.  Přepsat `InitializeShapeFields` metoda třídy obrazce.

    -   Vytvořte nový soubor kódu v projektu DSL a zapsat definice částečné třídy pro třídu tvaru. Přepište definici metody existuje.

3.  Zkontrolujte kód `InitializeShapeFields` v DSL\GeneratedCode\Shapes.cs.

     Ve své metodě přepsání volat základní metodu a poté vytvořit instanci třídy pole vlastní image. Tato možnost slouží k nahrazení běžné imagi pole v `shapeFields` seznamu.

## <a name="dynamic-icons"></a>Dynamické ikony
 V tomto příkladu je ikona změnit závisí na stavu prvku modelu obrazce.

> [!WARNING]
>  Tento příklad ukazuje, jak vytvořit dynamické image dekoratér. Pokud chcete přepnout mezi jednu nebo dvě bitové kopie v závislosti na stavu modelu proměnné, je jednodušší vytvořte několik dekoratéry bitové kopie, vyhledejte na stejné pozici ve tvaru a pak nastavte filtr viditelnosti závisí na konkrétní hodnoty modelu, ale Proměnná. Pokud chcete nastavit tento filtr, vyberte mapový tvar v definici DSL, otevřete okno Podrobnosti DSL a klikněte na kartu Dekorátory.

 Pokud chcete spustit tento příklad kódu, vytvořte nové řešení DSL pomocí minimální jazykový šablony. Přidat logickou doménová vlastnost, která `AlternateState` do ExampleElement doménové třídy. Přidejte do třídy ExampleShape dekoratér ikony a vytvořit obrazovou k souboru rastrového obrázku. Klikněte na tlačítko **Transformovat všechny šablony**. Přidejte nový soubor kódu v projektu DSL a vložte následující kód.

 Pro otestování kódu, stiskněte klávesu F5 a ladění řešení, otevřete diagram vzorku. Výchozí stav ikony by se zobrazit. Vyberte obrazec a v okně Vlastnosti změňte hodnotu **AlternateState** vlastnost. Ikona by pak otočený do 90 stupňů, v tomto tvaru.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Viz také

- [Definování obrazců a konektorů](../modeling/defining-shapes-and-connectors.md)
- [Nastavení obrázku pozadí v diagramu](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)