---
title: Přizpůsobení textových a obrazových polí
description: Přečtěte si o přizpůsobení textových a obrázových souborů. Dále se dozvíte, že když definujete dekorátor textu ve tvaru, reprezentuje ho pole TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389264"
---
# <a name="customizing-text-and-image-fields"></a>Přizpůsobení textových a obrazových polí
Když definujete dekoratér textu ve tvaru, je reprezentován polem TextField. Příklady inicializace textových polí a dalších polí ShapeField najdete v souboru Dsl\GeneratedCode\Shapes.cs v řešení DSL.

 Pole TextField je objekt, který spravuje oblast v rámci obrazce, například prostor přiřazený k popisku. Jedna instance TextField je sdílena mezi mnoha tvary stejné třídy. Instance TextField neukládá text popisku samostatně pro každou instanci: místo toho metoda přebírá tvar jako parametr a může hledat text závislý na aktuálním stavu obrazce a jeho prvku `GetDisplayText(ShapeElement)` modelu.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Jak se určuje vzhled textového pole
 Voláním `DoPaint()` metody se zobrazí pole na obrazovce. Můžete buď přepsat výchozí `DoPaint(),` hodnotu, nebo můžete přepsat některé metody, které volá. Následující zjednodušená verze výchozích metod vám může pomoct pochopit, jak přepsat výchozí chování:

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

 Existuje několik dalších párů metod a `Get` `Default` vlastností, například `DefaultMultipleLine/GetMultipleLine()` . Můžete přiřadit hodnotu k vlastnosti Default a změnit hodnotu pro všechny instance pole obrazce. Pokud chcete, aby se hodnota licha od jedné instance obrazce k jiné, nebo aby závisel na stavu tvaru nebo jeho prvku modelu, přepište `Get` metodu .

## <a name="static-customizations"></a>Statická přizpůsobení
 Pokud chcete změnit všechny instance tohoto pole obrazce, nejprve zjistěte, jestli můžete nastavit vlastnost v definici DSL. Můžete například nastavit velikost a styl písma v okno Vlastnosti.

 Pokud ne, přepište metodu třídy shape a přiřaďte hodnotu příslušné `InitializeShapeFields` vlastnosti `Default...` textového pole.

> [!WARNING]
> `InitializeShapeFields()`Chcete-li přepsat , je nutné nastavit vlastnost Generates Double **Derived** třídy obrazce na `true` v definici DSL.

 V tomto příkladu má tvar textové pole, které se použije pro komentáře uživatelů. Chceme použít standardní písmo komentáře. Protože se jedná o standardní písmo ze sady stylů, můžeme nastavit výchozí ID písma:

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

## <a name="dynamic-customizations"></a>Dynamická přizpůsobení
 Pokud chcete, aby se vzhled lichá v závislosti na stavu obrazce nebo jeho prvku modelu, odvozte vlastní podtřídu třídy a `TextField` přepište jednu nebo více `Get...` metod. Je také nutné přepsat metodu InitializeShapeFields obrazce a nahradit instanci PoleText instancí vlastní třídy.

 Následující příklad vytvoří písmo textového pole závislé na stavu logické vlastnosti domény prvku modelu obrazce.

 Pokud chcete spustit tento příklad kódu, vytvořte nové řešení DSL pomocí šablony minimálního jazyka. Přidejte do třídy domény `AlternateState` ExampleElement logickou vlastnost domény. Přidejte dekorátor ikony do třídy ExampleShape a nastavte jeho obrázek na soubor bitmapy. Klikněte **na Transformovat všechny šablony.** Do projektu DSL přidejte nový soubor kódu a vložte následující kód.

 Pokud chcete kód otestovat, stiskněte klávesu F5 a v řešení ladění otevřete ukázkový diagram. Měl by se zobrazit výchozí stav ikony. Vyberte obrazec a v okno Vlastnosti změňte hodnotu vlastnosti **AlternateState.** Písmo názvu elementu by se mělo změnit.

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

## <a name="style-sets"></a>Sady stylů
 Předchozí příklad ukazuje, jak můžete změnit textové pole na libovolné dostupné písmo. Vhodnější metodou je ale změnit ji na jednu ze sady stylů, která je přidružena k tvaru nebo aplikaci. Chcete-li to provést, přepište <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> nebo GetTextBrushId().

 Případně zvažte změnu sady stylů obrazce přepsáním <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . To má za následek změnu písem a štětců pro všechna pole obrazce.

## <a name="customizing-image-fields"></a>Přizpůsobení polí obrázků
 Když definujete dekoratér obrázků ve tvaru a definujete tvar obrázku, oblast, ve které je tvar zobrazen, je spravována polem ImageField. Příklady inicializace vlastností ImageField a dalších vlastností ShapeField najdete v souboru Dsl\GeneratedCode\Shapes.cs v řešení DSL.

 ImageField je objekt, který spravuje oblast v rámci obrazce, například prostor přiřazený dekorátoru. Jedna instance ImageField je sdílená mezi mnoha tvary stejné třídy obrazce. Instance ImageField neukládá samostatný obrázek pro každý obrazec: místo toho metoda přebírá tvar jako parametr a může hledat obrázek závislý na aktuálním stavu obrazce a jeho prvku `GetDisplayImage(ShapeElement)` modelu.

 Pokud chcete speciální chování, jako je obrázek proměnné, můžete vytvořit vlastní třídu odvozenou z ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Vytvoření podtřídy ImageField

1. Nastavte **vlastnost Generates Double Derived** třídy nadřazeného tvaru v definici DSL.

2. Přepište `InitializeShapeFields` metodu třídy shape.

    - Vytvořte nový soubor kódu v projektu DSL a zapište částečnou definici třídy pro třídu shape. Tady přepište definici metody.

3. Zkontrolujte kód v `InitializeShapeFields` souboru DSL\GeneratedCode\Shapes.cs.

     V metodě přepsání zavolejte základní metodu a pak vytvořte instanci vlastní třídy pole image. Tuto možnost použijte k nahrazení běžného pole obrázku v `shapeFields` seznamu.

## <a name="dynamic-icons"></a>Dynamické ikony
 V tomto příkladu je změna ikony závislá na stavu prvku modelu obrazce.

> [!WARNING]
> Tento příklad ukazuje, jak vytvořit dynamický dekoratér obrázků. Pokud ale chcete přepínat pouze mezi jedním nebo dvěma obrázky v závislosti na stavu proměnné modelu, je jednodušší vytvořit několik dekorátorů obrázků, najít je na stejné pozici na tvaru a pak nastavit filtr Viditelnost tak, aby závisel na konkrétních hodnotách proměnné modelu. Pokud chcete tento filtr nastavit, vyberte mapu obrazce v definici DSL, otevřete okno Podrobnosti DSL a klikněte na kartu Dekorátory.

 Pokud chcete spustit tento příklad kódu, vytvořte nové řešení DSL pomocí šablony minimálního jazyka. Přidejte do třídy domény `AlternateState` ExampleElement logickou vlastnost domény. Přidejte dekorátor ikony do třídy ExampleShape a nastavte jeho obrázek na soubor bitmapy. Klikněte **na Transformovat všechny šablony.** Do projektu DSL přidejte nový soubor kódu a vložte následující kód.

 Pokud chcete kód otestovat, stiskněte klávesu F5 a v řešení ladění otevřete ukázkový diagram. Měl by se zobrazit výchozí stav ikony. Vyberte obrazec a v okno Vlastnosti změňte hodnotu vlastnosti **AlternateState.** Ikona by se pak měla v tomto tvaru zobrazit otočením o 90 stupňů.

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