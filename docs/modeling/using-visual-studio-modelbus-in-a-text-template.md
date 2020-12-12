---
title: Použití ModelBus v textové šabloně
description: Naučte se řešit odkazy na cílové modely přístupu, pokud píšete šablony textu, které čtou model, který obsahuje Visual Studio ModelBus odkazy.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1025e7d35c20dc18c87942e23cf71b598d85637a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361362"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Použití prvku Visual Studio ModelBus v textové šabloně

Pokud píšete šablony textu, které čtou model, který obsahuje Visual Studio ModelBus odkazy, můžete chtít vyřešit odkazy na přístup k cílovým modelům. V takovém případě je nutné upravit textové šablony a odkazované jazyky specifické pro doménu (DSL):

- Linka DSL, která je cílem odkazů, musí mít adaptér ModelBus, který je nakonfigurován pro přístup z textových šablon. Pokud k DSL přistupujete taky z jiného kódu, vyžaduje se kromě standardního adaptéru ModelBus i překonfigurovaný adaptér.

     Správce adaptéru musí dědit z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) a musí mít atribut `[HostSpecific(HostName)]` .

- Šablona musí dědit z [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Pokud chcete číst modely DSL, které neobsahují odkazy ModelBus, můžete použít procesory direktiv, které jsou generovány v projektech DSL. Další informace naleznete v tématu [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md).

Další informace o textových šablonách naleznete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Vytvoření adaptéru modelové sběrnice pro přístup z textových šablon

Chcete-li přeložit odkaz na ModelBus v textové šabloně, musí mít cílový DSL kompatibilní adaptér. Textové šablony jsou spouštěny v samostatné doméně AppDomain z editorů dokumentů sady Visual Studio, a proto adaptér musí načíst model namísto přístupu přes DTE.

1. Pokud cílové řešení DSL nemá projekt **ModelBusAdapter** , vytvořte ho pomocí Průvodce rozšířením ModelBus:

    1. Pokud jste to ještě neudělali, Stáhněte a nainstalujte Visual Studio ModelBus rozšíření. Další informace najdete v tématu [sada SDK pro vizualizaci a modelování](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Otevřete soubor definice DSL. Klikněte pravým tlačítkem myši na návrhovou plochu a pak klikněte na **povolit ModelBus**.

    3. V dialogovém okně vyberte možnost **chci zveřejnit tuto DSL pro ModelBus**. Obě možnosti můžete vybrat, pokud chcete, aby tato DSL mohla vystavovat své modely a využívat odkazy na jiné DSL.

    4. Klikněte na **OK**. Do řešení DSL se přidá nový projekt "ModelBusAdapter".

    5. Klikněte na **transformovat všechny šablony**.

    6. Znovu sestavte řešení.

2. Pokud chcete použít DSL z textové šablony a z jiného kódu, jako je například příkaz, duplikujte projekt **ModelBusAdapter** :

    1. V Průzkumníku Windows zkopírujte a vložte složku, která obsahuje **ModelBusAdapter. csproj**.

    2. Přejmenujte soubor projektu (například na **T4ModelBusAdapter. csproj**).

    3. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel řešení, přejděte na **Přidat** a pak klikněte na **existující projekt**. Vyhledejte nový projekt adaptéru **T4ModelBusAdapter. csproj**.

    4. V každém `*.tt` souboru nového projektu změňte obor názvů.

    5. Klikněte pravým tlačítkem na nový projekt v **Průzkumník řešení** a pak klikněte na **vlastnosti**. V editoru vlastností změňte názvy vygenerovaného sestavení a výchozí obor názvů.

    6. V projektu DslPackage přidejte odkaz na projekt nového adaptéru, aby měl odkazy na oba adaptéry.

    7. Do DslPackage\source.extension.tt přidejte řádek, který odkazuje na váš projekt nového adaptéru.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformujte všechny šablony** a znovu sestavte řešení. By neměly nastat žádné chyby sestavení.

3. V projektu nového adaptéru přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. TextTemplating. 11.0
    - Microsoft. VisualStudio. TextTemplating. Modelings. 11.0

4. V AdapterManager.tt:

    - Změňte deklaraci AdapterManagerBase tak, aby dědila z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Poblíž konce souboru, nahraďte atribut HostSpecific před třídou správce. Odeberte následující řádek:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Vložte následující řádek:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Tento atribut filtruje sadu adaptérů, které jsou k dispozici, když ModelBus příjemce vyhledá adaptér.

5. **Transformujte všechny šablony** a znovu sestavte řešení. By neměly nastat žádné chyby sestavení.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Napsat textovou šablonu, která může vyřešit odkazy ModelBus

Obvykle začínáte šablonou, která čte a generuje soubory ze zdroje DSL "zdroj". Tato šablona používá direktivu, která je generována ve zdrojovém projektu DSL pro čtení souborů zdrojového modelu způsobem, který je popsán v tématu [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md). Zdroj DSL ale obsahuje odkazy ModelBus na "cílovou" DSL. Proto je vhodné povolit kód šablony pro překlad odkazů a přístup k cílové DSL. Proto je nutné šablonu přizpůsobit pomocí následujících kroků:

- Změňte základní třídu šablony na [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Zahrňte `hostspecific="true"` do direktivy Template.

- Přidejte odkazy na sestavení do cílové DSL a jeho adaptéru a povolte ModelBus.

- Nepotřebujete direktivu, která se generuje jako součást cílové DSL.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Při spuštění této textové šablony `SourceDsl` direktiva načte soubor `Sample.source` . Šablona má přístup k prvkům modelu, počínaje od `this.ModelRoot` . Kód může používat doménové třídy a vlastnosti této DSL.

 Kromě toho může šablona vyřešit odkazy ModelBus. Kde odkazy odkazují na cílový model, direktivy sestavení umožňují, aby kód používal doménové třídy a vlastnosti DSL tohoto modelu.

- Pokud nepoužijete direktivu, která je generována projektem DSL, měli byste také zahrnout následující.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Použijte `this.ModelBus` k získání přístupu k ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Návod: testování textové šablony, která používá ModelBus
 V tomto návodu provedete tyto kroky:

1. Vytvořte dvě DSL. Jedna DSL, *příjemce*, má `ModelBusReference` vlastnost, která může odkazovat na jinou DSL, *poskytovatele*.

2. Vytvořte dva adaptéry ModelBus ve zprostředkovateli: jeden pro přístup pomocí textových šablon, druhý pro běžný kód.

3. Vytvořte modely instancí DSL v jednom experimentálním projektu.

4. Nastavte doménovou vlastnost v jednom modelu tak, aby odkazovala na jiný model.

5. Napište obslužnou rutinu poklikání, která otevře model, na který se odkazuje.

6. Napište textovou šablonu, která může načíst první model, použijte odkaz na jiný model a přečtěte si druhý model.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Vytvoření DSL, která je přístupná pro ModelBus

1. Vytvořte nové řešení DSL. V tomto příkladu vyberte šablonu řešení Flow úlohy. Nastavte název jazyka na `MBProvider` a přípona názvu souboru na ". Poskytněte".

2. V diagramu definice DSL klikněte pravým tlačítkem myši na prázdnou část diagramu, která není blízko horní části, a pak klikněte na **povolit ModelBus**.

   Pokud nevidíte **možnost povolit ModelBus**, Stáhněte a nainstalujte rozšíření ModelBus VMSDK.

3. V dialogovém okně **povolit ModelBus** vyberte možnost **zpřístupnit tuto DSL pro ModelBus** a pak klikněte na **OK**.

    `ModelBusAdapter`Do řešení se přidá nový projekt.

Nyní máte k dispozici DSL, ke které mají prostřednictvím šablony textu prostřednictvím ModelBus k dispozici. Odkazy na ni lze vyřešit v kódu příkazů, obslužných rutin událostí nebo pravidel, která jsou provozována v doméně AppDomain editoru souborů modelu. Textové šablony se ale spouštějí v samostatné doméně AppDomain a při úpravách nemůžou přistupovat k modelu. Pokud chcete získat přístup k ModelBus odkazům na tuto DSL z textové šablony, musíte mít samostatnou ModelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Vytvoření adaptéru ModelBus, který je nakonfigurovaný pro textové šablony

1. V Průzkumníku souborů zkopírujte a vložte složku, která obsahuje *ModelBusAdapter. csproj*.

    Pojmenujte složku **T4ModelBusAdapter**.

    Přejmenujte soubor projektu *T4ModelBusAdapter. csproj*.

2. V Průzkumník řešení přidejte T4ModelBusAdapter do řešení MBProvider. Klikněte pravým tlačítkem myši na uzel řešení, přejděte na **Přidat** a pak klikněte na **existující projekt**.

3. Klikněte pravým tlačítkem na uzel projektu T4ModelBusAdapter a pak klikněte na vlastnosti. V okně Vlastnosti projektu změňte **název sestavení** a **výchozí obor názvů** na `Company.MBProvider.T4ModelBusAdapters` .

4. V každém souboru *. TT v T4ModelBusAdapter vložte "T4" do poslední části oboru názvů, aby se řádek podobat následujícímu.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. V `DslPackage` projektu přidejte odkaz na projekt do `T4ModelBusAdapter` .

6. V DslPackage\source.extension.tt přidejte následující řádek do `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. Do `T4ModelBusAdapter` projektu přidejte odkaz na: **Microsoft. VisualStudio. TextTemplating. modelings. 11.0**

8. Otevřete T4ModelBusAdapter\AdapterManager.tt:

   1. Změňte základní třídu AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Tato část souboru se teď podobá následujícímu:

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. Poblíž konce souboru vložte následující další atribut před třídu správce.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Výsledek se podobá následujícímu.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. V záhlaví Průzkumník řešení klikněte na **transformovat všechny šablony** .

10. Stiskněte klávesu **F5**.

11. Ověřte, že DSL funguje. V experimentálním projektu otevřete `Sample.provider` . Zavřete experimentální instanci sady Visual Studio.

    Odkazy na tuto DSL ModelBus se teď dají vyřešit v textových šablonách a také v běžném kódu.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Vytvoření DSL pomocí vlastnosti referenční domény ModelBus

1. Vytvořte novou DSL pomocí šablony minimálního jazyka řešení. Pojmenujte jazyk MBConsumer a nastavte příponu názvu souboru na ". spotřebovávají".

2. V projektu DSL přidejte odkaz na sestavení MBProvider DSL. Klikněte pravým tlačítkem  `MBConsumer\Dsl\References` a potom klikněte na **Přidat odkaz**. Na kartě **Procházet** vyhledejte `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    To vám umožní vytvořit kód, který používá jinou DSL. Pokud chcete vytvořit odkazy na několik DSL, přidejte je také.

3. V diagramu definice DSL klikněte pravým tlačítkem na diagram a pak klikněte na **povolit ModelBus**. V dialogovém okně vyberte **Povolit tuto DSL pro využívání ModelBus**.

4. Ve třídě `ExampleElement` přidejte novou vlastnost domény `MBR` a v okno Vlastnosti nastavte typ na `ModelBusReference` .

5. Klikněte pravým tlačítkem na doménovou vlastnost v diagramu a pak klikněte na **Upravit ModelBusReference specifické vlastnosti**. V dialogovém okně vyberte **prvek modelu**.

    Nastavte filtr dialogového okna souboru na následující.

    `Provider File|*.provide`

    Podřetězec po "&#124;" je filtr pro dialogové okno Výběr souboru. Můžete ji nastavit tak, aby umožňovala použití souborů *.\*

    V seznamu **typ elementu modelu** zadejte názvy jedné nebo více doménových tříd v zprostředkovateli DSL (například Company. MBProvider. Task). Můžou to být abstraktní třídy. Pokud necháte seznam prázdný, uživatel může nastavit odkaz na libovolný element.

6. Zavřete dialogové okno a **Transformujte všechny šablony**.

   Vytvořili jste DSL, který může obsahovat odkazy na elementy v jiné DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Vytvořit ModelBus odkaz na jiný soubor v řešení

1. V řešení MBConsumer stiskněte klávesy CTRL + F5. V projektu **MBConsumer\Debugging** se otevře experimentální instance sady Visual Studio.

2. Přidejte kopii Sample. Poskytněte projektu **MBConsumer\Debugging** . To je nezbytné, protože odkaz ModelBus musí odkazovat na soubor ve stejném řešení.

   1. Klikněte pravým tlačítkem na projekt ladění, přejděte na **Přidat** a pak klikněte na **existující položka**.

   2. V dialogovém okně **Přidat položku** nastavte filtr na **všechny soubory ( \* . \* )**.

   3. Přejděte na `MBProvider\Debugging\Sample.provide` a klikněte na **Přidat**.

3. Otevřete `Sample.consume`.

4. Klikněte na jeden vzorový tvar a v okno Vlastnosti ve vlastnosti MBR klikněte na **[...]** . V dialogovém okně klikněte na tlačítko **Procházet** a vyberte `Sample.provide` . V okně elementy rozbalte úlohu typ a vyberte jeden z prvků.

5. Uložte soubor. (Zatím nezavírejte experimentální instanci sady Visual Studio.)

   Vytvořili jste model, který obsahuje odkaz ModelBus na prvek v jiném modelu.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Řešení odkazu na ModelBus v textové šabloně

1. V experimentální instanci aplikace Visual Studio otevřete ukázkový textový soubor šablony. Nastavte jeho obsah následujícím způsobem.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Všimněte si následujících bodů:

    - `hostSpecific` `inherits` `template` Musí být nastaveny atributy a direktivy.

    - K modelu příjemce se dostanete obvyklým způsobem prostřednictvím procesoru direktiv, který byl vygenerován v této DSL.

    - Direktivy Assembly a import musí být schopné získat přístup k ModelBus a typům DSL zprostředkovatele.

    - Pokud víte, že mnoho MBRs je propojeno se stejným modelem, je lepší volat CreateAdapter pouze jednou.

2. Uložte šablonu. Ověřte, zda se výsledný textový soubor podobá následujícímu.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Řešení odkazu na ModelBus v obslužné rutině gesta

1. Zavřete experimentální instanci sady Visual Studio, pokud je spuštěná.

2. Přidejte soubor s názvem *MBConsumer\Dsl\Custom.cs* a nastavte jeho obsah na následující:

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. Stiskněte klávesu **CTRL** + **F5**.

4. V experimentální instanci aplikace Visual Studio otevřete `Debugging\Sample.consume` .

5. Dvakrát klikněte na jeden obrazec.

    Pokud jste pro tento element nastavili MBR, otevře se odkazovaný model a je vybrán odkazový element.

## <a name="see-also"></a>Viz také:

- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Vytvoření kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
