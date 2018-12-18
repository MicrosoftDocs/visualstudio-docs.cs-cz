---
title: Generování souborů z modelu UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: afbb81a67d8d5f8f587979ab8adca4251562072a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804534"
---
# <a name="generate-files-from-a-uml-model"></a>Generování souborů z modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z modelu UML můžete generovat kód programu, schémata, dokumenty, prostředky a jiné artefakty jakéhokoli druhu. Jeden pohodlný způsob generování textových souborů z modelu UML je použití [textových šablon](../modeling/code-generation-and-t4-text-templates.md). Ty umožňují vložit kód programu uvnitř text, který chcete vygenerovat.  
  
 Existují tři hlavní scénáře:  
  
- [Generování souborů z příkazu nabídky](#Command) nebo gesta. Můžete definovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkaz, který je k dispozici v modelech UML.  
  
- [Generování souborů z aplikace](#Application). Můžete psát aplikace, která čte modely UML a generuje soubory.  
  
- [Generuje se při návrhu](#Design). Pomocí modelu můžete definovat některé funkce vaší aplikace a generovat kód, prostředky, a tak dále v rámci vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení.  
  
  Toto téma končí diskusi o [použití generování textu](#What). Další informace najdete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).  
  
##  <a name="Command"></a> Generování souborů z příkazu nabídky  
 Můžete použít předzpracování textové šablony v rámci příkazu nabídky UML. V rámci kódu textové šablony, nebo v samostatné částečné třídy si můžete přečíst model, který je zobrazit v diagramu.  
  
 Další informace o těchto funkcích najdete v následujících tématech:  
  
- [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [Procházení modelu UML](../modeling/navigate-the-uml-model.md)  
  
  Přístup ukázáno v následujícím příkladu je vhodný pro generování textu z jednoho modelu při zahájení operace z jednoho z diagramech modelů. Ke zpracování modelu v samostatné kontextu, zvažte použití [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md) pro přístup k modelu a jeho elementy.  
  
### <a name="example"></a>Příklad  
 Chcete-li spustit tento příklad, vytvořte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension (VSIX) projektu. Název projektu, který se používá v tomto příkladu je `VdmGenerator`. V **source.extension.vsixmanifest** souboru, klikněte na tlačítko **přidat obsah** a nastavte je v poli Typ **Komponenta MEF** a zdrojovou cestu odkazující na aktuální projekt. Další informace o tom, jak nastavit tento typ projektu, naleznete v tématu [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
 Přidejte do projektu soubor jazyka C#, která obsahuje následující kód. Tato třída definuje příkaz nabídky, který se zobrazí v diagramu tříd UML.  
  
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
  
 Tento soubor je textové šablony. Vygeneruje řádek textu pro každou třídu modelu UML v modelu a řádek pro jednotlivé atributy v každé třídě. Kód pro čtení modelu je vložený v textu, které jsou odděleny `<# ... #>`.  
  
 K vytvoření tohoto souboru, klikněte pravým tlačítkem na projekt v Průzkumníku řešení, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**. Vyberte **Předzpracované textové šablony**. Název souboru v tomto příkladu by měl být **VdmGen.tt**. **Custom Tool** vlastnost souboru by měla být **TextTemplatingFilePreprocessor**. Další informace o Předzpracované textové šablony najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
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
  
 Textová Šablona generuje C# částečnou třídu, která se stane součástí z vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. V samostatném souboru přidejte jiná částečná deklarace stejné třídy. Tento kód obsahuje šablony s přístupem k úložišti modelu UML:  
  
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
  
 Chcete-li testovací projekt, stiskněte **F5**. Novou instanci třídy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se spustí. V tomto případě otevřete nebo vytvořte model UML, který obsahuje diagram třídy. Přidat některé třídy do diagramu a přidat některé atributy pro každou třídu. Klikněte pravým tlačítkem myši v diagramu a potom klikněte na příkaz v příkladu `Generate VDM`. Příkaz vytvoří soubor `C:\Generated.txt`. Zkontrolujte, zda tento soubor. Jeho obsah by měl vypadat podobně jako následující text, ale zobrazí se seznam vlastní třídy a atributy:  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
##  <a name="Application"></a> Generování souborů z aplikace  
 Generování souborů z aplikace, který čte UML model. Pro tento účel je nejvíce pružnější a odolnější metoda přístupu k modelu a jeho prvky [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Můžete také použít rozhraní API základní načíst model a být model předán do textových šablon pomocí stejné postupy jako v předchozí části. Další informace o načtení modelu najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Design"></a> Generování souborů v době návrhu  
 Pokud má váš projekt standardní způsob interpretace UML jako kód, můžete vytvořit textových šablon, které vám umožňují generování kódu v rámci svého projektu z modelu UML. Obvykle by mít řešení, které obsahuje projekt modelu UML a jeden nebo více projektů pro kód aplikace. Každý Kódový projekt může obsahovat několik šablon, které generují program kód, prostředky a konfigurační soubory, na základě obsahu modelu. Vývojář můžete spustit všechny šablony kliknutím **Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení. Kód programu je obvykle generují v podobě částečné třídy, aby byl snadno integrovat ručně psanou částí.  
  
 A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu tento typ lze distribuovat ve formě šablonu, tak, aby každý člen týmu je schopna vytvářet projekty, které generují kód z modelu stejným způsobem. Šablona je obvykle součást rozšíření balíčku, který obsahuje omezení ověření v modelu, který má Ujistěte se, že jsou splněné předpoklady generování kódu.  
  
### <a name="outline-procedure-for-generating-files"></a>Popisují postup pro generování souborů  
  
-   Chcete-li přidat šablonu do projektu, **textové šablony** v dialogovém okně Přidat nový soubor. Přidat šablonu pro většinu typů projektu, ale ne projekty modelování.  
  
-   Nástroje pro vlastní vlastnost souboru šablony by měla být **TextTemplatingFileGenerator**, a příponu názvu souboru by měla být .tt.  
  
-   Šablona by měla obsahovat alespoň – direktiva output:  
  
     `<#@ output extension=".cs" #>`  
  
     Nastavte pole rozšíření podle jazyka vašeho projektu.  
  
-   Chcete-li povolit generování kódu v šabloně pro přístup k modelu, napište `<#@ assembly #>` direktivy pro sestavení potřebná pro čtení modelu UML. Použití `ModelingProject.LoadReadOnly()` a otevřete model. Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Šablona se spustí, až uložíte a po kliknutí na **Transformovat všechny šablony** v panelu nástrojů Průzkumníka řešení.  
  
-   Další informace o tomto typu šablony najdete v tématu [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
-   Obvyklou pro projekty je třeba několik šablon, které generují různé soubory ze stejného modelu. První část každé šablony budou stejné. Snížit tyto duplikace, přesuňte společné části do samostatných textového souboru a pak ho vyvolat pomocí direktivy `<#@include file="common.txt"#>` v každé šabloně.  
  
-   Můžete také definovat specializované procesoru direktiv, který umožňuje zadat parametry pro proces generování textu. Další informace najdete v tématu [přizpůsobení transformace textu T4](../modeling/customizing-t4-text-transformation.md).  
  
### <a name="example"></a>Příklad  
 Tento příklad vygeneruje třídy C# pro každou třídu modelu UML v modelu zdroje.  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Nastavit řešení sady Visual Studio pro účely tohoto příkladu  
  
1. Vytvoření diagramu tříd UML v projektu modelování v novém řešení.  
  
   1.  V **architektura** nabídky, klikněte na tlačítko **nový Diagram**.  
  
   2.  Vyberte **Diagram tříd UML**.  
  
   3.  Postupujte podle pokynů k vytvoření nového řešení a modelování projektu.  
  
   4.  Přidáte některé třídy do diagramu přetažením nástroj třída UML z panelu nástrojů.  
  
   5.  Uložte soubor.  
  
2. Vytvoření projektu jazyka C# nebo Visual Basic ve stejném řešení.  
  
   -   V Průzkumníku řešení klikněte pravým tlačítkem na řešení, přejděte na **přidat**a potom klikněte na tlačítko **nový projekt**. V části **nainstalované šablony**, klikněte na tlačítko **jazyka Visual Basic** nebo **Visual C#,** a pak vyberte typ projektu, jako je například **konzolovou aplikaci**.  
  
3. C# nebo Visual Basic projektu přidáte soubor s prostým textem. Tento soubor bude obsahovat kód, který je sdílen, pokud chcete zadat několik textových šablon.  
  
   - V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**. Vyberte **textový soubor**.  
  
     Vložte text, který je uvedené v následující části.  
  
4. C# nebo Visual Basic projektu přidáte soubor textové šablony.  
  
   - V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom klikněte na tlačítko **nová položka**. Vyberte **textové šablony**.  
  
     Vložte kód, který následuje do souboru textové šablony.  
  
5. Uložte soubor textové šablony.  
  
6. Prozkoumejte kód v souboru pobočkách. Měl by obsahovat třídu pro každou třídu modelu UML v modelu.  
  
   1.  V projektu jazyka Visual Basic, klikněte na tlačítko **zobrazit všechny soubory** v panelu nástrojů Průzkumníka řešení.  
  
   2.  Rozbalte uzel soubor šablony v Průzkumníku řešení.  
  
#### <a name="content-of-the-shared-text-file"></a>Obsah sdílený textového souboru  
 V tomto příkladu soubor se nazývá SharedTemplateCode.txt a je ve stejné složce jako textové šablony.  
  
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
 Následující text je umístěn v **.tt** souboru. Tento příklad vygeneruje třídy v souboru C# z tříd UML v modelu. Však můžete generovat soubory libovolného typu. Jazyk vygenerovaný soubor se nevztahuje na jazyk, ve kterém je napsán kód textové šablony.  
  
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
  
##  <a name="What"></a> Jak používat generování textu  
 Skutečná síla modelování získáte při použití modelů pro návrh na úrovni požadavků nebo architektury. Textové šablony můžete provést určitou část práce převodu vysoké úrovně své nápady do kódu. V mnoha případech to nenastane shoda mezi prvky v modelech UML a třídy nebo jiných částí kódu programu.  
  
 Kromě toho transformace závisí na vaší domény problém. neexistuje žádný univerzální mapování mezi modely a kódu.  
  
 Tady jsou některé příklady generování kódu z modelů:  
  
-   **Produktové řady**. Fabrikam, Inc. vytvoří a nainstaluje letiště sobě systémy zpracování. Velká část softwaru je velmi podobné mezi jedna instalace a další, ale konfigurace softwaru závisí na jaké kontejner objektů a dat zpracování strojů je nainstalován, a jak tyto části jsou propojeny pomocí dopravní pásy. Na začátku kontrakt analytici společnosti Fabrikam požadavky se správou letišti a zachycení plán hardwaru pomocí diagram činností UML. Z tohoto modelu vývojový tým generuje konfigurační soubory, programový kód, plány a dokumenty uživatele. Dokončení práce podle ruční přidání a úpravy kódu. Jak získávají prostředí z jednoho projektu do druhého, jejich rozšíření oboru generované materiálu.  
  
-   **Vzory**. Vývojáři ve společnosti Contoso, Ltd často vytvářet weby a navrhnout navigační schéma používání diagramů tříd UML. Každá webová stránka je reprezentován třídou a asociace reprezentují navigační odkazy. Vývojáři generovat velkou část kódu webové stránky z modelu. Každé webové stránky odpovídá několik tříd a položkách souboru prostředků.  Tato metoda má výhody, které konstrukce každou stránku odpovídá jedné vzor, spolehlivé a flexibilní než ručně psanou kódu. Vzor je v generování šablon, ale model se používá k zachycení proměnné aspekty.  
  
-   **Schémata**. ABC pojištění obsahuje tisíce systémy po celém světě. Tyto systémy pomocí různých databází, jazyků a rozhraní. Centrální architektura týmu publikuje interně modely obchodních konceptů a procesů. Z těchto modelů místní týmy generovat část jejich databáze a výměnu schémata, deklarace v programovém kódu a tak dále. Grafické znázornění modely pomáhá týmům projednat návrhy. Týmy vytvořit více diagramů, které ukazují podmnožiny modelu, které se vztahují na různé obchodní oblasti. Také používají barevné zvýraznění oblastí může změnit.  
  
## <a name="important-techniques-for-generating-artifacts"></a>Důležité technik pro generování artefaktů  
 V předchozích příkladech se používají modely pro různé účely závislé na obchodní a výklad modelování prvků, jako jsou třídy a aktivity se liší od jedné aplikace do jiné. Následující postupy jsou užitečné při generování artefakty z modelů.  
  
-   **Profily**. Dokonce i v rámci jednoho pracovního prostoru se může lišit výklad typ elementu. Například v diagramu webu některé třídy může představovat webových stránek a dalších představují bloky obsahu. Chcete-li usnadnit uživatelům zaznamenat tyto rozdíly, definujte stereotypy. Stereotypy také umožňují připojit další vlastnosti, které se vztahují na elementy tohoto typu. V rámci profily jsou zabaleny stereotypy. Další informace najdete v tématu [definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md).  
  
     V kódu šablony se snadno k datům Stereotypy, které jsou definovány pro objekt. Příklad:  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
-   **Omezené modely**. Ne všechny modely, které můžete vytvořit jsou platné pro všechny účely. Například v modelech sobě letiště společnosti Fabrikam, je nesprávná mít helpdesku vrácení se změnami bez odchozí dopravní. Můžete definovat ověřovací funkce, které pomáhají uživatelům dodržovat těchto omezení. Další informace najdete v tématu [definovat omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
-   **Zachovat ruční změny**. Pouze některé soubory řešení mohou být generovány z modelu. Ve většině případů musíte být schopni přidat nebo upravit vygenerovaný obsah ručně. Je ale důležité, že tyto ručních změn by měla být zachována při dalším spuštění transformace šablony.  
  
     Pokud vaše šablony generování kódu v [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] jazyky, by měl generovat částečné třídy tak, aby vývojáři mohou přidat, metody a kódu. Je také užitečné vygenerovat každá třída jako dvojice: abstraktní základní třídu obsahující metody a dědičné třídě, která obsahuje pouze konstruktor. To umožňuje vývojářům přepsání metod. Povolit pro inicializaci přepsání, to se provádí v samostatné metodě, místo v konstruktory.  
  
     Pokud šablonu generuje XML a další typy výstupu, může být obtížné zachovat ruční obsah odděleně od vygenerovaný obsah. Jedním ze způsobů je k vytvoření úlohy v procesu sestavení, která kombinuje dva soubory. Jinou metodou je pro vývojáře, chcete-li upravit místní kopii generování šablony.  
  
-   **Přesunout kód do samostatné sestavení**. Nedoporučujeme zápis velké části kódu v šablonách. Doporučuje se oddělovat generovaný obsah z výpočtu a textové šablony nejsou podporovány také pro úpravy kódu.  
  
     Místo toho pokud je nutné provést značné výpočty vygenerování textu, vytvoření těchto funkcí v samostatném sestavení a volat jeho metody ze šablony.



