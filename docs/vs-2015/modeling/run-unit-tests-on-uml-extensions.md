---
title: Spustit testy jednotek v rozšířeních UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f634f028dafea3260a69537893513f13cc0ebe83
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292547"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Spouštění testování částí v rozšířeních UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Abychom vám pomohli udržet kód v průběhu po sobě jdoucích změn, doporučujeme napsat testy jednotek a provádět je v rámci běžného procesu sestavení. Další informace najdete v tématu [svůj kód testu jednotek](../test/unit-test-your-code.md). Chcete-li nastavit testy pro rozšíření modelování sady Visual Studio, budete potřebovat některé klíčové informace. Souhrn:

- [Nastavení testu jednotek pro rozšíření VSIX](#Host)

   Spusťte testy s hostitelským adaptérem sady VS IDE. Každou testovací metodu zaprefixujte pomocí `[HostType("VS IDE")]`. Tento hostitelský adaptér se spustí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] při spuštění testů.

- [Přístup k DTE a úložišti ModelStore](#DTE)

   Obvykle budete muset otevřít model a jeho diagramy a přistupovat k `IModelStore` při inicializaci testu.

- [Otevření diagramu modelu](#Opening)

   Můžete přetypovat `EnvDTE.ProjectItem` na a z `IDiagramContext`.

- [Provádění změn ve vláknu UI](#UiThread)

   Testy, které provádějí změny v úložišti modelu, musí být provedeny ve vlákně UI. Pro tuto možnost můžete použít `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker`.

- [Testování příkazů, gest a dalších komponent MEF](#MEF)

   Chcete-li testovat komponenty MEF, je nutné explicitně připojit své importované vlastnosti k hodnotám.

  Tyto body jsou vypracované v následujících oddílech.

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="Host"></a>Nastavení testu jednotek pro rozšíření VSIX
 Metody v rozšířeních modelování obvykle pracují s diagramem, který je již otevřen. Metody používají importy MEF, například **IDiagramContext** a **ILinkedUndoContext**. Vaše testovací prostředí musí nastavit tento kontext před spuštěním testů.

#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Nastavení testu jednotek, který se provádí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Vytvořte projekt rozšíření UML a projekt testování částí.

    1. **Projekt rozšíření UML.** Obvykle to vytvoříte pomocí šablon projektů pro příkazy, gesta nebo ověřování. Například viz [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

    2. **Projekt testování částí.** Další informace najdete v tématu [svůj kód testu jednotek](../test/unit-test-your-code.md).

2. Vytvořte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které obsahuje projekt modelování UML. Toto řešení budete používat jako počáteční stav vašich testů. Mělo by být oddělené od řešení, ve kterém zapisujete rozšíření UML a testy jednotek. Další informace najdete v tématu [vytváření projektů a diagramů modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

3. **V projektu rozšíření UML**upravte soubor. csproj jako text a ujistěte se, že následující řádky ukazují `true`:

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     Chcete-li upravit soubor. csproj jako text, klikněte na tlačítko **Uvolnit projekt** v místní nabídce projektu v Průzkumník řešení. Pak zvolte **Upravit.... csproj**. Po úpravě textu vyberte **znovu načíst projekt**.

4. V projektu rozšíření UML přidejte následující řádek do **Properties\AssemblyInfo.cs**. To umožňuje jednotkovým testům přístup k metodám, které chcete testovat:

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **V projektu testování částí**přidejte následující odkazy na sestavení:

    - *Váš projekt rozšíření UML*

    - **EnvDTE.dll**

    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**

    - **Microsoft.VisualStudio.ComponentModelHost.dll**

    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**

    - **Microsoft.VisualStudio.Uml.Interfaces.dll**

    - **Microsoft.VSSDK.TestHostFramework.dll**

6. Prefixujte atribut `[HostType("VS IDE")]` ke každé testovací metodě, včetně inicializačních metod.

     Tím se zajistí, že se test spustí v experimentální instanci aplikace Visual Studio.

## <a name="DTE"></a>Přístup k DTE a úložišti ModelStore
 Napíšete metodu pro otevření projektu modelování v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Obvykle je vhodné otevřít řešení pouze jednou v každém testovacím běhu. Chcete-li spustit metodu pouze jednou, předponu metody s atributem `[AssemblyInitialize]`. Nezapomeňte, že pro každou testovací metodu budete potřebovat také atribut [HostType ("VS IDE")].  Příklad:

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
        // https://msdn.microsoft.com/library/ee791691.aspx
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

 Pokud instance <xref:EnvDTE.Project?displayProperty=fullName> představuje projekt modelování, můžete jej přetypovat na a z [IModelingProject](/previous-versions/ee789474(v=vs.140)).

## <a name="Opening"></a>Otevření diagramu modelu
 Pro každý test nebo třídu testů obvykle chcete pracovat s otevřeným diagramem. Následující příklad používá atribut `[ClassInitialize]`, který spustí tuto metodu před jinými metodami v této třídě testu. Znovu nezapomeňte, že pro každou testovací metodu budete potřebovat také atribut [HostType ("VS IDE")]:

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

## <a name="UiThread"></a>Provádění změn modelu ve vlákně UI
 Pokud vaše testy nebo metody v rámci testu provádějí změny v úložišti modelu, je nutné je spustit ve vlákně uživatelského rozhraní. Pokud to neuděláte, může se zobrazit `AccessViolationException`. Vložte kód testovací metody ve volání metody Invoke:

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

## <a name="MEF"></a>Testování příkazu, gesta a dalších komponent MEF
 Komponenty MEF používají deklarace vlastností, které mají atribut `[Import]` a jehož hodnoty jsou nastaveny podle jejich hostitelů. Obvykle tyto vlastnosti zahrnují IDiagramContext, SVsServiceProvider a ILinkedUndoContext. Při testování metody, která používá některou z těchto vlastností, je nutné před spuštěním testované metody nastavit jejich hodnoty. Například pokud jste napsali rozšíření příkazu podobné tomuto kódu:

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

 Importované vlastnosti pak můžete nastavit takto:

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

 Pokud chcete otestovat metodu, která přebírá importovanou vlastnost jako parametr, můžete importovat vlastnost do vaší třídy testu a použít `SatisfyImportsOnce` pro testovací instanci. Příklad:

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

 V tomto příkladu jsou dva atributy každé testovací metody kombinovány pro pohodlí do jednoho řádku.

## <a name="access-from-tests-to-private-methods-and-variables"></a>Přístup z testů do privátních metod a proměnných
 Někdy budete chtít otestovat metodu, která je soukromá, nebo chcete ověřit stav pole, které je soukromé, před a po provedení testované metody. To představuje obtížnost, protože testy jsou v samostatném sestavení pro zkoušené třídy. Existuje několik taktiku, které můžete zvážit, včetně následujících:

 Testujte pouze pomocí veřejné a interní položky zápis testů tak, aby používaly pouze veřejné (nebo interní) třídy a členy. Toto je nejlepší přístup. Vaše testy budou fungovat i v případě, že refaktorujte interní implementaci sestavení v rámci testu. Když použijete stejné testy před a po změnách, můžete si být jisti, že změny nezměnily chování sestavení.

 Aby to bylo možné, možná budete muset změnit strukturu kódu. Například může být nutné oddělit některé metody do jiné třídy.

 Díky vážnému zvážení tohoto přístupu často zjistíte, že váš kód bude čitelnější a může být změněn a méně náchylný k chybám, když jsou potřebné změny.

 Testovacímu sestavení můžete dovolit přístup k interním položkám přidáním atributu v **Properties\AssemblyInfo.cs** v projektu, který má být testován:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Definujte testovací rozhraní definovat rozhraní, které obsahuje veřejné členy třídy, které mají být testovány, a další vlastnosti a metody pro soukromé členy, které chcete, aby testy mohly používat. Přidejte toto rozhraní do projektu, který se má testovat. Příklad:

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 Přidejte metody do třídy, která má být testována, k explicitní implementaci metod přistupujícího objektu. Tyto další metody oddělte od hlavní třídy jejich zapsáním v definici částečné třídy v samostatném souboru. Příklad:

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 Umožněte testovacímu sestavení používat testovací rozhraní přidáním tohoto atributu do sestavení, které testujete:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 V metodách testování částí použijte testovací rozhraní. Příklad:

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 Definování přístupových objektů pomocí reflexe je to způsob, který doporučujeme nejméně. Starší verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytly nástroj, který automaticky vytvořil přístupovou metodu pro každou soukromou metodu. I když je to pohodlné, naše prostředí má za následek to, že má za následek testy jednotek, které jsou velmi silně spojeny s interní strukturou aplikace, kterou testuje. Výsledkem je další práce při změně požadavků nebo architektury, protože testy je třeba změnit společně s implementací. Všechny chybné předpoklady v návrhu implementace jsou také integrovány do testů, takže testy nenaleznou chyby.

## <a name="see-also"></a>Viz také
 [Anatomie testu jednotek](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) – [definice příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
