---
title: Přizpůsobení okna Vlastnosti
description: Zjistěte, jak můžete přizpůsobit vzhled a chování okna vlastností v jazyce specifickém pro doménu (DSL) v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e1bd54850264c33c5317a4395f219689a8e8634
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385796"
---
# <a name="customize-the-properties-window"></a>Přizpůsobení okno Vlastnosti

Můžete přizpůsobit vzhled a chování okna vlastností v jazyce specifickém pro doménu (DSL) v Visual Studio. V definici DSL definujete vlastnosti domény pro každou třídu domény. Když ve výchozím nastavení vyberete instanci třídy , buď v diagramu, nebo v Průzkumníku modelů, bude každá vlastnost domény uvedená v okně vlastností. To vám umožní zobrazit a upravit hodnoty vlastností domény, i když jste je nenamapovali na tvarování polí v diagramu.

## <a name="names-descriptions-and-categories"></a>Názvy, popisy a kategorie

**Název a Zobrazovaný název**. V definici vlastnosti domény je Zobrazovaný název vlastnosti název, který se zobrazí za běhu v okně vlastností. Naopak Název se používá při psaní kódu programu k aktualizaci vlastnosti. Název musí být správný alfanumerický název CLR, ale zobrazovaný název může obsahovat mezery.

Když nastavíte Název vlastnosti v definici DSL, její zobrazovaný název se automaticky nastaví na kopii názvu. Pokud napíšete název v jazyce Pascal, například FuelGauge, bude zobrazovaný název automaticky obsahovat mezeru s názvem "Fuel Gauge" (Měřidlo paliva). Zobrazovaný název ale můžete explicitně nastavit na jinou hodnotu.

**Popis:** Popis vlastnosti domény se zobrazí na dvou místech:

- Když uživatel vybere vlastnost, v dolní části okna vlastností. Můžete ho použít k vysvětlení, co vlastnost představuje uživateli.

- Ve vygenerované programové kódu. Pokud k extrakci dokumentace k rozhraní API použijete dokumentaci, zobrazí se v rozhraní API jako popis této vlastnosti.

**Kategorie**: Kategorie je nadpis v okno Vlastnosti.

## <a name="expose-style-features"></a>Vystavení funkcí stylu

Některé dynamické funkce grafických prvků mohou být reprezentovány nebo *zpřístupněny* jako vlastnosti domény. Funkce, která byla zveřejněna tímto způsobem, může být aktualizována uživatelem a lze ji snadněji aktualizovat pomocí programového kódu.

Klikněte pravým tlačítkem na třídu obrazce v definici DSL, přejděte na **Přidat vystavené** a zvolte funkci.

U tvarů můžete zveřejnit **vlastnosti FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** a **FillGradientMode.** U konektorů můžete zobrazit vlastnosti **Color** `,` **TextColor**, **DashStyle** **a Thickness.** V diagramech můžete zveřejnit vlastnosti **FillColor** a **TextColor.**

## <a name="forwarding-display-properties-of-related-elements"></a>Předávání: Zobrazení vlastností souvisejících prvků

Když uživatel vašeho DSL vybere prvek v modelu, vlastnosti tohoto prvku se zobrazí v okně vlastností. Můžete ale také zobrazit vlastnosti zadaných souvisejících prvků. To je užitečné, pokud jste definovali skupinu prvků, které spolupracují. Můžete například definovat hlavní prvek a volitelný element modulu plug-in. Pokud je hlavní prvek namapován na tvar a druhý není, je užitečné zobrazit všechny jejich vlastnosti, jako by byly na jednom prvku.

Tento efekt se nazývá *předávání vlastností* a v několika případech k tomu automaticky dochází. V jiných případech můžete předávání vlastností dosáhnout definováním popisovače typu domény.

### <a name="default-property-forwarding-cases"></a>Případy předávání výchozích vlastností

Když uživatel vybere tvar, konektor nebo prvek v Průzkumníku, zobrazí se v okně okno Vlastnosti:

- Vlastnosti domény, které jsou definovány v třídě domény prvku modelu, včetně vlastností definovaných v základních třídách. Výjimkou jsou vlastnosti domény, pro které jste **nastavili možnost Procházení na** `False` hodnotu .

- Názvy prvků, které jsou propojeny prostřednictvím relací, které mají násobnost 0..1. To poskytuje pohodlný způsob zobrazení volitelně propojených elementů, i když jste pro relaci nedefinovali mapování konektoru.

- Vlastnosti domény vztahu vkládání, který cílí na prvek. Vzhledem k tomu, že relace vkládání se obvykle nezobrazují explicitně, umožní to uživateli zobrazit jeho vlastnosti.

- Vlastnosti domény definované u vybraného obrazce nebo konektoru.

### <a name="add-property-forwarding"></a>Přidání předávání vlastností

Chcete-li předat vlastnost, definujete popisovač typu domény. Pokud máte doménový vztah mezi dvěma třídami domény, můžete použít popisovač typu domény a nastavit vlastnost domény v první třídě na hodnotu vlastnosti domény ve druhé třídě domény. Pokud máte například vztah mezi třídou domény Book **(Kniha)** a doménou **Author** (Autor), můžete pomocí popisovače typu domény nastavit vlastnost **Name** (Jméno) autora knihy na okno Vlastnosti, když uživatel vybere Knihu. 

> [!NOTE]
> Předávání vlastností ovlivňuje pouze okno Vlastnosti, když uživatel upravuje model. Nedefinuje vlastnost domény na přijímající třídě. Pokud chcete získat přístup k předané vlastnosti domény v jiných částech definice DSL nebo v kódu programu, musíte získat přístup k prvku předávání.

Následující postup předpokládá, že jste vytvořili DSL. V prvních několika krocích jsou shrnuty požadavky.

#### <a name="forward-a-property-from-another-element"></a>Předání vlastnosti z jiného prvku

1. Vytvořte řešení, které obsahuje alespoň dvě třídy, které se v tomto příkladu nazývají Book (Kniha) a [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] **Author (Autor).**  Mezi Book (Kniha) a **Author (Autor)** by **měl** být nějaký druh relace.

    Násobnost zdrojové role (role na  straně knihy) by měla být 0..1 nebo 1..1, aby každá kniha měla jednu **autorku**. 

2. V **Průzkumníku DSL** klikněte pravým tlačítkem na **třídu Doména** knihy a potom klikněte na Přidat **nový DomainTypeDescriptor**.

    Pod uzlem **Popisovač vlastního typu** se zobrazí uzel s názvem Cesty popisovačů vlastních **vlastností.**

3. Klikněte pravým tlačítkem **na uzel Popisovač vlastního** typu a potom klikněte na **Přidat novou vlastnost.**

    V uzlu Cesty popisovačů vlastních vlastností se zobrazí nová cesta **k vlastnosti.**

4. Vyberte novou cestu k vlastnosti a v **okně Vlastnosti** nastavte Cestu na **Vlastnost** na cestu k příslušnému prvku modelu.

    Cestu můžete upravit ve stromovém zobrazení kliknutím na šipku dolů vpravo od této vlastnosti. Další informace o cestách k doméně najdete v tématu [Syntaxe cesty k doméně.](../modeling/domain-path-syntax.md) Po úpravě by cesta měla vypadat podobně jako **BookReferencesAuthor.Author/! Autor:**.

5. Vlastnost **nastavte** na **vlastnost Doména** názvu v poli **Autor.**

6. **Zobrazovaný název nastavte** **na Jméno autora.**

7. Transformujte všechny šablony, sestavte a spusťte DSL.

8. V diagramu modelu vytvořte knihu, autora a propoojte je pomocí referenční relace. Vyberte prvek knihy a v okno Vlastnosti by se vedle vlastností knihy měl zobrazit Také jméno autora. Změňte jméno propojeného autora nebo propojíte knihu s jiným autorem a všimněte si, že se změní jméno autora knihy.

## <a name="custom-property-editors"></a>Editory vlastních vlastností

Okno vlastností poskytuje odpovídající výchozí prostředí pro úpravy pro typ jednotlivých vlastností domény. Například u výčtového typu se uživateli zobrazí rozevírací seznam a pro číselnou vlastnost může uživatel zadat číslice. To platí pouze pro předdefinové typy. Pokud zadáte externí typ, uživatel bude moct zobrazit hodnoty vlastnosti, ale nebude ji upravovat.

Můžete ale zadat následující editory a typy:

1. Jiný editor, který se používá se standardním typem. Můžete například zadat editor cest k souboru pro vlastnost řetězce.

2. Externí typ pro vlastnost domény a editor pro něj.

3. Editor .NET, například editor cest k souborům, nebo můžete vytvořit vlastní editor vlastností.

   Převod mezi externím typem a typem, například String, který má výchozí editor.

   V DSL je externí *typ* libovolný typ, který není jedním z jednoduchých typů (například logická hodnota nebo int32) nebo řetězec.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Definování vlastnosti domény, která má externí typ

1. V **Průzkumník řešení** přidejte odkaz na sestavení (DLL), které obsahuje externí typ, do **projektu Dsl.**

    Sestavení může být sestavení .NET nebo sestavení, které jste dodali.

2. Pokud jste to ještě neudělali, **přidejte** typ do seznamu Typy domén.

   1. Otevřete DslDefinition.dsl a v **Průzkumníku DSL** klikněte pravým tlačítkem na kořenový uzel a pak klikněte na **Přidat nový externí typ**.

        Pod uzlem Typy domén se **zobrazí nová** položka.

       > [!WARNING]
       > Položka nabídky je v kořenovém uzlu DSL, nikoli v **uzlu Typy** domén.

   2. Nastavte název a obor názvů nového typu v okno Vlastnosti.

3. Přidejte vlastnost domény do třídy domény obvyklým způsobem.

    V okno Vlastnosti v rozevíracím seznamu v poli Typ vyberte externí **typ.**

   V této fázi mohou uživatelé zobrazit hodnoty vlastnosti, ale nemohou ji upravovat. Zobrazené hodnoty se získávají z `ToString()` funkce . Můžete napsat programový kód, který nastaví hodnotu vlastnosti, například v příkazu nebo pravidle.

### <a name="set-a-property-editor"></a>Nastavení editoru vlastností

Přidejte atribut CLR do vlastnosti doména v následujícím tvaru:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Atribut můžete nastavit u vlastnosti pomocí položky **vlastního atributu** v okno Vlastnosti.

Typ `AnEditor` musí být odvozen od typu určeného ve druhém parametru. Druhý parametr by měl být buď <xref:System.Drawing.Design.UITypeEditor> nebo <xref:System.ComponentModel.ComponentEditor> . Další informace naleznete v tématu <xref:System.ComponentModel.EditorAttribute>.

Můžete zadat vlastní editor nebo editor .NET, například <xref:System.Windows.Forms.Design.FileNameEditor> nebo <xref:System.Drawing.Design.ImageEditor> . Například použijte následující postup, chcete-li mít vlastnost, ve které může uživatel zadat název souboru.

#### <a name="define-a-file-name-domain-property"></a>Definice vlastnosti doména názvu souboru

1. Přidejte doménovou vlastnost do doménové třídy v definici DSL.

2. Vyberte novou vlastnost. Do pole **vlastní atribut** v okno Vlastnosti zadejte následující atribut. Chcete-li zadat tento atribut, klikněte na tlačítko se třemi tečkami **[...]** a potom zadejte název atributu a parametry samostatně:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Ponechte typ doménové vlastnosti ve výchozím nastavení **řetězce**.

4. Chcete-li otestovat editor, ověřte, zda uživatelé mohou otevřít Editor názvů souborů pro úpravu doménové vlastnosti.

    1. Stiskněte klávesy CTRL + F5 nebo F5. V řešení ladění otevřete testovací soubor. Vytvořte prvek doménové třídy a vyberte ji.

    2. V okno Vlastnosti vyberte vlastnost doména. V poli hodnota se zobrazí tři tečky **[...]**.

    3. Klikněte na tlačítko se třemi tečkami. Zobrazí se dialogové okno soubor. Vyberte soubor a zavřete dialogové okno. Cesta k souboru je nyní hodnotou vlastnosti doména.

### <a name="define-your-own-property-editor"></a>Definice vlastního editoru vlastností

Můžete definovat vlastní editor. To umožňuje uživateli povolit buď úpravu typu, který jste definovali, nebo upravit standardní typ zvláštním způsobem. Můžete například uživateli dovolit zadat řetězec, který představuje vzorec.

Editor definujete tak, že zapíšete třídu, která je odvozena z <xref:System.Drawing.Design.UITypeEditor> . Vaše třída musí přepsat:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, pro interakci s uživatelem a aktualizaci hodnoty vlastnosti.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, chcete-li určit, zda má Editor otevřít dialogové okno nebo zadat rozevírací nabídku.

Můžete také zadat grafické znázornění hodnoty vlastnosti, která se zobrazí v mřížce vlastností. Uděláte to tak, že přepíšete `GetPaintValueSupported` a `PaintValue` .  Další informace naleznete v tématu <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Přidejte kód do samostatného souboru kódu v projektu **DSL** .

Příklad:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

Chcete-li použít tento editor, nastavte **vlastní atribut** doménové vlastnosti na:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Další informace naleznete v tématu <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Zadejte rozevírací seznam hodnot.

Můžete zadat seznam hodnot, z nichž si uživatel může vybrat.

> [!NOTE]
> Tento postup poskytuje seznam hodnot, které se mohou měnit v době běhu. Pokud chcete uvést seznam, který se nemění, zvažte místo toho použití výčtového typu jako typ vaší doménové vlastnosti.

Chcete-li definovat seznam standardních hodnot, přidejte do vlastnosti domény atribut CLR, který má následující tvar:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Definujte třídu, která je odvozena z <xref:System.ComponentModel.TypeConverter> . Přidejte kód do samostatného souboru v projektu **DSL** . Příklad:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
