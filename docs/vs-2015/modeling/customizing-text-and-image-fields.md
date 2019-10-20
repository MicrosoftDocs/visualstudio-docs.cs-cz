---
title: Přizpůsobení polí text a obrázek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6baaa9ceba8f40aa5ad7888384027131e0ffe94
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654973"
---
# <a name="customizing-text-and-image-fields"></a>Přizpůsobení textových a obrazových polí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při definování dekoratér textu v obrazci, je reprezentována TextField. Příklady inicializace TextField a dalších ShapeFields naleznete v Dsl\GeneratedCode\Shapes.cs v řešení DSL.

 TextField je objekt, který spravuje oblast uvnitř tvaru, jako je například prostor přiřazený popisku. Jedna instance TextField je sdílena mezi mnoha obrazci stejné třídy. Instance TextField neukládá text popisku samostatně pro každou instanci: místo toho metoda `GetDisplayText(ShapeElement)` převezme tvar jako parametr a může vyhledat text závislý na aktuálním stavu tvaru a jeho elementu modelu.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Jak je určeno zobrazení textového pole
 Je volána metoda `DoPaint()` pro zobrazení pole na obrazovce. Můžete buď přepsat výchozí `DoPaint(),`, nebo můžete přepsat některé z metod, které volá. Následující zjednodušená verze výchozích metod vám může porozumět tomu, jak potlačit výchozí chování:

```
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
// To change the brush for every field, change the shape’s styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application’s styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape’s styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application’s styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }

```

 Existuje několik dalších párů metod `Get` a `Default` vlastností, jako je například `DefaultMultipleLine/GetMultipleLine()`. Můžete přiřadit hodnotu k výchozí vlastnosti pro změnu hodnoty všech instancí pole Shape. Chcete-li, aby se hodnota lišila od jedné instance obrazce k druhé nebo závislá na stavu tvaru nebo jeho prvku modelu, přepište metodu `Get`.

## <a name="static-customizations"></a>Statická přizpůsobení
 Chcete-li změnit všechny instance tohoto pole obrazce, nejprve zjistěte, zda lze vlastnost nastavit v definici DSL. Můžete například nastavit velikost písma a styl v okno Vlastnosti.

 Pokud ne, přepište metodu `InitializeShapeFields` třídy Shape a přiřaďte hodnotu odpovídající vlastnosti `Default...` textového pole.

> [!WARNING]
> Chcete-li přepsat `InitializeShapeFields()`, je nutné nastavit vlastnost **vygenerované dvojitou odvozenou** třídu shape na `true` v definici DSL.

 V tomto příkladu má obrazec textové pole, které se bude používat pro komentáře uživatele. Chceme použít standardní písmo komentáře. Vzhledem k tomu, že se jedná o standardní písmo ze sady stylů, můžeme nastavit výchozí ID písma:

```

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

## <a name="dynamic-customizations"></a>Dynamická přizpůsobení
 Aby se vzhled lišil v závislosti na stavu tvaru nebo jeho prvku modelu, odvodíte vlastní podtřídu `TextField` a přepište jednu nebo více `Get...` metod. Musíte také přepsat metodu InitializeShapeFields obrazce a nahradit instanci třídy TextField instancí vlastní třídy.

 V následujícím příkladu je písmo textového pole závislé na stavu logické doménové vlastnosti elementu modelu daného obrazce.

 Chcete-li spustit tento příklad kódu, vytvořte nové řešení DSL pomocí šablony minimálního jazyka. Přidejte logickou vlastnost domény `AlternateState` do třídy domény ExampleElement. Přidejte ikonu dekoratér do třídy ExampleShape a nastavte její obrázek na rastrový soubor. Klikněte na **transformovat všechny šablony**. Přidejte nový soubor kódu do projektu DSL a vložte následující kód.

 Chcete-li otestovat kód, stiskněte klávesu F5 a v řešení ladění otevřete vzorový diagram. Měl by se zobrazit výchozí stav ikony. Vyberte tvar a v okno Vlastnosti změňte hodnotu vlastnosti **AlternateState** . Písmo názvu elementu by se mělo změnit.

```
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

## <a name="style-sets"></a>Sady stylů
 Předchozí příklad ukazuje, jak můžete změnit textové pole na libovolné dostupné písmo. Vhodnější metoda je však změnit ji na jednu ze sady stylů, která je spojena s obrazcem nebo s aplikací. Chcete-li to provést, přepište <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> nebo GetTextBrushId ().

 Případně můžete také zvážit změnu sady stylů tvaru přepsáním <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. To má vliv na změnu písma a štětců pro všechna pole obrazce.

## <a name="customizing-image-fields"></a>Přizpůsobení polí obrázku
 Při definování dekoratér obrázku v obrazci a při definování obrazce obrázku je oblast, ve které je obrazec zobrazený, spravovaná pomocí ImageField. Příklady inicializace ImageFields a dalších ShapeFields naleznete v Dsl\GeneratedCode\Shapes.cs v řešení DSL.

 ImageField je objekt, který spravuje oblast uvnitř tvaru, jako je například prostor přiřazený k dekoratér. Jedna instance ImageField je sdílena mezi mnoha tvary stejné třídy Shapes. Instance ImageField neukládá samostatnou bitovou kopii pro každý obrazec: místo toho metoda `GetDisplayImage(ShapeElement)` převezme tvar jako parametr a může vyhledat obrázek závislý na aktuálním stavu tvaru a jeho elementu modelu.

 Pokud chcete speciální chování, jako je například proměnná image, můžete vytvořit vlastní třídu odvozenou z ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Vytvoření podtřídy ImageField

1. Nastaví v definici DSL vlastnost **vygenerované dvojitě odvozené** vlastnosti nadřazené třídy Shape.

2. Přepište metodu `InitializeShapeFields` třídy Shape.

    - Vytvořte nový soubor kódu v projektu DSL a napište částečnou definici třídy pro třídu Shape. Přepište definici metody.

3. Kontrola kódu `InitializeShapeFields` v DSL\GeneratedCode\Shapes.cs.

     V metodě override volejte základní metodu a pak vytvořte instanci vlastní třídy pole obrázku. Použijte k nahrazení pole normální obrázek v seznamu `shapeFields`.

## <a name="dynamic-icons"></a>Dynamické ikony
 V tomto příkladu je změna ikony závislá na stavu prvku modelu obrazce.

> [!WARNING]
> Tento příklad ukazuje, jak vytvořit dynamickou bitovou kopii dekoratér. Pokud ale chcete přepínat jenom mezi jedním nebo dvěma obrázky v závislosti na stavu proměnné modelu, je jednodušší vytvořit několik dekoratéry obrázků, najít je ve stejné pozici na obrazci a pak nastavit filtr viditelnosti tak, aby byl závislý na konkrétních hodnotách modelu. variabilní. Tento filtr nastavíte tak, že vyberete mapu obrazce v definici DSL, otevřete okno Podrobnosti DSL a kliknete na kartu dekoratéry.

 Chcete-li spustit tento příklad kódu, vytvořte nové řešení DSL pomocí šablony minimálního jazyka. Přidejte logickou vlastnost domény `AlternateState` do třídy domény ExampleElement. Přidejte ikonu dekoratér do třídy ExampleShape a nastavte její obrázek na rastrový soubor. Klikněte na **transformovat všechny šablony**. Přidejte nový soubor kódu do projektu DSL a vložte následující kód.

 Chcete-li otestovat kód, stiskněte klávesu F5 a v řešení ladění otevřete vzorový diagram. Měl by se zobrazit výchozí stav ikony. Vyberte tvar a v okno Vlastnosti změňte hodnotu vlastnosti **AlternateState** . Ikona by se pak měla zobrazit otočená až 90 stupňů na tomto obrazci.

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
 [Definování obrazců a konektorů](../modeling/defining-shapes-and-connectors.md) [Nastavení obrázku pozadí v diagramu](../modeling/setting-a-background-image-on-a-diagram.md) [navigace a aktualizace modelu v](../modeling/navigating-and-updating-a-model-in-program-code.md) [psaní kódu programu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
