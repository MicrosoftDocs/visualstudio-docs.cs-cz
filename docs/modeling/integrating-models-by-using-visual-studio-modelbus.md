---
title: Integrace modelů pomocí ModelBus
description: Přečtěte si, že Visual Studio ModelBus poskytuje metodu pro vytváření propojení mezi modely a z jiných nástrojů do modelů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46705c7a614cd67d81c9e55c03e937f72c29a2fe
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360723"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Integrace modelů pomocí Visual Studio Modelbus

Visual Studio ModelBus poskytuje metodu pro vytváření propojení mezi modely a z jiných nástrojů do modelů. Můžete například propojit modely DSL (Domain-Specific Language) a modely UML. Můžete vytvořit integrovanou sadu DSL.

ModelBus umožňuje vytvořit jedinečný odkaz na model nebo na konkrétní prvek v rámci modelu. Tento odkaz může být uložen mimo model, například v prvku v jiném modelu. Když později nástroj chce získat přístup k prvku, infrastruktura sběrnice modelu načte příslušný model a vrátí element. Pokud chcete, můžete zobrazit model pro uživatele. Pokud se k souboru nemůžete dostat v předchozím umístění, ModelBus se požádá uživatele, aby ho našel. Pokud uživatel soubor najde, ModelBus vyřeší všechny odkazy na daný soubor.

> [!NOTE]
> V aktuální implementaci ModelBus sady Visual Studio musí být propojené modely položkami ve stejném řešení sady Visual Studio.

Další informace a ukázku kódu naleznete v tématu:

- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Sada Modeling SDK pro Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> Poskytnutí přístupu k DSL
 Než budete moci vytvořit ModelBus odkazy na model nebo jeho prvky, je nutné definovat ModelBusAdapter pro DSL. Nejjednodušší způsob, jak to provést, je použít rozšíření sběrnice sady Visual Studio, které přidá příkazy do návrháře DSL.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Vystavení definice DSL pro sběrnici modelu

1. Otevřete soubor definice DSL. Klikněte pravým tlačítkem myši na návrhovou plochu a pak klikněte na **povolit ModelBus**.

2. V dialogovém okně vyberte možnost **chci zveřejnit tuto DSL pro ModelBus**. Obě možnosti si můžete zvolit, pokud chcete, aby tato DSL mohla vystavovat své modely a využívat odkazy na jiné DSL.

3. Klikněte na **OK**. Do řešení DSL se přidá nový projekt "ModelBusAdapter".

4. Pokud chcete k DSL přistupovat z textové šablony, musíte upravit AdapterManager.tt v novém projektu. Tento krok vynechejte, pokud chcete k DSL přistupovat z jiného kódu, jako jsou příkazy a obslužné rutiny událostí. Další informace najdete v tématu [použití Visual Studio Modelbus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Změňte základní třídu AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Poblíž konce souboru vložte tento dodatečný atribut před třídy správce:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. V odkazech na projekt ModelBusAdapter přidejte **Microsoft. VisualStudio. TextTemplating. modelings. 11.0**.

      Pokud chcete k DSL přistupovat z textových šablon i z jiného kódu, budete potřebovat dva adaptéry, jednu upravenou a jednu nezměněnou.

5. Klikněte na **transformovat všechny šablony**.

6. Znovu sestavte řešení.

   ModelBus je teď možné otevřít na instancích této DSL.

   Složka `ModelBusAdapters\bin\*` obsahuje sestavení sestavená `Dsl` projektem a `ModelBusAdapters` projektem. Chcete-li odkazovat na tento DSL z jiné DSL, měli byste tato sestavení importovat.

### <a name="ensure-that-elements-can-be-referenced"></a>Ujistěte se, že se na elementy můžou odkazovat.

Visual Studio ModelBus adaptéry používají identifikátor GUID elementu k jeho identifikaci ve výchozím nastavení. Tyto identifikátory musí být proto trvalé v souboru modelu.

Aby bylo zajištěno, že identifikátory prvků jsou trvalé:

1. Otevřete DslDefinition. DSL.

2. V Průzkumníku DSL rozbalte **chování serializace XML** a potom **data třídy**.

3. Pro každou třídu, na kterou chcete vytvořit odkazy na sběrnici modelů:

    Klikněte na uzel třída a v okno Vlastnosti Ujistěte se, že je **ID serializace** nastaveno na `true` .

   Případně, pokud chcete použít názvy elementů k identifikaci prvků místo identifikátorů GUID, můžete přepsat části vygenerovaných adaptérů. Ve třídě adaptéru přepište následující metody:

- Přepsáním `GetElementId` vrátíte identifikátor, který chcete použít. Tato metoda je volána při vytváření odkazů.

- Přepište `ResolveElementReference` pro vyhledání správného prvku z odkazu sběrnice modelu.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Přístup k DSL z jiné DSL

Odkazy na sběrnici modelu můžete uložit v doménové vlastnosti v DSL a můžete napsat vlastní kód, který je používá. Můžete také dát uživateli možnost vytvořit odkaz na sběrnici vyvoláním souboru modelu a elementu v něm.

Pokud chcete DSL povolit použití odkazů na jinou DSL, měli byste nejdřív vytvořit *uživatele* s odkazy na sběrnici modelu.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Povolení použití odkazů na vystavenou DSL pomocí DSL

1. V diagramu definice DSL klikněte pravým tlačítkem myši na hlavní část diagramu a pak klikněte na **povolit ModelBus**.

2. V dialogovém okně vyberte možnost **Chci povolit tento model pro využívání odkazů na sběrnici modelu**.

3. V projektu DSL náročné na DSL přidejte následující sestavení do odkazů projektu. Tato sestavení (soubory. dll) se nacházejí v \\ adresáři ModelBusAdapter\bin * vystavené DSL.

    - Vystavené sestavení DSL, například **Fabrikam.FamilyTree.Dsl.dll**

    - Vystavené sestavení adaptéru sběrnice modelu, například **Fabrikam.FamilyTree.ModelBusAdapter.dll**

4. Přidejte následující sestavení .NET do odkazů projektu náročného projektu DSL.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Uložení odkazu na sběrnici modelu ve vlastnosti domény

1. V definici DSL pro spotřebovávání DSL přidejte vlastnost domény do doménové třídy a nastavte její název.

2. V okno Vlastnosti s vybranou doménovou vlastností nastavte **typ** na `ModelBusReference` .

   V této fázi kód programu může nastavit hodnotu vlastnosti, ale v okno Vlastnosti je jen pro čtení.

   Uživatelům můžete dovolit nastavit vlastnost pomocí specializovaného referenčního editoru ModelBus. Existují dvě verze tohoto editoru nebo *výběru:* jeden umožňuje uživatelům zvolit soubor modelu a druhý umožňuje uživatelům zvolit soubor modelu a prvek v modelu.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Umožnění uživateli nastavit odkaz sběrnice modelu ve vlastnosti domény

1. Klikněte pravým tlačítkem na doménovou vlastnost a pak klikněte na **Upravit ModelBusReference specifické vlastnosti**. Otevře se dialogové okno. Toto je *Výběr modelové sběrnice*.

2. Vyberte vhodný **druh ModelBusReference**: k modelu nebo prvku uvnitř modelu.

3. V řetězci filtru dialogu souboru zadejte řetězec, například `Family Tree files |*.ftree` . Nahraďte příponu souboru vystavené DSL.

4. Pokud jste se rozhodli odkazovat na prvek v modelu, můžete přidat seznam typů, které může uživatel vybrat, například Company. FamilyTree. Person.

5. Klikněte na **OK** a pak na **transformovat všechny šablony** na panelu nástrojů **Průzkumník řešení** .

    > [!WARNING]
    > Pokud jste nevybrali platný model nebo entitu, tlačítko OK nebude mít žádný účinek, i když se může zdát být povoleno.

6. Pokud jste zadali seznam cílových typů, jako je například Company. FamilyTree. person, pak je nutné přidat odkaz na sestavení k vašemu projektu DSL, který odkazuje na knihovnu DLL cílové DSL, například Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Testování odkazu sběrnice modelu

1. Sestavte vystavené a spotřebovávatelné DSL.

2. Stisknutím klávesy F5 nebo stisknutím kombinace kláves CTRL + F5 spusťte jednu z DSL v experimentálním režimu.

3. V projektu ladění v experimentální instanci aplikace Visual Studio přidejte soubory, které jsou instancemi každé DSL.

    > [!NOTE]
    > Visual Studio ModelBus může překládat pouze odkazy na modely, které jsou položky ve stejném řešení sady Visual Studio. Například nelze vytvořit odkaz na soubor modelu v jiné části systému souborů.

4. Vytvořte některé elementy a odkazy v instanci vystavené DSL a uložte je.

5. Otevřete instanci spotřebovávající DSL a vyberte prvek modelu, který má odkazovou vlastnost sběrnice modelu.

6. V okno Vlastnosti dvakrát klikněte na vlastnost reference sběrnice modelu. Otevře se dialogové okno pro výběr.

7. Klikněte na **Procházet** a vyberte instanci vystavené DSL.

     Výběr vám také umožní vybrat položku v modelu, pokud jste zadali typ specifický pro daný element odkaz sběrnice model.

## <a name="creating-references-in-program-code"></a>Vytváření odkazů v programovém kódu

Pokud chcete uložit odkaz na model nebo prvek v modelu, vytvoříte `ModelBusReference` . Existují dva typy `ModelBusReference` : odkazy na model a odkazy na prvky.

Chcete-li vytvořit odkaz na model, potřebujete správce DSL, pro který je model instancí, a název souboru nebo položku projektu sady Visual Studio modelu.

Chcete-li vytvořit odkaz na element, budete potřebovat adaptér pro soubor modelu a element, na který chcete odkazovat.

> [!NOTE]
> Pomocí Visual Studio ModelBus můžete vytvořit odkazy pouze na položky ve stejném řešení sady Visual Studio.

### <a name="import-the-exposed-dsl-assemblies"></a>Import vystavených sestavení DSL

V projektu spotřeby přidejte odkazy na projekt do sestavení DSL a ModelBusAdapter vystavené DSL.

Předpokládejme například, že chcete ukládat ModelBus odkazy v prvcích MusicLibrary DSL. Odkazy na ModelBus budou odkazovat na prvky FamilyTree DSL. V `Dsl` projektu řešení MusicLibrary přidejte v uzlu odkazy odkazy na následující sestavení:

- Fabrikam.FamilyTree.Dsl.dll – vystavená DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll – adaptér ModelBus vystavené DSL.

- Microsoft. VisualStudio. Modeling. SDK. Integration. 11.0

- Microsoft. VisualStudio. Modeling. SDK. Integration. Shell. 11.0

  Tato sestavení se dají najít v `ModelBusAdapters` projektu vystavené DSL, v části `bin\*` .

  V souboru kódu, kde budete vytvářet odkazy, obvykle budete muset importovat tyto obory názvů:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Vytvoření odkazu na model

Chcete-li vytvořit odkaz na model, získáte přístup k správce pro vystavenou DSL a použijete ji k vytvoření odkazu na model. Můžete zadat buď cestu k souboru, nebo `EnvDTE.ProjectItem` .

Z správce můžete získat adaptér, který poskytuje přístup k jednotlivým prvkům v modelu.

> [!NOTE]
> Až s tím budete hotovi, musíte adaptér uvolnit. Nejpohodlnější způsob, jak toho dosáhnout, je pomocí `using` příkazu. Toto dokládá následující příklad.

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

Pokud chcete mít možnost `modelReference` pozdější použití, můžete ji uložit do doménové vlastnosti, která má externí typ `ModelBusReference` :

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Chcete-li uživatelům dovolit tuto vlastnost domény upravit, použijte `ModelReferenceEditor` jako parametr v atributu Editor. Další informace najdete v tématu [Povolení úprav odkazu uživatelem](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Vytvoření odkazu na element

Adaptér, který jste vytvořili pro model, lze použít k vytvoření a vyřešení odkazů.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Pokud chcete mít možnost `elementReference` pozdější použití, můžete ji uložit do doménové vlastnosti, která má externí typ `ModelBusReference` . Chcete-li uživatelům dovolit, aby je mohli upravovat, použijte `ModelElementReferenceEditor` jako parametr v atributu Editor. Další informace najdete v tématu [Povolení úprav odkazu uživatelem](#editRef).

### <a name="resolving-references"></a>Řešení odkazů

Pokud máte `ModelBusReference` (MBR), můžete získat model nebo prvek modelu, na který odkazuje. Pokud je prvek zobrazen v diagramu nebo jiném zobrazení, můžete otevřít zobrazení a vybrat prvek.

Adaptér můžete vytvořit z hlavního spouštěcího záznamu (MBR). Z adaptéru můžete získat kořen modelu. Můžete také vyřešit MBRs, které odkazují na konkrétní prvky v modelu.

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

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Řešení odkazů na ModelBus v textové šabloně

1. DSL, ke kterým chcete získat přístup, musí mít adaptér ModelBus, který byl nakonfigurován pro přístup pomocí textových šablon. Další informace najdete v tématu [poskytnutí přístupu k DSL](#provide).

2. Obvykle budete přistupovat k cílové DSL pomocí referenčního modelu sběrnice (MBR), který je uložený ve zdrojové DSL. Vaše šablona proto obsahuje direktivu zdrojového DSL a také kód pro rozpoznání hlavního spouštěcího záznamu (MBR). Další informace o textových šablonách naleznete v tématu [generování kódu z Domain-Specificho jazyka](../modeling/generating-code-from-a-domain-specific-language.md).

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

   Další informace a návod najdete v tématu [použití Visual Studio Modelbus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md) .

## <a name="serializing-a-modelbusreference"></a>Serializace ModelBusReference

Pokud chcete uložit `ModelBusReference` (MBR) ve formě řetězce, můžete ho serializovat:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Hlavní spouštěcí záznam (MBR), který je tímto způsobem serializován, je nezávislý na kontextu. Pokud používáte jednoduchý adaptér souborové sběrnice, hlavní spouštěcí záznam obsahuje absolutní cestu k souboru. To je dostačující, pokud soubory modelu instance nikdy nebudou přesunuty. Soubory modelu jsou však obvykle položky v projektu aplikace Visual Studio. Vaši uživatelé budou mít možnost přesunout celý projekt do různých částí systému souborů. Očekává se také, že budou mít projekt pod správou zdrojových kódů a otevře se v různých počítačích. Názvy cest by proto měly být serializovány relativně k umístění projektu, který obsahuje soubory.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializace vzhledem k zadané cestě k souboru

`ModelBusReference`Obsahuje `ReferenceContext` , což je slovník, ve kterém můžete ukládat informace, například relativní cestu k souboru, do které by měl být serializován.

Pro serializaci relativně k cestě:

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

### <a name="modelbusreferences-created-by-other-adapters"></a>ModelBusReferences vytvořené jinými adaptéry
 Následující informace jsou užitečné, pokud chcete vytvořit vlastní adaptér.

 A `ModelBusReference` (MBR) se skládá ze dvou částí: hlavičky hlavního spouštěcího záznamu (MBR), která je deserializovaná sběrnicí modelu, a specifická pro adaptér, který je určený konkrétním správcem adaptéru. To umožňuje zadat vlastní formát serializace adaptéru. Například můžete odkazovat na databázi místo souboru nebo můžete uložit další informace v odkazu na adaptér. Vlastní adaptér může umístit další informace do `ReferenceContext` .

 Při deserializaci hlavního spouštěcího záznamu (MBR) je nutné zadat ReferenceContext, který je pak uložen v objektu MBR. Při serializaci hlavního spouštěcího záznamu (MBR) používá adaptér uložené ReferenceContext k vytvoření řetězce. Deserializovaný řetězec neobsahuje všechny informace v ReferenceContext. Například v jednoduchém adaptéru založeném na souboru obsahuje ReferenceContext cestu ke kořenovému souboru, který není uložen v serializovaném řetězci MBR.

 Hlavní spouštěcí záznam (MBR) je deserializovaný ve dvou fázích:

- `ModelBusReferencePropertySerializer` je standardní serializátor, který se zabývá hlavičkou MBR. Používá standardní `SerializationContext` kontejner vlastností DSL, který je uložený v `ReferenceContext` kódu pomocí klíče `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` . Konkrétně `SerializationContext` by měl obsahovat instanci `ModelBus` .

- Váš adaptér ModelBus se zabývá součástí hlavního spouštěcího záznamu (MBR), které jsou specifické pro adaptér. Může použít další informace uložené v ReferenceContext hlavního spouštěcího panelu. Jednoduchý adaptér založený na souboru udržuje cesty kořenových souborů pomocí klíčů `FilePathLoadContextKey` a `FilePathSaveContextKey` .

     Odkaz na adaptér v souboru modelu je deserializován pouze v případě, že je použit.

## <a name="to-create-a-model"></a>Vytvoření modelu

### <a name="creating-opening-and-editing-a-model"></a>Vytváření, otevírání a úpravy modelu
 Následující fragment je pořízen z ukázky stavového stroje na webu VMSDK. Ukazuje použití ModelBusReferences k vytvoření a otevření modelu a k získání diagramu přidruženého k modelu.

 V této ukázce název cílové DSL je StateMachine. Z něj je odvozeno několik názvů, jako je například název třídy modelu a název ModelBusAdapter.

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
 BrokenReferenceDetector testuje všechny vlastnosti domény v úložišti, které mohou obsahovat ModelBusReferences. Volá akci, kterou zadáte, kde se najde nějaká akce. To je zvlášť užitečné pro metody ověřování. Následující metoda ověřování testuje úložiště při pokusu o uložení modelu a hlásí poškozené odkazy v okně chyby:

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

Následující informace nejsou nezbytné, ale mohou být užitečné, pokud provedete rozsáhlé používání ModelBus.

Rozšíření ModelBus provede v řešení DSL tyto změny.

Když kliknete pravým tlačítkem myši na diagram definice DSL, klikněte na **povolit ModelBus** a pak vyberte **Povolit tuto DSL pro využívání ModelBus**:

- V projektu DSL se přidá odkaz na **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- V definici DSL je přidán odkaz na externí typ: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference` .

   Odkaz můžete zobrazit v **Průzkumníku DSL** v části **typy domén**. Chcete-li přidat odkazy na externí typ ručně, klikněte pravým tlačítkem na kořenový uzel.

- Přidá se nový soubor šablony, **Dsl\GeneratedCode\ModelBusReferencesSerialization.TT**.

Když nastavíte typ doménové vlastnosti na ModelBusReference, kliknete pravým tlačítkem na vlastnost a kliknete na **Povolit ModelBusReference specifické vlastnosti**:

- Do doménové vlastnosti se přidalo několik atributů CLR. Můžete je zobrazit v poli vlastní atributy v okno Vlastnosti. V **Dsl\GeneratedCode\DomainClasses.cs** uvidíte atributy v deklaraci vlastnosti:

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

Po kliknutí pravým tlačítkem na diagram definice DSL klikněte na **povolit ModelBus** a vyberte možnost **zveřejnit tuto DSL pro ModelBus**:

- `ModelBusAdapter`Do řešení se přidá nový projekt.

- Odkaz na `ModelBusAdapter` je přidán do `DslPackage` projektu. `ModelBusAdapter` má odkaz na `Dsl` projekt.

- V **DslPackage\source.extention.TT** `|ModelBusAdapter|` je přidána jako Komponenta MEF.

## <a name="see-also"></a>Viz také:

- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Použití prvku Visual Studio ModelBus v textové šabloně](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
