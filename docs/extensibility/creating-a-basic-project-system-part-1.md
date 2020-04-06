---
title: Vytvoření základního projektového systému, část 1 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739721"
---
# <a name="create-a-basic-project-system-part-1"></a>Vytvoření základního projektového systému, část 1
V sadě Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání souborů zdrojového kódu a dalších datových zdrojů. Projekty se zobrazí jako podřízené řešení v **Průzkumníku řešení**. Projekty umožňují organizovat, vytvářet, ladit a nasazovat zdrojový kód a vytvářet odkazy na webové služby, databáze a další prostředky.

 Projekty jsou definovány v souborech projektu, například soubor *.csproj* pro projekt Visual C#. Můžete vytvořit vlastní typ projektu, který má vlastní příponu názvu souboru projektu. Další informace o typech projektů naleznete v [tématu Typy projektů](../extensibility/internals/project-types.md).

> [!NOTE]
> Pokud potřebujete rozšířit Visual Studio s vlastním typem projektu, důrazně doporučujeme využít [systém projektu Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), který má řadu výhod oproti vytváření systému projektu od začátku:
>
> - Snadnější nástup.  Dokonce i základní projektový systém vyžaduje desítky tisíc řádků kódu.  Využití VSPS snižuje náklady na připojení na několik kliknutí, než budete připraveni přizpůsobit jej vašim potřebám.
> - Snadnější údržba.  Využitím VSPS, stačí udržovat své vlastní scénáře.  Staráme se o údržbu veškeré infrastruktury projektového systému.
>
>   Pokud potřebujete cílit na verze Sady Visual Studio starší než Visual Studio 2013, nebudete moct využít VSPS v rozšíření Visual Studio.  Pokud tomu tak je, tento návod je dobrým místem, kde můžete začít.

 Tento návod ukazuje, jak vytvořit typ projektu, který má příponu názvu souboru projektu *.myproj*. Tento návod si vypůjčí z existujícího systému projektu Visual C#.

> [!NOTE]
> Další příklady projektů rozšíření naleznete [v tématu VSSDK ukázky](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Tento návod učí, jak provádět tyto úkoly:

- Vytvořte základní typ projektu.

- Vytvořte základní šablonu projektu.

- Zaregistrujte šablonu projektu pomocí sady Visual Studio.

- Vytvořte instanci projektu otevřením dialogového okna **Nový projekt** a potom pomocí šablony.

- Vytvořte továrnu projektu pro systém projektu.

- Vytvořte uzel projektu pro systém projektu.

- Přidejte vlastní ikony pro systém projektu.

- Implementujte nahrazení základního parametru šablony.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Musíte také stáhnout zdrojový kód pro [rozhraní Spravovaného balíčku pro projekty](https://github.com/tunnelvisionlabs/MPFProj10). Extrahujte soubor do umístění, které je přístupné řešení, které se chystáte vytvořit.

## <a name="create-a-basic-project-type"></a>Vytvoření základního typu projektu
 Vytvořte projekt C# VSIX s názvem **SimpleProject**. (File**New** > **New** > **Project** a potom Visual **C#** > **Rozšiřitelnost** > **VSIX Project).** Přidejte šablonu položky projektu balíčku sady Visual Studio (v **Průzkumníku řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**a pak přejděte na balíček **Rozšiřitelnost** > **visual studia).** Pojmenujte soubor *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Vytvoření základní šablony projektu
 Nyní můžete upravit tento základní VSPackage implementovat nový typ projektu *.myproj.* Chcete-li vytvořit projekt, který je založen na typu projektu *.myproj,* visual studio musí vědět, které soubory, prostředky a odkazy přidat do nového projektu. Chcete-li tyto informace poskytnout, vložte soubory projektu do složky šablony projektu. Když uživatel použije projekt *.myproj* k vytvoření projektu, soubory jsou zkopírovány do nového projektu.

### <a name="to-create-a-basic-project-template"></a>Vytvoření základní šablony projektu

1. Přidejte do projektu tři složky, jednu pod druhou: *Templates\Projects\SimpleProject*. (V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu **SimpleProject,** přejděte na **přidat**a potom klepněte na příkaz **Nová složka**. Pojmenujte složku *Šablony*. Ve složce *Šablony* přidejte složku s názvem *Projekty*. Do složky *Projekty* přidejte složku s názvem *SimpleProject*.)

2. Ve složce *Templates\Projects\SimpleProject* přidejte soubor bitového obrázku, který chcete použít jako ikonu s názvem *SimpleProject.ico*. Po klepnutí na tlačítko **Přidat**se otevře editor ikon.

3. Zasazte se o to, aby se ikona rozlišuje Tato ikona se zobrazí v dialogovém okně **Nový projekt** později v návodu.

    ![Ikona jednoduchého projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Uložte ikonu a zavřete editor ikon.

5. Ve složce *Templates\Projects\SimpleProject* přidejte položku **třídy** s názvem *Program.cs*.

6. Nahraďte existující kód následujícími řádky.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > Toto není konečná podoba *Program.cs* kódu; náhradní parametry budou řešeny v pozdějším kroku. Mohou se zobrazit chyby kompilace, ale tak dlouho, dokud soubor **BuildAction** je **obsah**, měli byste být schopni sestavit a spustit projekt jako obvykle.

7. Uložte soubor.

8. Zkopírujte *soubor AssemblyInfo.cs* ze složky *Vlastnosti* do složky *Projekty\SimpleProject.*

9. Ve složce *Projekty\SimpleProject* přidejte soubor XML s názvem *SimpleProject.myproj*.

   > [!NOTE]
   > Přípona názvu souboru pro všechny projekty tohoto typu je *.myproj*. Pokud ji chcete změnit, musíte ji změnit všude, kde je uveden v návodu.

10. Nahraďte existující obsah následujícími řádky.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Uložte soubor.

12. V okně **Vlastnosti** nastavte **akci sestavení** *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico*a *SimpleProject.myproj* na **obsah**a nastavte jejich vlastnosti Zahrnout **do VSIX** na **Hodnotu True**.

    Tato šablona projektu popisuje základní projekt jazyka Visual C#, který má konfiguraci ladění i konfiguraci vydání. Projekt obsahuje dva zdrojové soubory, *AssemblyInfo.cs* a *Program.cs*a několik odkazů na sestavení. Při vytvoření projektu ze šablony je hodnota ProjectGuid automaticky nahrazena novým identifikátorem GUID.

    V **Průzkumníku řešení**by se měla rozšířená složka **Šablony** zobrazit takto:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Vytvoření základní továrny projektu
 Je nutné sdělit Visual Studio umístění složky šablony projektu. Chcete-li to provést, přidejte atribut do třídy VSPackage, která implementuje továrnu projektu tak, aby umístění šablony bylo zapsáno do systémového registru při vytváření vspackage. Začněte vytvořením základní továrny projektu, která je identifikována identifikátorem GUID továrny projektu. Pomocí <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributu připojte továrnu `SimpleProjectPackage` projektu ke třídě.

### <a name="to-create-a-basic-project-factory"></a>Vytvoření základní továrny projektu

1. Vytvořte identifikátory GUID pro továrnu projektu (v nabídce **Nástroje** klepněte na **tlačítko Vytvořit identifikátor GUID**) nebo použijte identifikátor GUID v následujícím příkladu. Přidejte identifikátory GUID do `SimpleProjectPackage` třídy v `PackageGuidString`blízkosti oddílu s již definovaným . Identifikátory GUID musí být ve formě GUID i ve formě řetězce. Výsledný kód by se měl podobat následujícímu příkladu.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Přidejte třídu do horní složky *SimpleProject* s názvem *SimpleProjectFactory.cs*.

3. Pomocí direktiv přidejte následující příkazy:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Přidejte atribut GUID `SimpleProjectFactory` do třídy. Hodnota atributu je nový identifikátor GUID továrny projektu.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Nyní můžete zaregistrovat šablonu projektu.

### <a name="to-register-the-project-template"></a>Registrace šablony projektu

1. V *SimpleProjectPackage.cs*přidejte <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atribut `SimpleProjectPackage` do třídy následujícím způsobem.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Znovu sestavte řešení a ověřte, zda je sestavení bez chyb.

    Opětovné sestavení registruje šablonu projektu.

   Parametry `defaultProjectExtension` a `possibleProjectExtensions` jsou nastaveny na příponu názvu souboru projektu (*.myproj*). Parametr `projectTemplatesDirectory` je nastaven na relativní cestu složky *Šablony.* Během sestavení bude tato cesta převedena na úplné sestavení a přidána do registru pro registraci systému projektu.

## <a name="test-the-template-registration"></a>Otestovat registraci šablony
 Registrace šablony sděluje Visual Studiu umístění složky šablony projektu, aby visual studio mohlo zobrazit název a ikonu šablony v dialogovém okně **Nový projekt.**

### <a name="to-test-the-template-registration"></a>Testování registrace šablony

1. Stisknutím **klávesy F5** spusťte ladění experimentální instance sady Visual Studio.

2. V experimentální instanci vytvořte nový projekt nově vytvořeného typu projektu. V dialogovém okně **Nový projekt** byste měli vidět **SimpleProject** v části **Nainstalované šablony**.

   Nyní máte továrnu projektu, která je registrována. Však ještě nelze vytvořit projekt. Balíček projektu a továrna projektu spolupracují na vytvoření a inicializaci projektu.

## <a name="add-the-managed-package-framework-code"></a>Přidání kódu rozhraní spravovaného balíčku
 Implementujte připojení mezi balíčkem projektu a továrnou projektu.

- Importujte soubory zdrojového kódu pro rozhraní Managed Package Framework.

    1. Uvolněte projekt SimpleProject (v **Průzkumníku řešení**vyberte uzel projektu a v místní nabídce klepněte na **tlačítko Uvolnit projekt**.) a otevřete soubor projektu v editoru XML.

    2. Přidejte následující bloky do souboru \<projektu (těsně nad bloky importu>). Nastavte `ProjectBasePath` umístění souboru *ProjectBase.files* v kódu rozhraní Spravovaného balíčku, který jste právě stáhli. Možná budete muset přidat zpětné lomítko k cestě. Pokud tak neučiníte, projektu nemusí najít zdrojový kód rozhraní spravovaného balíčku framework.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Nezapomeňte na zpětné lomítko na konci cesty.

    3. Znovu načtěte projekt.

    4. Přidejte odkazy na následující sestavení:

        - `Microsoft.VisualStudio.Designer.Interfaces`(v * \<sadě VSSDK nainstalujte>\VisualStudioIntegration\Common\Assemblyies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Inicializaci továrny projektu

1. Do *SimpleProjectPackage.cs* souboru přidejte následující `using` direktivu.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Odvodit třídu `SimpleProjectPackage` z `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Zaregistrujte továrnu projektu. Přidejte následující řádek `SimpleProjectPackage.Initialize` k metodě, těsně za `base.Initialize`.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementujte abstraktní `ProductUserContext`vlastnost :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. V *SimpleProjectFactory.cs*přidejte `using` za stávající `using` směrnice následující direktivu.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Odvodit třídu `SimpleProjectFactory` z `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Přidejte do třídy `SimpleProjectFactory` následující metodu figuríny. Tuto metodu implementujete v pozdější části.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Přidejte do `SimpleProjectFactory` třídy následující pole a konstruktor. Tento `SimpleProjectPackage` odkaz je uložen do mezipaměti v soukromém poli, aby jej bylo možné použít při nastavování webu poskytovatele služeb.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Znovu sestavte řešení a ověřte, zda je sestavení bez chyb.

## <a name="test-the-project-factory-implementation"></a>Otestujte realizaci továrny na projekt
 Otestujte, zda je volána konstruktor pro implementaci továrny projektu.

### <a name="to-test-the-project-factory-implementation"></a>Testování implementace továrny projektu

1. V *souboru SimpleProjectFactory.cs* nastavte zarážku na `SimpleProjectFactory` následujícím řádku v konstruktoru.

    ```csharp
    this.package = package;
    ```

2. Stisknutím **klávesy F5** spusťte experimentální instanci sady Visual Studio.

3. V experimentální instanci začněte vytvářet nový projekt. V dialogovém okně **Nový projekt** vyberte typ projektu **SimpleProject** a klepněte na tlačítko **OK**. Spuštění zastaví na zarážky.

4. Zrušte zarážku a zastavte ladění. Vzhledem k tomu, že jsme ještě nevytvořili uzel projektu, kód vytvoření projektu stále vyvolá výjimky.

## <a name="extend-the-projectnode-class"></a>Rozšíření třídy ProjectNode
 Nyní můžete implementovat třídu, `SimpleProjectNode` která `ProjectNode` je odvozena od třídy. Základní `ProjectNode` třída zpracovává následující úkoly vytváření projektu:

- Zkopíruje soubor šablony projektu *SimpleProject.myproj*do nové složky projektu. Kopie je přejmenována podle názvu, který je zadán v dialogovém okně **Nový projekt.** Hodnota `ProjectGuid` vlastnosti je nahrazena novým identifikátorem GUID.

- Prochází prvky MSBuild souboru šablony projektu *SimpleProject.myproj* `Compile` a hledá prvky. Pro `Compile` každý cílový soubor zkopíruje soubor do nové složky projektu.

  Odvozené `SimpleProjectNode` třídy zpracovává tyto úkoly:

- Umožňuje vytvoření nebo výběr ikon uzlů projektu a souborů v **Průzkumníku řešení.**

- Umožňuje zadat další nahrazení parametrů šablony projektu.

### <a name="to-extend-the-projectnode-class"></a>Rozšíření třídy ProjectNode

1. Přidejte třídu s názvem `SimpleProjectNode.cs`.

2. Nahraďte existující kód následujícím kódem.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   Tato `SimpleProjectNode` implementace třídy má tyto přepsané metody:

- `ProjectGuid`, který vrátí identifikátor GUID továrny projektu.

- `ProjectType`, který vrátí lokalizovaný název typu projektu.

- `AddFileFromTemplate`, který zkopíruje vybrané soubory ze složky šablony do cílového projektu. Tato metoda je dále implementována v pozdější části.

  Konstruktor, `SimpleProjectNode` stejně `SimpleProjectFactory` jako konstruktor, `SimpleProjectPackage` ukládá odkaz v soukromém poli pro pozdější použití.

  Chcete-li `SimpleProjectFactory` připojit `SimpleProjectNode` třídu ke třídě, musíte `SimpleProjectNode` vytvořit `SimpleProjectFactory.CreateProject` instanci nové metody a ukládat ji do mezipaměti v soukromém poli pro pozdější použití.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Připojení třídy factory projektu a třídy uzlu

1. Do souboru *SimpleProjectFactory.cs* přidejte následující `using` direktivu:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Nahraďte metodu `SimpleProjectFactory.CreateProject` pomocí následujícího kódu.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Znovu sestavte řešení a ověřte, zda je sestavení bez chyb.

## <a name="test-the-projectnode-class"></a>Testování třídy ProjectNode
 Otestujte továrnu projektu a zjistěte, zda vytváří hierarchii projektu.

### <a name="to-test-the-projectnode-class"></a>Testování třídy ProjectNode

1. Stisknutím klávesy **F5** spusťte ladění. V experimentální instanci vytvořte nový SimpleProject.

2. Visual Studio by měla volat továrnu projektu k vytvoření projektu.

3. Zavřete experimentální instanci sady Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Přidání ikony vlastního uzlu projektu
 Ikona uzlu projektu v předchozí části je výchozí ikonou. Můžete ji změnit na vlastní ikonu.

### <a name="to-add-a-custom-project-node-icon"></a>Přidání ikony vlastního uzlu projektu

1. Do složky **Zdroje** přidejte bitmapový soubor s názvem *SimpleProjectNode.bmp*.

2. V oknech **Vlastnosti** zmenšete bitmapu na 16 x 16 obrazových bodů. Zvýrazněte bitmapu.

    ![Jednoduchá projektová komatista](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. V okně **Vlastnosti** změňte **akci Sestavení** bitmapy na **Vložený prostředek**.

4. V *SimpleProjectNode.cs*přidejte `using` následující směrnice:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Přidejte do `SimpleProjectNode` třídy následující statické pole a konstruktor.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Přidejte následující vlastnost na `SimpleProjectNode` začátek třídy.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Nahraďte konstruktor instance následujícím kódem.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Během statické `SimpleProjectNode` konstrukce načte bitmapu uzlu projektu ze zdrojů manifestu sestavení a uloží jej do mezipaměti v soukromém poli pro pozdější použití. Všimněte si <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> syntaxe cesty k obrázku. Chcete-li zobrazit názvy prostředků manifestu vložené <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> do sestavení, použijte metodu. Pokud je tato metoda `SimpleProject` použita na sestavení, výsledky by měly být následující:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Během stavby `ProjectNode` instance načte základní třída *Resources.imagelis.bmp*, ve kterém jsou vloženy běžně používané bitmapy 16 x 16 z *Resources\imagelis.bmp*. Tento seznam bitmap je `SimpleProjectNode` `ImageHandler.ImageList`k dispozici jako . `SimpleProjectNode`připojí bitmapu uzlu projektu do seznamu. Posun bitmapy uzlu projektu v seznamu obrázků je uložen do mezipaměti pro `ImageIndex` pozdější použití jako hodnota veřejné vlastnosti. Visual Studio používá tuto vlastnost k určení bitmapy, která se má zobrazit jako ikona uzlu projektu.

## <a name="test-the-custom-project-node-icon"></a>Otestovat ikonu vlastního uzlu projektu
 Otestujte továrnu projektu a zjistěte, zda vytvoří hierarchii projektu, která má ikonu vlastního uzlu projektu.

### <a name="to-test-the-custom-project-node-icon"></a>Testování ikony vlastního uzlu projektu

1. Spusťte ladění a v experimentální instanci vytvořte nový SimpleProject.

2. V nově vytvořeném projektu všimněte si, že *SimpleProjectNode.bmp* se používá jako ikona uzlu projektu.

     ![Uzel nového projektu jednoduchého projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjektNode")

3. Otevřete soubor *Program.cs* v editoru kódu. Měli byste vidět zdrojový kód, který se podobá následující kód.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Všimněte si, že parametry šablony $nameSpace$ a $className$ nemají nové hodnoty. V další části se dozvíte, jak implementovat nahrazení parametrů šablony.

## <a name="substitute-template-parameters"></a>Nahradit parametry šablony
 V dřívější části jste zaregistrovali šablonu projektu `ProvideProjectFactory` s Visual Studio pomocí atributu. Registrace cesty ke složce šablony tímto způsobem umožňuje povolit nahrazení základního `ProjectNode.AddFileFromTemplate` parametru šablony přepsáním a rozšířením třídy. Další informace naleznete [v tématu Nová generace projektu: Pod kapotou, část druhá](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Nyní přidejte náhradní `AddFileFromTemplate` kód do třídy.

### <a name="to-substitute-template-parameters"></a>Nahrazení parametrů šablony

1. Do *SimpleProjectNode.cs* souboru přidejte následující `using` direktivu.

   ```csharp
   using System.IO;
   ```

2. Nahraďte metodu `AddFileFromTemplate` pomocí následujícího kódu.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Nastavte zarážku v metodě, těsně za příkazem `className` přiřazení.

   Příkazy přiřazení určují přiměřené hodnoty pro obor názvů a nový název třídy. Dvě `ProjectNode.FileTemplateProcessor.AddReplace` volání metody nahradit odpovídající hodnoty parametrů šablony pomocí těchto nových hodnot.

## <a name="test-the-template-parameter-substitution"></a>Otestovat nahrazení parametru šablony
 Nyní můžete otestovat nahrazení parametrů šablony.

### <a name="to-test-the-template-parameter-substitution"></a>Testování nahrazení parametru šablony

1. Spusťte ladění a v experimentální instanci vytvořte nový SimpleProject.

2. Spuštění zastaví na zarážky `AddFileFromTemplate` v metodě.

3. Zkontrolujte hodnoty `nameSpace` parametrů `className` a.

   - `nameSpace`je uvedena hodnota \<prvku RootNamespace> v souboru šablony projektu *\Templates\Projects\SimpleProject\SimpleProject.myproj.* V tomto případě je `MyRootNamespace`hodnota .

   - `className`je uvedena hodnota názvu zdrojového souboru třídy bez přípony názvu souboru. V tomto případě je první soubor, který má být zkopírován do cílové složky *AssemblyInfo.cs*; proto je `AssemblyInfo`hodnota className .

4. Odeberte zarážku a stisknutím **klávesy F5** pokračujte v provádění.

    Visual Studio by měl dokončit vytváření projektu.

5. Otevřete soubor *Program.cs* v editoru kódu. Měli byste vidět zdrojový kód, který se podobá následující kód.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Všimněte si, že `MyRootNamespace` obor názvů je `Program`nyní a název třídy je nyní .

6. Spusťte ladění projektu. Nový projekt by měl zkompilovat, spustit a zobrazit "Hello VSX!!!" v okně konzoly.

    ![Jednoduchý příkaz projektu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Blahopřejeme! Implementovali jste základní systém spravovaného projektu.
