---
title: Použití ModelBus v textové šabloně
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: caadb1c7d97d377959f03bec559e18f445093d03
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111509"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Použití prvku Visual Studio ModelBus v textové šabloně

Při zápisu textových šablon, které čtou modelu, který obsahuje odkazy na Visual Studio ModelBus, můžete k vyřešení odkazů pro přístup k modelů cíl. V takovém případě budete muset přizpůsobit textových šablon a odkazované jazyky specifickými pro doménu (DSL):

- DSL, která je cílem dané odkazy musí být ModelBus adaptér, který je nakonfigurovaný pro přístup z textové šablony. Pokud můžete také získat přístup k DSL od jiného kódu, se vyžaduje kromě standardní adaptér ModelBus překonfigurovaná adaptér.

     Správce adaptéru musí dědit z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) a musí mít atribut `[HostSpecific(HostName)]`.

- Šablona musí dědit z [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Pokud chcete číst DSL modely, které neobsahují ModelBus odkazy, můžete použít procesorů pro direktivy, které jsou generovány ve vašich projektech DSL. Další informace najdete v tématu [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md).

Další informace o textových šablonách naleznete v tématu [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Vytvoření adaptéru modelové sběrnice pro přístup z textových šablon

Přeložit odkaz ModelBus v textové šabloně, cíl DSL musí mít kompatibilní adaptéru. Spuštění textové šablony v oddělené doméně AppDomain. z dokumentu editory sady Visual Studio, a proto má adaptér načíst model ne přístup prostřednictvím DTE.

1. Pokud nemá žádné cílové řešení DSL **objekt ModelBusAdapter** projekt, vytvořte ji pomocí Průvodce rozšířením Modelbus:

    1. Stáhněte a nainstalujte Visual Studio ModelBus rozšíření, pokud jste to ještě neudělali. Další informace najdete v tématu [Visualization and Modeling SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Otevření souboru definice DSL. Klikněte pravým tlačítkem na návrhové ploše a potom klikněte na tlačítko **povolit Modelbus**.

    3. V dialogovém okně vyberte **chci zveřejnit tento DSL k ModelBus**. Obě možnosti můžete vybrat, pokud chcete tento DSL zveřejnit své modely a využívat odkazy na další DSL.

    4. Klikněte na tlačítko **OK**. Nový projekt "Objekt ModelBusAdapter" je přidán do řešení DSL.

    5. Klikněte na tlačítko **Transformovat všechny šablony**.

    6. Znovu sestavte řešení.

2. Pokud chcete získat přístup k DSL z textové šablony a od jiného kódu, jako je například příkazu Duplikovat **objekt ModelBusAdapter** projektu:

    1. V Průzkumníku Windows zkopírujte a vložte tato složka obsahuje **ModelBusAdapter.csproj**.

    2. Přejmenovat soubor projektu (například **T4ModelBusAdapter.csproj**).

    3. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení, přejděte na **přidat**a potom klikněte na tlačítko **existující projekt**. Vyhledejte nový projekt adaptér **T4ModelBusAdapter.csproj**.

    4. V každém `*.tt` souboru nového projektu změnit obor názvů.

    5. Klikněte pravým tlačítkem na nový projekt v **Průzkumník řešení** a pak klikněte na **vlastnosti**. V editoru vlastností změňte názvy generované sestavení a výchozí obor názvů.

    6. V projektu DslPackage přidejte odkaz na nový projekt adaptéru tak, aby se odkazy na obou adaptérů.

    7. V DslPackage\source.extension.tt přidejte řádek, který odkazuje na nový projekt adaptéru.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformovat všechny šablony** a znovu sestavte řešení. Žádné chyby buildu se budou objevovat.

3. V novém adaptéru projektu přidejte odkazy na následující sestavení:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. V AdapterManager.tt:

    - Změňte deklaraci AdapterManagerBase tak, aby dědila z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Na konci souboru nahraďte atribut HostSpecific před AdapterManager třídy. Odebrání následujícího řádku:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Vložte následující řádek:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Tento atribut filtruje sadu adaptérů, která je k dispozici, když modelbus příjemce hledá adaptér.

5. **Transformovat všechny šablony** a znovu sestavte řešení. Žádné chyby buildu se budou objevovat.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Napsat textovou šablonu, která může vyřešit odkazy ModelBus

Obvykle začněte šablonou, která čte a generuje soubory z "zdroj" DSL. Tato šablona používá směrnice, které se generuje v projektu DSL zdroje pro čtení zdrojových souborů modelu způsobem, který je popsaný v [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md). Zdroj DSL však obsahuje ModelBus odkazy na "cíl" DSL. Proto budete chtít povolit kód šablony k vyřešení odkazů a přístup k cíli DSL. Proto musíte přizpůsobit šablonu pomocí následujících kroků:

- Změňte základní třídu šablony na [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Zahrnout `hostspecific="true"` v direktivě šablony.

- Přidáte odkazy na sestavení cílové DSL a jeho adaptéru a povolit ModelBus.

- Není nutné směrnice, který je generován jako součást cíle DSL.

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

 Při spuštění této textové šablony `SourceDsl` směrnice načte soubor `Sample.source`. Šablony můžete přistupovat k prvkům tohoto modelu, počínaje `this.ModelRoot`. Kód můžete použít doménové třídy a vlastnosti této DSL.

 Kromě toho šablony může rozpoznat odkazy ModelBus. Pokud odkazují na cílovém modelu, dejte direktivy sestavení kódu použít doménové třídy a vlastnosti tohoto modelu DSL.

- Pokud nepoužíváte direktivu, který je generován projekt DSL, měli byste také zahrnout následující.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Použití `this.ModelBus` získat přístup k ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Návod: Testování textové šablony, která používá ModelBus
 V tomto podrobném návodu postupujte takto:

1. Vytvoření dvou DSL. Jednom DSL *příjemce*, má `ModelBusReference` vlastnost, která mohou odkazovat na jiné DSL *poskytovatele*.

2. Vytvořit dva adaptéry ModelBus ve zprostředkovateli: jeden pro zabezpečení přístupu pomocí textových šablon, druhá pro běžné kódu.

3. Vytvoření instance modely DSL v jednom projektu experimentální.

4. Nastavení vlastnosti domény v jednom modelu tak, aby odkazoval na model.

5. Zápis dvakrát klikněte na obslužnou rutinu, která se otevře model, který ukazuje.

6. Zápis textové šablony, která může načíst první model, postupujte podle odkazu na model a číst jiný model.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Vytvoření DSL, který je přístupný ModelBus

1. Vytvořte nové řešení DSL. V tomto příkladu vyberte šablonu toku úkolů řešení. Nastavte název jazyka `MBProvider` a příponu názvu souboru na ".provide".

2. V definici DSL diagramu, klikněte pravým tlačítkem na prázdnou část diagramu, který není v horní části a klikněte na **povolit Modelbus**.

   Pokud nevidíte **možnost povolit ModelBus**, Stáhněte a nainstalujte rozšíření ModelBus VMSDK.

3. V **povolit Modelbus** dialogu **zveřejnit tento DSL k ModelBus**a potom klikněte na tlačítko **OK**.

    Nový projekt `ModelBusAdapter`, je přidán do řešení.

Teď máte DSL, který je přístupný pomocí textových šablon pomocí ModelBus. Odkazy na ni může být vyřešen v kódu příkazy, obslužné rutiny událostí nebo pravidla, které pracují v AppDomain soubor editoru modelů. Ale textových šablon spustit v oddělené doméně AppDomain a nemůžou přistupovat modelu se právě upravuje. Pokud chcete získat přístup ModelBus odkazy na tento DSL z textové šablony, musíte mít samostatný objekt ModelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Vytvoření adaptéru ModelBus, který je nakonfigurovaný pro textové šablony

1. V Průzkumníku souborů zkopírujte a vložte složku, která obsahuje *ModelBusAdapter. csproj*.

    Pojmenujte složku **T4ModelBusAdapter**.

    Přejmenujte soubor projektu *T4ModelBusAdapter. csproj*.

2. V Průzkumníku řešení přidejte do řešení MBProvider T4ModelBusAdapter. Klikněte pravým tlačítkem na uzel řešení, přejděte na **přidat**a potom klikněte na tlačítko **existující projekt**.

3. Klikněte pravým tlačítkem na uzel projektu T4ModelBusAdapter a potom klikněte na možnost Vlastnosti. V okně Vlastnosti projektu změnit **název sestavení** a **výchozí Namespace** k `Company.MBProvider.T4ModelBusAdapters`.

4. V každém *.tt souboru T4ModelBusAdapter insert "T4" poslední část oboru názvů tak, aby řádku vypadá přibližně takto.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. V `DslPackage` projektu, přidejte odkaz na projekt `T4ModelBusAdapter`.

6. V DslPackage\source.extension.tt, přidejte následující řádek pod `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. V `T4ModelBusAdapter` projektu, přidejte odkaz na: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Otevřete T4ModelBusAdapter\AdapterManager.tt:

   1. Změňte základní třídu AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Tato část souboru teď vypadá podobně jako tento.

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

   2. Na konci souboru vložte následující další atribut před třídy AdapterManager.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Výsledek vypadá podobně jako tento.

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

9. Klikněte na tlačítko **Transformovat všechny šablony** v nadpisu panel z Průzkumníka řešení.

10. Stiskněte klávesu **F5**.

11. Ověřte, že DSL funguje. V experimentální projektu otevřete `Sample.provider`. Ukončete experimentální instanci sady Visual Studio.

    Nyní možné vyřešit ModelBus odkazy na tento DSL textové šablony a taky na běžnou kódu.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Vytvoření DSL pomocí doménová vlastnost, která odkaz ModelBus

1. Vytvořte nový DSL pomocí šablony řešení jazyka minimální. Název jazyka MBConsumer a nastavit příponu názvu souboru na ".consume".

2. V projektu DSL přidejte odkaz na sestavení MBProvider DSL. Klikněte pravým tlačítkem na `MBConsumer\Dsl\References` a potom klikněte na tlačítko **přidat odkaz**. V **Procházet** kartu, vyhledejte `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    To umožňuje vytvořit kód, který používá jiné DSL. Pokud chcete vytvořit odkazy na několik DSL, přidejte je také.

3. V definici DSL diagramu, klikněte pravým tlačítkem na diagramu a potom klikněte na **povolit ModelBus**. V dialogovém okně vyberte **povolit tento DSL využívat ModelBus**.

4. Ve třídě `ExampleElement`, přidat nové vlastnosti domény `MBR`a v okně Vlastnosti nastavte její typ `ModelBusReference`.

5. Klikněte pravým tlačítkem na vlastnost domény v diagramu a potom klikněte na **upravit ModelBusReference specifické vlastnosti**. V dialogovém okně vyberte **prvku modelu**.

    Nastavte na následující dialogové okno filtru souborů.

    `Provider File|*.provide`

    Podřetězec po "&#124;" je filtr pro dialogové okno Výběr souboru. Můžete ji povolit všechny soubory s použitím nastavit *.\*

    V **typ prvku modelu** seznamu, zadejte jména jednoho nebo více domény třídy ve zprostředkovateli DSL (například Company.MBProvider.Task). Můžou být abstraktní třídy. Pokud seznam nezadáte, může uživatel nastavit odkaz na libovolný element.

6. Zavřete dialogové okno a **Transformovat všechny šablony**.

   Vytvořili jste DSL, která mohou obsahovat odkazy na prvky v jiném DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Vytvořit odkaz na jiný soubor ModelBus v řešení

1. V řešení MBConsumer stisknutím kláves CTRL + F5. Otevře se v experimentální instanci sady Visual Studio **MBConsumer\Debugging** projektu.

2. Přidat kopii Sample.provide k **MBConsumer\Debugging** projektu. To je nezbytné, protože odkaz ModelBus musí odkazovat na soubor ve stejném řešení.

   1. Klikněte pravým tlačítkem na projekt ladění, přejděte na **přidat**a potom klikněte na tlačítko **existující položku**.

   2. V **přidat položku** dialogové okno, nastavte filtr **všechny soubory (\*.\*)** .

   3. Přejděte do `MBProvider\Debugging\Sample.provide` a potom klikněte na tlačítko **přidat**.

3. Otevřete `Sample.consume`.

4. Klikněte na jeden příklad obrazec a v okně Vlastnosti klikněte na tlačítko **[...]**  ve vlastnosti MBR. V dialogovém okně klikněte na tlačítko **Procházet** a vyberte `Sample.provide`. V okně prvky typu úloh rozbalte a vyberte jeden z prvků.

5. Uložte soubor. (Ještě nezavírejte experimentální instanci sady Visual Studio.)

   Vytvořili jste model, který obsahuje odkaz ModelBus na prvek v jiném modelu.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Přeložení odkazu ModelBus v textové šabloně

1. V experimentální instanci sady Visual Studio otevřete šablonu ukázkového textového souboru. Nastavte jeho obsah následujícím způsobem.

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

     Všimněte si, že následující body:

    - `hostSpecific` a `inherits` atributy `template` – direktiva musí být nastavena.

    - Modelu oddělených příjemců přistupuje prostřednictvím procesor direktiv, který byl vygenerován v tomto DSL obvyklým způsobem.

    - Direktivy sestavení a import musí mít pro přístup k ModelBus a typy zprostředkovatele DSL.

    - Pokud víte, že mnoho MBRs jsou propojeny do stejného modelu, je lepší volat CreateAdapter pouze jednou.

2. Uložte šablonu. Ověřte, že výsledný textový soubor vypadá přibližně takto.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Přeložení odkazu ModelBus v obslužné rutiny gesta

1. Ukončete experimentální instanci sady Visual Studio, pokud je spuštěn.

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

3. Stiskněte klávesu **Ctrl**+**F5**.

4. V experimentální instanci sady Visual Studio, otevřete `Debugging\Sample.consume`.

5. Dvakrát klikněte na jeden prvek.

    Pokud nastavíte MBR pro tento element otevře odkazovaným modelem a odkazovaný element je vybrán.

## <a name="see-also"></a>Viz také:

- [Integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Vytvoření kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
