---
title: Vytvoření základního projektového systému, část 1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20637fb47d85b7cb8341df22d056ffe44534835f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295493"
---
# <a name="creating-a-basic-project-system-part-1"></a>Vytvoření systému základního projektu, část 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio jsou projekty kontejnery, které vývojáři používají k uspořádání souborů zdrojového kódu a dalších prostředků. Projekty se zobrazí jako podřízené položky řešení v **Průzkumník řešení**. Projekty umožňují organizovat, sestavovat, ladit a nasazovat zdrojový kód a vytvářet odkazy na webové služby, databáze a další prostředky.  
  
 Projekty jsou definovány v souborech projektu, například soubor. csproj pro vizuální C# projekt. Můžete vytvořit vlastní typ projektu, který má vlastní příponu názvu souboru projektu. Další informace o typech projektů naleznete v tématu [typy projektů](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Pokud potřebujete sadu Visual Studio rozšíříte pomocí vlastního typu projektu, důrazně doporučujeme využívat [systém projektu sady Visual Studio](https://github.com/Microsoft/VSProjectSystem) , který má několik výhod oproti vytvoření systému projektu od začátku:  
> 
> - Snadnější připojování.  I systém základních projektů vyžaduje desítky tisíc řádků kódu.  Využití služby CPS snižuje náklady na registraci až na několik kliknutí, než budete připraveni k jejich přizpůsobení vašim potřebám.  
>   - Jednodušší údržba.  Využitím služby CPS potřebujete zachovat vlastní scénáře.  Zpracováváme si udržování všech infrastrukturních systémů projektů.  
> 
>   Pokud potřebujete cílit na verze sady Visual Studio starší než Visual Studio 2013, nebudete moci využít službu CPS v rozšíření sady Visual Studio.  V takovém případě je tento návod dobrým místem, kde začít.  
  
 Tento návod ukazuje, jak vytvořit typ projektu, který má příponu názvu souboru projektu. myproj. Tento názorný postup je vypůjčen z existujícího C# systému Visual Project.  
  
> [!NOTE]
> Ucelený vzorek kompletního systému projektu jazyka najdete v [ukázkách VSSDK](../misc/vssdk-samples.md)Sample podrobně v ukázce ironpythonu.  
  
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
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Také je nutné stáhnout zdrojový kód pro [spravované balíčky architektury pro projekty](https://archive.codeplex.com/?p=mpfproj12). Extrahujte soubor do umístění, které je přístupné pro řešení, které budete vytvářet.  
  
## <a name="creating-a-basic-project-type"></a>Vytvoření základního typu projektu  
 Vytvořte projekt C# VSIX s názvem **SimpleProject**. (**Soubor, nový, projekt** a pak  **C#, rozšiřitelnost, balíček sady Visual Studio**). Přidejte šablonu položky projektu balíčku sady Visual Studio (na Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat/nová položka**, přejít k **rozšíření/balíček sady Visual Studio**). Název souboru **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Vytvoření základní šablony projektu  
 Nyní můžete upravit tento základní VSPackage pro implementaci nového typu projektu. myproj. Chcete-li vytvořit projekt, který je založen na typu projektu. myproj, aplikace Visual Studio musí zjistit, které soubory, prostředky a odkazy mají být přidány do nového projektu. Chcete-li poskytnout tyto informace, umístěte soubory projektu do složky šablony projektu. Když uživatel použije projekt. myproj k vytvoření projektu, soubory se zkopírují do nového projektu.  
  
#### <a name="to-create-a-basic-project-template"></a>Vytvoření základní šablony projektu  
  
1. Přidejte do projektu tři složky, jednu pod druhou: **Templates\Projects\SimpleProject**. (V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **SimpleProject** , přejděte na **Přidat**a klikněte na **Nová složka**. Pojmenujte `Templates`složky. Ve složce **šablony** přidejte složku s názvem `Projects`. Do složky **projekty** přidejte složku s názvem `SimpleProject`.)  
  
2. Do složky **Projects\SimpleProject** přidejte soubor ikony s názvem `SimpleProject.ico`. Když kliknete na tlačítko **Přidat**, otevře se editor ikon.  
  
3. Označit ikonu jako odlišnou. Tato ikona se zobrazí v dialogovém okně **Nový projekt** dále v tomto návodu.  
  
    ![Ikona jednoduchého projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. Uložte ikonu a zavřete editor ikon.  
  
5. Ve složce **Projects\SimpleProject** přidejte položku **třídy** s názvem `Program.cs`.  
  
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
   > Nejedná se o konečnou formu Program.cs kódu; parametry nahrazení budou řešeny v pozdějším kroku. Může dojít k chybám při kompilaci, ale pokud je **BuildAction** souboru **obsahu**, měli byste být schopni sestavit a spustit projekt obvyklým způsobem.  
  
7. Uložte soubor.  
  
8. Zkopírujte soubor AssemblyInfo.cs ze složky **Properties** do složky **Projects\SimpleProject** .  
  
9. Ve složce **Projects\SimpleProject** přidejte soubor XML s názvem `SimpleProject.myproj`.  
  
   > [!NOTE]
   > Přípona názvu souboru pro všechny projekty tohoto typu je. myproj. Pokud ho chcete změnit, musíte ho změnit všude, kde je zmíněný v tomto návodu.  
  
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
  
11. Uložte soubor.  
  
12. V okně **vlastnosti** nastavte **akci sestavení** pro AssemblyInfo.cs, program.cs, SimpleProject. ico a SimpleProject. myproj na **obsah**a nastavte jejich **zahrnutí do vlastností VSIX** na **hodnotu true**.  
  
    Tato šablona projektu popisuje základní vizuální C# projekt, který obsahuje konfiguraci ladění a konfiguraci vydání. Projekt obsahuje dva zdrojové soubory, AssemblyInfo.cs a Program.cs a několik odkazů na sestavení. Při vytvoření projektu ze šablony je hodnota ProjectGuid automaticky nahrazena novým identifikátorem GUID.  
  
    V **Průzkumník řešení**by se měla zobrazit složka rozšířených **šablon** takto:  
  
    Šablony  
  
    Projekty  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Vytvoření základního objektu pro vytváření projektů  
 Musíte aplikaci Visual Studio sdělit umístění složky šablony projektu. Chcete-li to provést, přidejte atribut do třídy VSPackage, která implementuje objekt pro vytváření projektu, aby bylo umístění šablony zapsáno do systémového registru při sestavení VSPackage. Začněte vytvořením základního objektu pro vytváření projektů, který je identifikován identifikátorem GUID objektu pro vytváření projektu. Pomocí atributu <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> Připojte objekt pro vytváření projektu ke třídě SimpleProjectPackage.  
  
#### <a name="to-create-a-basic-project-factory"></a>Vytvoření základního objektu pro vytváření projektů  
  
1. Otevřete SimpleProjectPackageGuids.cs v editoru kódu.  
  
2. Vytvořte identifikátory GUID pro objekt pro vytváření projektu (v nabídce **nástroje** klikněte na příkaz **vytvořit GUID**) nebo použijte ten v následujícím příkladu. Přidejte identifikátory GUID do třídy SimpleProjectPackageGuids. Identifikátory GUID musí být ve formátu GUID i ve formě řetězce. Výsledný kód by měl vypadat podobně jako v následujícím příkladu.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. Přidejte třídu do horní složky **SimpleProject** s názvem `SimpleProjectFactory.cs`.  
  
4. Přidejte následující příkazy using:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Přidejte atribut GUID do třídy SimpleProjectFactory. Hodnota atributu je nový identifikátor GUID objektu pro vytváření projektu.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Nyní můžete zaregistrovat šablonu projektu.  
  
#### <a name="to-register-the-project-template"></a>Registrace šablony projektu  
  
1. V SimpleProjectPackage.cs přidejte atribut <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> do třídy SimpleProjectPackage následujícím způsobem.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Znovu sestavte řešení a ověřte, zda se jedná o sestavení bez chyb.  
  
    Nové sestavení registruje šablonu projektu.  
  
   Parametry `defaultProjectExtension` a `possibleProjectExtensions` jsou nastaveny na příponu názvu souboru projektu (. myproj). Parametr `projectTemplatesDirectory` je nastaven na relativní cestu složky Templates. Během sestavení bude tato cesta převedena na úplné sestavení a přidána do registru pro registraci systému projektu.  
  
## <a name="testing-the-template-registration"></a>Testování registrace šablony  
 Registrace šablony obsahuje informace o umístění složky šablony projektu v aplikaci Visual Studio, aby v aplikaci Visual Studio bylo možné zobrazit název šablony a ikonu v dialogovém okně **Nový projekt** .  
  
#### <a name="to-test-the-template-registration"></a>Otestování registrace šablony  
  
1. Stisknutím klávesy F5 spusťte ladění experimentální instance sady Visual Studio.  
  
2. V experimentální instanci vytvořte nový projekt nově vytvořeného typu projektu. V dialogovém okně **Nový projekt** byste měli vidět **SimpleProject** v části **Nainstalované šablony**.  
  
   Nyní máte objekt pro vytváření projektu, který je zaregistrován. Zatím ale nemůže vytvořit projekt. Balíček projektu a továrna projektu pracují společně pro vytvoření a inicializaci projektu.  
  
## <a name="add-the-managed-package-framework-code"></a>Přidat kód spravovaného balíčku rozhraní  
 Implementujte připojení mezi balíčkem projektu a objektem pro vytváření projektů.  
  
- Importujte soubory zdrojového kódu pro Managed Package Framework.  
  
    1. Uvolněte projekt SimpleProject (v **Průzkumník řešení**vyberte uzel projektu a v místní nabídce klikněte na položku **Uvolnit projekt**.) a otevřete soubor projektu v editoru XML.  
  
    2. Přidejte následující bloky do souboru projektu (hned nad \<importovat > bloky). Nastavte ProjectBasePath na umístění souboru ProjectBase. Files ve spravovaném kódu architektury balíčku, který jste právě stáhli. Je možné, že budete muset do cesty přidat zpětné lomítko. Pokud to neuděláte, může se stát, že projekt nenalezne kód spravovaného balíčku rozhraní.  
  
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
  
        - Microsoft. VisualStudio. Designer. Interfaces (ve \<VSSDK Install > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Inicializace objektu pro vytváření projektu  
  
1. Do souboru SimpleProjectPackage.cs přidejte následující příkaz `using`.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Odvodit třídu `SimpleProjectPackage` z `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Zaregistrujte objekt pro vytváření projektu. Přidejte následující řádek do metody `SimpleProjectPackage.Initialize`, a to hned po `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Implementovat abstraktní vlastnost `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. V SimpleProjectFactory.cs přidejte následující příkaz `using` za existující příkazy `using`.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Odvodit třídu `SimpleProjectFactory` z `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Přidejte následující fiktivní metodu do třídy `SimpleProjectFactory`. Tuto metodu budete implementovat v pozdější části.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Přidejte následující pole a konstruktor do třídy `SimpleProjectFactory`. Tento `SimpleProjectPackage` odkaz je uložen v mezipaměti v soukromém poli, aby jej bylo možné použít v nastavení webu poskytovatele služeb.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Znovu sestavte řešení a ověřte, zda se jedná o sestavení bez chyb.  
  
## <a name="testing-the-project-factory-implementation"></a>Testování implementace továrny projektu  
 Otestujte, zda je volán konstruktor pro implementaci vaší továrny projektu.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Testování implementace továrny projektu  
  
1. V souboru SimpleProjectFactory.cs nastavte zarážku na následujícím řádku v konstruktoru `SimpleProjectFactory`.  
  
    ```  
    this.package = package;  
    ```  
  
2. Stisknutím klávesy F5 spusťte experimentální instanci sady Visual Studio.  
  
3. V experimentální instanci začněte vytvářet nový projekt. V dialogovém okně **Nový projekt** vyberte typ projektu SimpleProject a klikněte na tlačítko **OK**. Spuštění se zastaví na zarážce.  
  
4. Zrušte zarážku a zastavte ladění. Vzhledem k tomu, že jsme ještě nevytvořili uzel projektu, kód pro vytváření projektu stále vyvolává výjimky.  
  
## <a name="extending-the-project-node-class"></a>Rozšíření třídy uzlu projektu  
 Nyní můžete implementovat třídu `SimpleProjectNode`, která je odvozena z třídy `ProjectNode`. `ProjectNode` základní třída zpracovává následující úlohy při vytváření projektu:  
  
- Zkopíruje soubor šablony projektu SimpleProject. myproj do složky nového projektu. Kopie je přejmenována podle názvu, který je zadán v dialogovém okně **Nový projekt** . Hodnota vlastnosti `ProjectGuid` je nahrazena novým identifikátorem GUID.  
  
- Projde prvky MSBuild souboru šablony projektu SimpleProject. myproj a vyhledá prvky `Compile`. Pro každý cílový soubor `Compile` zkopíruje soubor do složky nového projektu.  
  
  Odvozená třída `SimpleProjectNode` zpracovává tyto úlohy:  
  
- Umožňuje vytvořit nebo vybrat ikony pro uzly projektu a souboru v **Průzkumník řešení** .  
  
- Povoluje zadání dalších náhrad parametrů šablony projektu.  
  
#### <a name="to-extend-the-project-node-class"></a>Chcete-li zvětšit třídu uzlu projektu  
  
1. 
  
2. Přidejte třídu s názvem `SimpleProjectNode.cs`.  
  
3. Nahraďte existující kód následujícím kódem.  
  
   ```  
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
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
   Tato implementace `SimpleProjectNode` třídy obsahuje tyto přepsané metody:  
  
- `ProjectGuid`, která vrací GUID objektu pro vytváření projektu.  
  
- `ProjectType`, která vrací lokalizovaný název typu projektu.  
  
- `AddFileFromTemplate`, která kopíruje vybrané soubory ze složky šablony do cílového projektu. Tato metoda je dále implementována v pozdější části.  
  
  Konstruktor `SimpleProjectNode`, jako je například konstruktor `SimpleProjectFactory`, ukládá do mezipaměti odkaz `SimpleProjectPackage` v soukromém poli pro pozdější použití.  
  
  Chcete-li připojit třídu `SimpleProjectFactory` ke třídě `SimpleProjectNode`, je nutné vytvořit instanci nového `SimpleProjectNode` v metodě `SimpleProjectFactory.CreateProject` a uložit ji do mezipaměti v soukromém poli pro pozdější použití.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Připojení třídy factory projektu a třídy Node  
  
1. Do souboru SimpleProjectFactory.cs přidejte následující příkaz `using`:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Metodu `SimpleProjectFactory.CreateProject` nahraďte pomocí následujícího kódu.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Znovu sestavte řešení a ověřte, zda se jedná o sestavení bez chyb.  
  
## <a name="testing-the-project-node-class"></a>Testování třídy uzlu projektu  
 Otestujte objekt pro vytváření projektu, abyste viděli, zda vytváří hierarchii projektu.  
  
#### <a name="to-test-the-project-node-class"></a>Otestování třídy uzlu projektu  
  
1. Stisknutím klávesy F5 spusťte ladění. V experimentální instanci vytvořte nový SimpleProject.  
  
2. Visual Studio by mělo volat objekt pro vytváření projektu a vytvořit tak projekt.  
  
3. Ukončete experimentální instanci sady Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Přidání ikony vlastního uzlu projektu  
 Ikona uzlu projektu v předchozí části je výchozí ikona. Můžete ho změnit na vlastní ikonu.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Přidání ikony vlastního uzlu projektu  
  
1. Ve složce **Resources (prostředky** ) přidejte rastrový soubor s názvem SimpleProjectNode. bmp.  
  
2. V oknech **vlastnosti** zmenšete rastrový obrázek na 16 × 16 pixelů. Nastavit rastrový obrázek jako výrazný  
  
    ![Jednoduchý projekt – komunikace](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. V okně **vlastnosti** změňte **akci sestavení** rastrového obrázku na **Integrovaný prostředek**.  
  
4. Do SimpleProjectNode.cs přidejte následující příkazy `using`:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Přidejte následující statické pole a konstruktor do třídy `SimpleProjectNode`.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Do začátku `SimpleProjectNode` třídy přidejte následující vlastnost.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Nahraďte konstruktor instance následujícím kódem.  
  
   ```  
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
  
   Během statické konstrukce `SimpleProjectNode` načítá rastrový obrázek uzlu projektu z prostředků manifestu sestavení a ukládá je do mezipaměti v soukromém poli pro pozdější použití. Všimněte si syntaxe cesty k obrázku <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>. Chcete-li zobrazit názvy prostředků manifestu vložených do sestavení, použijte metodu <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>. Pokud je tato metoda použita pro sestavení `SimpleProject`, výsledky by měly být následující:  
  
- SimpleProject. Resources. Resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources. imagelis. bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject. Resources. SimpleProjectNode. bmp  
  
  Při konstrukci instance načítá `ProjectNode` základní třída Resources. imagelis. bmp, ve kterém jsou vloženy běžně používané rastry 16 x 16 rastrů z Resources\imagelis.bmp. Tento rastrový seznam je zpřístupněn pro `SimpleProjectNode` jako ImageHandler. ImageList. `SimpleProjectNode` připojí rastrový obrázek uzlu projektu k seznamu. Posun rastrového obrázku uzlu projektu v seznamu obrázků je uložen do mezipaměti pro pozdější použití jako hodnota vlastnosti Public `ImageIndex`. Visual Studio používá tuto vlastnost k určení, který rastrový obrázek se má zobrazit jako ikona uzlu projektu.  
  
## <a name="testing-the-custom-project-node-icon"></a>Testování ikony vlastního uzlu projektu  
 Otestujte objekt pro vytváření projektu, abyste viděli, zda vytváří hierarchii projektu, která má vlastní ikonu uzlu projektu.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Otestování ikony vlastního uzlu projektu  
  
1. Spusťte ladění a v experimentální instanci vytvořte nový SimpleProject.  
  
2. V nově vytvořeném projektu si všimněte, že se jako ikona uzlu projektu používá SimpleProjectNode. bmp.  
  
     ![Jednoduchý projekt – uzel nového projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. Otevřete Program.cs v editoru kódu. Měl by se zobrazit zdrojový kód, který se podobá následujícímu kódu.  
  
    ```  
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
  
## <a name="substituting-template-parameters"></a>Nahrazování parametrů šablony  
 V předchozí části jste zaregistrovali šablonu projektu v aplikaci Visual Studio pomocí atributu `ProvideProjectFactory`. Registrace cesty ke složce šablony tímto způsobem umožňuje povolit substituci základní šablony přepsáním a rozšířením `ProjectNode.AddFileFromTemplate` třídy. Další informace naleznete v tématu [Nová generace projektů: pod digestoří, druhá část](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Nyní přidejte náhradní kód do třídy `AddFileFromTemplate`.  
  
#### <a name="to-substitute-template-parameters"></a>Náhrada parametrů šablony  
  
1. Do souboru SimpleProjectNode.cs přidejte následující příkaz `using`.  
  
   ```  
   using System.IO;  
   ```  
  
2. Metodu `AddFileFromTemplate` nahraďte pomocí následujícího kódu.  
  
   ```  
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
  
   Příkazy přiřazení určují přiměřené hodnoty pro obor názvů a nový název třídy. Druhá metoda `ProjectNode.FileTemplateProcessor.AddReplace` volá náhradu odpovídajících hodnot parametrů šablony pomocí těchto nových hodnot.  
  
## <a name="testing-the-template-parameter-substitution"></a>Testování nahrazení parametru šablony  
 Nyní můžete otestovat nahrazování parametrů šablony.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Otestování nahrazení parametru šablony  
  
1. Spusťte ladění a v experimentální instanci vytvořte nový SimpleProject.  
  
2. Spuštění se zastaví na zarážce v metodě `AddFileFromTemplate`.  
  
3. Projděte si hodnoty parametrů `nameSpace` a `className`.  
  
   - `nameSpace` je předána hodnota prvku \<RootNamespace > v souboru šablony projektu \Templates\Projects\SimpleProject\SimpleProject.myproj. V tomto případě je hodnota "MyRootNamespace".  
  
   - `className` je předána hodnota názvu zdrojového souboru třídy bez přípony názvu souboru. V takovém případě je první soubor, který se má zkopírovat do cílové složky, AssemblyInfo.cs; Proto hodnota className je "AssemblyInfo".  
  
4. Odeberte zarážku a stisknutím klávesy F5 pokračujte v provádění.  
  
    Visual Studio by mělo dokončit vytváření projektu.  
  
5. Otevřete Program.cs v editoru kódu. Měl by se zobrazit zdrojový kód, který se podobá následujícímu kódu.  
  
   ```  
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
  
    Všimněte si, že obor názvů je nyní "MyRootNamespace" a název třídy je nyní "program".  
  
6. Spusťte ladění projektu. Nový projekt by měl kompilovat, spouštět a zobrazovat "Hello VSX!!!" v okně konzoly.  
  
    ![Jednoduchý projekt – příkaz](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   Blahopřejeme! Implementovali jste základní spravovaný projektový systém.
