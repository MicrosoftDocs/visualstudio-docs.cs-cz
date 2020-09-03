---
title: Generování souborů z modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 832dc3f7fea959ff4d2834aba921cd16f1117b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666151"
---
# <a name="generate-files-from-a-uml-model"></a>Generování souborů z modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z modelu UML můžete generovat programový kód, schémata, dokumenty, prostředky a další artefakty libovolného druhu. Jednou z pohodlných metod generování textových souborů z modelu UML je použití [textových šablon](../modeling/code-generation-and-t4-text-templates.md). Ty umožňují vložit kód programu do textu, který chcete vygenerovat.

 Existují tři hlavní scénáře:

- [Generování souborů z příkazu nabídky](#Command) nebo gesta. Definujete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkaz, který je k dispozici v modelech UML.

- [Generování souborů z aplikace](#Application) Napíšete aplikaci, která čte modely UML a generuje soubory.

- [Generuje se v době návrhu](#Design). Model můžete použít k definování některých funkcí vaší aplikace a k vygenerování kódu, prostředků a tak dále v rámci vašeho [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení.

  Toto téma končí diskuzí o [tom, jak používat generování textu](#What). Další informace najdete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="generating-files-from-a-menu-command"></a><a name="Command"></a> Generování souborů z příkazu nabídky
 Můžete použít předběžné zpracování šablon textu v rámci příkazu nabídky UML. V rámci kódu textové šablony nebo v samostatné částečné třídě si můžete přečíst model, který je zobrazen v diagramu.

 Další informace o těchto funkcích si můžete přečíst v následujících tématech:

- [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md)

- [Procházení modelu UML](../modeling/navigate-the-uml-model.md)

  Přístup, který je znázorněn v následujícím příkladu je vhodný pro vygenerování textu z jednoho modelu při inicializaci operace z jednoho z diagramů modelu. Chcete-li zpracovat model v samostatném kontextu, zvažte použití [aplikace Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md) pro přístup k modelu a jeho prvkům.

### <a name="example"></a>Příklad
 Chcete-li spustit tento příklad, vytvořte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt rozšíření (VSIX). Název projektu, který je použit v tomto příkladu, je `VdmGenerator` . V souboru **source. extension. vsixmanifest** klikněte na možnost **Přidat obsah** a nastavte pole typ na **součást MEF** a zdrojovou cestu odkazující na aktuální projekt. Další informace o tom, jak nastavit tento typ projektu, naleznete v tématu [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

 Přidejte do projektu soubor C#, který obsahuje následující kód. Tato třída definuje příkaz nabídky, který se zobrazí v diagramu tříd UML.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace VdmGenerator
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  public class GenerateVdmFromClasses : ICommandExtension
  {
    [Import] public IDiagramContext DiagramContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      // Initialize the template with the Model Store.
      VdmGen generator = new VdmGen(
             DiagramContext.CurrentDiagram.ModelStore);
      // Generate the text and write it.
      System.IO.File.WriteAllText
        (System.IO.Path.Combine(
            Environment.GetFolderPath(
                Environment.SpecialFolder.Desktop),
            "Generated.txt")
         , generator.TransformText());
    }
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }
    public string Text
    { get { return "Generate VDM"; } }
  }
}
```

 Následující soubor je textová šablona. Generuje řádek textu pro každou třídu UML v modelu a řádek pro každý atribut v každé třídě. Kód pro čtení modelu je vložen do textu, oddělený `<# ... #>` .

 Chcete-li vytvořit tento soubor, klikněte pravým tlačítkem myši na projekt v Průzkumník řešení, přejděte na **Přidat**a klikněte na **Nová položka**. Vyberte **předzpracovaný textovou šablonu**. Název souboru pro tento příklad by měl být **VdmGen.TT**. Vlastnost **vlastního nástroje** souboru by měla být **TextTemplatingFilePreprocessor**. Další informace o předzpracovaných textových šablonách naleznete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

```
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#
   foreach (IClass classElement in store.AllInstances<IClass>())   {
#>
Type <#= classElement.Name #> ::
<#
     foreach (IProperty attribute in classElement.OwnedAttributes)     {
#>
       <#= attribute.Name #> : <#=
           attribute.Type == null ? ""
                                  : attribute.Type.Name #>
<#
     }   }
#>
```

 Textová šablona generuje částečnou třídu jazyka C#, která se stala součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. V samostatném souboru přidejte další částečnou deklaraci stejné třídy. Tento kód poskytuje šablonu s přístupem k úložišti modelů UML:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
namespace VdmGenerator
{
    public partial class VdmGen
    {
        private IModelStore store;
        public VdmGen(IModelStore s)
        { store = s; }
    }
}
```

 Chcete-li projekt otestovat, stiskněte klávesu **F5**. Spustí se nová instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . V této instanci otevřete nebo vytvořte model UML, který obsahuje diagram tříd. Přidejte do diagramu některé třídy a přidejte některé atributy do každé třídy. Klikněte pravým tlačítkem myši na diagram a pak klikněte na příkaz příklad `Generate VDM` . Příkaz vytvoří soubor `C:\Generated.txt` . Zkontrolujte tento soubor. Obsah by měl vypadat podobně jako následující text, ale zobrazí seznam vlastních tříd a atributů:

```
Type Class1 ::
          Attribute1 : int
          Attribute2 : string
Type Class2 ::
          Attribute3 : string
```

## <a name="generating-files-from-an-application"></a><a name="Application"></a> Generování souborů z aplikace
 Můžete vygenerovat soubory z aplikace, která čte model UML. Pro účely tohoto účelu je nejpružnější a robustní metoda přístupu k modelu a jeho prvkům [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 K načtení modelu můžete použít také základní rozhraní API a předat model do textových šablon pomocí stejných technik jako v předchozí části. Další informace o načítání modelu naleznete [v tématu čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="generating-files-at-design-time"></a><a name="Design"></a> Generování souborů v době návrhu
 Pokud má váš projekt standardní metodu interpretace UML jako kódu, můžete vytvořit textové šablony, které umožňují vygenerovat kód v rámci projektu z modelu UML. Obvykle byste měli mít řešení, které obsahuje projekt modelu UML, a jeden nebo více projektů pro kód aplikace. Každý projekt kódu může obsahovat několik šablon, které generují kód programu, prostředky a konfigurační soubory, a to na základě obsahu modelu. Vývojář může spustit všechny šablony kliknutím na tlačítko **transformace všech šablon** na panelu nástrojů Průzkumník řešení. Kód programu je obvykle generován ve formě dílčích tříd, aby bylo možné snadno integrovat ručně zapsané části.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Projekt tohoto druhu lze distribuovat ve formě šablony, aby každý člen týmu mohl vytvářet projekty, které generují kód z modelu stejným způsobem. Šablona je obvykle součástí balíčku rozšíření, který obsahuje omezení ověřování pro model, aby bylo zajištěno, že jsou splněny předběžné podmínky kódu generování.

### <a name="outline-procedure-for-generating-files"></a>Postup vytváření osnovy pro generování souborů

- Chcete-li přidat šablonu do projektu, vyberte možnost **šablona textu** v dialogovém okně Přidat nový soubor. Můžete přidat šablonu do většiny typů projektu, ale nikoli pro modelování projektů.

- Vlastnost vlastních nástrojů souboru šablony by měla být **hodnotu TextTemplatingFileGenerator**a přípona názvu souboru by měla být. tt.

- Šablona by měla obsahovat alespoň direktivu output:

     `<#@ output extension=".cs" #>`

     Nastavte pole rozšíření podle jazyka vašeho projektu.

- Chcete-li, aby generovaný kód ve vaší šabloně měl přístup k modelu, `<#@ assembly #>` direktivy Write pro sestavení potřebná ke čtení modelu UML. Použijte `ModelingProject.LoadReadOnly()` k otevření modelu. Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).

- Šablona se spustí, když ji uložíte a kliknete na **transformovat všechny šablony** na panelu nástrojů Průzkumník řešení.

- Další informace o tomto typu šablony naleznete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

- V typickém projektu budete mít několik šablon, které generují různé soubory ze stejného modelu. První část každé šablony bude stejná. Chcete-li omezit tuto duplicitu, přesuňte společné části do samostatného textového souboru a potom ji vyvolejte pomocí direktivy `<#@include file="common.txt"#>` v každé šabloně.

- Můžete také definovat specializovaný procesor direktiv, který vám umožní zadat parametry procesu generování textu. Další informace najdete v tématu [Přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md).

### <a name="example"></a>Příklad
 Tento příklad generuje třídu jazyka C# pro každou třídu UML ve zdrojovém modelu.

##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Nastavení řešení sady Visual Studio pro tento příklad

1. Vytvoření diagramu tříd UML v projektu modelování v novém řešení.

   1. V nabídce **Architektura** klikněte na **Nový diagram**.

   2. Vyberte **Diagram tříd UML**.

   3. Podle pokynů vytvořte nový projekt řešení a modelování.

   4. Přidejte do diagramu některé třídy přetažením nástroje třídy UML ze sady nástrojů.

   5. Uložte soubor.

2. Vytvořte projekt v jazyce C# nebo Visual Basic ve stejném řešení.

   - V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, přejděte na **Přidat**a pak klikněte na **Nový projekt**. V části **Nainstalované šablony**klikněte na **Visual Basic** nebo **Visual C#** a pak vyberte typ projektu, jako je například **Konzolová aplikace**.

3. Přidejte soubor s prostým textem do projektu C# nebo Visual Basic. Tento soubor bude obsahovat kód, který je sdílen, pokud chcete vytvořit několik textových šablon.

   - V Průzkumník řešení klikněte pravým tlačítkem myši na projekt, přejděte na **Přidat**a klikněte na **Nová položka**. Vyberte **textový soubor**.

     Vložte text, který je zobrazen v následující části.

4. Přidejte textový soubor šablony do projektu C# nebo Visual Basic.

   - V Průzkumník řešení klikněte pravým tlačítkem myši na projekt, přejděte na **Přidat**a klikněte na **Nová položka**. Vyberte **textovou šablonu**.

     Vložte kód, který následuje, do textového souboru šablony.

5. Uložte textový soubor šablony.

6. Zkontrolujte kód v souboru pobočky. Měl by obsahovat třídu pro každou třídu UML v modelu.

   1. V Visual Basic projektu klikněte na tlačítko **Zobrazit všechny soubory** na panelu nástrojů Průzkumník řešení.

   2. Rozbalte uzel soubor šablony v Průzkumník řešení.

#### <a name="content-of-the-shared-text-file"></a>Obsah sdíleného textového souboru
 V tomto příkladu se soubor nazývá SharedTemplateCode.txt a je ve stejné složce jako textové šablony.

```
<# /* Common material for inclusion in my model templates */ #>
<# /* hostspecific allows access to the Visual Studio API */ #>
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>
<#+  // Note this is a Class Feature Block
///<summary>
/// Text templates are run in a common AppDomain, so
/// we can cache the model store that we find.
///</summary>
private IModelStore StoreCache
{
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }
}
private bool CacheIsOld()
{
    DateTime? dt = AppDomain.CurrentDomain
           .GetData("latestAccessTime") as DateTime?;
    DateTime t = dt.HasValue ? dt.Value : new DateTime();
    DateTime now = DateTime.Now;
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);
    return now.Subtract(t).Seconds > 3;
}

///<summary>
/// Find the UML modeling project in this solution,
/// and load the model.
///</summary>
private IModelStore ModelStore
{
  get
  {
    // Avoid loading the model for every template:
    if (StoreCache == null || CacheIsOld())
    {
      // Use Visual Studio API to find modeling project:
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
      EnvDTE.Project project = null;
      foreach (EnvDTE.Project p in dte.Solution.Projects)
      {
        if (p.FullName.EndsWith(".modelproj"))
        {
          project = p;
          break;
        }
      }
      if (project == null) return null;

      // Load UML model into this AppDomain
      // and access model store:
      IModelingProjectReader reader =
           ModelingProject.LoadReadOnly(project.FullName);
      StoreCache = reader.Store;
    }
    return StoreCache;
  }
}
#>
```

#### <a name="content-of-the-text-template-file"></a>Obsah souboru textové šablony
 Následující text je umístěn v souboru **. TT** . Tento příklad generuje třídy v souboru C# z tříd UML v modelu. Můžete však vygenerovat soubory libovolného typu. Jazyk generovaného souboru nesouvisí s jazykem, ve kterém je napsán kód textové šablony.

```
<#@include file="SharedTemplateCode.txt"#>
<#@ output extension=".cs" #>
namespace Test{
<#
      foreach (IClass c in ModelStore.AllInstances<IClass>())
      {
#>
   public partial class <#=c.Name#>
   {   }
<#
      }
#>
}
```

## <a name="how-to-use-text-generation"></a><a name="What"></a> Jak používat generování textu
 Skutečná síla modelování se získává při použití modelů k návrhu na úrovni požadavků nebo architektury. Můžete použít textové šablony k provedení některých úkolů převodu nápadů na vysoké úrovni do kódu. V mnoha případech to nevede k korespondenci mezi prvky v modelech a třídách UML nebo v jiných částech kódu programu.

 Navíc transformace závisí na vaší doméně problému; mezi modely a kódem neexistuje žádné obecné mapování.

 Tady je několik příkladů generování kódu z modelů:

- **Produktové řádky**. Společnost Fabrikam, Inc. sestaví a instaluje systémy zpracování zavazadel na letištích. Většina softwaru je velmi podobná mezi jednou instalací a další, ale konfigurace softwaru závisí na tom, jaké strojní vybavení pro zpracování balíčku je nainstalované, a na tom, jak se tyto části vzájemně spojují s pásy přes pás. Na začátku smlouvy si Analytiki společnosti Fabrikam projednávají požadavky se správou letišť a zachytí plán hardwaru pomocí diagramu činnosti UML. Z tohoto modelu vygeneruje vývojový tým konfigurační soubory, kód programu, plány a dokumenty uživatele. Dokončí práci ručními dodatky a úpravami kódu. Když získají zkušenosti z jedné úlohy do další, rozšíří rozsah vygenerovaného materiálu.

- **Vzory**. Vývojáři ve společnosti Contoso, Ltd často vytvářejí weby a navrhují navigační schéma pomocí diagramů tříd UML. Každá webová stránka je reprezentována třídou a přidružení představují navigační odkazy. Vývojáři generují mnohem z kódu webu z modelu. Každá webová stránka odpovídá několika třídám a záznamům souborů prostředků.  Tato metoda má výhody, které konstrukce každé stránky odpovídá jednomu vzoru, takže je spolehlivější a pružnější než ruční zápis kódu. Vzor je v šablonách generování, zatímco model je použit k zachycení proměnných aspektů.

- **Schémata**. Humongous pojištění má tisíce systémů po celém světě. Tyto systémy využívají různé databáze, jazyky a rozhraní. Tým centrální architektury zveřejňuje interně modely obchodních konceptů a procesů. Z těchto modelů místní týmy generují části jejich schémat databáze a výměny, deklarace v programovém kódu atd. Grafická prezentace modelů pomáhá týmům diskutovat o návrzích. Týmy vytvářejí více diagramů, které zobrazují podmnožiny modelu, které platí pro různé obchodní oblasti. Používají také barvu k zvýraznění oblastí, které se mohou změnit.

## <a name="important-techniques-for-generating-artifacts"></a>Důležité techniky pro generování artefaktů
 V předchozích příkladech se modely používají pro nejrůznější obchodní účely a interpretace prvků modelování, jako jsou třídy a aktivity, se liší od jedné aplikace k druhé. Následující techniky jsou užitečné, když generujete artefakty z modelů.

- **Profily**: I v rámci jedné obchodní oblasti se interpretace typu prvku může lišit. Například v diagramu webu mohou některé třídy představovat webové stránky a jiné reprezentují bloky obsahu. Aby si uživatelé mohli snadno zaznamenat tato odlišná nastavení, definovat stereotypy. Stereotypy také umožňují připojit další vlastnosti, které se vztahují na prvky daného druhu. Stereotypy jsou zabaleny v rámci profilů. Další informace najdete v tématu [Definování profilu pro rozšiřování UML](../modeling/define-a-profile-to-extend-uml.md).

     V kódu šablony je snadné přistupovat ke stereotypům, které jsou definovány v objektu. Příklad:

    ```
    public bool HasStereotype(IClass c, string profile, string stereo)
    { return c.AppliedStereotypes.Any
       (s => s.Profile == profile && s.Name == stereo ); }
    ```

- **Omezené modely**. Ne všechny modely, které lze vytvořit, jsou platné pro každý účel. Například v modelech zavazadel společnosti Fabrikam by byl nesprávný pracovní stůl bez odchozího dopravníku. Můžete definovat funkce ověřování, které uživatelům pomůžou tato omezení sledovat. Další informace najdete v tématu [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).

- **Zachovat ruční změny**. Z modelu lze vygenerovat pouze některé ze souborů řešení. Ve většině případů je potřeba, abyste mohli přidat nebo upravit generovaný obsah ručně. Je však důležité, aby při opětovném spuštění transformace šablony byly zachovány tyto ruční změny.

     Kde vaše šablony generují kód v [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] jazycích, měly by generovat částečné třídy, aby mohli vývojáři přidat metody a kód. Je také užitečné vygenerovat každou třídu jako dvojici: abstraktní základní třídu, která obsahuje metody, a třídu dědění, která obsahuje pouze konstruktor. To umožňuje vývojářům přepsat metody. Aby bylo možné inicializaci přepsat, je provedeno v samostatné metodě namísto v konstruktorech.

     Kde Šablona generuje XML a jiné typy výstupu, může být obtížnější zachovat ruční obsah oddělený od generovaného obsahu. Jedna z metod je vytvořit úlohu v procesu sestavení, která kombinuje dva soubory. Další metodou je, aby vývojáři upravili místní kopii šablony pro generování.

- **Přesune kód do samostatných sestavení**. V šablonách nedoporučujeme psát velké tělo kódu. Je vhodnější zachovat generovaný obsah oddělený od výpočtu a textové šablony nejsou dobře podporovány pro úpravy kódu.

     Místo toho, pokud je třeba provést zásadní výpočty pro generování textu, sestavte tyto funkce v samostatném sestavení a zavolejte své metody ze šablony.
