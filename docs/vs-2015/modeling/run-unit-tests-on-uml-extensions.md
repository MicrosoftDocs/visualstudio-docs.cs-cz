---
title: Spouštění testování částí v rozšířeních UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6ba485b40beb82db9ea8cfe573cb6d9e6742ecea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817318"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Spouštění testování částí v rozšířeních UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K udržení stabilní prostřednictvím po sobě jdoucích změn kódu, doporučujeme, abyste zápis testů jednotek a provádět jako součást procesu regulárního sestavení. Další informace najdete v tématu [svůj kód testu jednotek](../test/unit-test-your-code.md). Nastavení testů pro rozšíření modelování Visual Studio, budete potřebovat několik důležitých informací. V souhrnu:  
  
- [Nastavení testu jednotek pro rozšíření VSIX](#Host)  
  
   Spusťte testy s hostitelského adaptéru VS IDE. Předpona každou metodu testu `[HostType("VS IDE")]`. Spuštění tohoto hostitelského adaptéru [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] při spuštění testů.  
  
- [Přístup k DTE a modelstore modelu](#DTE)  
  
   Obvykle budete muset otevřít modelu a jeho diagramy a přístup `IModelStore` inicializace testu.  
  
- [Otevření diagramu modelu](#Opening)  
  
   Můžete přetypovat `EnvDTE.ProjectItem` do a z `IDiagramContext`.  
  
- [Provádění změn ve vlákně uživatelského rozhraní](#UiThread)  
  
   Testy, které provádět změny v úložišti modelu se musí provádět ve vlákně uživatelského rozhraní. Můžete použít `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` to.  
  
- [Testování příkazy, gesta a další součásti MEF](#MEF)  
  
   K testování komponent MEF, musí explicitně připojit jejich importované vlastností hodnoty.  
  
  Tyto body jsou podrobně uvedeno v následující části.  
  
  Ukázka rozšíření UML jednotek testování najdete na galerii vzorových příkladů kódu na [UML – rychlé položku pomocí textu](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).  
  
## <a name="requirements"></a>Požadavky  
 Zobrazit [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="Host"></a> Nastavení testu jednotek pro rozšíření VSIX  
 Metody v rozšíření modelování obvykle pracovat diagram, který je již otevřen. Metody jako například použít importů MEF **IDiagramContext** a **ILinkedUndoContext**. Testovací prostředí, musíte nastavit kontext, před spuštěním testů.  
  
#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Nastavení, který se spustí v testu jednotek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1.  Vytvořte projekt rozšíření UML a projekt testu jednotek.  
  
    1.  **Projekt rozšíření UML.** Obvykle to vytvoříte pomocí příkazu, gesta nebo šablony projektu ověřování. Viz například [definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
    2.  **Projekt testování částí.** Další informace najdete v tématu [svůj kód testu jednotek](../test/unit-test-your-code.md).  
  
2.  Vytvoření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které obsahuje projekt modelování UML. Toto řešení bude používat jako počáteční stav testů. By měla být oddělena od řešení, ve kterém píšete rozšíření UML a jeho testování částí. Další informace najdete v tématu [vytvořit modelování projektů a diagramů UML](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
3.  **V projektu rozšíření UML**, upravíte soubor .csproj jako text a ujistěte se, že tyto řádky zobrazit `true`:  
  
    ```  
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>  
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>  
    ```  
  
     Chcete-li upravit soubor .csproj jako text, zvolte **uvolnit projekt** v místní nabídce projektu v Průzkumníku řešení. Klikněte na tlačítko **upravit. .csproj**. Po úpravě textu, zvolte **znovu načíst projekt**.  
  
4.  V projektu rozšíření UML, přidejte následující řádek, který **Properties\AssemblyInfo.cs**. To umožňuje testování částí pro přístup k metodám, které chcete testovat:  
  
    ```csharp  
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
    ```  
  
5.  **V projektu testování částí**, přidejte následující odkazy na sestavení:  
  
    -   *Projekt pro rozšíření UML*  
  
    -   **EnvDTE.dll**  
  
    -   **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**  
  
    -   **Microsoft.VisualStudio.ComponentModelHost.dll**  
  
    -   **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**  
  
    -   **Microsoft.VisualStudio.Uml.Interfaces.dll**  
  
    -   **Microsoft.VSSDK.TestHostFramework.dll**  
  
6.  Předpona atributu `[HostType("VS IDE")]` do jednotlivých testovacích metod, včetně metod inicializace.  
  
     Tím se zajistí, že test bude spuštěn v experimentální instanci sady Visual Studio.  
  
##  <a name="DTE"></a> Přístup k DTE a modelstore modelu  
 Zápis metody k otevření projektu modelování v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Obvykle chcete otevřít řešení pouze jednou v každém testovacím běhu. Metoda spustit jenom jednou, předpona metody `[AssemblyInitialize]` atribut. Nezapomeňte, že potřebujete atribut [HostType ("VS IDE")] v jednotlivých testovacích metod.  Příklad:  
  
```csharp  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
  
namespace UnitTests  
{  
  [TestClass]  
  public static class TestSetup  
  {  
  
    // Location of a VS Solution that defines an initial state for your tests:  
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";  
    // Name of a modeling project within the test solution:  
    private const string testModelingProjectName = "MyTestModel";  
  
    // Make Solution and IModelStore available to test methods:  
    public static Solution ModelSolution = null;  
    public static IModelingProject ModelingProject = null;  
    public static IModelStore ModelStore = null;  
  
    // This method will be performed once to initialize tests for this assembly:  
    [AssemblyInitialize]   
    [HostType("VS IDE")]  
    public static void OpenTestModelingProject(TestContext testContext)  
    {  
      // To make sure that we always start the tests in the same state,  
      // copy the test solution from a read-only directory:  
      // TODO: copy test solution folder.  
  
      // Open a solution that is the initial state for your tests:  
      ModelSolution = VsIdeTestHostContext.Dte.Solution;  
      ModelSolution.Open(testSolutionFilePath);  
  
      // Find the ModelingProject and IModelStore:  
      foreach (Project project in ModelSolution.Projects)  
      {  
        // http://msdn.microsoft.com/library/ee791691.aspx  
        ModelingProject = project as IModelingProject;  
        if (ModelingProject != null)  
        {  
          // This is a modeling project.  
          ModelStore = ModelingProject.Store;  
          break;  
        }  
        // else this is another kind of project.  
      }  
  
      Assert.IsNotNull(ModelSolution, "VS solution not found");  
      Assert.IsNotNull(ModelStore, "Modeling store not found");  
    }  
    [AssemblyCleanup]  
    public static void RemoveTestSolution ()  
    {  
      // TODO: Remove copied test solution directory.  
    }  
  }  
}  
  
```  
  
 Pokud instance <xref:EnvDTE.Project?displayProperty=fullName> představuje projekt modelování a lze jej přetypovat do a z <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.IModelingProject>.  
  
##  <a name="Opening"></a> Otevření diagramu modelu  
 Pro každý test nebo třída testů je obvykle chcete pracovat Otevřít diagram. V následujícím příkladu `[ClassInitialize]` atribut, který spustí tuto metodu před jinými metodami v této testovací třídy. Znovu nezapomeňte, že potřebujete každou metodu testu atribut [HostType ("VS IDE")]:  
  
```csharp  
//   
private IDiagram diagram;  
// This class contains unit tests:  
[TestClass]  
public class MyTestClass  
{  
  // Map filenames to open diagram files:  
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();  
  
  // This method will be called once for this test class:  
  [ClassInitialize]  
  [HostType("VS IDE")]  
  public static void TestClassInitialize(TestContext testContext)  
  {  
    // Open all the diagrams in the model:  
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)  
    {  
      // Get the filename of the principal file (not the .layout subsidiary):  
      string fileName = item.FileNames[0];  
      // If this is a model diagram file, it can be cast to IDiagramContext:  
      IDiagramContext modelingItem = item as IDiagramContext;  
      if (modelingItem != null)  
      {  
        IDiagram diagram = modelingItem.CurrentDiagram;  
        if (diagram == null)  
        {  
          // Diagram is closed. Open it:  
          item.Open().Activate();  
          diagram = modelingItem.CurrentDiagram;  
        }  
        diagrams[fileName] = diagram;  
      }  
      // else item is not a model diagram.  
    }  
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");  
  }  
// Insert test methods here ...  
}  
  
```  
  
##  <a name="UiThread"></a> Provádění změn modelu ve vlákně uživatelského rozhraní  
 Pokud testy nebo metody v rámci testu, provést změny modelu úložiště, musíte je spouštět ve vlákně uživatelského rozhraní. Pokud to neprovedete, může se zobrazit `AccessViolationException`. Ve volání metody Invoke uvést kód testovací metody:  
  
```  
using System.Windows.Forms;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
 ...  
    [TestMethod]  
    [HostType("VS IDE")]  
    public void MyTest1()  
    {  
      // Store operations must run in the UI thread:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        SetupTestState(TestSetup.ModelStore, diagram);  
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);  
      });  
    }  
```  
  
##  <a name="MEF"></a> Testování příkazu, gesta a další součásti MEF  
 Deklarace vlastností, které mají používat komponent MEF `[Import]` atribut a jehož hodnoty jsou nastavené podle jejich hostitelů. Tyto vlastnosti obvykle zahrnují IDiagramContext, SVsServiceProvider a ILinkedUndoContext. Pokud testujete metodu, která používá některou z těchto vlastností, je nutné nastavit jejich hodnoty před spuštěním testované metody. Například, pokud jste napsali rozšíření příkazu podobné tento kód:  
  
```  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class MyCommand : ICommandExtension  
  {  
    [Import] IDiagramContext context { get; set; }  
    [Import]   
Microsoft.VisualStudio.Shell.SVsServiceProvider  
serviceProvider {get;set;}  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      DoCommand();  
    }  
    private void DoCommand()  
    {  
      IDiagram diagram = context.CurrentDiagram;  
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))  
      { ... }}}  
  
```  
  
 Importované vlastnosti můžete nastavit následujícím způsobem:  
  
```  
  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ComponentModelHost;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
...  
    [TestMethod]   
    [HostType("VS IDE")]  
    public void Test1()  
    {  
      // Create an instance of the class under test:  
      MyCommand myCommand = new MyCommand();  
      // Get the components service:  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
        .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Set the imported properties of the instance under test:  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);  
      // Call method(s) under test:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        myCommand.DoCommand();  
      });  
...}  
```  
  
 Pokud chcete otestovat metodu, která přebírá jako parametr importovanou vlastnost, pak můžete importovat vlastnost do vaší testovací třídy a použít `SatisfyImportsOnce` do testovací instance. Příklad:  
  
```  
  
using System.ComponentModel.Composition;  
...  
  [TestClass]  
  public class MyTestClass  
  {  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called before each test method:  
    [TestInitialize, HostType("VS IDE")]   
    public void TestInitializer()  
    {  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
            .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(this);  
    }  
    [TestMethod, HostType("VS IDE")]  
    public void Test2()  
    {   
     UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
      // Pass context items to class under test:  
      Class1 item1 = new Class1(this.linkedUndoContext);  
      item1.Method1(); // Can use linkedUndoContext  
     });  
   }  
}  
  
```  
  
 V tomto příkladu jsou dva atributy u každé zkušební metody kombinovat pro usnadnění práce do jednoho řádku.  
  
## <a name="access-from-tests-to-private-methods-and-variables"></a>Přístup z testů k privátní metody a proměnné  
 Někdy chcete otestovat metodu, která je privátní, nebo chcete ověřit stav pole, které je privátní, před a po provedení metody v rámci testu. To představuje problém, protože jsou testy v samostatném sestavení na třídy v rámci testu. Existuje několik taktika, které můžete zvážit, včetně následujících:  
  
 Testování pouze s použitím veřejné a vnitřní položky  
 Zápis testů tak, aby se používají pouze veřejné (nebo interní) třídy a členy. Toto je nejlepším řešením. Testy budou fungovat i v případě Refaktorujte vnitřní implementace sestavení v rámci testu. S použitím stejné testy před a po změně, máte jistotu, že vaše změny nebyly změnit chování sestavení.  
  
 Chcete-li to možné, budete muset změnit strukturu kódu. Například můžete potřebovat rozdělit některé metody do jiné třídy.  
  
 Zadáním důkladně zvážit tohoto přístupu často zjistíte, že váš kód je snazší pro čtení a změnit a méně prone k chybám při potřebné změnám.  
  
 Můžete povolit přístup k interním položky tak, že přidáte atribut v sestavení testu **Properties\AssemblyInfo.cs** v Testovaný projekt:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Definujte testovací rozhraní  
 Definujte rozhraní, která obsahuje jak veřejné členy třídy má být testována a další vlastnosti a metody pro soukromé členy, které chcete testy moct dál používat. Přidejte tato rozhraní Testovaný projekt. Příklad:  
  
```csharp  
internal interface MyClassTestInterface {  
  void PublicMethod1();  
  string PublicProperty1 { get; }  
  string privateField1_Accessor { get; }  
  int privateMethod1_Accessor (string p1);   
 }  
```  
  
 Přidání metody do třídy má být testována, explicitně implementovat přístupové metody. Tyto další metody oddělte od hlavní třída jejich zapsáním do částečné třídy definice v samostatném souboru. Příklad:  
  
```csharp  
partial public class MyClass  
{  
  string MyClassTestInterface.privateField1_Accessor  
  { get { return privateField1; } }  
  int MyClassTestInterface.privateMethod1_Accessor (string p1)  
  { return privateMethod1(p1); }  
}  
  
```  
  
 Povolit testovací sestavení používat testovací rozhraní přidáním tohoto atributu na sestavení, které testujete:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Do metody jednotkového testu použijte rozhraní testu. Příklad:  
  
```csharp  
MyClassTestInterface testInstance = new MyClass();  
testInstance.PublicMethod1();  
Assert.AreEqual("hello", testInstance.privateField1_Accessor);  
```  
  
 Definujte přístupové objekty pomocí reflexe  
 Toto je způsob, doporučujeme vám nejméně. Starší verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroj, který automaticky vytvoří přístupové metody pro každou privátní metodu k dispozici. I když je to pohodlné, naše prostředí pro naznačuje, že je obvykle za následek testy jednotek, které jsou velmi silného spjat s interní aplikace, kterou testují. Výsledkem je práce navíc při změně požadavků nebo architekturu, protože testy musí být změněny spolu s implementací. Navíc závěry chybné v návrhu implementace jsou také součástí testy, tak, aby testy nelze najít chyby.  
  
## <a name="see-also"></a>Viz také  
 [Anatomie testování částí](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML – rychlé položku pomocí textu](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)



