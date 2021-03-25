---
title: Vytvoření základního systému projektu, část 2 | Microsoft Docs
description: Naučte se, jak do projektu vytvořeného v předchozím článku přidat šablonu, stránku vlastností a další funkce sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a60bdc7a6cbd73e85248f6ea5897ad3e56337113
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089417"
---
# <a name="create-a-basic-project-system-part-2"></a>Vytvoření základního projektového systému, část 2
První návod v této sérii, který [vytvoří základní projektový systém, část 1](../extensibility/creating-a-basic-project-system-part-1.md), ukazuje, jak vytvořit základní projektový systém. Tento návod sestaví základní systém projektu přidáním šablony sady Visual Studio, stránky vlastností a dalších funkcí. Před zahájením tohoto postupu je nutné nejprve provést první návod.

Tento návod vás seznámí s postupem vytvoření typu projektu, který má příponu názvu souboru projektu *. myproj*. K dokončení tohoto návodu nemusíte vytvářet vlastní jazyk, protože návod je vypůjčen z existujícího systému projektu Visual C#.

Tento návod učí, jak provádět tyto úlohy:

- Vytvořte šablonu sady Visual Studio.

- Nasaďte šablonu sady Visual Studio.

- V dialogovém okně **Nový projekt** Vytvořte podřízený uzel typu projektu.

- Povolte substituci parametrů v šabloně sady Visual Studio.

- Vytvoří stránku vlastností projektu.

> [!NOTE]
> Kroky v tomto návodu jsou založeny na projektu C#. Avšak s výjimkou specifických jako přípon názvů souborů a kódu, můžete použít stejný postup pro Visual Basic projekt.

## <a name="create-a-visual-studio-template"></a>Vytvoření šablony sady Visual Studio
- [Vytvoření základního projektového systému, část 1 ukazuje,](../extensibility/creating-a-basic-project-system-part-1.md) jak vytvořit základní šablonu projektu a přidat ji do systému projektu. Také ukazuje, jak zaregistrovat tuto šablonu v aplikaci Visual Studio pomocí <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atributu, který zapisuje úplnou cestu ke složce *\\ Templates\Projects\SimpleProject \\* v systémovém registru.

Pomocí šablony sady Visual Studio (soubor *. vstemplate* ) namísto základní šablony projektu můžete určit, jak se šablona zobrazí v dialogovém okně **Nový projekt** a jak budou nahrazeny parametry šablony. Soubor *. vstemplate* je soubor XML, který popisuje, jak se mají zahrnout zdrojové soubory při vytvoření projektu pomocí šablony systém projektu. Samotný projektový systém je sestaven tak, že shromažďuje soubor *. vstemplate* a zdrojové soubory v souboru *. zip* a je nasazen zkopírováním souboru *. zip* do umístění, které je známo v aplikaci Visual Studio. Tento proces je podrobněji vysvětlen dále v tomto návodu.

1. V aplikaci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otevřete řešení SimpleProject, které jste vytvořili pomocí následujícího způsobu [Vytvoření základního projektového systému, část 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. V souboru *SimpleProjectPackage. cs* Najděte atribut ProvideProjectFactory. Nahraďte druhý parametr (název projektu) hodnotou null a čtvrtým parametrem (cestu ke složce šablony projektu) řetězcem ". \\ \NullPath ", jak je znázorněno níže.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Přidejte soubor XML s názvem *SimpleProject. vstemplate* do složky *\\ Templates\Projects\SimpleProject \\* .

4. Nahraďte obsah *SimpleProject. vstemplate* následujícím kódem.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. V okně **vlastnosti** vyberte všechny pět souborů ve složce *\\ Templates\Projects\SimpleProject \\* a nastavte **akci sestavení** na **ZipProject**.

    ![Jednoduchá složka projektu](../extensibility/media/simpproj2.png "SimpProj2")

    \<TemplateData>Oddíl určuje umístění a vzhled typu projektu SimpleProject v dialogovém okně **Nový projekt** následujícím způsobem:

- \<Name>Element pojmenovává šablonu projektu, aby se SimpleProject aplikace.

- \<Description>Element obsahuje popis, který se zobrazí v dialogovém okně **Nový projekt** při výběru šablony projektu.

- \<Icon>Prvek určuje ikonu, která se zobrazí spolu s typem projektu SimpleProject.

- \<ProjectType>Element pojmenuje typ projektu v dialogovém okně **Nový projekt** . Tento název nahrazuje parametr názvu projektu atributu ProvideProjectFactory.

  > [!NOTE]
  > \<ProjectType>Element musí odpovídat `LanguageVsTemplate` argumentu `ProvideProjectFactory` atributu v souboru SimpleProjectPackage. cs.

  \<TemplateContent>Oddíl popisuje tyto soubory, které jsou generovány při vytvoření nového projektu:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Všechny tři soubory jsou `ReplaceParameters` nastaveny na hodnotu true, což umožňuje substituci parametrů. Soubor *program. cs* je `OpenInEditor` nastaven na hodnotu true, což způsobí, že se soubor při vytvoření projektu otevře v editoru kódu.

  Další informace o prvcích ve schématu šablony sady Visual Studio naleznete v tématu Referenční dokumentace [schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Pokud má projekt více než jednu šablonu sady Visual Studio, Každá šablona je v samostatné složce. Každý soubor v této složce musí mít **akci sestavení** nastavenou na **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Přidání minimálního souboru. vsct
 Aby bylo možné rozpoznat novou nebo upravenou šablonu sady Visual Studio, je nutné spustit aplikaci Visual Studio v režimu instalace. Režim instalace vyžaduje, aby byl k dispozici soubor *. vsct* . Proto musíte do projektu přidat minimální soubor *. vsct* .

1. Do projektu SimpleProject přidejte soubor XML s názvem *SimpleProject. vsct* .

2. Obsah souboru *SimpleProject. vsct* nahraďte následujícím kódem.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Nastavte **akci sestavení** tohoto souboru na **VSCTCompile**. To lze provést pouze v souboru *. csproj* , nikoli v okně **vlastnosti** . Ujistěte se, že **Akce sestavení** tohoto souboru je v tomto okamžiku nastavena na **hodnotu None** .

    1. Klikněte pravým tlačítkem na uzel SimpleProject a pak klikněte na **Upravit SimpleProject. csproj**.

    2. V souboru *. csproj* Najděte položku *SimpleProject. vsct* .

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Změňte akci sestavení na **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. soubor projektu a zavřít editor.

    5. Uložte uzel SimpleProject a potom v **Průzkumník řešení** klikněte na **znovu načíst projekt**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Projděte si postup sestavení šablony sady Visual Studio.
 Systém sestavení projektu VSPackage obvykle spouští aplikaci Visual Studio v režimu instalace, když je změněn soubor *. vstemplate* , nebo je znovu sestaven projekt, který obsahuje soubor *. vstemplate* . Můžete postupovat podle nastavení úrovně podrobností MSBuild na normální nebo vyšší.

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Rozbalte uzel **projekty a řešení** a pak vyberte **sestavení a spustit**.

3. Nastavte **Podrobnosti výstupu sestavení projektu MSBuild** na **normální**. Klikněte na **OK**.

4. Znovu sestavte projekt SimpleProject.

    Krok sestavení pro vytvoření souboru projektu *. zip* by měl vypadat podobně jako v následujícím příkladu.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Nasazení šablony sady Visual Studio
Šablony sady Visual Studio neobsahují informace o cestě. Proto musí být soubor template *. zip* nasazen do umístění, které je známo v aplikaci Visual Studio. Umístění složky ProjectTemplates je obvykle *<% localappdata% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.

K nasazení objektu pro vytváření projektu musí mít Instalační program oprávnění správce. Nasadí šablony pod uzlem instalace sady Visual Studio: *. ..\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testování šablony sady Visual Studio
Otestujte objekt pro vytváření projektu, abyste viděli, zda vytváří hierarchii projektu pomocí šablony sady Visual Studio.

1. Resetovat experimentální instanci sady Visual Studio SDK.

    Zapnuto [!INCLUDE[win7](../debugger/includes/win7_md.md)] : v nabídce **Start** Najděte složku **Microsoft Visual Studio/Microsoft Visual Studio SDK/nástroje** a pak vyberte **obnovit Microsoft Visual Studio experimentální instanci**.

    V novějších verzích Windows: na obrazovce **Start** zadejte **resetování Microsoft Visual Studio \<version> experimentální instance**.

2. Zobrazí se okno příkazového řádku. Po zobrazení slov **stiskněte libovolnou klávesu a pokračujte** tím, že kliknete na **ENTER**. Po zavření okna otevřete Visual Studio.

3. Znovu sestavte projekt SimpleProject a spusťte ladění. Objeví se experimentální instance.

4. V experimentální instanci vytvořte projekt SimpleProject. V dialogovém okně **Nový projekt** vyberte **SimpleProject**.

5. Měla by se zobrazit nová instance SimpleProject.

    ![Jednoduchá instance nového projektu](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Moje nová instance projektu](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Vytvoření podřízeného uzlu typu projektu
Můžete přidat podřízený uzel do uzlu typ projektu v dialogovém okně **Nový projekt** . Například pro typ projektu SimpleProject můžete mít podřízené uzly pro konzolové aplikace, aplikace oken, webové aplikace a tak dále.

Podřízené uzly jsou vytvořeny změnou souboru projektu a přidáním \<OutputSubPath> podřízených \<ZipProject> prvků do prvků. Při kopírování šablony během sestavení nebo nasazení se každý podřízený uzel stal podsložkou složky šablony projektu.

V této části se dozvíte, jak vytvořit podřízený uzel konzoly pro typ projektu SimpleProject.

1. Přejmenujte složku *\\ Templates\Projects\SimpleProject \\* na *\\ Templates\Projects\ConsoleApp \\*.

2. V okně **vlastnosti** vyberte všechny pět souborů ve složce *\\ Templates\Projects\ConsoleApp \\* a ujistěte se, že je **Akce sestavení** nastavena na **ZipProject**.

3. V souboru SimpleProject. vstemplate přidejte následující řádek na konci \<TemplateData> oddílu těsně před uzavírací značku.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    To způsobí, že se Šablona konzolové aplikace zobrazí v podřízeném uzlu konzoly i v nadřazeném uzlu SimpleProject, což je jedna úroveň nad podřízený uzel.

4. Uložte soubor *SimpleProject. vstemplate* .

5. V souboru *. csproj* přidejte \<OutputSubPath> do každého elementu ZipProject. Uvolněte projekt jako dříve a upravte soubor projektu.

6. Vyhledejte \<ZipProject> prvky. Do každého \<ZipProject> elementu přidejte \<OutputSubPath> prvek a přidělte mu hodnotu Console. ZipProject

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Přidejte tento \<PropertyGroup> soubor do souboru projektu:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Uložte soubor projektu a znovu načtěte projekt.

## <a name="test-the-project-type-child-node"></a>Test podřízeného uzlu typu projektu
Otestujte upravený soubor projektu, abyste viděli, zda se v dialogovém okně **Nový projekt** zobrazuje podřízený uzel **konzoly** .

1. Spusťte **resetování nástroje Microsoft Visual Studio experimentální instance** .

2. Znovu sestavte projekt SimpleProject a spusťte ladění. Experimentální instance by se měla zobrazit

3. V dialogovém okně **Nový projekt** klikněte na uzel **SimpleProject** . V podokně **šablony** by se měla zobrazit Šablona **konzolové aplikace** .

4. Rozbalte uzel **SimpleProject** . Měl by se zobrazit podřízený uzel **konzoly** . Šablona **aplikace SimpleProject** se v podokně **šablony** stále zobrazuje.

5. Klikněte na **Zrušit** a zastavte ladění.

    ![Jednoduché Shrnutí projektů](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Jednoduchý uzel konzoly projektu](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Nahradit parametry šablony projektu
- Při [vytváření základního projektového systému, část 1](../extensibility/creating-a-basic-project-system-part-1.md) ukázala, jak přepsat `ProjectNode.AddFileFromTemplate` metodu pro provedení základního typu nahrazení parametru šablony. V této části se naučíte, jak používat propracovanější parametry šablon sady Visual Studio.

Při vytváření projektu pomocí šablony sady Visual Studio v dialogovém okně **Nový projekt** jsou parametry šablony nahrazeny řetězcem pro přizpůsobení projektu. Parametr šablony je speciální token, který začíná a končí znakem dolaru, například $time $. Následující dva parametry jsou zvláště užitečné pro povolení přizpůsobení v projektech, které jsou založeny na šabloně:

- $GUID [1-10] $ nahrazuje nový identifikátor GUID. Můžete zadat až 10 jedinečných identifikátorů GUID, například $guid $1.

- $safeprojectname $ je název poskytnutý uživatelem v dialogovém okně **Nový projekt** , který se upraví tak, aby se odebraly všechny nezabezpečené znaky a mezery.

  Úplný seznam parametrů šablony najdete v tématu [parametry šablony](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Náhrada parametrů šablony projektu

1. V souboru *SimpleProjectNode. cs* odeberte `AddFileFromTemplate` metodu.

2. V souboru *\\ Templates\Projects\ConsoleApp\SimpleProject.myproj* vyhledejte \<RootNamespace> vlastnost a změňte její hodnotu na $safeprojectname $.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. V souboru *\\ Templates\Projects\SimpleProject\Program.cs* nahraďte obsah souboru následujícím kódem:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Znovu sestavte projekt SimpleProject a spusťte ladění. Měla by se zobrazit experimentální instance.

5. Vytvořte novou konzolovou aplikaci SimpleProject. (V podokně **typy projektů** vyberte možnost **SimpleProject**. V části **Nainstalované šablony sady Visual Studio** vyberte **Konzolová aplikace**.)

6. V nově vytvořeném projektu otevřete *program. cs*. Měl by vypadat nějak takto (hodnoty GUID v souboru se budou lišit.):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Vytvoření stránky vlastností projektu
Můžete vytvořit stránku vlastností pro typ projektu, aby uživatelé mohli zobrazit a změnit vlastnosti v projektech, které jsou založeny na vaší šabloně. V této části se dozvíte, jak vytvořit stránku vlastností nezávislá na konfiguraci. Tato základní stránka vlastností používá mřížku vlastností k zobrazení veřejných vlastností, které vystavíte ve třídě stránky vlastností.

Odvodit třídu stránky vlastností ze `SettingsPage` základní třídy. Mřížka vlastností poskytovaná `SettingsPage` třídou ví o většině primitivních datových typů a ví, jak je zobrazit. Kromě toho `SettingsPage` třída ví, jak uchovat hodnoty vlastností do souboru projektu.

Stránka vlastností, kterou vytvoříte v této části, vám umožní změnit a uložit tyto vlastnosti projektu:

- Doplňk

- OutputType

- RootNamespace.

1. V souboru *SimpleProjectPackage. cs* přidejte tento `ProvideObject` atribut do `SimpleProjectPackage` třídy:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Tím se registruje třída stránky vlastností `GeneralPropertyPage` s com.

2. V souboru *SimpleProjectNode. cs* přidejte tyto dvě přepsané metody do `SimpleProjectNode` třídy:

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Obě tyto metody vracejí pole identifikátorů GUID stránky vlastností. Identifikátor GUID GeneralPropertyPage je jediným prvkem v poli, takže se v dialogovém okně **stránky vlastností** zobrazí pouze jedna stránka.

3. Přidejte do projektu SimpleProject soubor třídy s názvem *GeneralPropertyPage. cs* .

4. Obsah tohoto souboru nahraďte pomocí následujícího kódu:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    `GeneralPropertyPage`Třída zveřejňuje tři veřejné vlastnosti AssemblyName, OutputType a RootNamespace. Protože parametr AssemblyName nemá žádnou metodu set, je zobrazen jako vlastnost jen pro čtení. Element OutputType je Výčtová konstanta, takže se zobrazuje jako rozevírací seznam.

    `SettingsPage`Základní třída zajišťuje `ProjectMgr` zachování vlastností. `BindProperties`Metoda používá `ProjectMgr` k načtení trvalých hodnot vlastností a nastavení odpovídajících vlastností. `ApplyChanges`Metoda používá `ProjectMgr` k získání hodnot vlastností a jejich uchování do souboru projektu. Metoda set vlastnosti nastaví `IsDirty` na hodnotu true, aby označovala, že vlastnosti musí být trvalé. K trvalosti dojde při uložení projektu nebo řešení.

5. Znovu sestavte řešení SimpleProject a spusťte ladění. Měla by se zobrazit experimentální instance.

6. V experimentální instanci vytvořte novou aplikaci SimpleProject.

7. Visual Studio volá vaši továrnu projektu, aby vytvořila projekt pomocí šablony sady Visual Studio. Nový soubor *program. cs* je otevřen v editoru kódu.

8. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a pak klikněte na **vlastnosti**. Zobrazí se dialogové okno **Stránky vlastností**.

    ![Stránka vlastností jednoduchého projektu](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testování stránky vlastností projektu
Nyní můžete testovat, zda lze upravit a změnit hodnoty vlastností.

1. V dialogovém okně **stránky vlastností MyConsoleApplication** změňte **DefaultNamespace** na **MyApplication**.

2. Vyberte vlastnost **OutputType** a pak vyberte **Knihovna tříd**.

3. Klikněte na **použít** a pak na **OK**.

4. Znovu otevřete dialogové okno **stránky vlastností** a ověřte, zda byly vaše změny trvalé.

5. Zavřete experimentální instanci sady Visual Studio.

6. Znovu otevřete experimentální instanci.

7. Znovu otevřete dialogové okno **stránky vlastností** a ověřte, zda byly vaše změny trvalé.

8. Zavřete experimentální instanci sady Visual Studio.
    ![Zavřít experimentální instanci](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
