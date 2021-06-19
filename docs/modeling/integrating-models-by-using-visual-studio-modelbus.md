---
title: Integrace modelů pomocí modelbusu
description: Zjistěte, Visual Studio ModelBus poskytuje metodu pro vytváření propojení mezi modely a z jiných nástrojů do modelů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 350398d91d73a722956d195b300311f313ff34db
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391059"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Integrace modelů pomocí Visual Studio Modelbus

Visual Studio ModelBus poskytuje metodu pro vytváření propojení mezi modely a z jiných nástrojů do modelů. Můžete například propojit modely jazyka (DSL) specifické pro doménu a modely UML. Můžete vytvořit integrovanou sadu adres DSL.

ModelBus umožňuje vytvořit jedinečný odkaz na model nebo na konkrétní prvek uvnitř modelu. Tento odkaz může být uložen mimo model, například v elementu v jiném modelu. Když v pozdějších případech chce nástroj získat přístup k prvku, infrastruktura Model Bus načte příslušný model a vrátí prvek . Pokud chcete, můžete model zobrazit uživateli. Pokud k souboru nelze získat přístup v předchozím umístění, ModelBus požádá uživatele, aby ho našel. Pokud uživatel soubor najde, ModelBus opraví všechny odkazy na tento soubor.

> [!NOTE]
> V aktuální implementaci Visual Studio ModelBus musí být propojené modely položkami ve stejném Visual Studio řešení.

Další informace a vzorový kód najdete v těchto tématu:

- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Modeling SDK pro Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> Poskytnutí přístupu k DSL
 Než budete moci vytvořit odkazy ModelBus na model nebo jeho prvky, musíte definovat ModelBusAdapter pro DSL. Nejjednodušší způsob, jak to provést, je použít rozšíření Visual Studio Model Bus, které přidává příkazy do návrháře DSL.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Vystavení definice DSL sběrnici modelu

1. Otevřete definiční soubor DSL. Klikněte pravým tlačítkem na návrhovou plochu a pak klikněte **na Povolit Modelbus.**

2. V dialogovém okně zvolte I want to expose this DSL to the ModelBus (Chci tento DSL zveřejnit **pro ModelBus).** Obě možnosti můžete zvolit, pokud chcete, aby tento DSL zpřístupňuje své modely i spotřebovává odkazy na jiné seznamy DSL.

3. Klikněte na **OK**. Do řešení DSL se přidá nový projekt ModelBusAdapter.

4. Pokud chcete přistupovat k DSL z textové šablony, musíte upravit AdapterManager.tt v novém projektu. Pokud chcete k DSL přistupovat z jiného kódu, jako jsou příkazy a obslužné rutiny událostí, tento krok vy vynechat. Další informace najdete v tématu [Použití Visual Studio ModelBus v textové šabloně.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

   1. Změňte základní třídu AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Na konec souboru vložte tento další atribut před třídu AdapterManager:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. V části Odkazy projektu ModelBusAdapter přidejte **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.

      Pokud chcete k DSL přistupovat z textových šablon i z jiného kódu, potřebujete dva adaptéry, jeden upravený a jeden nezměněný.

5. Klikněte **na Transformovat všechny šablony.**

6. Znovu sestavte řešení.

   ModelBus teď může otevírat instance tohoto DSL.

   Složka `ModelBusAdapters\bin\*` obsahuje sestavení sestavená `Dsl` projektem a `ModelBusAdapters` projektem. Chcete-li odkazovat na tento DSL z jiného DSL, měli byste tato sestavení importovat.

### <a name="ensure-that-elements-can-be-referenced"></a>Ujistěte se, že na elementy lze odkazovat.

Visual Studio ModelBus adaptéry ve výchozím nastavení používají identifikátor GUID elementu k jeho identifikaci. Tyto identifikátory proto musí být zachovány v souboru modelu.

Pokud chcete zajistit zachování ID elementů:

1. Otevřete DslDefinition.dsl.

2. V Průzkumníku DSL rozbalte **chování serializace XML** a pak **data třídy**.

3. Pro každou třídu, na kterou chcete vytvořit odkazy Model Bus:

    Klikněte na uzel třídy a v okno Vlastnosti se ujistěte, že je možnost **Serialize ID nastavená** na `true` .

   Pokud chcete k identifikaci prvků místo identifikátorů GUID použít názvy prvků, můžete také přepsat části generovaných adaptérů. Přepište následující metody ve třídě adapter:

- Přepsáním `GetElementId` vrátíte identifikátor, který chcete použít. Tato metoda se volá při vytváření odkazů.

- Přepsáním `ResolveElementReference` vyhledejte správný prvek z odkazu Model Bus.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Přístup k DSL z jiného DSL

Odkazy sběrnice modelu můžete ukládat do vlastnosti domény v DSL a můžete napsat vlastní kód, který je používá. Můžete také nechat uživatele vytvořit odkaz na sběrnici modelu výběrem souboru modelu a elementu v jeho souboru.

Pokud chcete dsl povolit použití odkazů na jiný DSL, měli byste nejprve z něj udělat *příjemce* odkazů modelové sběrnice.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Povolení, aby DSL spotřebovává odkazy na vystavený DSL

1. V diagramu definice DSL klikněte pravým tlačítkem na hlavní část diagramu a pak klikněte na **Povolit Modelbus.**

2. V dialogovém okně vyberte Chci povolit, aby tento **model spotřebovává odkazy sběrnice modelu.**

3. V projektu Dsl spotřebovávajícího DSL přidejte do odkazů na projekt následující sestavení. Tato sestavení (.dll souborů) najdete v adresáři ModelBusAdapter\bin \\ * zveřejněné dsl.

    - Vystavené sestavení DSL, například **Fabrikam.FamilyTree.Dsl.dll**

    - Vystavené sestavení adaptéru sběrnice modelu, například **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. Přidejte následující sestavení .NET do odkazů projektu využívajícího projekt DSL.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Uložení odkazu modelové sběrnice do vlastnosti domény

1. V definici DSL spotřebovávajícího DSL přidejte vlastnost domény do třídy domény a nastavte její název.

2. V okno Vlastnosti s vybranou vlastností domény nastavte **Typ** na `ModelBusReference` .

   V této fázi může programový kód nastavit hodnotu vlastnosti, ale je jen pro čtení v okno Vlastnosti.

   Uživatelům můžete povolit nastavení vlastnosti pomocí specializovaného referenčního editoru ModelBus. Existují dvě verze tohoto editoru nebo *výběru:* jedna umožňuje uživatelům zvolit soubor modelu a druhá umožňuje uživatelům zvolit soubor modelu a prvek v rámci modelu.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Umožnění uživateli nastavit odkaz na sběrnici modelu ve vlastnosti domény

1. Pravým tlačítkem myši klikněte na vlastnost domény a pak klikněte na **Upravit modelReferenční vlastnosti specifické probusreference.** Otevře se dialogové okno. Toto je *výběr sběrnice modelu*.

2. Vyberte vhodný **Druh PrvkuBusReference**: na model nebo na prvek uvnitř modelu.

3. Do řetězce filtru dialogového okna souboru zadejte řetězec, například `Family Tree files |*.ftree` . Nahraďte příponu souboru zveřejněným DSL.

4. Pokud jste se rozhodli odkazovat na prvek v modelu, můžete přidat seznam typů, které uživatel může vybrat, například Company.FamilyTree.Person.

5. Klikněte **na OK** a potom na panelu nástrojů **Průzkumník řešení** Transformovat **všechny** šablony.

    > [!WARNING]
    > Pokud jste nevy vybrali platný model nebo entitu, tlačítko OK nebude mít žádný vliv, i když se může zobrazit povolené.

6. Pokud jste zadali seznam cílových typů, například Company.FamilyTree.Person, musíte do projektu DSL přidat odkaz na sestavení a odkazovat na knihovnu DLL cílového DSL, například Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Testování odkazu modelové sběrnice

1. Sestavíte vystavené i využívající seznamy DSL.

2. Stisknutím kláves F5 nebo CTRL+F5 spusťte jeden z těchto souborů DSL v experimentálním režimu.

3. V projektu Ladění v experimentální instanci Visual Studio přidejte soubory, které jsou instancemi každého DSL.

    > [!NOTE]
    > Visual Studio ModelBus lze přeložit pouze odkazy na modely, které jsou položky ve stejném Visual Studio řešení. Nemůžete například vytvořit odkaz na soubor modelu v jiné části systému souborů.

4. Vytvořte některé prvky a propojení v instanci vystavených DSL a uložte je.

5. Otevřete instanci spotřebovávajícího DSL a vyberte prvek modelu, který má vlastnost odkazu sběrnice modelu.

6. V okno Vlastnosti dvakrát klikněte na vlastnost odkaz na sběrnici modelu. Otevře se dialogové okno pro výběr.

7. Klikněte **na Procházet** a vyberte instanci vystavených DSL.

     Výběrem také můžete zvolit položku v modelu, pokud jste zadali typ odkazu sběrnice modelu specifický pro prvek.

## <a name="creating-references-in-program-code"></a>Vytváření odkazů v kódu programu

Pokud chcete uložit odkaz na model nebo prvek uvnitř modelu, vytvoříte `ModelBusReference` . Existují dva druhy : odkazy na model a `ModelBusReference` odkazy na elementy.

K vytvoření odkazu na model potřebujete AdapterManager (Správce adaptéru) dsl, jehož je model instancí, a název souboru nebo Visual Studio položky projektu modelu.

K vytvoření odkazu na prvek potřebujete adaptér pro soubor modelu a element, na který chcete odkazovat.

> [!NOTE]
> Pomocí Visual Studio ModelBus můžete vytvářet odkazy pouze na položky ve stejném Visual Studio řešení.

### <a name="import-the-exposed-dsl-assemblies"></a>Import vystavených sestavení DSL

Ve spotřebě projektu přidejte odkazy projektu na sestavení DSL a ModelBusAdapter vystavený DSL.

Předpokládejme například, že chcete uložit odkazy ModelBus do prvků DSL MusicLibrary. Odkazy ModelBus budou odkazovat na prvky DSL FamilyTree. V projektu řešení MusicLibrary v uzlu Odkazy přidejte odkazy na `Dsl` následující sestavení:

- Fabrikam.FamilyTree.Dsl.dll – vystavený DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll – adaptér ModelBus vystaveného DSL.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Tato sestavení lze najít v projektu `ModelBusAdapters` vystavený DSL v části `bin\*` .

  V souboru kódu, kde budete vytvářet odkazy, budete obvykle muset importovat tyto obory názvů:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Vytvoření odkazu na model

Pokud chcete vytvořit odkaz na model, přistupte ke Správci adaptéru pro vystavený DSL a použijte ho k vytvoření odkazu na model. Můžete zadat buď cestu k souboru, nebo `EnvDTE.ProjectItem` .

Ve Správci adaptéru můžete získat adaptér, který poskytuje přístup k jednotlivým prvkům v modelu.

> [!NOTE]
> Jakmile s adaptérem skončíte, musíte adaptér zlikvidovat. Nejpohodlnější způsob, jak toho dosáhnout, je pomocí `using` příkazu . Toto dokládá následující příklad.

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

Pokud chcete mít možnost později použít, můžete ji uložit do vlastnosti `modelReference` domény s externím typem `ModelBusReference` :

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Pokud chcete uživatelům povolit úpravy této vlastnosti domény, použijte `ModelReferenceEditor` jako parametr v atributu Editor. Další informace najdete v tématu [Povolení uživateli upravit odkaz.](#editRef)

### <a name="to-create-a-reference-to-an-element"></a>Vytvoření odkazu na element

Adaptér, který jste vytvořili pro model, můžete použít k vytvoření a vyřešení odkazů.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Pokud budete chtít později použít , můžete ho uložit do vlastnosti `elementReference` domény s externím typem `ModelBusReference` . Pokud chcete uživatelům povolit jeho úpravy, `ModelElementReferenceEditor` použijte v atributu Editor jako parametr . Další informace najdete v tématu [Povolení uživateli upravit odkaz.](#editRef)

### <a name="resolving-references"></a>Řešení odkazů

Pokud máte `ModelBusReference` (MBR), můžete získat model nebo prvek modelu, na který odkazuje. Pokud je prvek zobrazen v diagramu nebo jiném zobrazení, můžete otevřít zobrazení a vybrat prvek.

Adaptér můžete vytvořit z MBR. Z adaptéru můžete získat kořen modelu. Můžete také vyřešit pravidla mbr, která odkazují na konkrétní prvky v rámci modelu.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Řešení odkazů ModelBus v textové šabloně

1. DSL, ke které chcete získat přístup, musí mít adaptér ModelBus, který je nakonfigurovaný pro přístup pomocí textových šablon. Další informace najdete v tématu [Poskytnutí přístupu k DSL.](#provide)

2. Obvykle budete přistupovat k cílovému DSL pomocí odkazu modelové sběrnice (MBR) uloženého ve zdrojovém DSL. Vaše šablona proto obsahuje direktivu zdrojového DSL a kód pro překlad MBR. Další informace o textových šablonách najdete v tématu [Generování kódu z Domain-Specific Jazyka](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   Další informace a názorný postup najdete v tématu [Použití Visual Studio ModelBus v textové šabloně.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Serializace ModeluBusReference

Pokud chcete uložit `ModelBusReference` (MBR) ve formě řetězce, můžete jej serializovat:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

MBR serializovaný tímto způsobem je nezávislý na kontextu. Pokud používáte jednoduchý souborový adaptér modelové sběrnice, obsahuje MBR absolutní cestu k souboru. To je dostačující, pokud se soubory modelu instance nikdy nepřesounou. Soubory modelu však budou obvykle položky v Visual Studio projektu. Uživatelé budou očekávat, že budou moct přesunout celý projekt do různých částí systému souborů. Budou také očekávat, že projekt budou moct udržovat pod schůdnou zdrojového kódu a otevírat ho na různých počítačích. Názvy cest by proto měly být serializovány vzhledem k umístění projektu, který obsahuje soubory.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializace relativní vzhledem k zadané cestě k souboru

obsahuje , což je slovník, ve kterém lze ukládat informace, jako je cesta k souboru relativní vzhledem `ModelBusReference` `ReferenceContext` k, ke kterému by měl být serializován.

K serializaci relativní k cestě:

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Načtení odkazu z řetězce:

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Objekty ModelBusReference vytvořené jinými adaptéry
 Následující informace jsou užitečné, pokud chcete vytvořit vlastní adaptér.

 (MBR) se skládá ze dvou částí: hlavičky MBR, která je deserializována sběrnici modelu, a adaptéru specifického, který je zpracováván konkrétním `ModelBusReference` správcem adaptéru. To vám umožní zadat vlastní formát serializace adaptéru. Můžete například odkazovat na databázi místo na soubor nebo do odkazu na adaptér uložit další informace. Vlastní adaptér může do souboru umístit další `ReferenceContext` informace.

 Při deserializaci MBR, je nutné zadat ReferenceContext, který je poté uložen v objektu MBR. Při serializaci MBR, uložená ReferenceContext používá adaptér k vygenerování řetězce. Deserializovaný řetězec neobsahuje všechny informace v ReferenceContext. Například v jednoduchém souborových adaptérech obsahuje ReferenceContext cestu ke kořenovému souboru, která není uložena v serializovaném řetězci MBR.

 MBR je deserializován ve dvou fázích:

- `ModelBusReferencePropertySerializer` je standardní serializátor, který se zabývá hlavičkou MBR. Používá standardní sáček `SerializationContext` vlastností DSL, který je uložený v `ReferenceContext` pomocí klíče `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` . Konkrétně by `SerializationContext` měl obsahovat instanci `ModelBus` .

- ModelBus Adapter se zabývá částí MBR specifickou pro adaptér. Může používat další informace uložené v objektu ReferenceContext MBR. Jednoduchý adaptér založený na souboru udržuje kořenové cesty k souborům pomocí klíčů `FilePathLoadContextKey` `FilePathSaveContextKey` a .

     Odkaz na adaptér v souboru modelu je deserializován pouze při použití.

## <a name="to-create-a-model"></a>Vytvoření modelu

### <a name="creating-opening-and-editing-a-model"></a>Vytvoření, otevření a úprava modelu
 Následující fragment je převzatý z ukázky stavového počítače na webu VMSDK. Znázorňuje použití ModelBusReferences k vytvoření a otevření modelu a získání diagramu přidruženého k modelu.

 V této ukázce je název cílového DSL StateMachine. Je z něj odvozeno několik názvů, například název třídy modelu a název modeluBusAdapter.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Ověřování odkazů
 BrokenReferenceDetector testuje všechny vlastnosti domény v obchodě, který může obsahovat ModelBusReferences. Volá akci, kterou poskytnete tam, kde se nějaká akce nachází. To je užitečné zejména pro metody ověřování. Následující metoda ověřování testuje úložiště při pokusu o uložení modelu a v okně chyb hlásí poškozené odkazy:

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>Akce prováděné rozšířením ModelBus

Následující informace nejsou nezbytné, ale můžou být užitečné, pokud modelBus ve velké části využijete.

Rozšíření ModelBus provede v řešení DSL následující změny.

Když kliknete pravým tlačítkem na diagram definice DSL, klikněte na **Povolit modelbus** a pak vyberte Povolit **tento DSL pro použití ModelBus:**

- V projektu DSL se přidá  odkaz naMicrosoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll

- V definici DSL je přidán odkaz na externí typ: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference` .

   Odkaz můžete zobrazit v **Průzkumníku DSL v** části **Typy domén**. Pokud chcete odkazy na externí typ přidat ručně, klikněte pravým tlačítkem na kořenový uzel.

- Přidá se nový soubor šablony **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

Když nastavíte typ vlastnosti domény na ModelBusReference, kliknete pravým tlačítkem na vlastnost a kliknete na Povolit vlastnosti specifické **pro ModelBusReference:**

- Do vlastnosti domény je přidáno několik atributů CLR. Můžete je zobrazit v poli Vlastní atributy v okno Vlastnosti. V **souboru Dsl\GeneratedCode\DomainClasses.cs** můžete zobrazit atributy v deklaraci vlastnosti:

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

Když kliknete pravým tlačítkem na diagram definice DSL, klikněte na Enable ModelBus (Povolit **modelbus)** a vyberte Expose this DSL to the ModelBus (Vystavit **tento DSL pro ModelBus):**

- Do řešení `ModelBusAdapter` se přidá nový projekt.

- Do projektu `ModelBusAdapter` se přidá odkaz na `DslPackage` . `ModelBusAdapter` má odkaz na `Dsl` projekt.

- Do **DslPackage\source.extention.tt** se `|ModelBusAdapter|` přidá jako komponenta MEF.

## <a name="see-also"></a>Viz také

- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Použití prvku Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
