---
title: 'Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 56f50a3c50156cbd932fc7a7247fd96c4c6c2834
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296252"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1
  Projekty SharePoint jsou kontejnery pro jeden nebo více položek projektu služby SharePoint. Systém projektu služby SharePoint v sadě Visual Studio můžete rozšířit vytvořením vlastních typů položek projektu služby SharePoint a potom jejich přidružení šablony projektu. V tomto návodu bude definovat typ položky projektu pro vytvoření sloupce webu a pak vytvoříte šablonu projektu, který slouží k vytvoření nového projektu, který obsahuje položky projektu sloupce webu.  
  
 Tento návod demonstruje následující úkoly:  
  
- Vytváření rozšíření pro Visual Studio, který definuje nový typ položky projektu služby SharePoint pro sloupce webu. Typ položky projektu zahrnuje jednoduchý vlastní vlastnost, která se zobrazí **vlastnosti** okna.  
  
- Vytváření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] šablona projektu pro položky projektu.  
  
- Vytváření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension (VSIX) balíčku pro nasazení šablony projektu a sestavení rozšíření.  
  
- Ladění a testování položky projektu.  
  
  Toto je samostatný návodu. Po dokončení tohoto návodu, můžete zvýšit položky projektu tak, že přidáte do šablony projektu průvodce. Další informace najdete v tématu [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
> Řadu ukázkový pracovní postupy, najdete v části [ukázky pracovního postupu služby SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované vydání systému Microsoft Windows, SharePoint a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení položky projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Sloupce webu ve službě SharePoint. Další informace najdete v tématu [sloupce](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
- Šablony projektů v sadě Visual Studio. Další informace najdete v tématu [vytváření projektů a šablon položek](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, budete muset vytvořit tři projekty:  
  
- Projekt VSIX. Tento projekt vytvoří balíčku VSIX k nasazení položky projektu sloupce webu a šablony projektu.  
  
- Projekt šablony projektu. Tento projekt vytvoří šablonu projektu, který slouží k vytvoření nového projektu služby SharePoint, který obsahuje položky projektu sloupce webu.  
  
- Projekt knihovny tříd. Tento projekt, který implementuje rozšíření sady Visual Studio, která definuje chování položky projektu sloupce webu.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** je vybrán v seznamu verzí rozhraní .NET Framework.  
  
4.  Rozbalte **jazyka Visual Basic** nebo **Visual C#** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
    > [!NOTE]  
    >  **Rozšiřitelnost** uzel je dostupný jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
5.  V seznamu šablon projektu vyberte **projekt VSIX**.  
  
6.  V **název** zadejte **SiteColumnProjectItem**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **SiteColumnProjectItem** projektu **Průzkumníka řešení**.  
  
#### <a name="to-create-the-project-template-project"></a>Chcete-li vytvořit projekt šablony projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** je vybrán v seznamu verzí rozhraní .NET Framework.  
  
3.  Rozbalte **Visual C#** nebo **jazyka Visual Basic** uzel a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
4.  V seznamu šablon projektu vyberte **šablonu projektu C#** nebo **šablonu projektu jazyka Visual Basic** šablony.  
  
5.  V **název** zadejte **SiteColumnProjectTemplate**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **SiteColumnProjectTemplate** projektu do řešení.  
  
6.  Odstraňte soubor kódu Class1 z projektu.  
  
7.  Pokud jste vytvořili projekt jazyka Visual Basic, odstraňte také následující soubory z projektu:  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *Resources.resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.Settings  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** je vybrán v seznamu verzí rozhraní .NET Framework.  
  
3.  Rozbalte **Visual C#** nebo **jazyka Visual Basic** uzlů, zvolte **Windows** uzel a klikněte na tlačítko **knihovny tříd** šablony.  
  
4.  V **název** zadejte **ProjectItemTypeDefinition** a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **ProjectItemTypeDefinition** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Přidejte soubory kódu a odkazy na sestavení ke konfiguraci projektu rozšíření.  
  
#### <a name="to-configure-the-project"></a>Konfigurace projektu  
  
1.  V projektu ProjectItemTypeDefinition přidejte soubor kódu, který je pojmenován **SiteColumnProjectItemTypeProvider**.  
  
2.  V panelu nabídky zvolte **projektu** > **přidat odkaz**.  
  
3.  V **správce odkazů - ProjectItemTypeDefinition** dialogového okna rozbalte **sestavení** uzlu, vyberte **Framework** uzlu a pak vyberte System.ComponentModel.Composition zaškrtávací políčko.  
  
4.  Zvolte **rozšíření** uzlu, zaškrtněte políčko vedle Microsoft.VisualStudio.SharePoint sestavení a klikněte na tlačítko **OK** tlačítko.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Definujte nový typ položky projektu SharePoint
 Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní k definování chování novému typu položky projektu. Toto rozhraní implementujte, kdykoli budete chtít definovat nový typ položky projektu.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Chcete-li definovat novému typu položky projektu SharePoint  
  
1.  V **SiteColumnProjectItemTypeProvider** soubor kódu, nahraďte kód následujícím kódem a pak soubor uložte.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Vytvoření šablony projektů sady Visual Studio
 Tím, že vytvoříte šablonu projektu, můžete další vývojářům umožňují vytvářet projekty SharePoint, které obsahují položky projektu sloupce webu. Šablona projektu služby SharePoint obsahuje soubory potřebné pro všechny projekty v sadě Visual Studio, například *.csproj* nebo *.vbproj* a *.vstemplate* soubory a soubory, které jsou specifické pro projekty SharePoint. Další informace najdete v tématu [položky vytvářet šablony a šablony projektů pro položky Sharepointového projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 V tomto postupu vytvoříte prázdný projekt SharePoint ke generování soubory, které jsou specifické pro projekty SharePoint. Potom přidáte tyto soubory do projektu SiteColumnProjectTemplate tak, že jsou zahrnuté v šabloně, který je generován z tohoto projektu. Můžete také nakonfigurovat soubor projektu SiteColumnProjectTemplate k určení, kde se zobrazí v šabloně projektů **nový projekt** dialogové okno.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Postup vytvoření souborů pro šablony projektu  
  
1. Spusťte druhou instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s přihlašovacími údaji správce.  
  
2. Vytvoření projektu služby SharePoint 2010, který je pojmenován **BaseSharePointProject**.  
  
   > [!IMPORTANT]  
   >  V **Průvodce přizpůsobením SharePoint**, nevybírejte **nasadit jako řešení farmy** přepínač.  
  
3. Přidat prázdný Element položku do projektu a potom zadejte název položky **pole1**.  
  
4. Uložte projekt a poté zavřete druhou instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5. V instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , který má otevřené řešení SiteColumnProjectItem, v **Průzkumníka řešení**, otevřete místní nabídku **SiteColumnProjectTemplate** uzel projektu, zvolte  **Přidat**a klikněte na tlačítko **existující položku**.  
  
6. V **přidat existující položku** dialogové okno, otevřete seznam přípon souborů a klikněte na tlačítko **všechny soubory (\*.\*)** .  
  
7. V adresáři, který obsahuje projekt BaseSharePointProject, vyberte soubor klíč.snk a klikněte na tlačítko **přidat** tlačítko.  
  
   > [!NOTE]  
   >  Šablony projektu, který vytvoříte v tomto názorném postupu používá stejný soubor klíč.snk k podepisování každý projekt, který je vytvořen pomocí šablony. Zjistěte, jak rozšířit této ukázky si vytvořte soubor různých klíč.snk u každé instance projektu, najdete v článku [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8. Opakujte kroky 5 až 8 přidejte následující soubory ze zadaného podsložek v adresáři BaseSharePointProject:  
  
   - *\Field1\Elements.XML*  
  
   - *\Field1\SharePointProjectItem.spdata*  
  
   - *\Features\Feature1\Feature1.Feature*  
  
   - *\Features\Feature1\Feature1.template.XML*  
  
   - *\Package\Package.Package*  
  
   - *\Package\Package.template.XML*  
  
     Přidat tyto soubory přímo do projektu SiteColumnProjectTemplate; nemusíte znovu vytvořit podsložky pole1, funkce nebo balíček v projektu. Další informace o těchto souborech najdete v tématu [položky vytvářet šablony a šablony projektů pro položky Sharepointového projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Ke konfiguraci, jak vývojáři zjistit šablony projektu v dialogovém okně Nový projekt
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **SiteColumnProjectTemplate** uzel projektu a klikněte na tlačítko **uvolnit projekt**. Pokud se zobrazí výzva k uložení změn do všech souborů, zvolte **Ano** tlačítko.  
  
2.  Otevřete místní nabídku **SiteColumnProjectTemplate** uzlu znovu a klikněte na tlačítko **upravit SiteColumnProjectTemplate.csproj** nebo **upravit SiteColumnProjectTemplate.vbproj**.  
  
3.  V souboru projektu vyhledejte následující `VSTemplate` elementu.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Tento prvek nahraďte následující kód XML.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Prvek určuje další složky v cestě, pod kterým šabloně projektu je vytvořen při sestavení projektu. Složky tady zadané, ujistěte se, že šablona projektu bude k dispozici pouze v případě, že zákazníci otevřít **nový projekt** dialogového okna rozbalte **SharePoint** uzel a klikněte na tlačítko **2010**  uzlu.  
  
5.  Soubor uložte a zavřete.  
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku **SiteColumnProjectTemplate** projektu a klikněte na tlačítko **znovu načíst projekt**.  
  
## <a name="edit-the-project-template-files"></a>Upravit soubory šablon projektu
 V projektu SiteColumnProjectTemplate upravte následující soubory, které chcete definovat chování projektu šablony:  
  
- *AssemblyInfo.cs* nebo *AssemblyInfo.vb*  
  
- *Elements.XML*  
  
- *SharePointProjectItem.spdata*  
  
- *Feature1.Feature*  
  
- *Package.Package*  
  
- *SiteColumnProjectTemplate.vstemplate*  
  
- *ProjectTemplate.csproj* nebo *ProjectTemplate.vbproj*  
  
  V následujících postupech přidáte nahraditelné parametry k některé z těchto souborů. Nahraditelných parametrů je token, který začíná a končí znakem dolaru ($). Když uživatel tuto šablonu projektu pro vytvoření projektu, Visual Studio automaticky nahradí tyto parametry v novém projektu konkrétní hodnoty. Další informace najdete v tématu [nahraditelné parametry](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Chcete-li upravit soubor AssemblyInfo.cs nebo AssemblyInfo.vb
  
1.  V projektu SiteColumnProjectTemplate otevřete *AssemblyInfo.cs* nebo *AssemblyInfo.vb* souboru a potom přidejte následující příkaz na začátek:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Když **řešení v izolovaném prostoru** projektu služby SharePoint je nastavena na **True**, sada Visual Studio přidá <xref:System.Security.AllowPartiallyTrustedCallersAttribute> do souboru AssemblyInfo kódu. Však nepodporuje import souboru AssemblyInfo kódu v šabloně projektu <xref:System.Security> oboru názvů ve výchozím nastavení. Je nutné přidat tento **pomocí** nebo **importy** příkaz, aby se zabránilo chyby kompilace.  
  
2.  Soubor uložte a zavřete.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Chcete-li upravit soubor Elements.xml
  
1.  V projektu SiteColumnProjectTemplate nahraďte obsah *Elements.xml* soubor s následující kód XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Přidá nové XML `Field` element, který definuje název sloupce webu, jeho základní typ a skupiny, ve které k výpisu sloupce webu ve galerii. Další informace o obsahu tohoto souboru najdete v tématu [schématu definice pole](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Soubor uložte a zavřete.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Chcete-li upravit soubor SharePointProjectItem.spdata
  
1. V projektu SiteColumnProjectTemplate nahraďte obsah *SharePointProjectItem.spdata* soubor s následující kód XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
     <Files>  
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
     </Files>   
   </ProjectItem>  
   ```  
  
    Nové XML umožňuje následující změny do souboru:  
  
   - Změny `Type` atribut `ProjectItem` element na stejný řetězec, který je předán <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> na definici položky projektu ( `SiteColumnProjectItemTypeProvider` třídu, která jste vytvořili dříve v tomto názorném postupu).  
  
   - Odebere `SupportedTrustLevels` a `SupportedDeploymentScopes` atributy z `ProjectItem` elementu. Tyto hodnoty atributů nejsou potřeba, protože úrovně důvěryhodnosti a obory nasazení jsou uvedeny v `SiteColumnProjectItemTypeProvider` třídu v projektu ProjectItemTypeDefinition.  
  
     Další informace o obsahu *.spdata* soubory, naleznete v tématu [referenční dokumentace schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2. Soubor uložte a zavřete.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Chcete-li upravit soubor Feature1.feature
  
1. V projektu SiteColumnProjectTemplate nahraďte obsah *Feature1.feature* soubor s následující kód XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
     <projectItems>  
       <projectItemReference itemId="$guid2$" />  
     </projectItems>  
   </feature>  
   ```  
  
    Nové XML umožňuje následující změny do souboru:  
  
   - Změní hodnoty `Id` a `featureId` atributy `feature` elementu `$guid4$`.  
  
   - Změní hodnoty `itemId` atribut `projectItemReference` elementu `$guid2$`.  
  
     Další informace o *.feature* soubory, naleznete v tématu [položky vytvářet šablony a šablony projektů pro položky Sharepointového projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Soubor uložte a zavřete.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Chcete-li upravit soubor Package.package
  
1. V projektu SiteColumnProjectTemplate nahraďte obsah *Package.package* soubor s následující kód XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
     <features>  
       <featureReference itemId="$guid4$" />  
     </features>  
   </package>  
   ```  
  
    Nové XML umožňuje následující změny do souboru:  
  
   - Změní hodnoty `Id` a `solutionId` atributy `package` elementu `$guid3$`.  
  
   - Změní hodnoty `itemId` atribut `featureReference` elementu `$guid4$`.  
  
     Další informace o *.package* soubory, naleznete v tématu [položky vytvářet šablony a šablony projektů pro položky Sharepointového projektu](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Soubor uložte a zavřete.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Chcete-li upravit soubor sitecolumnprojecttemplate.vstemplate
  
1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru SiteColumnProjectTemplate.vstemplate jednu z následujících částí XML.  
  
   -   Pokud vytváříte šablonu projektu Visual C#, použijte následující kód XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>CSharp</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
   -   Pokud vytváříte šablonu projektu jazyka Visual Basic, použijte následující kód XML.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>VisualBasic</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Nové XML umožňuje následující změny do souboru:  
  
   - Nastaví `Name` prvku na hodnotu **sloupce webu**. (Tento název se zobrazí v **nový projekt** dialogové okno).  
  
   - Přidá `ProjectItem` prvky pro každý filethat uživatele zahrnuta v každé instanci projektu.  
  
   - Používá obor názvů "<http://schemas.microsoft.com/developer/vstemplate/2005>". Další soubory projektu v tomto řešení "<http://schemas.microsoft.com/developer/msbuild/2003>" oboru názvů. Proto se vygeneruje zprávy upozornění schématu XML, ale můžete je ignorovat v tomto názorném postupu.  
  
     Další informace o obsahu *.vstemplate* soubory, naleznete v tématu [Visual Studio odkaz na schéma šablon](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2. Soubor uložte a zavřete.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Chcete-li upravit soubor projecttemplate.csproj nebo projecttemplate.vbproj
  
1.  V projektu SiteColumnProjectTemplate nahraďte obsah *ProjectTemplate.csproj* souboru nebo *ProjectTemplate.vbproj* soubor s jedním z následujících částí XML.  
  
    -   Pokud vytváříte šablonu projektu Visual C#, použijte následující kód XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Pokud vytváříte šablonu projektu jazyka Visual Basic, použijte následující kód XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Nové XML umožňuje následující změny do souboru:  
  
    -   Používá `TargetFrameworkVersion` element k určení rozhraní .NET Framework 3.5, ne 4.5.  
  
    -   Přidá `SignAssembly` a `AssemblyOriginatorKeyFile` prvky k podepsání výstupu projektu.  
  
    -   Přidá `Reference` odkazuje na prvky pro sestavení, které používají projekty služby SharePoint.  
  
    -   Přidá prvky pro každou výchozí soubor v projektu, jako například *Elements.xml* a *SharePointProjectItem.spdata*.  
  
2.  Soubor uložte a zavřete.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Vytvoření balíčku VSIX k nasazení šablony projektu
 Pokud chcete nasadit rozšíření, použijte VSIX projekt ve **SiteColumnProjectItem** řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest, který je součástí projektu VSIX. Potom vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX  
  
1.  V **Průzkumníka řešení**v **SiteColumnProjectItem** projektu, otevřete soubor source.extension.vsixmanifest v editoru manifestu.  
  
     Soubor source.extension.vsixmanifest je základem pro soubor extension.vsixmanifest, které vyžadují všechny balíčky VSIX. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **sloupce webu**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **projekt služby SharePoint pro vytvoření sloupce webu**.  
  
5.  Zvolte **prostředky** kartu a klikněte na tlačítko **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
6.  V **typ** klikněte na položku **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `ProjectTemplate` element v souboru extension.vsixmanifest. Tento prvek určuje podsložce v balíčku souboru VSIX, který obsahuje šablonu projektu. Další informace najdete v tématu [ProjectTemplate – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
8.  V **projektu** seznam a zvolte **SiteColumnProjectTemplate**a klikněte na tlačítko **OK** tlačítko.  
  
9. Zvolte **nový** tlačítko znovu.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
10. V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MefComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
11. V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
12. V **projektu** klikněte na položku **ProjectItemTypeDefinition**a klikněte na tlačítko **OK** tlačítko.  
  
13. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že se projekt zkompiluje bez chyb.  
  
## <a name="test-the-project-template"></a>Test šablony projektu
 Nyní jste připraveni k testování šablony projektu. Nejprve spusťte ladění řešení SiteColumnProjectItem v experimentální instanci sady Visual Studio. Pak test **sloupce webu** projektu v experimentální instanci sady Visual Studio. Nakonec sestavte a spusťte projekt SharePoint, chcete-li ověřit, že sloupec webu funguje podle očekávání.  
  
#### <a name="to-start-debugging-the-solution"></a>Spusťte ladění řešení  
  
1.  Restartujte sadu Visual Studio s přihlašovacími údaji správce a pak otevřete SiteColumnProjectItem řešení.  
  
2.  
  
3.  V souboru kódu SiteColumnProjectItemTypeProvider přidejte zarážku na první řádek kódu `InitializeType` metoda a klikněte na tlačítko **F5** klíč pro spuštění ladění.  
  
     Visual Studio nainstaluje rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Otestování projektu v sadě Visual Studio  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2.  Rozbalte **Visual C#** nebo **jazyka Visual Basic** uzel (v závislosti na jazyk, který podporuje šablony projektu), Rozbalit **SharePoint** uzel a klikněte na tlačítko **2010** uzlu.  
  
3.  V seznamu šablon projektu vyberte **sloupce webu** šablony.  
  
4.  V **název** zadejte **SiteColumnTest** a klikněte na tlačítko **OK** tlačítko.  
  
     V **Průzkumníka řešení**, zobrazí se nový projekt s položkou projektu s názvem **pole1**.  
  
5.  Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `InitializeType` metoda a klikněte na tlačítko **F5** klíč a pokračujte v ladění projektu.  
  
6.  V **Průzkumníka řešení**, zvolte **pole1** uzel a klikněte na tlačítko **F4** klíč.  
  
     **Vlastnosti** otevře se okno.  
  
7.  V seznamu vlastností, ověřte, že vlastnost **Příklad vlastnosti** se zobrazí.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>K otestování sloupce webu ve službě SharePoint  
  
1.  V **Průzkumníka řešení**, zvolte **SiteColumnTest** uzlu.  
  
2.  V **vlastnosti** okno, v textovém poli vedle **adresa URL webu** vlastnost, zadejte **http://localhost**.  
  
     Tento krok určuje místního webu služby SharePoint ve vývojovém počítači, který chcete použít pro ladění.  
  
    > [!NOTE]  
    >  **Adresa URL webu** vlastnost je ve výchozím nastavení prázdné, protože šablona projektu sloupce webu neposkytuje k shromažďování údajů o tuto hodnotu při vytvoření projektu průvodce. Zjistěte, jak přidat průvodce, který se zeptá vývojář pro tuto hodnotu a pak nastaví tuto vlastnost v novém projektu, najdete v článku [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Zvolte **F5** klíč.  
  
     Sloupec webu je zabalit a nasadit na web služby SharePoint, který je zadán v **adresa URL webu** vlastnost projektu. Webový prohlížeč otevře výchozí stránku webu.  
  
    > [!NOTE]  
    >  Pokud **ladění skriptů zakázáno** dialogové okno se zobrazí, zvolte **Ano** tlačítka pokračovat v ladění projektu.  
  
4.  Na **Akce webu** nabídce zvolte **nastavení webu**.  
  
5.  Na **nastavení webu** stránce v části **Galerie** klikněte na položku **sloupce webu** odkaz.  
  
6.  V seznamu sloupců webu, ověřte, že **vlastní sloupce** skupina obsahuje sloupec s názvem **SiteColumnTest**.  
  
7.  Zavřete webový prohlížeč.  
  
## <a name="clean-up-the-development-computer"></a>Vyčištění vývojovém počítači
 Po dokončení testování projektu odebrání šablony projektu experimentální instanci sady Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Chcete-li vyčistit vývojovém počítači  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **sloupce webu** rozšíření a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření.  
  
4.  Zvolte **Zavřít** tlačítko pro dokončení odinstalace.  
  
5.  Zavřete obě instance programu Visual Studio (experimentální instanci a instanci sady Visual Studio, ve kterém je otevřen SiteColumnProjectItem řešení).  
  
## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto postupu můžete přidat do šablony projektu průvodce. Když uživatel vytvoří projektu sloupce webu, zobrazí Průvodce požadavek uživatele pro adresu URL webu pro účely ladění a zda je nové řešení v izolovaném prostoru a Průvodce nakonfiguruje nový projekt s těmito informacemi. Průvodce taky shromažďuje informace o sloupci (například základní typ a skupiny, ve které seznam sloupců v galerii webů sloupce) a přidá tyto informace *Elements.xml* souboru v novém projektu. Další informace najdete v tématu [návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Viz také:
 [Návod: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Vytváření šablon položek a projektů pro položky projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Ukládání dat do rozšíření systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Přidružení vlastních dat k rozšíření nástrojů SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
