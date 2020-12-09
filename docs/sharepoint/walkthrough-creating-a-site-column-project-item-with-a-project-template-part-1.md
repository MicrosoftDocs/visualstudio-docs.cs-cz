---
title: Vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1
titleSuffix: ''
description: Definujte typ položky projektu pro vytvoření sloupce webu a poté vytvořte šablonu projektu, která bude použita pro vytvoření projektu služby SharePoint, který obsahuje položku projektu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 32f56f282dc5755b8162c4f19a9c036dc2e9cc5f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915211"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 1
  Projekty služby SharePoint jsou kontejnery pro jednu nebo více položek projektu služby SharePoint. Systém projektu služby SharePoint v aplikaci Visual Studio můžete roztáhnout tak, že vytvoříte vlastní typy položek projektu SharePoint a pak je přidružíte k šabloně projektu. V tomto návodu definujete typ položky projektu pro vytvoření sloupce web a potom vytvoříte šablonu projektu, kterou lze použít k vytvoření nového projektu, který obsahuje položku projektu sloupce webu.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření rozšíření aplikace Visual Studio, které definuje nový typ položky projektu služby SharePoint pro sloupec webu. Typ položky projektu obsahuje jednoduchou vlastní vlastnost, která se zobrazí v okně **vlastnosti** .

- Vytvoření [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] šablony projektu pro položku projektu.

- Sestavení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíčku rozšíření (VSIX) pro nasazení šablony projektu a sestavení rozšíření.

- Ladění a testování položky projektu.

  Toto je samostatný návod. Po dokončení tohoto návodu můžete vylepšit položku projektu přidáním průvodce do šablony projektu. Další informace najdete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Řadu ukázkových pracovních postupů najdete v tématu [ukázky pracovních postupů služby SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice Microsoft Windows, SharePointu a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Hodnota [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení položky projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalost následujícího konceptu je užitečná, ale nevyžaduje se k dokončení tohoto postupu:

- Sloupce webu ve službě SharePoint. Další informace najdete v tématu [sloupce](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Šablony projektů v aplikaci Visual Studio. Další informace naleznete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit tři projekty:

- Projekt VSIX. Tento projekt vytvoří balíček VSIX pro nasazení položky projektu sloupce webu a šablony projektu.

- Projekt šablony projektu. Tento projekt vytvoří šablonu projektu, kterou lze použít k vytvoření nového projektu služby SharePoint, který obsahuje položku projektu sloupce webu.

- Projekt knihovny tříd. Tento projekt, který implementuje rozšíření sady Visual Studio, které definuje chování položky projektu sloupce webu.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V horní části dialogového okna **Nový projekt** se ujistěte, že je v seznamu verzí .NET Framework zvolena možnost **.NET Framework 4,5** .

4. Rozbalte uzly **Visual Basic** nebo **Visual C#** a pak zvolte uzel **rozšiřitelnost** .

    > [!NOTE]
    > Uzel **rozšiřitelnosti** je k dispozici pouze v případě, že instalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

5. V seznamu šablon projektu vyberte **projekt VSIX**.

6. Do pole **název** zadejte **SiteColumnProjectItem** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **SiteColumnProjectItem** do **Průzkumník řešení**.

#### <a name="to-create-the-project-template-project"></a>Vytvoření projektu šablony projektu

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V horní části dialogového okna **Nový projekt** se ujistěte, že je v seznamu verzí .NET Framework zvolena možnost **.NET Framework 4,5** .

3. Rozbalte uzel **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

4. V seznamu šablon projektů vyberte šablonu **projektu C#** nebo šablonu šablony **projektu Visual Basic** .

5. Do pole **název** zadejte **SiteColumnProjectTemplate** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **SiteColumnProjectTemplate** do řešení.

6. Odstraňte soubor kódu Class1 z projektu.

7. Pokud jste vytvořili projekt Visual Basic, odstraňte také následující soubory z projektu:

    - *MyApplication. Designer. vb*

    - MyApplication. myapp

    - *Resources. Designer. vb*

    - *Resources. resx*

    - *Settings. Designer. vb*

    - Settings. Settings

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení** otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat** a pak zvolte možnost **Nový projekt**.

2. V horní části dialogového okna **Nový projekt** se ujistěte, že je v seznamu verzí .NET Framework zvolena možnost **.NET Framework 4,5** .

3. Rozbalte uzly **Visual C#** nebo **Visual Basic** , zvolte uzel **Windows** a pak zvolte šablonu **knihovny tříd** .

4. Do pole **název** zadejte **ProjectItemTypeDefinition** a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **ProjectItemTypeDefinition** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Přidejte soubory kódu a odkazy na sestavení pro konfiguraci projektu rozšíření.

#### <a name="to-configure-the-project"></a>Konfigurace projektu

1. V projektu ProjectItemTypeDefinition přidejte soubor kódu s názvem **SiteColumnProjectItemTypeProvider**.

2. Na panelu nabídek vyberte **projekt**  >  **Přidat odkaz**.

3. V dialogovém okně **Správce odkazů – ProjectItemTypeDefinition** rozbalte uzel **sestavení** , zvolte uzel **rozhraní** a pak zaškrtněte políčko System. ComponentModel. kompozice.

4. Zvolte uzel **rozšíření** , zaškrtněte políčko vedle sestavení Microsoft. VisualStudio. SharePoint a pak klikněte na tlačítko **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Definovat nový typ položky projektu služby SharePoint
 Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní pro definování chování nového typu položky projektu. Implementujte toto rozhraní vždy, když chcete definovat nový typ položky projektu.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Definování nového typu položky projektu služby SharePoint

1. V souboru kódu **SiteColumnProjectItemTypeProvider** nahraďte výchozí kód následujícím kódem a poté soubor uložte.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Vytvoření šablony projektu sady Visual Studio
 Vytvořením šablony projektu umožníte ostatním vývojářům vytvářet projekty služby SharePoint, které obsahují položky projektu sloupce webu. Šablona projektu služby SharePoint obsahuje soubory, které jsou požadovány pro všechny projekty v aplikaci Visual Studio, například soubory *. csproj* nebo *. vbproj* a *. vstemplate* , a soubory, které jsou specifické pro projekty služby SharePoint. Další informace naleznete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 V tomto postupu vytvoříte prázdný projekt služby SharePoint pro generování souborů, které jsou specifické pro projekty služby SharePoint. Poté přidejte tyto soubory do projektu SiteColumnProjectTemplate, aby byly zahrnuty do šablony, která je vygenerována z tohoto projektu. Také nakonfigurujete soubor projektu SiteColumnProjectTemplate a určíte, kde se šablona projektu zobrazí v dialogovém okně **Nový projekt** .

#### <a name="to-create-the-files-for-the-project-template"></a>Vytvoření souborů pro šablonu projektu

1. Spusťte druhou instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s přihlašovacími údaji správce.

2. Vytvořte projekt SharePoint 2010 s názvem **BaseSharePointProject**.

   > [!IMPORTANT]
   > V **Průvodci vlastním nastavením služby SharePoint** nevybírejte možnost **nasadit jako řešení farmy** .

3. Přidejte do projektu prázdnou položku prvku a potom Pojmenujte položku **pole1**.

4. Uložte projekt a pak zavřete druhou instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

5. V instanci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , která má otevřené řešení SiteColumnProjectItem otevřete, v **Průzkumník řešení** otevřete místní nabídku uzlu projektu **SiteColumnProjectTemplate** , vyberte možnost **Přidat** a poté možnost **existující položka**.

6. V dialogovém okně **Přidat existující položku** otevřete seznam přípon souborů a pak zvolte možnost **všechny soubory ( \* . \* )**.

7. V adresáři, který obsahuje projekt BaseSharePointProject vyberte soubor Key. snk a pak klikněte na tlačítko **Přidat** .

   > [!NOTE]
   > V tomto návodu šablona projektu, kterou vytvoříte, používá stejný soubor Key. snk k podepsání každého projektu vytvořeného pomocí šablony. Informace o tom, jak rozbalit tuto ukázku pro vytvoření jiného souboru key. snk pro jednotlivé instance projektu, naleznete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Opakujte kroky 5-8 a přidejte následující soubory ze zadaných podsložek v adresáři BaseSharePointProject:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Přidejte tyto soubory přímo do projektu SiteColumnProjectTemplate; v projektu nevytvářejte znovu žádné podsložky, funkce nebo podsložky balíčku. Další informace o těchto souborech najdete v tématu [Vytvoření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Konfigurace způsobu, jakým vývojáři zjišťují šablonu projektu v dialogovém okně Nový projekt

1. V **Průzkumník řešení** otevřete místní nabídku uzlu projektu **SiteColumnProjectTemplate** a pak zvolte **Uvolnit projekt**. Pokud se zobrazí výzva k uložení změn do libovolného souboru, klikněte na tlačítko **Ano** .

2. Znovu otevřete místní nabídku uzlu **SiteColumnProjectTemplate** a pak zvolte **Upravit SiteColumnProjectTemplate. csproj** nebo **Upravit SiteColumnProjectTemplate. vbproj**.

3. V souboru projektu vyhledejte následující `VSTemplate` element.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Nahraďte tento prvek následujícím kódem XML.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Prvek určuje další složky v cestě, kde je vytvořena šablona projektu při sestavení projektu. Složky, které jsou zde uvedeny, zajistí, že šablona projektu bude k dispozici pouze v případě, že zákazníci otevřou dialogové okno **Nový projekt** , rozbalte uzel **služby SharePoint** a poté vyberte uzel **2010** .

5. Uložte soubor a zavřete ho.

6. V **Průzkumník řešení** otevřete místní nabídku pro projekt **SiteColumnProjectTemplate** a pak zvolte **znovu načíst projekt**.

## <a name="edit-the-project-template-files"></a>Upravit soubory šablon projektu
 V projektu SiteColumnProjectTemplate upravte následující soubory pro definování chování šablony projektu:

- *AssemblyInfo.cs* nebo *AssemblyInfo. vb*

- *Elements.xml*

- *SharePointProjectItem. spdata*

- *Feature1. funkce*

- *Package. Package*

- *SiteColumnProjectTemplate. vstemplate*

- *ProjectTemplate. csproj* nebo *ProjectTemplate. vbproj*

  V následujících postupech přidáte do některých těchto souborů nahraditelný parametr. Nahraditelný parametr je token, který začíná a končí znakem dolaru ($). Když uživatel použije tuto šablonu projektu k vytvoření projektu, Visual Studio automaticky nahradí tyto parametry v novém projektu konkrétními hodnotami. Další informace najdete v tématu [nahraditelných parametrů](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Úprava souboru AssemblyInfo.cs nebo AssemblyInfo. vb

1. V projektu SiteColumnProjectTemplate otevřete soubor *AssemblyInfo.cs* nebo *AssemblyInfo. vb* a přidejte do jeho horní části následující příkaz:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Pokud je vlastnost **řešení v izolovaném prostoru** projektu služby SharePoint nastavena na **hodnotu true**, sada Visual Studio přidá do <xref:System.Security.AllowPartiallyTrustedCallersAttribute> souboru kódu AssemblyInfo. Soubor kódu AssemblyInfo v šabloně projektu ale ve výchozím nastavení neimportuje <xref:System.Security> obor názvů. Chcete-li zabránit chybám kompilace, je nutné přidat příkaz **using** nebo **Imports** .

2. Uložte soubor a zavřete ho.

#### <a name="to-edit-the-elementsxml-file"></a>Postup úpravy souboru Elements.xml

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru *Elements.xml* následujícím kódem XML.

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

     Nový kód XML přidá `Field` prvek, který definuje název sloupce web, jeho základní typ a skupinu, ve které chcete zobrazit seznam sloupců webu v galerii. Další informace o obsahu tohoto souboru najdete v tématu [schéma definic polí](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Uložte soubor a zavřete ho.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Úprava souboru SharePointProjectItem. spdata

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru *SharePointProjectItem. spdata* následujícím kódem XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Nové XML provede následující změny v souboru:

   - Změní `Type` atribut `ProjectItem` elementu na stejný řetězec, který je předán do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> definice položky projektu ( `SiteColumnProjectItemTypeProvider` třída, kterou jste vytvořili dříve v tomto návodu).

   - Odebere `SupportedTrustLevels` atributy a `SupportedDeploymentScopes` z `ProjectItem` elementu. Tyto hodnoty atributu nejsou potřebné, protože úrovně důvěryhodnosti a rozsahy nasazení jsou zadány ve `SiteColumnProjectItemTypeProvider` třídě v projektu ProjectItemTypeDefinition.

     Další informace o obsahu souborů *. spdata* naleznete v tématu Referenční dokumentace [schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Uložte soubor a zavřete ho.

#### <a name="to-edit-the-feature1feature-file"></a>Úprava souboru Feature1. Feature

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru *Feature1. Feature* následujícím kódem XML.

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

    Nové XML provede následující změny v souboru:

   - Změní hodnoty `Id` `featureId` atributů a `feature` elementu na `$guid4$` .

   - Změní hodnoty `itemId` atributu `projectItemReference` elementu na `$guid2$` .

     Další informace o souborech *funkcí* najdete v tématu [vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Uložte soubor a zavřete ho.

#### <a name="to-edit-the-packagepackage-file"></a>Úprava souboru Package. Package

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru *Package. Package* následujícím kódem XML.

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

    Nové XML provede následující změny v souboru:

   - Změní hodnoty `Id` `solutionId` atributů a `package` elementu na `$guid3$` .

   - Změní hodnoty `itemId` atributu `featureReference` elementu na `$guid4$` .

     Další informace o souborech *. Package* naleznete v tématu [Create Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Uložte soubor a zavřete ho.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Úprava souboru SiteColumnProjectTemplate. vstemplate

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru SiteColumnProjectTemplate. vstemplate jedním z následujících oddílů XML.

   - Pokud vytváříte šablonu projektu Visual C#, použijte následující kód XML.

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

   - Pokud vytváříte šablonu projektu Visual Basic, použijte následující kód XML.

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

    Nové XML provede následující změny v souboru:

   - Nastaví `Name` element na **sloupec Value web**(hodnota). (Tento název se zobrazí v dialogovém okně **Nový projekt** ).

   - Přidá `ProjectItem` prvky pro každý prvek, který je zahrnutý v každé instanci projektu.

   - Používá obor názvů `http://schemas.microsoft.com/developer/vstemplate/2005` . Jiné soubory projektu v tomto řešení používají `http://schemas.microsoft.com/developer/msbuild/2003` obor názvů. Proto budou vygenerovány zprávy upozornění schématu XML, ale můžete je v tomto návodu ignorovat.

     Další informace o obsahu souborů *. vstemplate* naleznete v tématu Referenční dokumentace [schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

2. Uložte soubor a zavřete ho.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Úprava souboru ProjectTemplate. csproj nebo ProjectTemplate. vbproj

1. V projektu SiteColumnProjectTemplate nahraďte obsah souboru *ProjectTemplate. csproj* nebo *ProjectTemplate. vbproj* jedním z následujících oddílů XML.

    - Pokud vytváříte šablonu projektu Visual C#, použijte následující kód XML.

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

    1. Pokud vytváříte šablonu projektu Visual Basic, použijte následující kód XML.

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

     Nové XML provede následující změny v souboru:

    - Používá `TargetFrameworkVersion` element k určení .NET Framework 3,5, nikoli 4,5.

    - Přidá `SignAssembly` `AssemblyOriginatorKeyFile` prvky a pro podepsání výstupu projektu.

    - Přidá `Reference` prvky pro odkazy na sestavení, které používají projekty služby SharePoint.

    - Přidá prvky pro každý výchozí soubor v projektu, například *Elements.xml* a *SharePointProjectItem. spdata*.

2. Uložte soubor a zavřete ho.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Vytvoření balíčku VSIX pro nasazení šablony projektu
 Chcete-li nasadit rozšíření, použijte projekt VSIX v řešení **SiteColumnProjectItem** k vytvoření balíčku VSIX. Nejdřív nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest, který je zahrnutý v projektu VSIX. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX

1. V **Průzkumník řešení** v projektu **SiteColumnProjectItem** otevřete soubor source. extension. vsixmanifest v editoru manifestu.

     Soubor source. extension. vsixmanifest je základem pro soubor Extension. vsixmanifest, který vyžaduje všechny balíčky VSIX. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Do pole **název produktu** zadejte **sloupec web**.

3. Do pole **Autor** zadejte **Contoso**.

4. Do pole **Popis** zadejte **projekt služby SharePoint pro vytváření sloupců webu**.

5. Zvolte kartu **aktiva** a pak klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

6. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. ProjectTemplate**.

    > [!NOTE]
    > Tato hodnota odpovídá `ProjectTemplate` prvku v souboru extension. vsixmanifest. Tento prvek identifikuje podsložku v balíčku VSIX, který obsahuje šablonu projektu. Další informace naleznete v tématu [ProjectTemplate Element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

8. V seznamu **projekt** vyberte možnost **SiteColumnProjectTemplate** a pak klikněte na tlačítko **OK** .

9. Znovu klikněte na tlačítko **Nový** .

     Otevře se dialogové okno **Přidat nový prostředek** .

10. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MefComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

12. V seznamu **projekt** zvolte možnost **ProjectItemTypeDefinition** a pak klikněte na tlačítko **OK** .

13. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení** a pak se ujistěte, že se projekt zkompiluje bez chyb.

## <a name="test-the-project-template"></a>Testování šablony projektu
 Nyní jste připraveni otestovat šablonu projektu. Nejdřív začněte ladit řešení SiteColumnProjectItem v experimentální instanci sady Visual Studio. Pak testujte projekt **sloupce webu** v experimentální instanci aplikace Visual Studio. Nakonec sestavte a spusťte projekt služby SharePoint, abyste ověřili, že sloupec web funguje podle očekávání.

#### <a name="to-start-debugging-the-solution"></a>Spuštění ladění řešení

1. Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení SiteColumnProjectItem.

2. V souboru kódu SiteColumnProjectItemTypeProvider přidejte zarážku do prvního řádku kódu v `InitializeType` metodě a pak stiskněte klávesu **F5** pro spuštění ladění.

     Visual Studio nainstaluje rozšíření na%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 a spustí experimentální instanci sady Visual Studio. Budete testovat položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Testování projektu v aplikaci Visual Studio

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. Rozbalte uzel **Visual C#** nebo **Visual Basic** (v závislosti na jazyku, který podporuje šablona projektu), rozbalte uzel **SharePoint** a pak zvolte uzel **2010** .

3. V seznamu šablon projektů vyberte šablonu **sloupce web** .

4. Do pole **název** zadejte **SiteColumnTest** a poté klikněte na tlačítko **OK** .

     V **Průzkumník řešení** se zobrazí nový projekt s položkou projektu s názvem **pole1**.

5. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `InitializeType` metodě, a pak zvolte klávesu **F5** pro pokračování v ladění projektu.

6. V **Průzkumník řešení** vyberte uzel **pole1** a pak zvolte klávesu **F4** .

     Otevře se okno **vlastnosti** .

7. V seznamu Vlastnosti ověřte, zda se zobrazí **vlastnost příklad** vlastnosti.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Testování sloupce webu ve službě SharePoint

1. V **Průzkumník řešení** vyberte uzel **SiteColumnTest** .

2. V okně **vlastnosti** zadejte do textového pole vedle vlastnosti **Adresa URL webu** **http://localhost** .

     Tento krok určuje místní web služby SharePoint ve vývojovém počítači, který chcete použít pro ladění.

    > [!NOTE]
    > Vlastnost **Adresa URL webu** je ve výchozím nastavení prázdná, protože šablona projektu sloupce webu neposkytuje průvodce pro shromažďování této hodnoty při vytvoření projektu. Další informace o tom, jak přidat průvodce, který požaduje vývojáře pro tuto hodnotu a potom nakonfiguruje tuto vlastnost v novém projektu, najdete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Klikněte na klávesu **F5** .

     Sloupec web je zabalen a nasazen na webu služby SharePoint, který je zadán ve vlastnosti **Adresa URL webu** projektu. Webový prohlížeč otevře výchozí stránku tohoto webu.

    > [!NOTE]
    > Pokud se zobrazí dialogové okno **ladění skriptu zakázáno** , klikněte na tlačítko **Ano** a pokračujte v ladění projektu.

4. V nabídce **Akce webu** klikněte na možnost **Nastavení webu**.

5. Na stránce **nastavení lokality** v seznamu **Galerie** vyberte odkaz **sloupce lokality** .

6. V seznamu sloupců lokality ověřte, zda skupina **vlastních sloupců** obsahuje sloupec s názvem **SiteColumnTest**.

7. Zavřete webový prohlížeč.

## <a name="clean-up-the-development-computer"></a>Vyčištění vývojového počítače
 Po dokončení testování projektu odeberte šablonu projektu z experimentální instance aplikace Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Vyčištění vývojového počítače

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte rozšíření **sloupce lokality** a pak klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Ano** a potvrďte tak, že chcete rozšíření odinstalovat.

4. Kliknutím na tlačítko **Zavřít** dokončete odinstalaci.

5. Zavřete obě instance sady Visual Studio (experimentální instance a instance sady Visual Studio, ve které je otevřeno řešení SiteColumnProjectItem).

## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto návodu můžete přidat průvodce do šablony projektu. Když uživatel vytvoří projekt sloupce webu, průvodce požádá uživatele o adresu URL webu, který se má použít pro ladění, a jestli je nové řešení v izolovaném prostoru a Průvodce nakonfiguruje nový projekt s těmito informacemi. Průvodce také shromažďuje informace o sloupci (jako je základní typ a skupina, ve které se nachází seznam sloupců v galerii sloupců webu) a přidává tyto informace do souboru *Elements.xml* v novém projektu. Další informace najdete v tématu [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Viz také

- [Návod: vytvoření položky projektu sloupce webu pomocí šablony projektu, část 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Uložení dat v rozšířeních systému projektu služby SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Přidružit vlastní data k rozšířením nástrojů služby SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)