---
title: Vytvoření základního projektového systému, část 1 | Microsoft Docs
description: Naučte se vytvořit typ projektu s názvem Extension. myproj. V aplikaci Visual Studio jsou projekty kontejnery, které slouží k uspořádání souborů zdrojového kódu a dalších prostředků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1b21ef736e69c962db389a7bb1a3eb284ebdd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887364"
---
# <a name="create-a-basic-project-system-part-1"></a>Vytvoření základního projektového systému, část 1
V aplikaci Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání souborů zdrojového kódu a dalších prostředků. Projekty se zobrazí jako podřízené položky řešení v **Průzkumník řešení**. Projekty umožňují organizovat, sestavovat, ladit a nasazovat zdrojový kód a vytvářet odkazy na webové služby, databáze a další prostředky.

 Projekty jsou definovány v souborech projektu, například soubor *. csproj* pro projekt jazyka Visual C#. Můžete vytvořit vlastní typ projektu, který má vlastní příponu názvu souboru projektu. Další informace o typech projektů naleznete v tématu [typy projektů](../extensibility/internals/project-types.md).

> [!NOTE]
> Pokud potřebujete sadu Visual Studio rozšíříte pomocí vlastního typu projektu, důrazně doporučujeme využívat systém VSPS ( [Visual Studio Project System](https://github.com/Microsoft/VSProjectSystem) ), který má několik výhod oproti vytvoření systému projektu od začátku:
>
> - Snadnější připojování.  I systém základních projektů vyžaduje desítky tisíc řádků kódu.  Využití VSPS snižuje náklady na registraci až na několik kliknutí, než budete připraveni na přizpůsobení podle vašich potřeb.
> - Jednodušší údržba.  Využitím VSPS stačí zachovat vlastní scénáře.  Zpracováváme si udržování všech infrastrukturních systémů projektů.
>
>   Pokud potřebujete cílit na verze sady Visual Studio starší než Visual Studio 2013, nebudete moci využít VSPS v rozšíření sady Visual Studio.  V takovém případě je tento návod dobrým místem, kde začít.

 Tento návod ukazuje, jak vytvořit typ projektu, který má příponu názvu souboru projektu *. myproj*. Tento názorný postup je vypůjčen z existujícího systému projektu Visual C#.

> [!NOTE]
> Další příklady rozšiřujících projektů naleznete v tématu [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Tento návod učí, jak provádět tyto úlohy:

- Vytvoří základní typ projektu.

- Vytvoří základní šablonu projektu.

- Zaregistrujte šablonu projektu v aplikaci Visual Studio.

- Vytvořte instanci projektu otevřením dialogového okna **Nový projekt** a pak použijte šablonu.

- Vytvořte objekt pro vytváření projektu pro systém projektu.

- Vytvořte uzel projektu pro systém projektu.

- Přidejte vlastní ikony pro systém projektu.

- Implementujte základní substituci parametrů šablony.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Také je nutné stáhnout zdrojový kód pro [spravované balíčky architektury pro projekty](https://github.com/tunnelvisionlabs/MPFProj10). Extrahujte soubor do umístění, které je přístupné pro řešení, které budete vytvářet.

## <a name="create-a-basic-project-type"></a>Vytvoření základního typu projektu
 Vytvořte projekt VSIX v jazyce C# s názvem **SimpleProject**. (**Soubor**  >  **Nové**  >  **Projekt** a pak   >  **rozšiřitelný**  >  **projekt VSIX** v jazyce Visual C#). Přidejte šablonu položky projektu balíčku sady Visual Studio (na **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte **Přidat**  >  **novou položku** a pak přejděte na **rozšíření** sady  >  **Visual Studio – balíček**). Název souboru *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Vytvoření základní šablony projektu
 Nyní můžete upravit tento základní VSPackage pro implementaci nového typu projektu *. myproj* . Chcete-li vytvořit projekt, který je založen na typu projektu *. myproj* , aplikace Visual Studio musí zjistit, které soubory, prostředky a odkazy mají být přidány do nového projektu. Chcete-li poskytnout tyto informace, umístěte soubory projektu do složky šablony projektu. Když uživatel použije projekt *. myproj* k vytvoření projektu, soubory se zkopírují do nového projektu.

### <a name="to-create-a-basic-project-template"></a>Vytvoření základní šablony projektu

1. Přidejte do projektu tři složky, jednu pod druhou: *Templates\Projects\SimpleProject*. (V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu **SimpleProject** , přejděte na **Přidat** a klikněte na **Nová složka**. Pojmenujte *šablony* složek. Ve složce *šablony* přidejte složku s názvem *projekty*. Do složky *projekty* přidejte složku s názvem *SimpleProject*.)

2. Ve složce *Templates\Projects\SimpleProject* přidejte rastrový soubor obrázku, který se použije jako ikona s názvem *SimpleProject. ico*. Když kliknete na tlačítko **Přidat**, otevře se editor ikon.

3. Označit ikonu jako odlišnou. Tato ikona se zobrazí v dialogovém okně **Nový projekt** dále v tomto návodu.

    ![Ikona jednoduchého projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Uložte ikonu a zavřete editor ikon.

5. Ve složce *Templates\Projects\SimpleProject* přidejte položku **třídy** s názvem *program.cs*.

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
   > Nejedná se o konečnou formu *program.cs* kódu; parametry nahrazení budou řešeny v pozdějším kroku. Může dojít k chybám při kompilaci, ale pokud je **BuildAction** souboru **obsahu**, měli byste být schopni sestavit a spustit projekt obvyklým způsobem.

7. Soubor uložte.

8. Zkopírujte soubor *AssemblyInfo.cs* ze složky *Properties* do složky *Projects\SimpleProject* .

9. Ve složce *Projects\SimpleProject* přidejte soubor XML s názvem *SimpleProject. myproj*.

   > [!NOTE]
   > Přípona názvu souboru pro všechny projekty tohoto typu je *. myproj*. Pokud ho chcete změnit, musíte ho změnit všude, kde je zmíněný v tomto návodu.

10. Existující obsah nahraďte následujícími řádky.

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

11. Soubor uložte.

12. V okně **vlastnosti** nastavte **akci sestavení** pro *AssemblyInfo.cs*, *program.cs*, *SimpleProject. ico* a *SIMPLEPROJECT. myproj* na **obsah** a nastavte jejich **zahrnutí do vlastností VSIX** na **hodnotu true**.

    Tato šablona projektu popisuje základní projekt Visual C#, který obsahuje konfiguraci ladění i konfiguraci vydání. Projekt obsahuje dva zdrojové soubory, *AssemblyInfo.cs* a *program.cs* a několik odkazů na sestavení. Při vytvoření projektu ze šablony je hodnota ProjectGuid automaticky nahrazena novým identifikátorem GUID.

    V **Průzkumník řešení** by se měla zobrazit složka rozšířených **šablon** takto:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Vytvoření základního objektu pro vytváření projektů
 Musíte aplikaci Visual Studio sdělit umístění složky šablony projektu. Chcete-li to provést, přidejte atribut do třídy VSPackage, která implementuje objekt pro vytváření projektu, aby bylo umístění šablony zapsáno do systémového registru při sestavení VSPackage. Začněte vytvořením základního objektu pro vytváření projektů, který je identifikován identifikátorem GUID objektu pro vytváření projektu. Použijte <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atribut pro připojení objektu pro vytváření projektu ke `SimpleProjectPackage` třídě.

### <a name="to-create-a-basic-project-factory"></a>Vytvoření základního objektu pro vytváření projektů

1. Vytvořte identifikátory GUID pro objekt pro vytváření projektu (v nabídce **nástroje** klikněte na příkaz **vytvořit GUID**) nebo použijte ten v následujícím příkladu. Přidejte identifikátory GUID do `SimpleProjectPackage` třídy poblíž oddílu s již definovaným identifikátorem `PackageGuidString` . Identifikátory GUID musí být ve formátu GUID i ve formě řetězce. Výsledný kód by měl vypadat podobně jako v následujícím příkladu.

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

3. Přidejte následující direktivy using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Přidejte atribut GUID do `SimpleProjectFactory` třídy. Hodnota atributu je nový identifikátor GUID objektu pro vytváření projektu.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Nyní můžete zaregistrovat šablonu projektu.

### <a name="to-register-the-project-template"></a>Registrace šablony projektu

1. V *SimpleProjectPackage.cs* přidejte <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atribut do `SimpleProjectPackage` třídy následujícím způsobem.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Znovu sestavte řešení a ověřte, zda se jedná o sestavení bez chyb.

    Nové sestavení registruje šablonu projektu.

   Parametry `defaultProjectExtension` a `possibleProjectExtensions` jsou nastaveny na příponu názvu souboru projektu (*. myproj*). `projectTemplatesDirectory`Parametr je nastaven na relativní cestu složky *Templates* . Během sestavení bude tato cesta převedena na úplné sestavení a přidána do registru pro registraci systému projektu.

## <a name="test-the-template-registration"></a>Testování registrace šablony
 Registrace šablony obsahuje informace o umístění složky šablony projektu v aplikaci Visual Studio, aby v aplikaci Visual Studio bylo možné zobrazit název šablony a ikonu v dialogovém okně **Nový projekt** .

### <a name="to-test-the-template-registration"></a>Otestování registrace šablony

1. Stisknutím klávesy **F5** spusťte ladění experimentální instance sady Visual Studio.

2. V experimentální instanci vytvořte nový projekt nově vytvořeného typu projektu. V dialogovém okně **Nový projekt** byste měli vidět **SimpleProject** v části **Nainstalované šablony**.

   Nyní máte objekt pro vytváření projektu, který je zaregistrován. Zatím ale nemůže vytvořit projekt. Balíček projektu a továrna projektu pracují společně pro vytvoření a inicializaci projektu.

## <a name="add-the-managed-package-framework-code"></a>Přidat kód spravovaného balíčku rozhraní
 Implementujte připojení mezi balíčkem projektu a objektem pro vytváření projektů.

- Importujte soubory zdrojového kódu pro Managed Package Framework.

    1. Uvolněte projekt SimpleProject (v **Průzkumník řešení** vyberte uzel projektu a v místní nabídce klikněte na položku **Uvolnit projekt**.) a otevřete soubor projektu v editoru XML.

    2. Přidejte následující bloky do souboru projektu (těsně nad \<Import> bloky). Nastavte `ProjectBasePath` na umístění souboru *ProjectBase. Files* v kódu spravovaného balíčku, který jste právě stáhli. Je možné, že budete muset do cesty přidat zpětné lomítko. Pokud to neuděláte, projekt nemusí podařit najít zdrojový kód spravovaného balíčku.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Na konci cesty nezapomeňte zpětné lomítko.

    3. Znovu načtěte projekt.

    4. Přidejte odkazy na následující sestavení:

        - `Microsoft.VisualStudio.Designer.Interfaces`(v *\<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Inicializace objektu pro vytváření projektu

1. Do souboru *SimpleProjectPackage.cs* přidejte následující `using` direktivu.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Odvodit `SimpleProjectPackage` třídu z `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Zaregistrujte objekt pro vytváření projektu. Do metody přidejte následující řádek `SimpleProjectPackage.Initialize` , a to hned po `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implementovat abstraktní vlastnost `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. V *SimpleProjectFactory.cs* přidejte následující `using` direktivu za stávající `using` direktivy.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Odvodit `SimpleProjectFactory` třídu z `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Přidejte do třídy následující fiktivní metodu `SimpleProjectFactory` . Tuto metodu budete implementovat v pozdější části.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Do třídy přidejte následující pole a konstruktor `SimpleProjectFactory` . Tento `SimpleProjectPackage` odkaz je uložen do mezipaměti v soukromém poli, aby jej bylo možné použít v nastavení webu poskytovatele služeb.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Znovu sestavte řešení a ověřte, zda se jedná o sestavení bez chyb.

## <a name="test-the-project-factory-implementation"></a>Testování implementace továrny projektu
 Otestujte, zda je volán konstruktor pro implementaci vaší továrny projektu.

### <a name="to-test-the-project-factory-implementation"></a>Testování implementace továrny projektu

1. V souboru *SimpleProjectFactory.cs* nastavte zarážku na následujícím řádku v `SimpleProjectFactory` konstruktoru.

    ```csharp
    this.package = package;
    ```

2. Stisknutím klávesy **F5** spusťte experimentální instanci sady Visual Studio.

3. V experimentální instanci začněte vytvářet nový projekt. V dialogovém okně **Nový projekt** vyberte typ projektu **SimpleProject** a klikněte na tlačítko **OK**. Spuštění se zastaví na zarážce.

4. Zrušte zarážku a zastavte ladění. Vzhledem k tomu, že jsme ještě nevytvořili uzel projektu, kód pro vytváření projektu stále vyvolává výjimky.

## <a name="extend-the-projectnode-class"></a>Rozšiřování třídy ProjectNode
 Nyní můžete implementovat `SimpleProjectNode` třídu, která je odvozena od `ProjectNode` třídy. `ProjectNode`Základní třída zpracovává následující úlohy při vytváření projektu:

- Zkopíruje soubor šablony projektu *SimpleProject. myproj* do složky nového projektu. Kopie je přejmenována podle názvu, který je zadán v dialogovém okně **Nový projekt** . `ProjectGuid`Hodnota vlastnosti je nahrazena novým identifikátorem GUID.

- Projde prvky MSBuild souboru šablony projektu *SimpleProject. myproj* a vyhledá `Compile` prvky. Pro každý `Compile` cílový soubor zkopíruje soubor do složky nového projektu.

  Odvozená `SimpleProjectNode` Třída zpracovává tyto úlohy:

- Umožňuje vytvořit nebo vybrat ikony pro uzly projektu a souboru v **Průzkumník řešení** .

- Povoluje zadání dalších náhrad parametrů šablony projektu.

### <a name="to-extend-the-projectnode-class"></a>Postup rozšiřování třídy ProjectNode

1. Přidejte třídu s názvem `SimpleProjectNode.cs` .

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

- `ProjectGuid`, což vrátí GUID objektu pro vytváření projektu.

- `ProjectType`, který vrátí lokalizovaný název typu projektu.

- `AddFileFromTemplate`, který kopíruje vybrané soubory ze složky šablony do cílového projektu. Tato metoda je dále implementována v pozdější části.

  `SimpleProjectNode`Konstruktor, podobně jako `SimpleProjectFactory` konstruktor, ukládá do mezipaměti `SimpleProjectPackage` odkaz v soukromém poli pro pozdější použití.

  Chcete-li připojit `SimpleProjectFactory` třídu ke `SimpleProjectNode` třídě, je nutné vytvořit instanci nové `SimpleProjectNode` v `SimpleProjectFactory.CreateProject` metodě a uložit ji do mezipaměti v soukromém poli pro pozdější použití.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Připojení třídy factory projektu a třídy Node

1. Do souboru *SimpleProjectFactory.cs* přidejte následující `using` direktivu:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Nahraďte `SimpleProjectFactory.CreateProject` metodu pomocí následujícího kódu.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Znovu sestavte řešení a ověřte, zda se jedná o sestavení bez chyb.

## <a name="test-the-projectnode-class"></a>Test třídy ProjectNode
 Otestujte objekt pro vytváření projektu, abyste viděli, zda vytváří hierarchii projektu.

### <a name="to-test-the-projectnode-class"></a>Otestování třídy ProjectNode

1. Stisknutím klávesy **F5** spusťte ladění. V experimentální instanci vytvořte nový SimpleProject.

2. Visual Studio by mělo volat objekt pro vytváření projektu a vytvořit tak projekt.

3. Zavřete experimentální instanci sady Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Přidat vlastní ikonu uzlu projektu
 Ikona uzlu projektu v předchozí části je výchozí ikona. Můžete ho změnit na vlastní ikonu.

### <a name="to-add-a-custom-project-node-icon"></a>Přidání ikony vlastního uzlu projektu

1. Ve složce **Resources** přidejte rastrový soubor s názvem *SimpleProjectNode.bmp*.

2. V oknech **vlastnosti** zmenšete rastrový obrázek na 16 × 16 pixelů. Nastavit rastrový obrázek jako výrazný

    ![Jednoduchý projekt – komunikace](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. V okně **vlastnosti** změňte **akci sestavení** rastrového obrázku na **Integrovaný prostředek**.

4. Do *SimpleProjectNode.cs* přidejte následující `using` direktivy:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Do třídy přidejte následující statické pole a konstruktor `SimpleProjectNode` .

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Do začátku třídy přidejte následující vlastnost `SimpleProjectNode` .

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

   Během statické konstrukce `SimpleProjectNode` načítá z prostředků manifestu sestavení rastrový obrázek uzlu projektu a ukládá je do mezipaměti v soukromém poli pro pozdější použití. Všimněte si syntaxe cesty k <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> obrázku. Chcete-li zobrazit názvy prostředků manifestu vložených do sestavení, použijte <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metodu. Pokud je tato metoda použita na `SimpleProject` sestavení, výsledky by měly být následující:

- *SimpleProject. Resources. Resources*

- *VisualStudio. Project. Resources*

- *SimpleProject. VSPackage. Resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. Resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. Resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Během konstrukce instance `ProjectNode` načte základní třída *Resources.imagelis.bmp*, ve kterém se běžně používají 16 × 16 rastrových obrázků od *Resources\imagelis.bmp*. Tento rastrový seznam je zpřístupněn `SimpleProjectNode` jako `ImageHandler.ImageList` . `SimpleProjectNode` připojí rastrový obrázek uzlu projektu k seznamu. Posun rastrového obrázku uzlu projektu v seznamu obrázků je uložen do mezipaměti pro pozdější použití jako hodnota veřejné `ImageIndex` Vlastnosti. Visual Studio používá tuto vlastnost k určení, který rastrový obrázek se má zobrazit jako ikona uzlu projektu.

## <a name="test-the-custom-project-node-icon"></a>Test ikony vlastního uzlu projektu
 Otestujte objekt pro vytváření projektu, abyste viděli, zda vytváří hierarchii projektu, která má vlastní ikonu uzlu projektu.

### <a name="to-test-the-custom-project-node-icon"></a>Otestování ikony vlastního uzlu projektu

1. Spusťte ladění a v experimentální instanci vytvořte nový SimpleProject.

2. V nově vytvořeném projektu si všimněte, že *SimpleProjectNode.bmp* slouží jako ikona uzlu projektu.

     ![Jednoduchý projekt – uzel nového projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Otevřete soubor *Program.cs* v editoru kódu. Měl by se zobrazit zdrojový kód, který se podobá následujícímu kódu.

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

     Všimněte si, že parametry šablony $nameSpace $ a $className $ nemají nové hodnoty. Naučíte se, jak implementovat substituci parametrů šablony v další části.

## <a name="substitute-template-parameters"></a>Nahradit parametry šablony
 V předchozí části jste zaregistrovali šablonu projektu v aplikaci Visual Studio pomocí `ProvideProjectFactory` atributu. Registrace cesty ke složce šablony tímto způsobem umožňuje povolit substituci základních parametrů šablony přepsáním a rozšířením `ProjectNode.AddFileFromTemplate` třídy. Další informace naleznete v tématu [Nová generace projektů: pod digestoří, druhá část](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Nyní do třídy přidejte náhradní kód `AddFileFromTemplate` .

### <a name="to-substitute-template-parameters"></a>Náhrada parametrů šablony

1. Do souboru *SimpleProjectNode.cs* přidejte následující `using` direktivu.

   ```csharp
   using System.IO;
   ```

2. Nahraďte `AddFileFromTemplate` metodu pomocí následujícího kódu.

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

3. Nastavte zarážku v metodě hned za `className` příkaz přiřazení.

   Příkazy přiřazení určují přiměřené hodnoty pro obor názvů a nový název třídy. Dvě `ProjectNode.FileTemplateProcessor.AddReplace` volání metody nahrazují odpovídající hodnoty parametrů šablony pomocí těchto nových hodnot.

## <a name="test-the-template-parameter-substitution"></a>Test nahrazení parametru šablony
 Nyní můžete otestovat nahrazování parametrů šablony.

### <a name="to-test-the-template-parameter-substitution"></a>Otestování nahrazení parametru šablony

1. Spusťte ladění a v experimentální instanci vytvořte nový SimpleProject.

2. Spuštění se zastaví na zarážce v `AddFileFromTemplate` metodě.

3. Prověřte hodnoty `nameSpace` `className` parametrů a.

   - `nameSpace` je předána hodnota \<RootNamespace> prvku v souboru šablony projektu *\Templates\Projects\SimpleProject\SimpleProject.myproj* . V tomto případě je hodnota `MyRootNamespace` .

   - `className` je předána hodnota názvu zdrojového souboru třídy bez přípony názvu souboru. V takovém případě je první soubor, který se má zkopírovat do cílové složky, *AssemblyInfo.cs*; Proto je hodnota className `AssemblyInfo` .

4. Odeberte zarážku a stisknutím klávesy **F5** pokračujte v provádění.

    Visual Studio by mělo dokončit vytváření projektu.

5. Otevřete soubor *Program.cs* v editoru kódu. Měl by se zobrazit zdrojový kód, který se podobá následujícímu kódu.

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

    Všimněte si, že obor názvů je nyní `MyRootNamespace` a název třídy je nyní `Program` .

6. Spusťte ladění projektu. Nový projekt by měl kompilovat, spouštět a zobrazovat "Hello VSX!!!" v okně konzoly.

    ![Jednoduchý projekt – příkaz](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Gratulujeme! Implementovali jste základní spravovaný projektový systém.
