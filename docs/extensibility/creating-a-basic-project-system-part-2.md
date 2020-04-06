---
title: Vytvoření základního projektového systému, část 2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739711"
---
# <a name="create-a-basic-project-system-part-2"></a>Vytvoření základního projektového systému, část 2
První návod v této řadě [Vytvořit základní projektový systém, část 1](../extensibility/creating-a-basic-project-system-part-1.md), ukazuje, jak vytvořit základní systém projektu. Tento návod vychází ze základního systému projektu přidáním šablony sady Visual Studio, stránky vlastností a dalších funkcí. Před spuštěním tohoto návodu je nutné dokončit první návod.

Tento návod učí, jak vytvořit typ projektu, který má příponu název souboru projektu *.myproj*. Chcete-li dokončit návod, není třeba vytvořit vlastní jazyk, protože návod si vypůjčí z existujícího systému projektu Visual C#.

Tento návod učí, jak provádět tyto úkoly:

- Vytvořte šablonu sady Visual Studio.

- Nasazení šablony sady Visual Studio

- Vytvořte podřízený uzel typu projektu v dialogovém okně **Nový projekt.**

- Povolte nahrazení parametrů v šabloně sady Visual Studio.

- Vytvořte stránku vlastností projektu.

> [!NOTE]
> Kroky v tomto návodu jsou založeny na projektu Jazyka C#. Však s výjimkou specifika, jako je například přípony názvu souboru a kód, můžete použít stejné kroky pro projekt jazyka.

## <a name="create-a-visual-studio-template"></a>Vytvoření šablony Sady Visual Studio
- [Vytvořte základní systém projektu, část 1 ukazuje,](../extensibility/creating-a-basic-project-system-part-1.md) jak vytvořit základní šablonu projektu a přidat ji do systému projektu. Také ukazuje, jak zaregistrovat tuto šablonu <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> v sadě Visual Studio pomocí atributu, který zapisuje úplnou cestu ke složce * \\Templates\Projects\SimpleProject\\ * v systémovém registru.

Pomocí šablony sady Visual Studio (*soubor .vstemplate)* namísto základní šablony projektu můžete určit, jak se šablona zobrazí v dialogovém okně **Nový projekt** a jak budou nahrazeny parametry šablony. Soubor *.vstemplate* je soubor XML, který popisuje, jak mají být zahrnuty zdrojové soubory při vytváření projektu pomocí šablony systému projektu. Samotný systém projektu je vytvořen shromažďováním souboru *.vstemplate* a zdrojových souborů v souboru *ZIP* a nasazeným zkopírováním souboru *ZIP* do umístění, které je známé sadě Visual Studio. Tento proces je podrobněji vysvětlen dále v tomto návodu.

1. V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aplikaci otevřete řešení SimpleProject, které jste vytvořili v následující části [1 .](../extensibility/creating-a-basic-project-system-part-1.md)

2. V *souboru SimpleProjectPackage.cs* vyhledejte atribut ProvideProjectFactory. Nahraďte druhý parametr (název projektu) hodnotou null a čtvrtý parametr (cesta ke složce šablony projektu) hodnotou ". \\\NullPath", takto.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Přidejte soubor XML s názvem *SimpleProject.vstemplate* do složky * \\Templates\Projects\SimpleProject.\\ *

4. Nahraďte obsah *simpleproject.vstemplate* následujícím kódem.

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

5. V okně **Vlastnosti** vyberte všech pět souborů ve složce * \\Templates\Projects\SimpleProject\\ * a nastavte **akci sestavení** na **ZipProject**.

    ![Jednoduchá složka projektu](../extensibility/media/simpproj2.png "SimpProj2")

    Oddíl \<TemplateData> určuje umístění a vzhled typu projektu SimpleProject v dialogovém okně **Nový projekt** takto:

- Element \<Name> pojmenuje šablonu projektu jako aplikaci SimpleProject.

- Prvek \<Popis> obsahuje popis, který se zobrazí v dialogovém okně **Nový projekt,** když je vybrána šablona projektu.

- Prvek \<Icon> určuje ikonu, která se zobrazí společně s typem projektu SimpleProject.

- Prvek \<ProjectType> názvy typu projektu v dialogovém okně **Nový projekt.** Tento název nahradí parametr název projektu atributu ProvideProjectFactory.

  > [!NOTE]
  > Prvek \<ProjectType> musí `LanguageVsTemplate` odpovídat `ProvideProjectFactory` argumentu atributu v souboru SimpleProjectPackage.cs.

  Oddíl \<TemplateContent> popisuje tyto soubory, které jsou generovány při vytvoření nového projektu:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Všechny tři `ReplaceParameters` soubory mají nastavena na hodnotu true, což umožňuje nahrazení parametrů. Soubor *Program.cs* `OpenInEditor` nastavena na hodnotu true, což způsobí, že soubor má být otevřen v editoru kódu při vytvoření projektu.

  Další informace o prvcích ve schématu šablony sady Visual Studio naleznete v [odkazu na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Pokud projekt obsahuje více než jednu šablonu sady Visual Studio, každá šablona je v samostatné složce. Každý soubor v této složce musí mít **akci sestavení** nastavenou na **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Přidání minimálního souboru VSCT
 Visual Studio musí být spuštěno v režimu instalace, aby bylo možné rozpoznat novou nebo upravenou šablonu sady Visual Studio. Instalační režim vyžaduje, aby byl přítomen soubor *VSCT.* Proto je nutné přidat minimální *.vsct* soubor do projektu.

1. Přidejte do projektu SimpleProject soubor XML s názvem *SimpleProject.vsct.*

2. Nahraďte obsah souboru *SimpleProject.vsct* následujícím kódem.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Nastavte **akci sestavení** tohoto souboru na **VSCTCompile**. To lze provést pouze v souboru *.csproj,* nikoli v okně **Vlastnosti.** Ujistěte se, že **akce sestavení** tohoto souboru je nastavena na **žádný** v tomto okamžiku.

    1. Klepněte pravým tlačítkem myši na uzel SimpleProject a potom klepněte na příkaz **Upravit soubor SimpleProject.csproj**.

    2. V souboru *.csproj* vyhledejte položku *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Změňte akci sestavení na **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. a zavřete editor.

    5. Uložte uzel SimpleProject a potom v **Průzkumníku řešení** klepněte na tlačítko **Znovu načíst project**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Prohlédněte si kroky sestavení šablony sady Visual Studio
 Systém sestavení projektu VSPackage obvykle spouští visual studio v režimu instalace při změně souboru *.vstemplate* nebo při opětovném sestavení projektu, který obsahuje soubor *.vstemplate.* Můžete sledovat podél nastavením úroveň podrobností MSBuild na normální nebo vyšší.

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. Rozbalte uzel **Projekty a řešení** a pak vyberte **Sestavit a spustit**.

3. Nastavte **podrobnost výstupu sestavení projektu MSBuild** na **normální**. Klikněte na tlačítko **OK**.

4. Znovu sestavte projekt SimpleProject.

    Krok sestavení k vytvoření souboru projektu *ZIP* by se měl podobat následujícímu příkladu.

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

## <a name="deploy-a-visual-studio-template"></a>Nasazení šablony Sady Visual Studio
Šablony sady Visual Studio neobsahují informace o cestě. Proto musí být soubor *.zip* šablony nasazen do umístění, které je známé visual studio. Umístění složky ProjectTemplates je obvykle *<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.

Chcete-li nasadit továrnu projektu, musí mít instalační program oprávnění správce. Nasazuje šablony v instalačním uzlu sady Visual Studio: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testování šablony sady Visual Studio
Otestujte továrnu projektu a zjistěte, zda vytvoří hierarchii projektu pomocí šablony sady Visual Studio.

1. Obnovte experimentální instanci sady Visual Studio SDK.

    Zapnuto [!INCLUDE[win7](../debugger/includes/win7_md.md)]: V nabídce **Start** vyhledejte složku Microsoft **Visual Studio/Microsoft Visual Studio SDK/Tools** a pak vyberte **Obnovit instanci Microsoft Visual Studio Experimental**.

    V novějších verzích systému Windows: Na **úvodní** obrazovce zadejte **příkaz Reset verze aplikace Microsoft Visual Studio \<> Experimental Instance**.

2. Zobrazí se okno příkazového řádku. Po zobrazení slov **Pokračujte stisknutím libovolné klávesy**klepněte na tlačítko **ENTER**. Po zavření okna otevřete Visual Studio.

3. Znovu sestavte projekt SimpleProject a začněte ladění. Zobrazí se experimentální instance.

4. V experimentální instanci vytvořte projekt SimpleProject. V dialogovém okně **Nový projekt** vyberte Možnost **Jednoduchý projekt**.

5. Měli byste vidět novou instanci SimpleProject.

    ![Jednoduchá nová instance projektu](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Moje nová instance projektu](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Vytvoření podřízeného uzlu typu projektu
Podřízený uzel můžete přidat do uzlu typu projektu v dialogovém okně **Nový projekt.** Například pro typ projektu SimpleProject můžete mít podřízené uzly pro konzolové aplikace, aplikace oken, webové aplikace a tak dále.

Podřízené uzly jsou vytvořeny změnou \<souboru projektu a \<přidáním OutputSubPath> podřízené položky zipproject> prvky. Při kopírování šablony během sestavení nebo nasazení se každý podřízený uzel stane podsložkou složky šablon projektu.

Tato část ukazuje, jak vytvořit podřízený uzel konzoly pro typ projektu SimpleProject.

1. Přejmenujte složku * \\Templates\Projects\SimpleProject\\ * na * \\Templates\Projects\ConsoleApp\\*.

2. V okně **Vlastnosti** vyberte všech pět souborů ve složce * \\Templates\Projects\ConsoleApp\\ * a ujistěte se, že je **akce sestavení** nastavena na **zipproject**.

3. Do souboru SimpleProject.vstemplate přidejte následující řádek \<na konec části TemplateData> těsně před uzavírací značku.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    To způsobí, že šablona konzolové aplikace se zobrazí v podřízeném uzlu konzoly a v nadřazeném uzlu SimpleProject, který je o jednu úroveň nad podřízeným uzlem.

4. Uložte soubor *SimpleProject.vstemplate.*

5. V souboru *.csproj* přidejte \<outputsubpath> ke každému z prvků ZipProject. Uvolněte projekt stejně jako dříve a upravte soubor projektu.

6. Vyhledejte \<prvky> ZipProject. Ke \<každému prvku ZipProject \<> přidejte element OutputSubPath> a přiřazujte mu hodnotu Console. The ZipProject

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

7. Přidejte \<tuto> Skupiny vlastností do souboru projektu:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Uložte soubor projektu a znovu načtěte projekt.

## <a name="test-the-project-type-child-node"></a>Otestovat podřízený uzel typu projektu
Otestujte upravený soubor projektu a zjistěte, zda se podřízený uzel **konzoly** zobrazuje v dialogovém okně **Nový projekt.**

1. Spusťte nástroj Obnovit experimentální **instanci aplikace Microsoft Visual Studio.**

2. Znovu sestavte projekt SimpleProject a začněte ladění. Experimentální instance by se měla objevit

3. V dialogovém okně **Nový projekt** klikněte na uzel **SimpleProject.** Šablona **konzolové aplikace** by se měla zobrazit v podokně **Šablony.**

4. Rozbalte uzel **SimpleProject.** Měl by se zobrazit podřízený uzel **konzoly.** Šablona **aplikace SimpleProject** se nadále zobrazuje v podokně **Šablony.**

5. Klepněte na tlačítko **Storno** a zastavte ladění.

    ![Jednoduchá kumulativní aplikace projektu](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Uzel konzoly jednoduchého projektu](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Nahrazení parametrů šablony projektu
- [Vytvoření základního systému projektu, část 1 ukázala,](../extensibility/creating-a-basic-project-system-part-1.md) jak přepsat metodu `ProjectNode.AddFileFromTemplate` provést základní druh nahrazení parametrů šablony. Tato část učí, jak používat složitější parametry šablony sady Visual Studio.

Při vytváření projektu pomocí šablony sady Visual Studio v dialogovém okně **Nový projekt** jsou parametry šablony nahrazeny řetězci pro přizpůsobení projektu. Parametr šablony je speciální token, který začíná a končí znakem dolaru, například $time$. Následující dva parametry jsou užitečné zejména pro povolení vlastního nastavení v projektech, které jsou založeny na šabloně:

- $GUID[1-10]$ je nahrazen novým identifikátorem Guid. Můžete zadat až 10 jedinečných identifikátorů GUID, například $guid1$.

- $safeprojectname$ je název poskytnutý uživatelem v dialogovém okně **Nový projekt,** upraveného tak, aby odstranil všechny nebezpečné znaky a mezery.

  Úplný seznam parametrů šablony naleznete v tématu [Parametry šablony](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Nahrazení parametrů šablony projektu

1. V *souboru SimpleProjectNode.cs* `AddFileFromTemplate` metodu odeberte.

2. V souboru * \\Templates\Projects\ConsoleApp\SimpleProject.myproj* \<vyhledejte vlastnost RootNamespace> a změňte jeho hodnotu na $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. V souboru * \\Templates\Projects\SimpleProject\Program.cs* nahraďte obsah souboru následujícím kódem:

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

4. Znovu sestavte projekt SimpleProject a začněte ladění. Experimentální instance by se měla zobrazit.

5. Vytvořte novou aplikaci SimpleProject Console. (V podokně **Typy projektu** vyberte **Možnost SimpleProject**. V části **Nainstalované šablony sady Visual Studio**vyberte **konzolová aplikace**.)

6. V nově vytvořeném projektu otevřete *Program.cs*. Mělo by vypadat podobně jako následující (hodnoty GUID v souboru se budou lišit.):

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
Můžete vytvořit stránku vlastností pro typ projektu, aby uživatelé mohli zobrazit a změnit vlastnosti v projektech založených na vaší šabloně. Tato část ukazuje, jak vytvořit stránku vlastností nezávislou na konfiguraci. Tato stránka základních vlastností používá mřížku vlastností k zobrazení veřejných vlastností, které zveřejňujete ve třídě stránky vlastností.

Odvodit třídu `SettingsPage` stránky vlastností ze základní třídy. Mřížka vlastností poskytovaná třídou `SettingsPage` si je vědoma nejprimitivnějších datových typů a ví, jak je zobrazit. Kromě toho `SettingsPage` třída ví, jak zachovat hodnoty vlastností do souboru projektu.

Stránka vlastností, kterou vytvoříte v této části, umožňuje změnit a uložit tyto vlastnosti projektu:

- Assemblyname

- Typ výstupu

- Rootnamespace.

1. V *souboru SimpleProjectPackage.cs* `ProvideObject` přidejte `SimpleProjectPackage` tento atribut do třídy:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Tím se zaregistruje `GeneralPropertyPage` třídu stránky vlastností s com.

2. V *SimpleProjectNode.cs* souboru přidejte do třídy `SimpleProjectNode` tyto dvě přepsané metody:

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

    Obě tyto metody vrátí pole guid stránky vlastností. Identifikátor GUID GeneralPropertyPage je jediným prvkem v poli, takže dialogové okno **Stránky vlastností** zobrazí pouze jednu stránku.

3. Přidejte do projektu SimpleProject soubor třídy s názvem *GeneralPropertyPage.cs.*

4. Nahraďte obsah tohoto souboru pomocí následujícího kódu:

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

    Třída `GeneralPropertyPage` zpřístupňuje tři veřejné vlastnosti AssemblyName, OutputType a RootNamespace. Protože AssemblyName nemá žádnou metodu set, zobrazí se jako vlastnost jen pro čtení. OutputType je výčtová konstanta, takže se zobrazí jako rozevírací seznam.

    Základní `SettingsPage` třída `ProjectMgr` poskytuje zachovat vlastnosti. Metoda `BindProperties` používá `ProjectMgr` k načtení trvalých hodnot vlastností a nastavení odpovídajících vlastností. Metoda `ApplyChanges` používá `ProjectMgr` k získání hodnot vlastností a jejich uchování do souboru projektu. Metoda sady vlastností nastaví `IsDirty` hodnotu true, což znamená, že vlastnosti musí být trvalé. Trvalost dochází při uložení projektu nebo řešení.

5. Znovu sestavte řešení SimpleProject a spusťte ladění. Experimentální instance by se měla zobrazit.

6. V experimentální instanci vytvořte novou aplikaci SimpleProject.

7. Visual Studio volá továrnu projektu k vytvoření projektu pomocí šablony sady Visual Studio. Nový *soubor Program.cs* se otevře v editoru kódu.

8. Klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení**a potom klepněte na příkaz **Vlastnosti**. Zobrazí se dialogové okno **Stránky vlastností**.

    ![Stránka vlastností jednoduchého projektu](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Otestovat stránku vlastností projektu
Nyní můžete otestovat, zda můžete upravit a změnit hodnoty vlastností.

1. V dialogovém okně **Stránky vlastností aplikace MyConsoleApplication** změňte **výchozí obor Namespace** na **MyApplication**.

2. Vyberte vlastnost **OutputType** a pak vyberte **Knihovnu tříd**.

3. Klepněte na **tlačítko Použít**a potom klepněte na tlačítko **OK**.

4. Znovu otevřete dialogové okno **Stránky vlastností** a ověřte, zda byly změny trvalé.

5. Zavřete experimentální instanci sady Visual Studio.

6. Znovu otevřete experimentální instanci.

7. Znovu otevřete dialogové okno **Stránky vlastností** a ověřte, zda byly změny trvalé.

8. Zavřete experimentální instanci sady Visual Studio.
    ![Zavřít experimentální instanci](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
