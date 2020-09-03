---
title: Definování omezení ověření pro modely UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 258fc138f032d34e57df69386b6849fc3a0650a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547586"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definování omezení ověřování pro modely UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete definovat omezení ověřování, která otestuje, zda model splňuje podmínku, kterou zadáte. Můžete například definovat omezení, abyste se ujistili, že uživatel nevytvoří smyčku vztahů dědičnosti. Omezení je vyvoláno, když se uživatel pokusí otevřít nebo uložit model a lze jej také vyvolat ručně. Pokud se omezení nepovede, do okna chyby se přidá chybová zpráva, kterou definujete. Tato omezení můžete zabalit do rozšíření integrace sady Visual Studio ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)) a distribuovat je ostatním uživatelům aplikace Visual Studio.

 Můžete také definovat omezení, která ověřují model proti externím prostředkům, jako jsou databáze. Pokud chcete ověřit kód programu proti diagramu vrstvy, přečtěte si téma [Přidání ověření vlastní architektury do diagramů vrstev](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 Chcete-li zjistit, které verze aplikace Visual Studio podporují modely UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="applying-validation-constraints"></a>Aplikování omezení ověřování
 Omezení ověřování se používají ve třech případech: při uložení modelu; Když otevřete model; a po kliknutí na **ověřit model UML** v nabídce **Architektura** . V každém případě budou použity pouze omezení, která byla definována pro tento případ, i když je obvykle definováno omezení pro použití ve více než jednom případě.

 Chyby ověřování jsou hlášeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okně chyby a můžete dvakrát kliknout na chybu a vybrat prvky modelu, které jsou v chybě.

 Další informace o použití ověřování najdete v tématu [ověření modelu UML](../modeling/validate-your-uml-model.md).

## <a name="defining-a-validation-extension"></a>Definování rozšíření ověřování
 Chcete-li vytvořit rozšíření ověřování pro návrháře UML, je nutné vytvořit třídu, která definuje omezení ověřování a vložit třídu do rozšíření integrace sady Visual Studio (VSIX). VSIX funguje jako kontejner, který může omezení nainstalovat. Existují dvě alternativní metody definování rozšíření ověřování:

- **Vytvořte rozšíření ověřování ve vlastním souboru VSIX pomocí šablony projektu.** Toto je rychlejší metoda. Použijte ji v případě, že nechcete kombinovat omezení ověřování s jinými typy rozšíření, jako jsou příkazy nabídky, vlastní položky sady nástrojů nebo obslužné rutiny gesta. V jedné třídě můžete definovat několik omezení.

- **Vytvořte samostatnou třídu ověřování a projekty VSIX.** Tuto metodu použijte, pokud chcete zkombinovat několik typů rozšíření do stejného VSIX. Například pokud příkaz nabídky očekává, že model bude dodržovat konkrétní omezení, můžete jej vložit do stejného VSIX jako metodu ověřování.

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Vytvoření rozšíření ověřování ve vlastním souboru VSIX

1. V dialogovém okně **Nový projekt** , v části **modelování projektů**vyberte možnost **rozšíření ověřování**.

2. Otevřete soubor **. cs** v novém projektu a upravte třídu pro implementaci omezení ověření.

    Další informace najdete v tématu [vyhodnocení omezení ověření](#Implementing).

   > [!IMPORTANT]
   > Ujistěte se, že soubory **. cs** obsahují následující `using` příkaz:
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. Můžete přidat další omezení definováním nových metod. Chcete-li identifikovat metodu jako metodu ověřování, musí být označena atributy stejným způsobem jako metoda prvotního ověření.

4. Vyzkoušení vašich omezení stisknutím klávesy F5. Další informace najdete v tématu [spuštění omezení ověření](#Executing).

5. Nainstalujte příkaz nabídky do jiného počítače zkopírováním souboru **bin \\ \* \\ \* . vsix** sestaveného vaším projektem. Další informace najdete v tématu [instalace a odinstalace rozšíření](#Installing).

   Když přidáte jiné soubory **. cs** , budete obvykle vyžadovat následující `using` příkazy:

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 Tady je alternativní postup:

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Vytvoření samostatného omezení ověřování v projektu knihovny tříd

1. Vytvořte projekt knihovny tříd, buď jej přidejte do stávajícího řešení VSIX, nebo vytvořte nové řešení.

    1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

    2. V části **Nainstalované šablony**rozbalte položku **Visual C#** nebo **Visual Basic**a potom v prostředním sloupci zvolte možnost **Knihovna tříd**.

2. Vytvořte projekt VSIX, pokud ho vaše řešení ještě neobsahuje:

    1. V **Průzkumník řešení**v místní nabídce řešení vyberte možnost  **Přidat**, **Nový projekt**.

    2. V části **Nainstalované šablony**rozbalte položku **Visual C#** nebo **Visual Basic**a pak zvolte možnost **rozšiřitelnost**. V prostředním sloupci klikněte na **projekt VSIX**.

3. Nastavte projekt VSIX jako projekt po spuštění řešení.

    - V Průzkumník řešení v místní nabídce projektu VSIX vyberte **nastavit jako spouštěný projekt**.

4. V části **source. extension. vsixmanifest**v části **obsah**přidejte projekt knihovny tříd jako komponentu MEF:

    1. Na kartě **metadata** nastavte název VSIX.

    2. Na kartě **cíle instalace** nastavte jako cíle verze sady Visual Studio.

    3. Na kartě **assets (prostředky** ) vyberte **Nový**a v dialogovém okně nastavte:

         **Typ**  =  **Komponenta MEF**

         **Zdroj**  =  **Projekt v aktuálním řešení**

         **Projekt**  =  *Váš projekt knihovny tříd*

#### <a name="to-define-the-validation-class"></a>Definování třídy ověřování

1. Tento postup nebudete potřebovat, pokud jste vytvořili třídu ověřování s vlastním souborem VSIX ze šablony projektu ověření.

2. V projektu třídy ověřování přidejte odkazy na následující [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] sestavení:

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. Přidejte soubor do projektu knihovny tříd obsahující kód, který je podobný následujícímu příkladu.

    - Každé omezení ověření je obsaženo v metodě, která je označena konkrétním atributem. Metoda přijímá parametr typu prvku modelu. Při vyvolání ověřování bude rozhraní ověřování používat každou metodu ověřování pro každý prvek modelu, který odpovídá jeho typu parametru.

    - Tyto metody lze umístit do libovolných tříd a oborů názvů. Změňte své preference.

    ```
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using Microsoft.VisualStudio.Modeling.Validation;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.Uml.Classes;
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.

    namespace Validation
    {
      public class MyValidationExtensions
      {
        // SAMPLE VALIDATION METHOD.
        // All validation methods have the following attributes.
        [Export(typeof(System.Action<ValidationContext, object>))]
        [ValidationMethod(
           ValidationCategories.Save
         | ValidationCategories.Open
         | ValidationCategories.Menu)]
        public void ValidateClassNames
          (ValidationContext context,
           // This type determines what elements
           // will be validated by this method:
           IClass elementToValidate)
        {
          // A validation method should not change the model.

          List<string> attributeNames = new List<string>();
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)
          {
            string name = attribute.Name;
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))
            {
              context.LogError(
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),
                "001", elementToValidate);
            }
            attributeNames.Add(name);
          }

        }
        // Add more validation methods for different element types.
      }
    }
    ```

## <a name="executing-a-validation-constraint"></a><a name="Executing"></a> Spouští se omezení ověřování.
 Pro účely testování spusťte metody ověřování v režimu ladění.

#### <a name="to-test-the-validation-constraint"></a>Otestování omezení ověřování

1. Stiskněte klávesu **F5**nebo v nabídce **ladění** zvolte možnost **Spustit ladění**.

     Spustí se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     **Řešení potíží**: Pokud se nový [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí:

    - Pokud máte více než jeden projekt, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.

    - V Průzkumník řešení v místní nabídce spouštěcího nebo pouze projektu vyberte možnost **vlastnosti**. V editoru vlastností projektu vyberte kartu **ladění** . Ujistěte se, že řetězec v poli **spustit externí program** má úplnou cestu k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , obvykle:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. V experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování.

3. Chcete-li nastavit test pro omezení ukázky uvedené v předchozí části:

    1. Otevřete diagram tříd.

    2. Vytvořte třídu a přidejte dva atributy, které mají stejný název.

4. V místní nabídce kdekoli v diagramu vyberte **ověřit**.

5. Všechny chyby v modelu budou hlášeny v okně chyby.

6. Dvakrát klikněte na zprávu o chybách. Pokud jsou prvky uvedené v sestavě viditelné na obrazovce, budou zvýrazněny.

     **Řešení potíží**: Pokud se příkaz **ověřit** v nabídce nezobrazí, ujistěte se, že:

    - Ověřovací projekt je uveden jako Komponenta MEF na kartě **assets (prostředky** ) ve složce **source. Extensions. manifest** v projektu VSIX.

    - Správné `Export` atributy a `ValidationMethod` jsou připojeny k metodám ověřování.

    - `ValidationCategories.Menu` je obsažen v argumentu pro `ValidationMethod` atribut a je tvořen s jinými hodnotami pomocí logického operátoru OR (&#124;).

    - Parametry všech `Import` `Export` atributů a jsou platné.

## <a name="evaluating-the-constraint"></a><a name="Implementing"></a> Vyhodnocení omezení
 Metoda ověřování by měla určit, jestli má omezení ověřování, které chcete použít, hodnotu true nebo false. V případě hodnoty true by neměl dělat žádná akce. Pokud má hodnotu false, měla by hlásit chybu pomocí metod poskytovaných `ValidationContext` parametrem.

> [!NOTE]
> Metody ověřování by neměly měnit model. Když nebo v jakém pořadí se budou tato omezení provádět, není nijak zaručeno. Pokud je nutné předat informace mezi následným provedením ověřovací metody v rámci ověřovacího běhu, můžete použít kontextovou mezipaměť popsanou v tématu [koordinace více ověření](#ContextCache).

 Například pokud chcete zajistit, že každý typ (třída, rozhraní nebo enumerátor) má název, který je alespoň tři znaky dlouhý, můžete použít tuto metodu:

```
public void ValidateTypeName(ValidationContext context, IType type)
{
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)
  {
    context.LogError(
      string.Format("Type name {0} is too short", type.Name),
               "001", type);
   }
 }
```

 Informace o metodách a typech, které můžete použít k procházení a čtení modelu, najdete v tématu [programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md) .

### <a name="about-validation-constraint-methods"></a>O metodách omezení ověřování
 Každé omezení ověření je definováno metodou následujícího formuláře:

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 Atributy a parametry každé metody ověřování jsou následující:

|Podpis|Popis|
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Definuje metodu jako omezení ověřování pomocí Managed Extensibility Framework (MEF).|
|`[ValidationMethod (ValidationCategories.Menu)]`|Určuje, kdy bude provedeno ověřování. Použijte bitový operátor OR (&#124;), pokud chcete kombinovat více než jednu možnost.<br /><br /> `Menu` = vyvoláno v nabídce ověřit.<br /><br /> `Save` = vyvoláno při ukládání modelu.<br /><br /> `Open` = vyvoláno při otevírání modelu. `Load` = vyvoláno při ukládání modelu, ale u porušování se uživateli zobrazí upozornění, že není možné model znovu otevřít. Také voláno při načítání před analýzou modelu.|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Nahraďte druhý parametr `IElement` typem prvku, na který chcete omezení použít. Metoda omezení bude vyvolána pro všechny elementy v zadaném typu.<br /><br /> Název metody je neimportované.|

 Můžete definovat tolik metod ověřování, kolik chcete, s různými typy ve druhém parametru. Při vyvolání ověřování bude každá metoda ověřování volána pro každý prvek modelu, který odpovídá typu parametru.

### <a name="reporting-validation-errors"></a>Generování sestav – chyby ověření
 Chcete-li vytvořit zprávu o chybách, použijte metody, které poskytuje `ValidationContext` :

 `context.LogError("error string", errorCode, elementsWithError);`

- `"error string"` zobrazí se v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Seznam chyb

- `errorCode` je řetězec, který by měl být jedinečným identifikátorem chyby.

- `elementsWithError` Identifikuje elementy v modelu. Když uživatel dvakrát klikne na zprávu o chybách, bude vybrán obrazec představující tento prvek.

  `LogError(),``LogWarning()`a `LogMessage()` umístí zprávy do různých oddílů seznamu chyb.

## <a name="how-validation-methods-are-applied"></a>Způsob použití metod ověřování
 Ověřování se aplikuje na každý prvek v modelu, včetně vztahů a částí větších prvků, jako jsou atributy třídy a parametrů operace.

 Každá metoda ověřování je použita na každý prvek, který odpovídá typu v jeho druhém parametru. To znamená, že například pokud definujete metodu ověřování s druhým parametrem `IUseCase` a jinou s jeho nadtypem `IElement` , pak obě tyto metody budou použity pro každý případ použití v modelu.

 Hierarchie typů je shrnuta v [typech prvků modelu UML](../modeling/uml-model-element-types.md).

 K prvkům můžete přistupovat také pomocí následujících vztahů. Například pokud byste chtěli definovat metodu ověřování na `IClass` , můžete cyklicky procházet vlastními vlastnostmi:

```
public void ValidateTypeName(ValidationContext context, IClass c)
{
   foreach (IProperty property in c.OwnedAttributes)
   {
       if (property.Name.Length < 3)
       {
            context.LogError(
                 string.Format(
                        "Property name {0} is too short",
                        property.Name),
                 "001", property);
        }
   }
}
```

### <a name="creating-a-validation-method-on-the-model"></a>Vytvoření metody ověřování v modelu
 Pokud chcete zajistit, aby byla metoda ověřování volána přesně jednou během každého spuštění ověřování, můžete ověřit `IModel` :

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>Ověřování obrazců a diagramů
 Metody ověřování nejsou vyvolány na prvcích zobrazení, jako jsou diagramy a tvary, protože primárním účelem metod ověřování je ověřit model. K aktuálnímu diagramu ale můžete přistupovat pomocí kontextu diagramu.

 Ve vaší třídě ověřování deklarujte `DiagramContext` jako importovanou vlastnost:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 V metodě ověřování můžete použít `DiagramContext` pro přístup k aktuálnímu diagramu fokusu, pokud je nějaký:

```
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;
  if (focusDiagram != null)
  {
    foreach (IShape<IUseCase> useCaseShape in
              focusDiagram.GetChildShapes<IUseCase>())
    { ...
```

 Chcete-li zaznamenat chybu, je nutné získat prvek modelu, který tvar představuje, protože nelze předat tvar `LogError` :

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="coordinating-multiple-validations"></a><a name="ContextCache"></a> Koordinace více ověření
 Když je vyvoláno ověřování, například uživatel z nabídky diagramu, každá metoda ověřování je použita na každý prvek modelu. To znamená, že v jednom vyvolání architektury ověřování může být stejná metoda použita mnohokrát na různé prvky.

 To představuje problém pro ověření, která se týkají vztahů mezi prvky. Můžete například napsat ověření, které začíná, řekněme, případ použití, a projde vztahy **zahrnutí** a ověří, že nejsou k dispozici žádné smyčky. Ale pokud je metoda použita pro každý případ použití v modelu, který má mnoho odkazů **include** , je pravděpodobnější, že bude opakovaně zpracovávat stejné oblasti modelu.

 Aby k této situaci nedocházelo, existuje mezipaměť kontextu, ve které jsou informace zachovány během ověřovacího běhu. Můžete ji použít k předávání informací mezi různými spuštěními metod ověřování. Můžete například uložit seznam prvků, které již byly v rámci tohoto ověřovacího běhu zařízeny. Mezipaměť je vytvořena na začátku každého spuštění ověřování a nelze ji použít k předávání informací mezi různými běhy ověřování.

|Syntax|Popis|
|-|-|
|`context.SetCacheValue<T> (name, value)`|Uložení hodnoty|
|`context.TryGetCacheValue<T> (name, out value)`|Získat hodnotu. Vrátí hodnotu true, pokud bylo úspěšné.|
|`context.GetValue<T>(name)`|Získat hodnotu.|
|`Context.GetValue<T>()`|Získá hodnotu zadaného typu.|

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a> Instalace a odinstalace rozšíření
 Rozšíření můžete nainstalovat [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] na svém počítači i v jiných počítačích.

#### <a name="to-install-an-extension"></a>Instalace rozšíření

1. V počítači Najděte soubor **. vsix** , který byl SESTAVEN projektem VSIX.

    1. V **Průzkumník řešení**v místní nabídce projektu VSIX vyberte možnost **Otevřít složku v Průzkumníku Windows**.

    2. Vyhledejte soubor **bin \\ \* \\ **_YourProject_**. VSIX.**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat rozšíření. Může to být váš vlastní počítač nebo jiný.

    - Cílový počítač musí mít jednu z edicí, kterou [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] jste zadali v části **source. extension. vsixmanifest**.

3. V cílovém počítači otevřete soubor **. vsix** .

     **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření

1. V nabídce **nástroje** vyberte **rozšíření a aktualizace**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření a pak zvolte **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z následujícího umístění, kde *% localappdata%* je obvykle *jednotka*: \Users \\ *uživatelské_jméno*\AppData\Local:

   *% Localappdata%* **\Microsoft\VisualStudio \\ [verze] \Extensions**

## <a name="example"></a><a name="Example"></a> Případě
 Tento příklad najde smyčky v relaci závislosti mezi prvky.

 Provede ověření při uložení i v příkazu nabídky ověřit.

```
/// <summary>
/// Verify that there are no loops in the dependency relationsips.
/// In our project, no element should be a dependent of itself.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">Element to start validation from.</param>
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu
     | ValidationCategories.Save | ValidationCategories.Open)]
public void NoDependencyLoops(ValidationContext context, INamedElement element)
{
    // The validation framework will call this method
    // for every element in the model. But when we follow
    // the dependencies from one element, we will validate others.
    // So we keep a list of the elements that we don't need to validate again.
    // The list is kept in the context cache so that it is passed
    // from one execution of this method to another.
    List<INamedElement> alreadySeen = null;
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))
    {
       alreadySeen = new List<INamedElement>();
       context.SetCacheValue("No dependency loops", alreadySeen);
    }

    NoDependencyLoops(context, element,
                new INamedElement[0], alreadySeen);
}

/// <summary>
/// Log an error if there is any loop in the dependency relationship.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">The element to be validated.</param>
/// <param name="dependants">Elements we've followed in this recursion.</param>
/// <param name="alreadySeen">Elements that have already been validated.</param>
/// <returns>true if no error was detected</returns>
private bool NoDependencyLoops(ValidationContext context,
    INamedElement element, INamedElement[] dependants,
    List<INamedElement> alreadySeen)
{
    if (dependants.Contains(element))
    {
        context.LogError(string.Format("{0} should not depend on itself", element.Name),
        "Fabrikam.UML.NoGenLoops", // unique code for this error
        dependants.SkipWhile(e => e != element).ToArray());
            // highlight elements that are in the loop
        return false;
    }
    INamedElement[] dependantsPlusElement =
        new INamedElement[dependants.Length + 1];
    dependants.CopyTo(dependantsPlusElement, 0);
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;

    if (alreadySeen.Contains(element))
    {
        // We have already validated this when we started
        // from another element during this validation run.
        return true;
    }
    alreadySeen.Add(element);

    foreach (INamedElement supplier in element.GetDependencySuppliers())
    {
        if (!NoDependencyLoops(context, supplier,
             dependantsPlusElement, alreadySeen))
        return false;
    }
    return true;
}
```

## <a name="see-also"></a>Viz také
 [Definování a instalace programování rozšíření pro modelování](../modeling/define-and-install-a-modeling-extension.md) [pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)
