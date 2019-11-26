---
title: Pomocí ModelBus v textové šabloně | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0d18103d2990b2734e4db1d1e7dc4261e08e7a7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301374"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Použití prvku Visual Studio ModelBus v textové šabloně
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud píšete šablony textu, které čtou model, který obsahuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] odkazy na ModelBus, můžete chtít vyřešit odkazy pro přístup k cílovým modelům. V takovém případě budete muset přizpůsobit textových šablon a odkazované jazyky specifickými pro doménu (DSL):

- DSL, která je cílem dané odkazy musí být ModelBus adaptér, který je nakonfigurovaný pro přístup z textové šablony. Pokud můžete také získat přístup k DSL od jiného kódu, se vyžaduje kromě standardní adaptér ModelBus překonfigurovaná adaptér.

     Správce adaptéru musí dědit z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) a musí mít atribut `[HostSpecific(HostName)]`.

- Šablona musí dědit z [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Pokud chcete číst DSL modely, které neobsahují ModelBus odkazy, můžete použít procesorů pro direktivy, které jsou generovány ve vašich projektech DSL. Další informace naleznete v tématu [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md).

 Další informace o textových šablonách naleznete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Vytvoření adaptéru modelu Service Bus pro přístup z textových šablon
 Přeložit odkaz ModelBus v textové šabloně, cíl DSL musí mít kompatibilní adaptéru. Textové šablony jsou spouštěny v samostatné doméně AppDomain z editorů dokumentů [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a proto adaptér musí načíst model místo přístupu přes DTE.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Chcete-li vytvořit ModelBus adaptér, který je kompatibilní s textových šablon

1. Pokud cílové řešení DSL nemá projekt **ModelBusAdapter** , vytvořte ho pomocí Průvodce rozšířením ModelBus:

    1. Pokud jste to ještě neudělali, Stáhněte a nainstalujte rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. Další informace najdete v tématu [sada SDK pro vizualizaci a modelování](https://go.microsoft.com/fwlink/?LinkID=185579).

    2. Otevření souboru definice DSL. Klikněte pravým tlačítkem myši na návrhovou plochu a pak klikněte na **povolit ModelBus**.

    3. V dialogovém okně vyberte možnost **chci zveřejnit tuto DSL pro ModelBus**. Obě možnosti můžete vybrat, pokud chcete tento DSL zveřejnit své modely a využívat odkazy na další DSL.

    4. Klikněte na tlačítko **OK**. Nový projekt "Objekt ModelBusAdapter" je přidán do řešení DSL.

    5. Klikněte na **transformovat všechny šablony**.

    6. Znovu sestavte řešení.

2. Pokud chcete použít DSL z textové šablony a z jiného kódu, jako je například příkaz, duplikujte projekt **ModelBusAdapter** :

    1. V Průzkumníku Windows zkopírujte a vložte složku, která obsahuje **ModelBusAdapter. csproj**.

    2. Přejmenujte soubor projektu (například na **T4ModelBusAdapter. csproj**).

    3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení, přejděte na **Přidat**a pak klikněte na **existující projekt**. Vyhledejte nový projekt adaptéru **T4ModelBusAdapter. csproj**.

    4. V každém `*.tt` souboru nového projektu změňte obor názvů.

    5. Klikněte pravým tlačítkem na nový projekt v Průzkumníku řešení a potom klikněte na možnost Vlastnosti. V editoru vlastností změňte názvy generované sestavení a výchozí obor názvů.

    6. V projektu DslPackage přidejte odkaz na nový projekt adaptéru tak, aby se odkazy na obou adaptérů.

    7. V DslPackage\source.extension.tt přidejte řádek, který odkazuje na nový projekt adaptéru.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformujte všechny šablony** a znovu sestavte řešení. Žádné chyby buildu se budou objevovat.

3. V novém adaptéru projektu přidejte odkazy na následující sestavení:

    - Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. V AdapterManager.tt:

    - Změňte deklaraci AdapterManagerBase tak, aby dědila z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Na konci souboru nahraďte atribut HostSpecific před AdapterManager třídy. Odebrání následujícího řádku:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Vložte následující řádek:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Tento atribut filtruje sadu adaptérů, která je k dispozici, když modelbus příjemce hledá adaptér.

5. **Transformujte všechny šablony** a znovu sestavte řešení. Žádné chyby buildu se budou objevovat.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>Vytvoření textové šablony, který dokáže přeložit odkazy ModelBus
 Obvykle začněte šablonou, která čte a generuje soubory z "zdroj" DSL. Tato šablona používá direktivu, která je generována ve zdrojovém projektu DSL pro čtení souborů zdrojového modelu způsobem, který je popsán v tématu [přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md). Zdroj DSL však obsahuje ModelBus odkazy na "cíl" DSL. Proto budete chtít povolit kód šablony k vyřešení odkazů a přístup k cíli DSL. Proto musíte přizpůsobit šablonu pomocí následujících kroků:

- Změňte základní třídu šablony na [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Do direktivy Template přidejte `hostspecific="true"`.

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
    // (Let’s assume they’re all in the same model file):
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

 Při spuštění této textové šablony načte direktiva `SourceDsl` `Sample.source`souboru. Šablona má přístup k prvkům modelu, počínaje od `this.ModelRoot`. Kód můžete použít doménové třídy a vlastnosti této DSL.

 Kromě toho šablony může rozpoznat odkazy ModelBus. Pokud odkazují na cílovém modelu, dejte direktivy sestavení kódu použít doménové třídy a vlastnosti tohoto modelu DSL.

- Pokud nepoužíváte direktivu, který je generován projekt DSL, měli byste také zahrnout následující.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- K získání přístupu k ModelBus použijte `this.ModelBus`.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Návod: Testování textové šablony, která používá ModelBus
 V tomto podrobném návodu postupujte takto:

1. Vytvoření dvou DSL. Jedna DSL, *příjemce*má `ModelBusReference` vlastnost, která může odkazovat na jinou DSL, *poskytovatele*.

2. Vytvořit dva adaptéry ModelBus ve zprostředkovateli: jeden pro zabezpečení přístupu pomocí textových šablon, druhá pro běžné kódu.

3. Vytvoření instance modely DSL v jednom projektu experimentální.

4. Nastavení vlastnosti domény v jednom modelu tak, aby odkazoval na model.

5. Zápis dvakrát klikněte na obslužnou rutinu, která se otevře model, který ukazuje.

6. Zápis textové šablony, která může načíst první model, postupujte podle odkazu na model a číst jiný model.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Vytvoření DSL, který je přístupný ModelBus

1. Vytvořte nové řešení DSL. V tomto příkladu vyberte šablonu toku úkolů řešení. Nastavte název jazyka na `MBProvider` a přípona názvu souboru na ". Poskytněte".

2. V diagramu definice DSL klikněte pravým tlačítkem myši na prázdnou část diagramu, která není blízko horní části, a pak klikněte na **povolit ModelBus**.

   - Pokud nevidíte **možnost povolit ModelBus**, musíte si stáhnout a nainstalovat rozšíření VMSDK ModelBus. Najdete ho na webu VMSDK: [vizualizace a modelování sady SDK](https://go.microsoft.com/fwlink/?LinkID=185579).

3. V dialogovém okně **povolit ModelBus** vyberte možnost **zpřístupnit tuto DSL pro ModelBus**a pak klikněte na **OK**.

    Do řešení se přidá nový projekt, `ModelBusAdapter`.

   Teď máte DSL, který je přístupný pomocí textových šablon pomocí ModelBus. Odkazy na ni může být vyřešen v kódu příkazy, obslužné rutiny událostí nebo pravidla, které pracují v AppDomain soubor editoru modelů. Ale textových šablon spustit v oddělené doméně AppDomain a nemůžou přistupovat modelu se právě upravuje. Pokud chcete získat přístup ModelBus odkazy na tento DSL z textové šablony, musíte mít samostatný objekt ModelBusAdapter.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Chcete-li vytvořit ModelBus adaptér, který je nakonfigurovaný pro textové šablony

1. V Průzkumníku Windows zkopírujte a vložte tato složka obsahuje ModelBusAdapter.csproj.

    Název složky T4ModelBusAdapter.

    Přejmenujte soubor projektu T4ModelBusAdapter.csproj.

2. V Průzkumníku řešení přidejte do řešení MBProvider T4ModelBusAdapter. Klikněte pravým tlačítkem myši na uzel řešení, přejděte na **Přidat**a pak klikněte na **existující projekt**.

3. Klikněte pravým tlačítkem na uzel projektu T4ModelBusAdapter a potom klikněte na možnost Vlastnosti. V okně Vlastnosti projektu změňte **název sestavení** a **výchozí obor názvů** na `Company.MBProvider.T4ModelBusAdapters`.

4. V každém *.tt souboru T4ModelBusAdapter insert "T4" poslední část oboru názvů tak, aby řádku vypadá přibližně takto.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. V projektu `DslPackage` přidejte odkaz na projekt do `T4ModelBusAdapter`.

6. V DslPackage\source.extension.tt přidejte do `<Content>`následující řádek.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. V projektu `T4ModelBusAdapter` přidejte odkaz na: **Microsoft. VisualStudio. TextTemplating. modelings. 11.0**

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

9. V záhlaví Průzkumník řešení klikněte na **transformovat všechny šablony** .

10. Znovu sestavte řešení. Klikněte na tlačítko F5.

11. Ověřte, že DSL funguje stisknutím klávesy F5. V experimentálním projektu otevřete `Sample.provider`. Zavřete experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

    Nyní možné vyřešit ModelBus odkazy na tento DSL textové šablony a taky na běžnou kódu.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Vytvoření DSL pomocí doménová vlastnost, která odkaz ModelBus

1. Vytvořte nový DSL pomocí šablony řešení jazyka minimální. Název jazyka MBConsumer a nastavit příponu názvu souboru na ".consume".

2. V projektu DSL přidejte odkaz na sestavení MBProvider DSL. Klikněte pravým tlačítkem na `MBConsumer\Dsl\References` a pak klikněte na **Přidat odkaz**. Na kartě **Procházet** vyhledejte `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    To umožňuje vytvořit kód, který používá jiné DSL. Pokud chcete vytvořit odkazy na několik DSL, přidejte je také.

3. V diagramu definice DSL klikněte pravým tlačítkem na diagram a pak klikněte na **povolit ModelBus**. V dialogovém okně vyberte **Povolit tuto DSL pro využívání ModelBus**.

4. Ve třídě `ExampleElement`přidejte novou doménovou vlastnost `MBR`a v okno Vlastnosti nastavte typ na `ModelBusReference`.

5. Klikněte pravým tlačítkem na doménovou vlastnost v diagramu a pak klikněte na **Upravit ModelBusReference specifické vlastnosti**. V dialogovém okně vyberte **prvek modelu**.

    Nastavte na následující dialogové okno filtru souborů.

    `Provider File|*.provide`

    Podřetězec po "&#124;" je filtr pro dialogové okno Výběr souboru. Můžete ji nastavit tak, aby umožňovala použití souborů *.\*

    V seznamu **typ elementu modelu** zadejte názvy jedné nebo více doménových tříd v zprostředkovateli DSL (například Company. MBProvider. Task). Můžou být abstraktní třídy. Pokud seznam nezadáte, může uživatel nastavit odkaz na libovolný element.

6. Zavřete dialogové okno a **Transformujte všechny šablony**.

   Vytvořili jste DSL, která mohou obsahovat odkazy na prvky v jiném DSL.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Vytvořit odkaz na jiný soubor ModelBus v řešení

1. V řešení MBConsumer stisknutím kláves CTRL + F5. V projektu **MBConsumer\Debugging** se otevře experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Přidejte kopii Sample. Poskytněte projektu **MBConsumer\Debugging** . To je nezbytné, protože odkaz ModelBus musí odkazovat na soubor ve stejném řešení.

   1. Klikněte pravým tlačítkem na projekt ladění, přejděte na **Přidat**a pak klikněte na **existující položka**.

   2. V dialogovém okně **Přidat položku** nastavte filtr na **všechny soubory (\*.\*)** .

   3. Přejděte na `MBProvider\Debugging\Sample.provide` a pak klikněte na **Přidat**.

3. Otevřete `Sample.consume`.

4. Klikněte na jeden vzorový tvar a v okno Vlastnosti ve vlastnosti MBR klikněte na **[...]** . V dialogovém okně klikněte na tlačítko **Procházet** a vyberte možnost `Sample.provide`. V okně prvky typu úloh rozbalte a vyberte jeden z prvků.

5. Uložte soubor.

    (Zatím nezavírejte experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].)

   Vytvořili jste model, který obsahuje odkaz na prvek v jiném modelu ModelBus.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Přeložení odkazu ModelBus v textové šabloně

1. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete ukázkový textový soubor šablony. Nastavte jeho obsah následujícím způsobem.

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

    1. Musí být nastavené atributy `hostSpecific` a `inherits` direktivy `template`.

    2. Modelu oddělených příjemců přistupuje prostřednictvím procesor direktiv, který byl vygenerován v tomto DSL obvyklým způsobem.

    3. Direktivy sestavení a import musí mít pro přístup k ModelBus a typy zprostředkovatele DSL.

    4. Pokud víte, že mnoho MBRs jsou propojeny do stejného modelu, je lepší volat CreateAdapter pouze jednou.

2. Uložte šablonu. Ověřte, že výsledný textový soubor vypadá přibližně takto.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Přeložení odkazu ModelBus v obslužné rutiny gesta

1. Zavřete experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pokud je spuštěná.

2. Přidejte soubor, který je s názvem MBConsumer\Dsl\Custom.cs a nastavte jeho obsah následujícím.

    ```

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

3. Stisknutím kláves CTRL + F5.

4. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete `Debugging\Sample.consume`.

5. Dvakrát klikněte na jeden prvek.

     Pokud nastavíte MBR pro tento element otevře odkazovaným modelem a odkazovaný element je vybrán.

## <a name="see-also"></a>Viz také
 [Integrace modelů pomocí generování kódu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [a textových šablon T4](../modeling/code-generation-and-t4-text-templates.md)
