---
title: Integrace modelů pomocí Modelbus | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 77b29fe82b3203228b194d34d82444c4b62415fe
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851508"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Integrace modelů pomocí Visual Studio Modelbus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus poskytuje metodu pro vytvoření propojení mezi modely a z dalších nástrojů do modelů. Je třeba propojit modely jazyka specifického pro doménu (DSL) a modelech UML. Můžete vytvořit integrovaná sada DSL.

 ModelBus umožňuje vytvářet jedinečné odkazu na model nebo na konkrétní elementu v modelu. Tento odkaz mohou být uloženy mimo model, například do prvku v jiném modelu. Až na novější příležitosti, nástroj chce získat přístup k elementu, bude infrastruktury sběrnice modelu načíst příslušný model a vraťte se element. Pokud chcete, můžete zobrazit modelu pro uživatele. Pokud soubor není přístupný v jeho předchozí umístění, ModelBus požádá uživatele o nalezení ho. Pokud uživatel vyhledá soubor, ModelBus opraví všechny odkazy na daný soubor.

> [!NOTE]
> V aktuálním [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] provádění ModelBus propojené modely musí být položky ve stejném [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení.

 Další informace a ukázky kódu najdete v tématu:

- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Sada Modeling SDK pro Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

## <a name="provide"></a> Zajištění přístupu k DSL
 Před vytvořením ModelBus odkazy na model nebo jeho prvky, je nutné definovat objekt ModelBusAdapter pro DSL. Nejjednodušší způsob je použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření modelu Service Bus, které přidá příkazy do návrháře DSL.

### <a name="expose"></a> K vystavení definice DSL sběrnici modelu

1. Stáhněte a nainstalujte rozšíření sběrnice modelu Visual Studio, pokud jste ho už nainstalovali. Další informace najdete v tématu [Visualization and Modeling SDK](https://www.visualstudio.com/).

2. Otevření souboru definice DSL. Klikněte pravým tlačítkem na návrhové ploše a potom klikněte na tlačítko **povolit Modelbus**.

3. V dialogovém okně vyberte **chci zveřejnit tento DSL k ModelBus**. Obě možnosti můžete zvolit, pokud chcete tento DSL zveřejnit své modely a využívat odkazy na další DSL.

4. Klikněte na tlačítko **OK**. Nový projekt "Objekt ModelBusAdapter" je přidán do řešení DSL.

5. Pokud chcete získat přístup DSL z textové šablony, je třeba upravit AdapterManager.tt v novém projektu. Tento krok vynechte, pokud chcete získat přístup DSL od jiného kódu, jako je například příkazy a obslužnými rutinami událostí. Další informace najdete v tématu [pomocí Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Změňte základní třídu AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Na konci souboru vložte tento další atribut před třídy AdapterManager:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. Odkazy na objekt ModelBusAdapter projektu přidejte **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.

      Pokud chcete získat přístup DSL z textových šablon a od jiného kódu, budete potřebovat dva adaptéry, jeden upravený a jeden bez jakýchkoli úprav.

6. Klikněte na tlačítko **Transformovat všechny šablony**.

7. Znovu sestavte řešení.

   Nyní je možné pro ModelBus otevřít instance tento DSL.

   Složka `ModelBusAdapters\bin\*` obsahuje sestavení vytvořených `Dsl` projektu a `ModelBusAdapters` projektu. Pro tento DSL odkazovat z jiného DSL, měli byste importovat tato sestavení.

### <a name="making-sure-that-elements-can-be-referenced"></a>Ujistěte se, že může být odkazováno elementy
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Adaptéry ModelBus pomocí identifikátoru guid elementu pro identifikaci, ve výchozím nastavení. Tyto identifikátory musí proto nastavit jako trvalý v souboru modelu.

##### <a name="to-ensure-that-element-ids-are-persisted"></a>Chcete-li zajistit tento element jsou trvalé identifikátory

1. Otevřete DslDefinition.dsl.

2. V okně Průzkumník DSL, rozbalte **chování serializace Xml**, pak **Data třídy**.

3. Pro každou třídu, na který chcete vytvořit sběrnice modelu odkazuje:

    Klikněte na uzel třídy a v okně Vlastnosti, ujistěte se, že **serializovat Id** je nastavena na `true`.

   Případně pokud chcete použít k identifikaci prvků místo identifikátory GUID názvy elementů, můžete přepsat částmi generované adaptéry. Přepište následující metody ve třídě adaptér:

- Přepsat `GetElementId` vrátit identifikátor, který chcete použít. Tato metoda se volá při vytváření odkazů.

- Přepsat `ResolveElementReference` najít správný element z odkazu sběrnice modelu.

## <a name="editRef"></a> Přístup k DSL z jiného DSL
 Doménová vlastnost, která v DSL můžete ukládat odkazy na model Service bus, a můžete napsat vlastní kód, který je využívá. Můžete také umožníte uživateli vytvářet referenční informace k Service bus modelu výběrem souboru modelu a element v rámci něj.

 K povolení DSL použití odkazů na jiné DSL, měli byste nejprve si ho *příjemce* odkazů modelu Service bus.

#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Chcete-li povolit DSL používat odkazy zveřejněné DSL

1. V definici DSL diagramu, klikněte pravým tlačítkem na hlavní část diagramu a potom klikněte na **povolit Modelbus**.

2. V dialogovém okně vyberte **budu chtít povolit tento model k využívání reference na sběrnici modelu**.

3. V projektu Dsl náročné DSL přidáte následující sestavení v odkazech projektu. Tato sestavení (soubory .dll) najdete v ModelBusAdapter\bin\\* adresáři vystavené DSL.

    - Vystavené DSL sestavení, například **Fabrikam.FamilyTree.Dsl.dll**

    - Vystavených modelu Service bus sestavení adaptéru, například **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. Přidejte následující sestavení .NET do odkazů projektu náročné projektu DSL.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>K uložení odkazu sběrnice modelu ve vlastnosti domény

1. V definici DSL náročné DSL přidejte doménová vlastnost, která do doménové třídy a nastavte její název.

2. Ve vlastnostech okna, s doménovou vlastnost vybrané, nastavte **typ** k `ModelBusReference`.

   V této fázi programového kódu můžete nastavit hodnotu vlastnosti, ale je jen pro čtení v okně Vlastnosti.

   Můžete povolit uživatelům nastavit vlastnost s začínáte se speciálním editorem odkaz ModelBus. Existují dvě verze tohoto editoru nebo *výběr:* jeden umožňuje uživatelům zvolit soubor modelu a druhý umožňuje uživatelům zvolit soubor modelu a element v rámci modelu.

#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Aby uživatel mohl nastavit odkaz modelu Service Bus ve vlastnosti domény

1. Klikněte pravým tlačítkem na doménovou vlastnost a potom klikněte na tlačítko **upravit ModelBusReference specifické vlastnosti**. Otevře se dialogové okno. Toto je *Výběr modelu Service Bus*.

2. Vyberte příslušné **druh ModelBusReference**: model nebo na prvek v modelu.

3. V souboru řetězec filtru dialogové okno, zadejte řetězec `Family Tree files |*.ftree`. Nahraďte příponu vystavené DSL.

4. Pokud jste se rozhodli odkazovat na prvek v modelu, můžete přidat seznam typů, které uživatel může vybrat, například Company.FamilyTree.Person.

5. Klikněte na tlačítko **OK**a potom klikněte na tlačítko **Transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

    > [!WARNING]
    > Pokud jste nevybrali platný model nebo entity, na tlačítko OK se neprojeví, i když může zobrazit povoleno.

6. Pokud zadáte seznam cílové typy, jako je například Company.FamilyTree.Person, pak je nutné přidat odkaz na sestavení do projektu DSL odkazování na knihovnu DLL cíle DSL, například Company.FamilyTree.Dsl.dll

#### <a name="to-test-a-model-bus-reference"></a>Otestovat odkaz modelu Service Bus

1. Vytvoření DSL vystavené a náročné.

2. Spusťte některý z DSL v experimentálním režimu stisknutím klávesy F5 nebo CTRL + F5.

3. V ladění projektu v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], přidejte soubory, které jsou instancemi každý DSL.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus lze vyřešit pouze odkazy na modely, které jsou položky v rámci stejného [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení. Například nelze vytvořit odkaz na soubor modelu v jiné části systému souborů.

4. Vytvořte některé prvky a odkazy v instanci vystavené DSL a uložte ho.

5. Instance náročné DSL otevřete a vyberte prvku modelu, který má vlastnosti odkazu modelu Service bus.

6. V okně Vlastnosti klikněte dvakrát na vlastnost referenčního modelu Service bus. Otevře se dialogové okno pro výběr.

7. Klikněte na tlačítko **Procházet** a vyberte instanci vystavené DSL.

     Při výběru se vám také umožní zvolit položku v modelu, pokud zadaný typ elementu konkrétní referenční informace k modelu Service bus.

## <a name="creating-references-in-program-code"></a>Vytváření odkazů v kódu programu
 Když chcete k uložení odkazu na model nebo jeho element v modelu, můžete vytvořit `ModelBusReference`. Existují dva typy z `ModelBusReference`: odkazy a odkazy na prvek modelu.

 Chcete-li vytvořit odkaz na model, je třeba AdapterManager DSL, z nichž je model instance a název souboru nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] položky projektu model.

 Chcete-li vytvořit odkaz na element, musíte pro soubor modelu a element, který chcete odkazovat na adaptér.

> [!NOTE]
> S [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus, můžete vytvořit odkazy pouze na položky v rámci stejného [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení.

### <a name="import-the-exposed-dsl-assemblies"></a>Importovat vystavené sestavení DSL
 Používání projektu přidejte odkazy na sestavení DSL a objekt ModelBusAdapter vystavené DSL.

 Předpokládejme například, že chcete uložit ModelBus odkazy v elementech MusicLibrary DSL. Odkazy na ModelBus bude odkazovat na prvky FamilyTree DSL. V `Dsl` projektu MusicLibrary řešení, v uzlu odkazy, přidejte odkazy na následující sestavení:

- Fabrikam.FamilyTree.Dsl.dll - vystavené DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll - ModelBus adaptéru vystavené DSL.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Tyto sestavení lze nalézt v `ModelBusAdapters` projektu vystavené DSL v části `bin\*`.

  V souboru kódu, kde se vytvoří odkazy budete obvykle muset importovat tyto obory názvů:

```
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Chcete-li vytvořit odkaz na modelu
 Chcete-li vytvořit odkaz na model, přístup k AdapterManager pro vystavené DSL a použijte ji k vytvoření odkazu na model. Můžete zadat buď cestu k souboru, nebo `EnvDTE.ProjectItem`.

 Z AdapterManager můžete získat adaptér, který poskytuje přístup k jednotlivým prvkům v modelu.

> [!NOTE]
> Adaptér musí dispose po dokončení s ním. Je nejpohodlnější způsob, jak toho dosáhnout pomocí `using` příkazu. Toto dokládá následující příklad.

```
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

 Pokud chcete použít `modelReference` později, můžete ho uložit v doménová vlastnost, která má typ externího `ModelBusReference`:

```
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

 Chcete-li povolit uživatelům upravit toto doménová vlastnost, použijte `ModelReferenceEditor` jako parametr v atributu editoru. Další informace najdete v tématu [povolit uživatelům upravit odkaz](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Chcete-li vytvořit odkaz na prvek
 Adaptér, který jste vytvořili pro model lze použít k vytvoření a vyřešit odkazy.

```
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

 Pokud chcete použít `elementReference` později, můžete ho uložit v doménová vlastnost, která má typ externího `ModelBusReference`. Chcete-li povolit uživatelům upravit, použijte `ModelElementReferenceEditor` jako parametr v atributu editoru. Další informace najdete v tématu [povolit uživatelům upravit odkaz](#editRef).

### <a name="resolving-references"></a>Překládají se odkazy
 Pokud máte `ModelBusReference` (MBR) můžete získat model nebo na prvek modelu, na který odkazuje. Pokud element se zobrazí v diagramu nebo v jiném zobrazení, můžete otevřít zobrazení a vyberte požadovaný prvek.

 Adaptér můžete vytvořit z MBR. Z adaptéru můžete získat kořenu modelu. Můžete také vyřešit MBRs, které odkazují na konkrétní prvky v rámci modelu.

```
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

##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Chcete-li vyřešit odkazy ModelBus v textové šabloně

1. DSL, který chcete získat přístup, musí být adaptér ModelBus, která je nakonfigurovaná pro přístup k textu šablony. Další informace najdete v tématu [poskytuje přístup k DSL](#provide).

2. Obvykle které budou přistupovat k cíl DSL pomocí Service Bus odkaz modelu (MBR) uložené ve zdroji DSL. Šablony proto obsahuje směrnici zdroj DSL a navíc kód vyřešit hlavní spouštěcí záznam. Další informace o textových šablonách naleznete v tématu [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md).

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

   Názorný postup a další informace najdete v tématu [pomocí Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Serializace ModelBusReference
 Pokud chcete uložit `ModelBusReference` (MBR) ve formě řetězce, můžete ho serializovat:

```
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

 Hlavní spouštěcí záznam, který serializuje tímto způsobem je nezávislé na kontextu. Pokud použijete jednoduchý adaptér souborové sběrnice modelu, hlavní spouštěcí záznam obsahuje absolutní cestu k souboru. Toto je dostatečná, pokud se nikdy nepřesouvají soubory instance modelu. Ale budou se soubory modelu obvykle položky v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Uživatelé se očekávají, že se moct přesunout celého projektu do různých částí systému souborů. Očekávají se také budete moci pokračovat v projektu pod správou zdrojových kódů a otevřete ho v různých počítačích. Názvy cest by měly být serializovány proto relativní k umístění projektu, který obsahuje soubory.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializace relativní k cestě zadaného souboru
 A `ModelBusReference` obsahuje `ReferenceContext`, což je slovník, ve kterém můžete ukládat informace, jako je cesta k souboru relativně k by měly být serializovány.

 K serializaci relativní k cestě:

```
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

 K načtení odkazu z řetězce:

```
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Vytvoří další adaptéry ModelBusReferences
 Následující informace jsou užitečné, pokud chcete vytvořit vlastní adaptér.

 A `ModelBusReference` (MBR) se skládá ze dvou částí: MBR hlavičky, která je deserializovat ve sběrnici modelu a specifické pro adaptér, který zpracovává konkrétní adaptér správce. To umožňuje zadat vlastní formát serializace adaptéru. Například může odkazovat databázi spíš než soubor, nebo může ukládání dalších informací v odkazu na adaptéru. Vlastní adaptér můžete umístit další informace v `ReferenceContext`.

 Při deserializaci MBR, je nutné zadat ReferenceContext, které jsou pak uloženy v objektu MBR. Při serializaci MBR uložené ReferenceContext používá adaptér ke generování řetězce. Deserializovaná řetězec neobsahuje všechny informace ReferenceContext. Například v jednoduchý adaptér souborové ReferenceContext obsahuje kořenovou cestu souboru, který není uložený v řetězci serializovaná MBR.

 Hlavní spouštěcí záznam deserializován ve dvou fázích:

- `ModelBusReferencePropertySerializer` je standardní serializátoru, který se zabývá hlavičku MBR. Používá standardní DSL `SerializationContext` vlastnosti kontejneru objektů a dat, která je uložena v `ReferenceContext` pomocí klíče `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. Konkrétně se `SerializationContext` by měl obsahovat instanci `ModelBus`.

- Adaptér ModelBus se zabývá adaptér konkrétní součást hlavního spouštěcího záznamu. Další informace uložené v ReferenceContext hlavního spouštěcího záznamu může použít. Jednoduchý adaptér souborové udržuje kořenové cesty k souborům pomocí klíčů `FilePathLoadContextKey` a `FilePathSaveContextKey`.

     Odkaz na adaptér v souboru modelu je deserializovat pouze v případě, že se používá.

## <a name="to-create-a-model"></a>Vytvoření modelu

### <a name="creating-opening-and-editing-a-model"></a>Vytvoření, otevření a úprava modelu
 Následující fragment je převzat z ukázky stavového stroje na webu vmsdk následující položky. Ukazuje použití ModelBusReferences k vytvoření a otevření modelu a získat diagram spojené s modelem.

 V této ukázce se název cílového DSL stavový stroj StateMachine. Několik názvů jsou odvozeny z něj, jako je název třídy modelu a názvem objekt ModelBusAdapter.

```
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

## <a name="validating-references"></a>Ověřuje se odkazy
 BrokenReferenceDetector testů všechny vlastnosti v Store, který může obsahovat ModelBusReferences. Volání akce, který poskytuje, ve kterých se nachází žádnou akci. To je užitečné hlavně pro metody ověřování. Následující metody ověření testy úložiště při pokusu o uložení modelu a hlásí poškozenými odkazy v okně chyb:

```
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

## <a name="actions-performed-by-the-modelbus-extension"></a>Akce prováděné rozšíření ModelBus
 Tyto informace není nezbytné, ale může být užitečné, pokud provedete rozsáhlé používání šířky ModelBus.

 Rozšíření ModelBus provede tyto změny ve vašem řešení DSL.

 Když kliknete pravým tlačítkem na diagramem definice DSL, klikněte na tlačítko **povolit Modelbus**a pak vyberte **povolit tento DSL využívat ModelBus**:

- V projektu DSL se přidá odkaz na **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- V definici DSL, se přidá odkaz na externí: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Zobrazí se odkaz v **Průzkumník DSL**v části **typy domén**. Chcete-li ručně přidat odkazy na externí, klikněte pravým tlačítkem na kořenový uzel.

- Přidá nový soubor šablony, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

  Když nastavíte typu doménová vlastnost, která ModelBusReference a pak klikněte pravým tlačítkem na vlastnost a klikněte na **specifické vlastnosti povolit ModelBusReference**:

- Několik atributů CLR se přidají do doménové vlastnosti. Můžete vidět v pole vlastních atributů v okně Vlastnosti. V **Dsl\GeneratedCode\DomainClasses.cs**, můžete zobrazit atributy v deklaraci vlastnosti:

  ```
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

  Když kliknete pravým tlačítkem myši diagramem definice DSL, klikněte na tlačítko **povolit ModelBus**a vyberte **zveřejnit tento DSL k ModelBus**:

- Nový projekt `ModelBusAdapter` je přidán do řešení.

- Odkaz na `ModelBusAdapter` se přidá do `DslPackage` projektu. `ModelBusAdapter` obsahuje odkaz na `Dsl` projektu.

- V **DslPackage\source.extention.tt**, `|ModelBusAdapter|` se přidá jako komponentu MEF.

## <a name="see-also"></a>Viz také
 [Postupy: otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md) [modely UML integrovat s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md) [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md) [pomocí Visual Studio ModelBus v Textové šablony](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
