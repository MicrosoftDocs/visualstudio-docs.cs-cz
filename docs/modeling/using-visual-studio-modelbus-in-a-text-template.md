---
title: Použití modelbusu v textové šabloně
description: Zjistěte, jak vyřešit odkazy na přístup k cílovým modelům, pokud píšete textové šablony, které čtou model, který Visual Studio ModelBus odkazy.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2afe8de66b109793a4e15e8320c3f498a08b25ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388383"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Použití prvku Visual Studio ModelBus v textové šabloně

Pokud píšete textové šablony, které čtou model, který obsahuje Visual Studio ModelBus, můžete chtít přeložit odkazy pro přístup k cílovým modelům. V takovém případě musíte upravit textové šablony a odkazované jazyky specifické pro doménu (DSL):

- DSL, který je cílem odkazů, musí mít adaptér ModelBus, který je nakonfigurovaný pro přístup z textových šablon. Pokud k DSL přistupíte také z jiného kódu, vyžaduje se kromě standardního adaptéru ModelBus i překonfigurované adaptéry.

     Správce adaptéru musí dědit z [třídy VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) a musí mít atribut `[HostSpecific(HostName)]` .

- Šablona musí dědit z [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Pokud chcete číst modely DSL, které neobsahují odkazy ModelBus, můžete použít procesory direktiv, které jsou generovány v projektech DSL. Další informace najdete v tématu [Přístup k modelům z textových šablon.](../modeling/accessing-models-from-text-templates.md)

Další informace o textových šablonách najdete v tématu Generování kódu v době návrhu [pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Vytvoření adaptéru sběrnice modelu pro přístup z textových šablon

Pokud chcete přeložit odkaz ModelBus v textové šabloně, musí mít cílový DSL kompatibilní adaptér. Textové šablony se spouští v samostatné doméně AppDomain Visual Studio editorech dokumentů, a proto musí adaptér místo přístupu k modelu prostřednictvím DTE načíst model.

1. Pokud cílové řešení DSL nemá projekt **ModelBusAdapter,** vytvořte ho pomocí průvodce rozšířením Modelbus:

    1. Pokud jste to ještě neudělali, Visual Studio ModelBus a nainstalujte rozšíření klienta. Další informace najdete v tématu [Sada SDK vizualizace a modelování.](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

    2. Otevřete definiční soubor DSL. Klikněte pravým tlačítkem na návrhovou plochu a pak klikněte **na Povolit Modelbus.**

    3. V dialogovém okně vyberte I want to expose this DSL to the ModelBus (Chci tento DSL zveřejnit **pro ModelBus).** Obě možnosti můžete vybrat, pokud chcete, aby tento DSL zpřístupňuje své modely i spotřebovává odkazy na jiné seznamy DSL.

    4. Klikněte na **OK**. Do řešení DSL se přidá nový projekt ModelBusAdapter.

    5. Klikněte **na Transformovat všechny šablony.**

    6. Znovu sestavte řešení.

2. Pokud chcete získat přístup k DSL z textové šablony i z jiného kódu, jako je například příkaz, duplikujte **projekt ModelBusAdapter:**

    1. V Průzkumník Windows zkopírujte a vložte složku, která obsahuje **ModelBusAdapter.csproj.**

    2. Přejmenujte soubor projektu (například na **T4ModelBusAdapter.csproj).**

    3. V **Průzkumník řešení** klikněte pravým tlačítkem na uzel řešení, přejděte na **Přidat** a pak klikněte na **Existující projekt.** Vyhledejte nový projekt adaptéru **T4ModelBusAdapter.csproj.**

    4. V každém `*.tt` souboru nového projektu změňte obor názvů .

    5. Klikněte pravým tlačítkem na nový projekt v **Průzkumník řešení** pak klikněte na **Vlastnosti**. V editoru vlastností změňte názvy vygenerovaného sestavení a výchozí obor názvů.

    6. V projektu DslPackage přidejte odkaz na nový projekt adaptéru, aby měl odkazy na oba adaptéry.

    7. V adresáři DslPackage\source.extension.tt přidejte řádek, který odkazuje na nový projekt adaptéru.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformujte všechny šablony** a znovu sestavte řešení. Neměly by docházet k žádným chybám sestavení.

3. V novém projektu adaptéru přidejte odkazy na následující sestavení:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. V AdapterManager.tt:

    - Změňte deklaraci AdapterManagerBase tak, aby dědí z [třídy VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Na konci souboru nahraďte atribut HostSpecific před třídu AdapterManager. Odeberte následující řádek:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Vložte následující řádek:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Tento atribut filtruje sadu adaptérů, které jsou k dispozici, když příjemce sběrnice modelu vyhledá adaptér.

5. **Transformujte všechny šablony** a znovu sestavte řešení. Neměly by docházet k žádným chybám sestavení.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Napsání textové šablony, která dokáže přeložit odkazy ModelBus

Obvykle začínáte šablonou, která čte a generuje soubory ze "zdrojového" DSL. Tato šablona používá direktivu , která je vygenerována ve zdrojovém projektu DSL ke čtení zdrojových souborů modelu způsobem popsaným v části Přístup k modelům [z textových šablon](../modeling/accessing-models-from-text-templates.md). Zdrojový DSL však obsahuje odkazy ModelBus na "cílový" DSL. Proto chcete povolit kód šablony pro překlad odkazů a přístup k cílovému DSL. Proto je nutné přizpůsobit šablonu pomocí následujících kroků:

- Změňte základní třídu šablony na [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Do `hostspecific="true"` direktivy šablony zahrnte .

- Přidejte odkazy na sestavení k cílovému DSL a jeho adaptéru a povolte ModelBus.

- Direktivu, která je vygenerována jako součást cílového DSL, nepotřebujete.

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

 Při spuštění této textové šablony načte `SourceDsl` direktiva soubor `Sample.source` . Šablona má přístup k prvkům tohoto modelu, počínaje `this.ModelRoot` . Kód může používat třídy domény a vlastnosti tohoto DSL.

 Kromě toho může šablona vyřešit odkazy ModelBus. Pokud odkazy odkazují na cílový model, direktivy sestavení umožňují kódu používat třídy domény a vlastnosti DSL tohoto modelu.

- Pokud nepoužívejte direktivu, která je generována projektem DSL, měli byste také zahrnout následující.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Pomocí `this.ModelBus` získáte přístup k modelbusu.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Návod: Testování textové šablony, která používá ModelBus
 V tomto názorném postupu budete postupovat takto:

1. Vytvořte dva seznamy DSL. Jeden DSL, *příjemce*, má vlastnost, `ModelBusReference` která může odkazovat na druhý DSL, *zprostředkovatel*.

2. Ve zprostředkovateli vytvořte dva adaptéry ModelBus: jeden pro přístup pomocí textových šablon, druhý pro běžný kód.

3. Vytvoření modelů instancí adres DSL v jednom experimentálním projektu

4. Nastavte vlastnost domény v jednom modelu tak, aby odkazovat na druhý model.

5. Napište obslužnou rutinu poklikejte, která otevře model, na který se odkazuje.

6. Napište textovou šablonu, která může načíst první model, postupovat podle odkazu na druhý model a přečíst druhý model.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Vytvoření DSL, který je přístupný pro ModelBus

1. Vytvořte nové řešení DSL. V tomto příkladu vyberte šablonu řešení Tok úloh. Nastavte název jazyka na `MBProvider` a příponu názvu souboru na ".provide".

2. V diagramu definice DSL klikněte pravým tlačítkem na prázdnou část diagramu, která není v horní části, a potom klikněte na **Povolit modelbus**.

   Pokud možnost Povolit **Modelbus nevidíte,** stáhněte a nainstalujte rozšíření VMSDK ModelBus.

3. V dialogovém **okně Povolit modelbus** vyberte Expose this DSL to the ModelBus (Zveřejnit **tento DSL pro ModelBus)** a pak klikněte na **OK.**

    Do řešení se `ModelBusAdapter` přidá nový projekt .

Teď máte DSL, ke kterým mají přístup textové šablony prostřednictvím modelbusu. Odkazy na něj lze vyřešit v kódu příkazů, obslužných rutin událostí nebo pravidel, které fungují v doméně AppDomain editoru souborů modelu. Textové šablony však běží v samostatné doméně appdomain a při úpravách nemohou přistupovat k modelu. Pokud chcete získat přístup k odkazům ModelBus na tento DSL z textové šablony, musíte mít samostatný model ModelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Vytvoření adaptéru ModelBus, který je nakonfigurovaný pro textové šablony

1. V Průzkumník souborů zkopírujte a vložte složku, která obsahuje *ModelBusAdapter.csproj.*

    Složku **pojmechte T4ModelBusAdapter**.

    Přejmenujte soubor *projektu T4ModelBusAdapter.csproj.*

2. V Průzkumník řešení do řešení MBProvider přidejte T4ModelBusAdapter. Klikněte pravým tlačítkem na uzel řešení, přejděte **na Přidat a** pak klikněte na Existující **projekt**.

3. Klikněte pravým tlačítkem na uzel projektu T4ModelBusAdapter a pak klikněte na Vlastnosti. V okně vlastností projektu změňte **Název sestavení a** Výchozí obor **názvů** na `Company.MBProvider.T4ModelBusAdapters` .

4. V každém souboru *.tt v objektu T4ModelBusAdapter vložte do poslední části oboru názvů "T4", aby se řádek podobal následujícímu.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. V `DslPackage` projektu přidejte odkaz na projekt `T4ModelBusAdapter` do .

6. V adresáři DslPackage\source.extension.tt přidejte následující řádek pod `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. V `T4ModelBusAdapter` projektu přidejte odkaz na: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Otevřete T4ModelBusAdapter\AdapterManager.tt:

   1. Změňte základní třídu AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Tato část souboru teď vypadá podobně jako v následujícím příkladu.

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

   2. Na konec souboru vložte před třídu AdapterManager následující další atribut.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Výsledek vypadá podobně jako v následujícím příkladu.

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

9. V **záhlaví okna klikněte** na Transformovat všechny šablony Průzkumník řešení.

10. Stiskněte **klávesu F5**.

11. Ověřte, že DSL funguje. V experimentálním projektu otevřete `Sample.provider` . Zavřete experimentální instanci Visual Studio.

    Odkazy ModelBus na tento DSL je teď možné přeložit v textových šablonách a také v běžném kódu.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Vytvoření DSL s vlastností domény odkaz na ModelBus

1. Vytvořte nový DSL pomocí šablony řešení minimálního jazyka. Pojmete jazyk MBConsumer a nastavte příponu názvu souboru na ".consume".

2. V projektu DSL přidejte odkaz na sestavení MBProvider DSL. Klikněte pravým tlačítkem `MBConsumer\Dsl\References` a pak klikněte na Přidat **odkaz.** Na kartě **Procházet** vyhledejte `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    To vám umožní vytvořit kód, který používá druhý DSL. Pokud chcete vytvořit odkazy na několik adres DSL, přidejte je také.

3. V diagramu definice DSL klikněte pravým tlačítkem na diagram a pak klikněte na **Povolit ModelBus.** V dialogovém okně vyberte Enable this DSL to Consume the ModelBus (Povolit tento DSL pro **používání sběrnice ModeluBus).**

4. Do třídy přidejte novou vlastnost domény a do `ExampleElement` `MBR` okno Vlastnosti nastavte její typ na `ModelBusReference` .

5. Klikněte pravým tlačítkem na vlastnost domény v diagramu a pak klikněte na **Upravit modelBusReference – vlastnosti specifické pro**. V dialogovém okně vyberte **prvek modelu**.

    Nastavte filtr dialogového okna souboru na následující hodnotu.

    `Provider File|*.provide`

    Podřetězec za &#124; je filtrem dialogového okna pro výběr souboru. Můžete ho nastavit tak, aby povoll všechny soubory, pomocí *.\*

    V seznamu **Typ elementu** modelu zadejte názvy jedné nebo více tříd domény v zprostředkovateli DSL (například Company.MBProvider.Task). Mohou to být abstraktní třídy. Pokud seznam necháte prázdný, může uživatel nastavit odkaz na libovolný prvek.

6. Zavřete dialogové okno **a transformujte všechny šablony.**

   Vytvořili jste DSL, který může obsahovat odkazy na prvky v jiném DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Vytvoření odkazu ModelBus na jiný soubor v řešení

1. V řešení MBConsumer stiskněte kombinaci kláves CTRL+F5. Experimentální instance Visual Studio v **projektu MBConsumer\Debugging.**

2. Do projektu **MBConsumer\Debugging** přidejte kopii souboru Sample.provide. To je nezbytné, protože odkaz ModelBus musí odkazovat na soubor ve stejném řešení.

   1. Klikněte pravým tlačítkem na projekt Ladění, přejděte na **Přidat a** pak klikněte na **Existující položka.**

   2. V dialogovém **okně Přidat** položku nastavte filtr na Všechny soubory ( **. \* \* ).**

   3. Přejděte na `MBProvider\Debugging\Sample.provide` a pak klikněte na **Přidat.**

3. Otevřete `Sample.consume`.

4. Klikněte na jeden příklad tvaru a v okno Vlastnosti klikněte **na položku » ve** vlastnosti MBR. V dialogovém okně klikněte na **Procházet a** vyberte `Sample.provide` . V okně elementů rozbalte typ Úloha a vyberte jeden z prvků.

5. Soubor uložte. (Ještě nezadáte experimentální instanci Visual Studio.)

   Vytvořili jste model, který obsahuje odkaz ModelBus na prvek v jiném modelu.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Řešení odkazu ModelBus v textové šabloně

1. V experimentální instanci Visual Studio otevřete soubor ukázkové textové šablony. Obsah nastavte následujícím způsobem.

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

    - Musí `hostSpecific` `inherits` být nastaveny `template` atributy a direktivy .

    - K modelu příjemce se přistupuje obvyklým způsobem prostřednictvím procesoru direktiv, který byl vygenerován v tomto DSL.

    - Direktivy sestavení a import musí mít přístup k modelu ModelBus a typům DSL poskytovatele.

    - Pokud víte, že mnoho mbR je propojených se stejným modelem, je lepší volat createAdapter pouze jednou.

2. Uložte šablonu. Ověřte, že výsledný textový soubor vypadá podobně jako následující.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Řešení odkazu ModelBus v obslužné rutině gest

1. Zavřete experimentální instanci Visual Studio, pokud je spuštěná.

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

3. Stiskněte **Ctrl** + **F5**.

4. V experimentální instanci Visual Studio otevřete `Debugging\Sample.consume` .

5. Dvakrát klikněte na jeden obrazec.

    Pokud jste pro tento prvek nastavili MBR, otevře se odkazovaný model a vybraný odkazovaný prvek.

## <a name="see-also"></a>Viz také

- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Vytvoření kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
