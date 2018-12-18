---
title: Vytvoření systému základního projektu, část 1 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bc0be22f0a5f975f616bfcce942d59399a36ad6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792551"
---
# <a name="creating-a-basic-project-system-part-1"></a>Vytvoření systému základního projektu, část 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty v sadě Visual Studio, jsou kontejnery, které vývojáři použít k uspořádání souborů se zdrojovým kódem a dalších zdrojů. Projekty se zobrazují jako podřízené objekty daného řešení **Průzkumníka řešení**. Projekty umožňují organizovat, sestavovat, ladit a nasadit zdrojový kód a vytvořit odkazy na webové služby, databáze a další prostředky.  
  
 Projekty jsou definovány v souborech projektu, například soubor .csproj projektu Visual C#. Můžete vytvořit vlastní typ projektu, který má vlastní příponou názvu souboru projektu. Další informace o typech projektů naleznete v tématu [typy projektů](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Pokud potřebujete rozšířit do vlastního typu projektu sady Visual Studio, důrazně doporučujeme využívat [systém projektů Visual Studia](https://github.com/Microsoft/VSProjectSystem) které má několik výhod oproti sestavení systém projektu od začátku:  
> 
> - Jednodušší registraci.  Dokonce i systému základního projektu vyžaduje desítky tisíc řádků kódu.  Využití CPS snižuje náklady na připojování na pár kliknutí, předtím, než budete chtít přizpůsobit podle vašich potřeb.  
>   -   Snazší Údržba.  S využitím CPS, stačí udržovat vlastní scénáře.  My se postaráme udržování infrastruktura systému projektu.  
> 
>   Pokud potřebujete cílová verze sady Visual Studio starší než Visual Studio 2013, nebudete moci využít prohlášení CPS v rozšíření sady Visual Studio.  Pokud je to tento případ, Tento názorný postup je vhodné místo abyste mohli začít.  
  
 Tento návod ukazuje, jak vytvořit typ projektu, který má .myproj příponu názvu souboru projektu. Tento názorný postup vypůjčí z existující systém projektu Visual C#.  
  
> [!NOTE]
>  Začátku do konce vzorku systém projektu úplný jazyk, najdete v ukázkové Ironpythonu podrobné informace v [VSSDK ukázky](../misc/vssdk-samples.md).  
  
 Tento návod se naučíte k provedení následujících úkolů:  
  
-   Vytvoření základního projektu typu.  
  
-   Vytvořte šablonu základního projektu.  
  
-   Šablona projektu zaregistrujte pomocí sady Visual Studio.  
  
-   Vytvořit instanci projektu tak, že otevřete **nový projekt** dialogové okno a potom pomocí vlastní šablony.  
  
-   Vytvořte objekt pro vytváření projektu pro projekt systému.  
  
-   Vytvořte uzel projektu pro projekt systému.  
  
-   Přidáte vlastní ikony pro systém projektu.  
  
-   Implementace nahrazení parametru základní šablony.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Musíte si také stáhnout zdrojový kód [Managed Package Framework pro projekty](http://mpfproj12.codeplex.com/). Extrahujte soubor do umístění, které je přístupné k řešení, které se chystáte vytvořit.  
  
## <a name="creating-a-basic-project-type"></a>Vytvoření základního projektu typu  
 Vytvořte projekt VSIX C# s názvem **SimpleProject**. (**Soubor, nový, projekt** a potom **balíčku sady Visual Studio C#, rozšiřitelnosti,**). Přidat šablonu položky projektu balíček Visual Studio (v Průzkumníku řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **Add / nová položka**, pak přejděte na **rozšiřitelnost / balíček Visual Studio**). Název souboru **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Vytvoření základního projektu šablony  
 Nyní můžete upravit tento základní VSPackage implementovat nový typ projektu .myproj. Chcete-li vytvořit projekt, který je založen na typu projektu .myproj, Visual Studio obsahuje vědět, jaké soubory, prostředky a odkazy pro přidání do nového projektu. Tyto informace poskytnout, umístěte soubory projektu ve složce šablony projektu. Když uživatel .myproj projekt pro vytvoření projektu, soubory se zkopírují do nového projektu.  
  
#### <a name="to-create-a-basic-project-template"></a>Chcete-li vytvořit šablonu základního projektu  
  
1. Přidejte tři složky do projektu, jeden v jiné: **Templates\Projects\SimpleProject**. (V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **SimpleProject** uzel projektu, přejděte na **přidat**a potom klikněte na **novou složku**. Název složky `Templates`. V **šablony** složky, přidejte složku s názvem `Projects`. V **projekty** složky, přidejte složku s názvem `SimpleProject`.)  
  
2. V **Projects\SimpleProject** složky přidat soubor ikony s názvem `SimpleProject.ico`. Po kliknutí na **přidat**, otevře se editor ikon.  
  
3. Ujistěte se, na ikonu rozlišovací. Tato ikona se zobrazí v **nový projekt** dialogové okno později v tomto návodu.  
  
    ![Ikona Jednoduchý projekt](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. Ikona uložte a zavřete editor ikon.  
  
5. V **Projects\SimpleProject** složky, přidejte **třídy** položka s názvem `Program.cs`.  
  
6. Nahraďte stávající kód s následujícími řádky.  
  
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
   >  Toto není poslední formulář kód souboru Program.cs; nahrazující parametry budou řešena v pozdějším kroku. Může se zobrazit chyby, ale tak dlouho, dokud soubor **BuildAction** je **obsahu**, byste měli moct sestavit a spustit projekt jako obvykle.  
  
7. Uložte soubor.  
  
8. Zkopírujte soubor AssemblyInfo.cs ze **vlastnosti** složku **Projects\SimpleProject** složky.  
  
9. V **Projects\SimpleProject** složky přidejte soubor XML s názvem `SimpleProject.myproj`.  
  
   > [!NOTE]
   >  Přípona názvu souboru pro všechny projekty tohoto typu je .myproj. Pokud chcete změnit, musíte jej změnit všude, kde je uvedený v tomto návodu.  
  
10. Nahraďte existující obsah s následujícími řádky.  
  
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
  
12. V **vlastnosti** okno, nastaveno **akce sestavení** AssemblyInfo.cs, Program.cs, SimpleProject.ico a SimpleProject.myproj k **obsahu**a nastavte jejich  **Zahrnout do VSIX** vlastností **True**.  
  
    Tuto šablonu projektu popisuje základní Visual C# projekt, který má konfiguraci ladění a konfiguraci vydané verze. Projekt obsahuje dva zdrojové soubory, AssemblyInfo.cs a Program.cs a několik sestavení odkazů. Když se vytvoří projekt ze šablony, hodnota ProjectGuid automaticky nahrazena nový identifikátor GUID.  
  
    V **Průzkumníka řešení**, rozbalených **šablony** složka by měla vypadat následovně:  
  
    Šablony  
  
    Projekty  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Vytváří se objekt pro vytváření základního projektu  
 Visual Studio je zapotřebí sdělit umístění složky šablony projektu. K tomuto účelu přidání atributu do třídy balíčku VSPackage, která implementuje objekt pro vytváření projektů tak, aby umístění šablony se zapisují do systémového registru při vytváření sady VSPackage. Začněte tím, že vytvoříte objekt pro vytváření základního projektu, který je identifikován podle objekt pro vytváření projektu GUID. Použití <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atribut pro připojení k třídě SimpleProjectPackage objekt pro vytváření projektu.  
  
#### <a name="to-create-a-basic-project-factory"></a>Vytvořte objekt pro vytváření základního projektu  
  
1. Otevřete SimpleProjectPackageGuids.cs v editoru kódu.  
  
2. Vytvořit GUID objektu pro vytváření vašeho projektu (na **nástroje** nabídky, klikněte na tlačítko **Create GUID**), nebo použijte v následujícím příkladu. Přidáte identifikátory GUID pro třídu SimpleProjectPackageGuids. Identifikátory GUID musí být ve formátu identifikátoru GUID a formátu řetězce. Výsledný kód by měl vypadat podobně jako v následujícím příkladu.  
  
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
  
3. Přidání třídy do horní části **SimpleProject** složku s názvem `SimpleProjectFactory.cs`.  
  
4. Přidejte následující příkazy using:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Přidáte atribut Guid pro třídu SimpleProjectFactory. Hodnota atributu je nový objekt factory projektu GUID.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Nyní můžete zaregistrovat šablony projektu.  
  
#### <a name="to-register-the-project-template"></a>Chcete-li šablonu projektu zaregistrovat  
  
1. V SimpleProjectPackage.cs, přidejte <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atribut třídy SimpleProjectPackage následujícím způsobem.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Znovu sestavte řešení a ověřte, že sestaví bez chyb.  
  
    Šablona projektu znovu sestavit zaregistruje.  
  
   Parametry `defaultProjectExtension` a `possibleProjectExtensions` jsou nastaveny na příponu názvu souboru projektu (.myproj). `projectTemplatesDirectory` Parametr je nastaven na relativní cestu ke složce šablon. Během sestavování tuto cestu převést na úplné sestavení a přidá do registru k registraci systém projektu.  
  
## <a name="testing-the-template-registration"></a>Testování šablona registrace  
 Šablona registrace instruuje Visual Studio umístění složky projektu šablony tak, aby Visual Studio můžete zobrazit název šablony a ikona v **nový projekt** dialogové okno.  
  
#### <a name="to-test-the-template-registration"></a>K otestování šablona registrace  
  
1. Stisknutím klávesy F5 spusťte ladění v experimentální instanci sady Visual Studio.  
  
2. V experimentální instanci aplikace vytvořte nový projekt typu nově vytvořeného projektu. V **nový projekt** dialogové okno, měli byste vidět **SimpleProject** pod **instalované šablony**.  
  
   Teď máte objekt pro vytváření projektu, který je registrovaný. To však ještě nejde vytvořit projekt. Balíček projektu a objektu pro vytváření projektu společně k vytváření a inicializace projektu.  
  
## <a name="add-the-managed-package-framework-code"></a>Přidejte kód Managed Package Framework  
 Implementace připojení mezi balíček projekt a objektu pro vytváření projektu.  
  
-   Naimportujte soubory zdrojového kódu pro Managed Package Framework.  
  
    1.  Uvolněte projekt SimpleProject (v **Průzkumníka řešení**, vyberte uzel projektu a v místní nabídce klikněte na tlačítko **uvolnit projekt**.) a otevřete soubor projektu v editoru XML.  
  
    2.  Přidejte následující bloky do souboru projektu (přímo nad \<Import > bloků). Nastavte ProjectBasePath na umístění souboru ProjectBase.files v Managed Package Framework kód, který jste si právě stáhli. Budete muset přidat do cesty zpětné lomítko. Pokud ho nevidíte, může selhat projektu nalezení kódu Managed Package Framework.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  Nezapomeňte zpětné lomítko na konci cesty.  
  
    3.  Znovu načte projekt.  
  
    4.  Přidejte odkazy na následující sestavení:  
  
        -   Microsoft.VisualStudio.Designer.Interfaces (v \<VSSDK instalace > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Chcete-li inicializovat objekt pro vytváření projektů  
  
1.  V souboru SimpleProjectPackage.cs, přidejte následující `using` příkazu.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Odvodit `SimpleProjectPackage` třídy z `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Zaregistrujte objekt pro vytváření projektu. Přidejte následující řádek, který `SimpleProjectPackage.Initialize` metoda, hned za `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementovat abstraktní vlastnost `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  V souboru SimpleProjectFactory.cs, přidejte následující `using` příkazem za stávající `using` příkazy.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Odvodit `SimpleProjectFactory` třídy z `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Přidejte následující metodu založenou na `SimpleProjectFactory` třídy. Tato metoda se implementovat v další části.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Přidejte následující pole a konstruktor, aby `SimpleProjectFactory` třídy. To `SimpleProjectPackage` odkaz se uloží do mezipaměti v soukromé pole tak, aby ho můžete použít při nastavení Web poskytovatele služeb.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Znovu sestavte řešení a ověřte, že sestaví bez chyb.  
  
## <a name="testing-the-project-factory-implementation"></a>Testování projektu implementace objektu Factory  
 Otestujte, zda je zavolán konstruktor pro objekt pro vytváření implementaci projektu.  
  
#### <a name="to-test-the-project-factory-implementation"></a>K otestování implementace objektu factory projektu  
  
1.  V souboru SimpleProjectFactory.cs nastavit zarážku na řádek v `SimpleProjectFactory` konstruktoru.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Stisknutím klávesy F5 spusťte experimentální instanci sady Visual Studio.  
  
3.  V experimentální instanci start k vytvoření nového projektu. V **nový projekt** dialogové okno, vyberte SimpleProject typ projektu a pak klikněte na tlačítko **OK**. Provádění zastaví na zarážce.  
  
4.  Zarážka zrušte a zastavte ladění. Protože jsme uzel projektu ještě nevytvořili, kód pro vytvoření projektu stále vyvolá výjimky.  
  
## <a name="extending-the-project-node-class"></a>Rozšíření třídy uzlu projektu  
 Teď můžete implementovat `SimpleProjectNode` třída, která je odvozena z `ProjectNode` třídy. `ProjectNode` Základní třída zpracovává následující úlohy vytvoření projektu:  
  
- Zkopíruje soubor šablony projektu, SimpleProject.myproj, do nové složky projektu. Kopírování je přejmenovat podle názvu, který je zadán v **nový projekt** dialogové okno. `ProjectGuid` Hodnota vlastnosti je nahrazena nový identifikátor GUID.  
  
- Prochází přes prvky MSBuild soubor šablony projektu, SimpleProject.myproj a hledá `Compile` elementy. Pro každou `Compile` cílový soubor, zkopíruje soubor do nové složky projektu.  
  
  Odvozená `SimpleProjectNode` třída zpracovává tyto úlohy:  
  
- Umožňuje ikony pro projekt a soubor uzly v **Průzkumníka řešení** vytvořili, nebo vybraná.  
  
- Umožňuje náhrad parametrů šablony další projekt zadat.  
  
#### <a name="to-extend-the-project-node-class"></a>Rozšíření třídy uzlu projektu  
  
1. 
  
2. Přidejte třídu pojmenovanou `SimpleProjectNode.cs`.  
  
3. Nahraďte stávající kód následujícím kódem.  
  
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
  
   To `SimpleProjectNode` třída implementace má tyto přepsané metody:  
  
- `ProjectGuid`, která vrací objekt pro vytváření projektu GUID.  
  
- `ProjectType`, která vrací lokalizovaný název typu projektu.  
  
- `AddFileFromTemplate`, který zkopíruje vybrané soubory ze složky šablony na cílový projekt. Tato metoda je implementována dále v další části.  
  
  `SimpleProjectNode` Konstruktoru, třeba `SimpleProjectFactory` konstruktor ukládá do mezipaměti `SimpleProjectPackage` odkaz v soukromé pole pro pozdější použití.  
  
  Pro připojení `SimpleProjectFactory` třídu `SimpleProjectNode` třídy, je nutné vytvořit novou instanci `SimpleProjectNode` v `SimpleProjectFactory.CreateProject` metoda a ukládání do mezipaměti v soukromé pole pro pozdější použití.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Pro připojení třídy objekt pro vytváření projektů a uzlu  
  
1.  V souboru SimpleProjectFactory.cs, přidejte následující `using` – příkaz:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Nahradit `SimpleProjectFactory.CreateProject` metoda pomocí následujícího kódu.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Znovu sestavte řešení a ověřte, že sestaví bez chyb.  
  
## <a name="testing-the-project-node-class"></a>Třída Project Node testování  
 Otestujte svůj projekt objekt pro vytváření zobrazíte, jestli se vytvoří hierarchii projektu.  
  
#### <a name="to-test-the-project-node-class"></a>K otestování třída project node  
  
1.  Stisknutím klávesy F5 spusťte ladění. V experimentální instanci aplikace vytvořte nový SimpleProject.  
  
2.  Visual Studio by měly volat výrobce projekt pro vytvoření projektu.  
  
3.  Ukončete experimentální instanci sady Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Přidání uzlu ikony vlastních projektů  
 Ikona uzel projektu v dřívější části je výchozí ikona. Můžete ho změnit na vlastní ikonu.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Chcete-li přidat ikonu uzel vlastní projekt  
  
1. V **prostředky** složky, přidejte soubor rastrového obrázku s názvem SimpleProjectNode.bmp.  
  
2. V **vlastnosti** windows, snižte rastrového obrázku nastaven na 16 × 16 pixelů. Zkontrolujte rozlišovací rastrového obrázku.  
  
    ![Jednoduchý projekt – příkaz](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. V **vlastnosti** okno Změnit **akce sestavení** rastrového obrázku na **integrovaný prostředek**.  
  
4. V souboru SimpleProjectNode.cs, přidejte následující `using` příkazy:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Přidejte následující statická pole a konstruktoru `SimpleProjectNode` třídy.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Přidejte následující vlastnost na začátek `SimpleProjectNode` třídy.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Konstruktor instance nahraďte následujícím kódem.  
  
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
  
   Během statické konstrukce `SimpleProjectNode` načte rastrového obrázku uzlu projektu z prostředky manifestu sestavení a ukládá do mezipaměti v soukromé pole pro pozdější použití. Všimněte si, že syntaxe <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> cestu k bitové kopii. Chcete-li zobrazit názvy prostředky manifestu vložen do sestavení, použijte <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metody. Když tato metoda platí pro `SimpleProject` sestavení, výsledky by měl vypadat takto:  
  
- SimpleProject.Resources.resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources.imagelis.bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Při vytváření instance `ProjectNode` Resources.imagelis.bmp, ve kterém jsou vložené běžně používaných bitmapy 16 x 16 z Resources\imagelis.bmp načte základní třídy. Tento seznam rastrového obrázku je k dispozici `SimpleProjectNode` jako ImageHandler.ImageList. `SimpleProjectNode` připojí rastrového obrázku uzlu projektu do seznamu. Posun rastrového obrázku uzlu projektu v seznamu obrázků se uloží do mezipaměti pro pozdější použití jako hodnota veřejnosti `ImageIndex` vlastnost. Visual Studio používá tuto vlastnost k určení, které rastrový obrázek pro zobrazit jako ikonu uzlu projektu.  
  
## <a name="testing-the-custom-project-node-icon"></a>Uzel ikona vlastních projektů testování  
 Otestujte svůj projekt objekt pro vytváření zobrazíte, jestli se vytvoří hierarchii projektu, který má ikonu uzel vaše vlastní projekt.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Uzel ikona vlastních projektů testování  
  
1.  Spustit ladění a vytvořte nový SimpleProject v experimentální instanci aplikace.  
  
2.  V nově vytvořeného projektu Všimněte si, že SimpleProjectNode.bmp slouží jako ikona uzlu projektu.  
  
     ![Jednoduchý projekt nový uzel projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Otevřete soubor Program.cs v editoru kódu. Měli byste vidět zdrojový kód, který vypadá podobně jako následující kód.  
  
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
  
     Všimněte si, že parametry šablony $nameSpace$ a $className$ nemají nové hodnoty. Se dozvíte, jak implementovat nahrazení parametru šablony v další části.  
  
## <a name="substituting-template-parameters"></a>Nahraďte parametry šablony  
 V předchozí části jste zaregistrovali šablona projektu pomocí sady Visual Studio pomocí `ProvideProjectFactory` atribut. Registrace cestu ke složce šablon tímto způsobem umožňuje povolit nahrazení parametru základní šablony pomocí přepisování a rozšiřování `ProjectNode.AddFileFromTemplate` třídy. Další informace najdete v tématu [nová generace projektů: pod pokličkou, část dvě](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Teď přidejte kód nahrazení, který `AddFileFromTemplate` třídy.  
  
#### <a name="to-substitute-template-parameters"></a>Nahradit parametry šablony  
  
1. V souboru SimpleProjectNode.cs, přidejte následující `using` příkazu.  
  
   ```  
   using System.IO;  
   ```  
  
2. Nahradit `AddFileFromTemplate` metoda pomocí následujícího kódu.  
  
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
  
3. Nastavte zarážku v metodě bezprostředně po `className` příkazu přiřazení.  
  
   Přiřazovací příkazy určit rozumné hodnoty pro obor názvů a nový název třídy. Dva `ProjectNode.FileTemplateProcessor.AddReplace` volání metody nahradí odpovídající hodnoty parametrů šablony s použitím těchto nových hodnot.  
  
## <a name="testing-the-template-parameter-substitution"></a>Testování nahrazení parametru šablony  
 Nyní můžete otestovat nahrazení parametru šablony.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>K otestování nahrazení parametru šablony  
  
1. Spustit ladění a vytvořte nový SimpleProject v experimentální instanci aplikace.  
  
2. Provádění zastaví na zarážce v `AddFileFromTemplate` metody.  
  
3. Zkontrolujte hodnoty `nameSpace` a `className` parametry.  
  
   -   `nameSpace` je přiřazena hodnota \<RootNamespace > element v souboru šablony projektu \Templates\Projects\SimpleProject\SimpleProject.myproj. V tomto případě je hodnota "MyRootNamespace".  
  
   -   `className` Hodnota třídy název zdrojového souboru, bez přípony názvu souboru je uveden. V tomto případě prvního souboru, které se mají zkopírovat do cílové složky je AssemblyInfo.cs; Hodnota className tedy "AssemblyInfo".  
  
4. Odeberte zarážku a stisknutím klávesy F5 pokračovat v provádění.  
  
    Visual Studio by měl dokončit vytváření projektu.  
  
5. Otevřete soubor Program.cs v editoru kódu. Měli byste vidět zdrojový kód, který vypadá podobně jako následující kód.  
  
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
  
    Všimněte si, že obor názvů je nyní "MyRootNamespace" a název třídy je nyní "Program".  
  
6. Spusťte ladění projektu. Nový projekt by měl kompilaci, spuštění a zobrazí "Hello VSX!!!" v okně konzoly.  
  
    ![Příkaz Jednoduchý projekt](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   Blahopřejeme! Jste implementovali systému základního spravovaného projektu.

