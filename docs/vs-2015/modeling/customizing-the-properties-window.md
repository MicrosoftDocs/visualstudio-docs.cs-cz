---
title: Přizpůsobení okna vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
ms.assetid: b6658de5-4e85-4628-93b2-5cc12f63d25b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f628cdecbebbb10b7bb2709a2022297e1171a427
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654935"
---
# <a name="customizing-the-properties-window"></a>Přizpůsobení okna Vlastnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete přizpůsobit vzhled a chování okna vlastnosti v jazyce specifickém pro doménu (DSL). V definici DSL definujete vlastnosti domény v každé třídě domény. Ve výchozím nastavení, když vyberete instanci třídy, buď v diagramu nebo v Průzkumníku modelů, je každá doménová vlastnost uvedena v okně Vlastnosti. To vám umožní zobrazit a upravit hodnoty vlastností domény, a to i v případě, že jste je nemapovali na pole obrazce v diagramu.

## <a name="names-descriptions-and-categories"></a>Názvy, popisy a kategorie
 **Název a zobrazované jméno**. V definici doménové vlastnosti je zobrazovaný název vlastnosti název, který se zobrazí za běhu v okně Vlastnosti. Naopak název se používá při psaní kódu programu pro aktualizaci vlastnosti. Název musí být správný alfanumerický název CLR, ale zobrazovaný název může obsahovat mezery.

 Když nastavíte název vlastnosti v definici DSL, její zobrazovaný název se automaticky nastaví na kopii názvu. Pokud napíšete název Pascal použita, jako je například "FuelGauge", zobrazované jméno bude automaticky obsahovat mezeru: "měřič pohonu". Zobrazované jméno ale můžete nastavit explicitně na jinou hodnotu.

 **Popis**. Popis doménové vlastnosti se zobrazí na dvou místech:

- V dolní části okna vlastnosti, když uživatel vybere vlastnost. Můžete ji použít k vysvětlení uživateli, co vlastnost představuje.

- Ve vygenerovaném programovém kódu. Pokud používáte dokumentaci k extrakci dokumentace k rozhraní API, zobrazí se jako popis této vlastnosti v rozhraní API.

  **Kategorie**. Kategorie je záhlaví v okno Vlastnosti.

## <a name="exposing-style-features"></a>Vystavení funkcí stylu
 Některé dynamické funkce grafických prvků mohou být reprezentovány nebo *vystaveny* jako vlastnosti domény. Funkce, která byla vystavena tímto způsobem, může být aktualizována uživatelem a lze ji snáze aktualizovat pomocí kódu programu.

 V definici DSL klikněte pravým tlačítkem myši na třídu Shape, přejděte na **Přidat vystavené**a pak zvolte funkci.

 V obrazcích můžete vystavit vlastnosti **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** a **FillGradientMode** . V konektorech můžete zpřístupnit **barvy** `,`**TextColor**, **DashStyle**a vlastnosti **tloušťky** . V diagramech můžete zveřejnit vlastnosti **FillColor** a **TextColor** .

## <a name="forwarding-displaying-properties-of-related-elements"></a>Předávání: zobrazení vlastností souvisejících elementů
 Když uživatel vaší DSL vybere prvek v modelu, zobrazí se vlastnosti tohoto prvku v okně Vlastnosti. Můžete ale také zobrazit vlastnosti zadaných souvisejících prvků. To je užitečné, pokud jste definovali skupinu prvků, které pracují dohromady. Například můžete definovat hlavní prvek a volitelný element modulu plug-in. Je-li hlavní prvek mapován na tvar a druhý není, je užitečné zobrazit všechny vlastnosti, jako kdyby byly na jednom prvku.

 Tento efekt se nazývá *předávání vlastností*a v několika případech k němu dojde automaticky. V jiných případech můžete dosáhnout předávání vlastností definováním popisovače typu domény.

### <a name="default-property-forwarding-cases"></a>Výchozí případy předávání vlastností
 Když uživatel vybere obrazec nebo spojnici nebo prvek v Průzkumníkovi, zobrazí se v okno Vlastnosti následující vlastnosti:

- Vlastnosti domény, které jsou definovány v doméně třídy elementu modelu, včetně těch, které jsou definovány v základních třídách. Výjimkou jsou doménové vlastnosti, pro které jste nastavili, aby **bylo možné je procházet** `False`.

- Názvy prvků, které jsou propojeny pomocí relací, které mají násobnost 0.. 1. To poskytuje pohodlný způsob, jak zobrazit volitelně propojené prvky, i když jste pro relaci nedefinovali mapování spojnice.

- Vlastnosti domény relace vložení, která cílí na element. Vzhledem k tomu, že se vztahy vložení obvykle nezobrazují explicitně, umožní uživateli zobrazit jeho vlastnosti.

- Vlastnosti domény, které jsou definovány na vybraném tvaru nebo spojnici.

### <a name="adding-property-forwarding"></a>Přidání předávání vlastností
 Chcete-li vlastnost předává, definujte popisovač typu domény. Pokud máte doménový vztah mezi dvěma doménovými třídami, můžete použít popisovač typu domény k nastavení doménové vlastnosti v první třídě na hodnotu vlastnosti domény ve druhé třídě domény. Pokud například máte relaci mezi třídou domény **knihy** a doménou **autora** , můžete použít popisovač typu domény a nastavit vlastnost **název** **autora** knihy na okno Vlastnosti, když uživatel vybere knihu.

> [!NOTE]
> Přeposílání vlastností ovlivňuje pouze okno Vlastnosti, když uživatel upravuje model. Pro přijímací třídu nedefinuje doménovou vlastnost. Chcete-li získat přístup k vlastnosti předané domény v jiných částech definice DSL nebo v kódu programu, je nutné získat přístup k elementu pro předávání.

 Následující postup předpokládá, že jste vytvořili DSL. První pár kroků shrnuje požadavky.

##### <a name="to-forward-a-property-from-another-element"></a>Přeposlání vlastnosti z jiného elementu

1. Vytvořte [!INCLUDE[dsl](../includes/dsl-md.md)] řešení, které obsahuje alespoň dvě třídy, v tomto příkladu se říká **Kniha** a **Autor**. Mezi **knihou** a **autorem**by měl existovat vztah obou druhů.

     Násobnost zdrojové role (role na straně **knihy** ) by měla být 0.. 1 nebo 1.. 1, aby každá **Kniha** měla jednoho **autora**.

2. V **Průzkumníku DSL**klikněte pravým tlačítkem na třídu doména **knihy** a pak klikněte na **Přidat nový DomainTypeDescriptor**.

     Uzel s názvem **cesty popisovačů vlastních vlastností** se zobrazí v uzlu **vlastní deskriptor typu** .

3. Klikněte pravým tlačítkem na uzel **vlastní popisovač typu** a pak klikněte na **Přidat nový PropertyPath**.

     V uzlu **cesty vlastních popisovačů vlastností** se zobrazí nová cesta k vlastnosti.

4. Vyberte novou cestu vlastnosti a v okně **vlastnosti** nastavte **cestu k vlastnosti** na cestu příslušného prvku modelu.

     Cestu ve stromovém zobrazení můžete upravit kliknutím na šipku dolů napravo od této vlastnosti. Další informace o cestách k doméně najdete v tématu [syntaxe cesty k doméně](../modeling/domain-path-syntax.md). Pokud jste ho upravili, cesta by měla vypadat podobně jako **BookReferencesAuthor. Author/! Autor**:

5. **Vlastnost** nastavte na vlastnost **název** domény **Autor**.

6. Nastavte **zobrazované jméno** na **jméno autora**.

7. Transformujte všechny šablony, sestavte a spusťte DSL.

8. V diagramu modelu vytvořte knihu, autora a propojte ji pomocí referenčního vztahu. Vyberte prvek Book a v okno Vlastnosti měli byste vedle vlastností knihy zobrazovat jméno autora. Změňte název propojeného autora nebo propojte knihu s jiným autorem a sledujte, že se změní jméno autora knihy.

## <a name="custom-property-editors"></a>Vlastní editory vlastností
 Okno vlastností poskytuje vhodné výchozí prostředí pro úpravy pro typ každé doménové vlastnosti. Například pro výčtový typ uživatel uvidí rozevírací seznam a pro číselnou vlastnost může uživatel zadat číslice. To platí pouze pro předdefinované typy. Pokud zadáte externí typ, bude uživatel moci zobrazit hodnoty vlastnosti, ale nebude je upravovat.

 Můžete však zadat následující editory a typy:

1. Jiný editor, který se používá se standardním typem. Můžete například zadat editor cesty k souboru pro řetězcovou vlastnost.

2. Externí typ pro doménovou vlastnost a editor.

3. Editor .NET, jako je například editor cesty k souboru, nebo můžete vytvořit vlastní editor vlastností.

    Převod mezi externím typem a typem, jako je například String, který má výchozí editor.

   V DSL je *externí typ* libovolný typ, který není jedním z jednoduchých typů (například Boolean nebo Int32) nebo String.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Definování doménové vlastnosti, která má externí typ

1. V **Průzkumník řešení**přidejte odkaz na sestavení (DLL), které obsahuje externí typ, v projektu **DSL** .

    Sestavení může být sestavení .NET nebo sestavení, které vám dodal.

2. Přidejte typ do seznamu **typy domén** , pokud jste to ještě neudělali.

   1. Otevřete DslDefinition. DSL a v **Průzkumníku DSL**klikněte pravým tlačítkem na kořenový uzel a pak klikněte na **Přidat nový externí typ**.

        V uzlu **typy domén** se zobrazí nová položka.

       > [!WARNING]
       > Položka nabídky je na kořenovém uzlu DSL, nikoli v uzlu **typy domén** .

   2. Nastavte název a obor názvů nového typu v okno Vlastnosti.

3. Obvyklým způsobem přidejte do doménové třídy doménovou vlastnost.

    V okno Vlastnosti v poli **typ** vyberte externí typ z rozevíracího seznamu.

   V této fázi si uživatelé můžou zobrazit hodnoty vlastnosti, ale nemůžou je upravovat. Zobrazené hodnoty jsou získány z funkce `ToString()`. Můžete napsat programový kód, který nastaví hodnotu vlastnosti, například v příkazu nebo pravidle.

### <a name="setting-a-property-editor"></a>Nastavení editoru vlastností
 Přidejte atribut CLR do vlastnosti doména v následujícím tvaru:

```
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]

```

 Atribut můžete nastavit u vlastnosti pomocí položky **vlastního atributu** v okno Vlastnosti.

 Typ `AnEditor` musí být odvozen od typu zadaného ve druhém parametru. Druhý parametr by měl být buď <xref:System.Drawing.Design.UITypeEditor>, nebo <xref:System.ComponentModel.ComponentEditor>. Další informace najdete v tématu <xref:System.ComponentModel.EditorAttribute>.

 Můžete zadat buď vlastní editor, nebo editor dodaný v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], například <xref:System.Windows.Forms.Design.FileNameEditor> nebo <xref:System.Drawing.Design.ImageEditor>. Například použijte následující postup, chcete-li mít vlastnost, ve které může uživatel zadat název souboru.

##### <a name="to-define-a-file-name-domain-property"></a>Definování vlastnosti doména názvu souboru

1. Přidejte doménovou vlastnost do doménové třídy v definici DSL.

2. Vyberte novou vlastnost. Do pole **vlastní atribut** v okno Vlastnosti zadejte následující atribut. Chcete-li zadat tento atribut, klikněte na tlačítko se třemi tečkami **[...]** a potom zadejte název atributu a parametry samostatně:

    ```
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Ponechte typ doménové vlastnosti ve výchozím nastavení **řetězce**.

4. Chcete-li otestovat editor, ověřte, zda uživatelé mohou otevřít Editor názvů souborů pro úpravu doménové vlastnosti.

    1. Stiskněte klávesy CTRL + F5 nebo F5. V řešení ladění otevřete testovací soubor. Vytvořte prvek doménové třídy a vyberte ji.

    2. V okno Vlastnosti vyberte vlastnost doména. V poli hodnota se zobrazí tři tečky **[...]** .

    3. Klikněte na tlačítko se třemi tečkami. Zobrazí se dialogové okno soubor. Vyberte soubor a zavřete dialogové okno. Cesta k souboru je nyní hodnotou vlastnosti doména.

### <a name="defining-your-own-property-editor"></a>Definování vlastního editoru vlastností
 Můžete definovat vlastní editor. To umožňuje uživateli povolit buď úpravu typu, který jste definovali, nebo upravit standardní typ zvláštním způsobem. Můžete například uživateli dovolit zadat řetězec, který představuje vzorec.

 Editor definujete tak, že zapíšete třídu, která je odvozena od <xref:System.Drawing.Design.UITypeEditor>. Vaše třída musí přepsat:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> pro interakci s uživatelem a aktualizaci hodnoty vlastnosti.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, chcete-li určit, zda má Editor otevřít dialogové okno nebo zadat rozevírací nabídku.

  Můžete také zadat grafické znázornění hodnoty vlastnosti, která se zobrazí v mřížce vlastností. Provedete to tak, že přepíšete `GetPaintValueSupported` a `PaintValue`.  Další informace najdete v tématu <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Přidejte kód do samostatného souboru kódu v projektu **DSL** .

 Příklad:

```
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

```
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]

```

 Další informace najdete v tématu <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Poskytnutí rozevíracího seznamu hodnot
 Můžete zadat seznam hodnot, z nichž si uživatel může vybrat.

> [!NOTE]
> Tento postup poskytuje seznam hodnot, které se můžou měnit za běhu. Pokud chcete uvést seznam, který se nemění, zvažte místo toho použití výčtového typu jako typ vaší doménové vlastnosti.

 Chcete-li definovat seznam standardních hodnot, přidejte do vlastnosti domény atribut CLR, který má následující tvar:

```
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]

```

 Definujte třídu, která je odvozena z <xref:System.ComponentModel.TypeConverter>. Přidejte kód do samostatného souboru v projektu **DSL** . Příklad:

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
 [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
