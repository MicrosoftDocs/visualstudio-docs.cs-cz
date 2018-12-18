---
title: Přizpůsobení okna Vlastnosti
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 76e7b9433fe76464e7af385081ac3577d53919e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813893"
---
# <a name="customizing-the-properties-window"></a>Přizpůsobení okna Vlastnosti
Ve svém jazyce specifického pro doménu (DSL) v sadě Visual Studio můžete přizpůsobit vzhled a chování v okně Vlastnosti. V definici DSL definovat vlastnosti domény na každou doménovou třídu. Ve výchozím nastavení, když vyberete instance třídy v diagramu nebo v Průzkumníku modelu každé domény je uvedena vlastnost v okně Vlastnosti. To vám umožní zobrazit a upravit hodnoty vlastnosti domény, i když ještě je mapována na pole obrazec v diagramu.

## <a name="names-descriptions-and-categories"></a>Názvy, popisy a kategorie
 **Název a zobrazovaný název**. Zobrazovaný název vlastnosti v definici vlastnosti domény je název, který se zobrazí za běhu v okně Vlastnosti. Naopak název se používá při psaní kódu programu aktualizovat vlastnost. Název musí být správná alfanumerický název CLR, ale zobrazovaný název nemůže obsahovat mezery.

 Pokud název vlastnosti v definici DSL, své zobrazované jméno se automaticky nastaví na kopii tohoto názvu. Pokud píšete cased název Pascal, například "FuelGauge", zobrazovaný název bude automaticky obsahovat mezeru: "Posílit měřidla". Nicméně zobrazovaný název explicitně nastavena na jinou hodnotu.

 **Popis**. Popis doménová vlastnost, která se zobrazí na dvou místech:

- V dolní části okna vlastnosti, když uživatel vybere vlastnost. Slouží k vysvětlení uživatel, co představuje vlastnost.

- V kódu generovaného programu. Pokud používáte zařízení dokumentaci k extrakci dokumentace k rozhraní API, zobrazí se jako popis této vlastnosti v rozhraní API.

  **Kategorie**. Kategorie je záhlaví v okně Vlastnosti.

## <a name="exposing-style-features"></a>Vystavení stylu funkce
 Některé z dynamických funkcí grafické prvky může být reprezentován nebo *vystavený* jako vlastnosti domény. Funkce, která byla vystavena tímto způsobem je možné aktualizovat podle uživatele a další snadno aktualizovat pomocí kódu programu.

 Klikněte pravým tlačítkem na třídu tvar v definici DSL, přejděte na **přidat vystavený**a klikněte na tlačítko funkce.

 Ve tvarech můžete zveřejnit **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** a **FillGradientMode** vlastnosti. Na konektory můžete zveřejnit **barva**`,`**TextColor**, **DashStyle**, a **tloušťka** vlastnosti. V diagramech můžete zveřejnit **FillColor** a **TextColor** vlastnosti.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Předávání: Zobrazení vlastností souvisejících elementů
 Když uživatel tohoto kódu DSL vybere elementu v modelu, zobrazí se tento prvek vlastnosti v okně Vlastnosti. Můžete však také zobrazit vlastnosti zadané elementy související. To je užitečné, pokud jste definovali skupiny prvků, které spolupracují. Například můžete třeba definovat main element a volitelný prvek modulu plug-in. Pokud hlavní prvek je namapovaná na obrazec a druhý není, je vhodné zobrazíte jeho vlastnosti, jako by byly na jeden element.

 Tento efekt je s názvem *vlastnost předávání*, a to se stane automaticky v několika případech. V jiných případech může dosáhnout vlastnost předávání definováním popisovač typu domény.

### <a name="default-property-forwarding-cases"></a>Výchozí vlastnost předávání případy
 Když uživatel vybere obrazec nebo konektor nebo element v Průzkumníkovi, následující vlastnosti jsou zobrazeny v okně Vlastnosti:

-   Vlastnosti domény, které jsou definovány ve třídě domény prvku modelu, včetně těch, které jsou definovány v základních tříd. Výjimkou je vlastnosti domény, pro které jste nastavili **je Prohlížitelná** k `False`.

-   Názvy elementů, které jsou propojeny prostřednictvím vztahy, které mít násobnost 0.. 1. Poskytuje pohodlný způsob volitelně zobrazuje propojené prvky, i když jste nedefinovali mapování konektoru pro daný vztah.

-   Vlastnosti domény vztah obsažení, který cílí element. Protože vkládání relace se obvykle explicitně nezobrazují, to umožňuje uživateli zobrazit jejich vlastnosti.

-   Vlastnosti domény, které jsou definovány pro vybraný obrazec nebo spojnici.

### <a name="adding-property-forwarding"></a>Přidání vlastnosti předávání
 Chcete-li předat vlastnost, definovat popisovač typu domény. Pokud máte doménového vztahu mezi dvěma doménovými třídami, můžete nastavení vlastnosti domény první třídy k hodnotě vlastnosti domény v druhém doménové třídy popisovač typu domény. Například, pokud máte vztah mezi **knihy** doménové třídy a **Autor** doménovou třídu, můžete použít popisovač typu domény provádět **název** vlastnost Knihy **Autor** se zobrazí v okně Vlastnosti, když uživatel vybere knihy.

> [!NOTE]
>  Vlastnost předávání má vliv pouze v okně Vlastnosti, když uživatel upravuje model. Doménová vlastnost, která nedefinuje přijímající třídy. Pokud chcete získat přístup k vlastnosti předané domény v další části definice DSL nebo v programovém kódu, musí přístup k elementu předávání.

 Následující postup předpokládá, že jste vytvořili DSL. První několika krocích vytvořit souhrn požadavky.

##### <a name="to-forward-a-property-from-another-element"></a>Přeposílat vlastnost z jiného elementu

1. Vytvoření [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] řešení, které obsahuje alespoň dvě třídy, které v tomto příkladu se nazývají **knihy** a **Autor**. Měla by existovat relace mezi buď typu **knihy** a **Autor**.

    Násobnost zdrojové role (roli na **knihy** na straně) musí být 0.. 1 nebo 1..1, tak že každý **knihy** má jeden **Autor**.

2. V **Průzkumník DSL**, klikněte pravým tlačítkem na **knihy** doménové třídy a pak klikněte na tlačítko **přidat nové DomainTypeDescriptor**.

    Uzel s názvem **cesty popisovačů vlastnosti vlastní** je zobrazen **popisovači vlastního typu** uzlu.

3. Klikněte pravým tlačítkem myši **popisovači vlastního typu** uzlu a pak klikněte na tlačítko **přidat nové PropertyPath**.

    Nová cesta vlastnosti je zobrazen **cesty popisovačů vlastnosti vlastní** uzlu.

4. Vyberte novou vlastnost cestu a **vlastnosti** okno, nastavte **cesta k vlastnosti** cestu prvek odpovídající modelu.

    Kliknutím na šipku dolů napravo od této vlastnosti můžete upravit cestu ve stromovém zobrazení. Další informace o cestách domény, najdete v části [syntaxe cesty domény](../modeling/domain-path-syntax.md). Jakmile ji upravila cesta by měl vypadat podobně jako **BookReferencesAuthor.Author/! Autor**.

5. Nastavte **vlastnost** k **název** doménovou vlastnost elementu **Autor**.

6. Nastavte **zobrazovaný název** k **vytvářet název**.

7. Transformovat všechny šablony, sestavte a spusťte DSL.

8. V diagramu modelu vytvořit knize, autor a propojte je pomocí vztahu odkazu. Vybrat element knihy a v okně Vlastnosti byste měli vidět jméno autora vlastnostem knihy. Změna názvu propojené Autor nebo propojit různé autor knihy a podívejte se, že jméno autora knihu mění.

## <a name="custom-property-editors"></a>Editory vlastní vlastnost
 V okně Vlastnosti poskytuje vhodné výchozí nastavení prostředí pro typ každá vlastnost domain pro úpravy. Například pro výčtový typ, uživateli se zobrazí rozevírací seznam a pro číselné hodnoty, může uživatel zadat číslic. To platí jenom pro předdefinované typy. Při zadání externí typ, uživatel bude moct zobrazit hodnoty vlastnosti, ale nikoli upravovat.

 Můžete však zadat následující editory a typy:

1. Jiný editor, který se používá k typu standard. Můžete například zadat cestu editor souborů pro vlastnosti typu string.

2. Externí typ pro vlastnost domain a editor pro něj.

3. .NET editoru, jako je například editor cesta k souboru, nebo můžete vytvořit vlastní vlastnosti editor.

    Převod mezi externí a typem, jako je například řetězec, který má výchozí editor.

   V DSL *externí* je libovolný typ, který není součástí jednoduché typy (například logické hodnoty nebo Int32) nebo řetězec.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Chcete-li definovat doménová vlastnost, která má typ externího

1. V **Průzkumníka řešení**, přidejte odkaz na sestavení (DLL) obsahující externí typ, **Dsl** projektu.

    Sestavení může být sestavení .NET, nebo vámi zadané sestavení.

2. Přidat typ, který má **typy domén** seznamu, pokud jste tak již neučinili.

   1.  Otevřete DslDefinition.dsl a v **Průzkumník DSL**, klikněte pravým tlačítkem na kořenový uzel a potom klikněte na tlačítko **přidat novou externí typ**.

        Nový záznam se zobrazí v části **typy domén** uzlu.

       > [!WARNING]
       >  Položka nabídky není na uzlu root DSL **typy domén** uzlu.

   2.  V okně Vlastnosti nastavte název a obor názvů nového typu.

3. Doménová vlastnost, která přidejte do doménové třídy obvyklým způsobem.

    V okně Vlastnosti vyberte z rozevíracího seznamu v externí **typ** pole.

   V této fázi se uživatelé můžou zobrazovat hodnoty vlastnosti, ale nemůžou ho upravovat. Zobrazené hodnoty jsou získány z `ToString()` funkce. Můžete napsat programový kód, který nastavuje hodnotu vlastnosti, například v příkazu nebo pravidlo.

### <a name="setting-a-property-editor"></a>Nastavení editoru vlastností
 Přidáte atribut typu CLR pro vlastnost domain, v následujícím tvaru:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

 Atribut u vlastnosti můžete nastavit pomocí **vlastní atribut** záznam v okně Vlastnosti.

 Typ `AnEditor` musí být odvozen od typu určeného v druhý parametr. Druhý parametr by měl být buď <xref:System.Drawing.Design.UITypeEditor> nebo <xref:System.ComponentModel.ComponentEditor>. Další informace naleznete v tématu <xref:System.ComponentModel.EditorAttribute>.

 Můžete zadat vlastní editor nebo v editoru [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], jako například <xref:System.Windows.Forms.Design.FileNameEditor> nebo <xref:System.Drawing.Design.ImageEditor>. Například použijte následující postup vlastnosti, ve kterém může uživatel zadat název souboru.

##### <a name="to-define-a-file-name-domain-property"></a>Chcete-li definovat vlastnost souboru název domény

1.  Doménová vlastnost, která přidejte do doménové třídy v definici DSL.

2.  Vyberte novou vlastnost. V **vlastní atribut** pole v okně Vlastnosti, zadejte následující atribut. Chcete-li zadat Tento atribut, klikněte na tlačítko se třemi tečkami **[...]**  a potom zadejte název atributu a parametry samostatně:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3.  Ponechte výchozí nastavení z typu vlastnosti domény **řetězec**.

4.  Otestovat editoru, ověřte, že uživatelé mohou otevřít editor název souboru pro úpravu doménové vlastnosti.

    1.  Stiskněte kombinaci kláves CTRL + F5 nebo F5. Ladění řešení otevřete soubor testu. Vytvoření prvku doménové třídy a vyberte ji.

    2.  V okně Vlastnosti vyberte doménové vlastnosti. Hodnota pole zobrazí tři tečky **[...]** .

    3.  Klikněte na tlačítko se třemi tečkami. Zobrazí se dialogové okno. Vyberte soubor a zavřete dialogové okno. Cesta k souboru je nyní hodnoty vlastnosti domény.

### <a name="defining-your-own-property-editor"></a>Definování vlastní editor vlastností
 Můžete definovat vlastní editor. Provedli byste to umožňuje uživateli upravit typ, který jste definovali nebo upravit standardní typ zvláštním způsobem. Například můžete umožnit uživatelům vstupní řetězec, který představuje vzorec.

 Definice editoru zápisem, která je odvozena z třídy <xref:System.Drawing.Design.UITypeEditor>. Vaše třída musí přepsat:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, chcete-li komunikovat s uživatelem a aktualizujte hodnotu vlastnosti.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, chcete-li určit, zda editoru se otevře dialogové okno nebo rozevírací nabídky.

  Můžete také zadat grafická reprezentace hodnotu vlastnosti, která se zobrazí v mřížce vlastností. Chcete-li to provést, přepište `GetPaintValueSupported`, a `PaintValue`.  Další informace naleznete v tématu <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Přidejte kód v samostatném souboru kódu v **Dsl** projektu.

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

 Chcete-li použít tento editor, nastavte **vlastní atribut** vlastnosti domény:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

 Další informace naleznete v tématu <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Poskytuje rozevírací seznam hodnot
 Můžete zadat seznam hodnot pro uživatele lze vybírat.

> [!NOTE]
>  Tento postup obsahuje seznam hodnot, které můžete změnit za běhu. Pokud chcete poskytnout seznam, který se nemění, zvažte místo toho pomocí Výčtový typ jako typ doménové vlastnosti.

 Pokud chcete definovat seznam standardních hodnot, přidáte do doménová vlastnost CLR atribut, který má následující tvar:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

 Definujte třídu, která je odvozena z <xref:System.ComponentModel.TypeConverter>. Přidejte kód v samostatném souboru v **Dsl** projektu. Příklad:

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