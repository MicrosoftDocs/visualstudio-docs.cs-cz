---
title: 'Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8144723f68b9343c1c7d74f7a940aec569dd7969
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296122"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1
  Systém projektu služby SharePoint v sadě Visual Studio můžete rozšířit tak, že vytvoříte svůj vlastní projekt typy položek. V tomto návodu vytvoříte položku projektu, který lze přidat do projektu služby SharePoint pro vytvoření vlastní akce na Sharepointovém webu. Vlastní akce ho přidá položku nabídky **Akce webu** nabídku z webu služby SharePoint.  
  
 Tento návod demonstruje následující úkoly:  
  
- Vytváření rozšíření pro Visual Studio, který definuje nový typ položky projektu služby SharePoint pro vlastní akci. Nový typ položky projektu implementuje několik vlastních funkcí:  
  
  -   Místní nabídka, která slouží jako výchozí bod pro další úlohy související s položkou projektu, jako je například zobrazení návrháře pro vlastní akce v sadě Visual Studio.  
  
  -   Kód, který se spustí, když vývojáři změní některé její vlastnosti položky projektu a projekt, který jej obsahuje.  
  
  -   Vlastní ikony, který se zobrazí vedle položky projektu v **Průzkumníka řešení**.  
  
- Vytvoření šablony položky sady Visual Studio pro položku projektu.  
  
- Vytváření balíčku rozšíření Visual Studio (VSIX) k nasazení šablony položky projektu a sestavení rozšíření.  
  
- Ladění a testování položky projektu.  
  
  Toto je samostatný návodu. Po dokončení tohoto návodu, můžete zvýšit položky projektu tak, že přidáte průvodce k šabloně položky. Další informace najdete v tématu [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Můžete si stáhnout ukázky z [Githubu](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , který ukazuje, jak vytvořit vlastní aktivity pracovního postupu.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat následující komponenty na vývojovém počítači k dokončení tohoto návodu:  
  
- Podporované vydání systému Microsoft Windows, SharePoint a Visual Studio.
  
- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Tento návod používá **projekt VSIX** šablony v sadě SDK k vytvoření balíčku VSIX k nasazení položky projektu. Další informace najdete v tématu [rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znalost následujících konceptů je užitečná, ale není požadována k dokončení návodu:  
  
- Vlastní akce v Sharepointu. Další informace najdete v tématu [vlastní akce](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
- Šablony položek v sadě Visual Studio. Další informace najdete v tématu [vytváření projektů a šablon položek](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Vytváření projektů
 K dokončení tohoto návodu, budete muset vytvořit tři projekty:  
  
- Projekt VSIX. Tento projekt vytvoří balíčku VSIX k nasazení položky projektu služby SharePoint.  
  
- Projekt šablony položky. Tento projekt vytvoří šablonu položky, který slouží k přidání položky projektu služby SharePoint do projektu služby SharePoint.  
  
- Projekt knihovny tříd. Tento projekt implementuje rozšíření sady Visual Studio, která definuje chování položky projektu služby SharePoint.  
  
  Začněte postup vytvořením projektů.  
  
#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3.  V seznamu v horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** zaškrtnuto.  
  
4.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
    > [!NOTE]  
    >  **Rozšiřitelnost** uzel je dostupný jenom v případě, že nainstalujete Visual Studio SDK. Další informace najdete v oddílu požadavky dříve v tomto tématu.  
  
5.  Zvolte **projekt VSIX** šablony.  
  
6.  V **název** zadejte **CustomActionProjectItem**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **CustomActionProjectItem** projektu **Průzkumníka řešení**.  
  
#### <a name="to-create-the-item-template-project"></a>Chcete-li vytvořit šablonu položky projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V seznamu v horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** zaškrtnuto.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzly a klikněte na tlačítko **rozšiřitelnost** uzlu.  
  
4.  V seznamu šablon projektu vyberte **C# šablonu položky** nebo **šablony položky Visual Basic** šablony.  
  
5.  V **název** zadejte **ItemTemplate**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **ItemTemplate** projektu do řešení.  
  
#### <a name="to-create-the-extension-project"></a>Chcete-li vytvořit projekt rozšíření  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel řešení, zvolte **přidat**a klikněte na tlačítko **nový projekt**.  
  
2.  V seznamu v horní části **nový projekt** dialogové okno pole, ujistěte se, že **rozhraní .NET Framework 4.5** zaškrtnuto.  
  
3.  V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** uzlů, zvolte **Windows** uzel a klikněte na tlačítko  **Knihovna tříd** šablony projektu.  
  
4.  V **název** zadejte **ProjectItemDefinition**a klikněte na tlačítko **OK** tlačítko.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá **ProjectItemDefinition** projektu do řešení a otevře soubor výchozího kódu Class1.  
  
5.  Odstraňte soubor kódu Class1 z projektu.  
  
## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Než napíšete kód, který definuje typ položky projektu služby SharePoint, budete muset přidat soubory kódu a odkazy na sestavení do projektu rozšíření.  
  
#### <a name="to-configure-the-project"></a>Konfigurace projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **ProjectItemDefinition** projektu, zvolte **přidat**, klikněte na tlačítko **nová položka**.  
  
2.  V seznamu položek projektu, zvolte **souboru s kódem**.  
  
3.  V **název** zadejte název **CustomAction** příslušnou příponu názvu souboru a klikněte na tlačítko **přidat** tlačítko.  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku **ProjectItemDefinition** projektu a klikněte na tlačítko **přidat odkaz**.  
  
5.  V **správce odkazů - ProjectItemDefinition** dialogového okna zvolte **sestavení** uzel a klikněte na tlačítko **Framework** uzlu.  
  
6.  Zaškrtněte políčko vedle každé následující sestavení:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Zvolte **rozšíření** uzlu, zaškrtněte políčko vedle Microsoft.VisualStudio.Sharepoint sestavení a klikněte na tlačítko **OK** tlačítko.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Definujte nový typ položky projektu SharePoint
 Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní k definování chování novému typu položky projektu. Toto rozhraní implementujte, kdykoli budete chtít definovat nový typ položky projektu.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Chcete-li definovat novému typu položky projektu SharePoint  
  
1.  V projektu ProjectItemDefinition otevřete soubor kódu CustomAction.  
  
2.  Nahraďte kód v tomto souboru následujícím kódem.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Vytvoření ikony pro položku projektu v Průzkumníku řešení
 Když vytvoříte vlastní položky projektu služby SharePoint, můžete přidružit image (ikona nebo rastrový obrázek) s položkou projektu. Tento obrázek se zobrazí vedle položky projektu v **Průzkumníka řešení**.  
  
 V následujícím postupu vytvoříte ikonu pro položku projektu a vložení ikonu sestavení rozšíření. Tato ikona se odkazuje <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> z `CustomActionProjectItemTypeProvider` třídu, která jste vytvořili dříve.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Chcete-li vytvořit vlastní ikonu pro položku projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **ProjectItemDefinition** projektu, zvolte **přidat**a klikněte na tlačítko **novou položku...** .  
  
2.  V seznamu položek projektu, zvolte **soubor ikony** položky.  
  
    > [!NOTE]  
    >  V projektech Visual Basicu, je nutné vybrat **Obecné** uzel k zobrazení **soubor ikony** položky.  
  
3.  V **název** zadejte **CustomAction_SolutionExplorer.ico**a klikněte na tlačítko **přidat** tlačítko.  
  
     Nová ikona se otevře v **Editor obrázků**.  
  
4.  Rozměr 16 × 16 verze souboru s ikonou upravte tak, aby byly návrhu můžete rozpoznat a uložte soubor ikony.  
  
5.  V **Průzkumníka řešení**, zvolte **CustomAction_SolutionExplorer.ico**.  
  
6.  V **vlastnosti** okna, klikněte na šipku vedle položky **akce sestavení** vlastnost.  
  
7.  V zobrazeném seznamu zvolte **integrovaný prostředek**.  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku návodu je celý kód pro položky projektu v projektu. Sestavte projekt a ověřte, že se zkompiluje bez chyb.  
  
#### <a name="to-build-your-project"></a>K sestavení projektu  
  
1.  Otevřete místní nabídku **ProjectItemDefinition** projekt a zvolte **sestavení**.  
  
## <a name="create-a-visual-studio-item-template"></a>Vytvoření šablony položky sady Visual Studio
 Pokud chcete povolit ostatním vývojářům použít vaši položku projektu, musíte vytvořit šablonu projektu nebo šablony položky. Vývojáři použít tyto šablony v sadě Visual Studio k vytvoření instance položky projektu tak, že vytvoříte nový projekt nebo přidáním položky do existujícího projektu. V tomto návodu použijte ke konfiguraci položky projektu projekt ItemTemplate.  
  
#### <a name="to-create-the-item-template"></a>Chcete-li vytvořit šablonu položky  
  
1.  Odstraňte soubor kódu Class1 z projektu ItemTemplate.  
  
2.  V projektu ItemTemplate, otevřete *ItemTemplate.vstemplate* souboru.  
  
3.  Nahraďte obsah souboru následující kód XML a pak uložte a zavřete soubor.  
  
    > [!NOTE]  
    >  Následující kód XML je k šabloně položky Visual C#. Pokud vytváříte šablonu položky Visual Basic, nahraďte hodnotu `ProjectType` element s `VisualBasic`.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Tento soubor definuje obsah a chování šablony položky. Další informace o obsahu tohoto souboru najdete v tématu [Visual Studio odkaz na schéma šablon](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku **ItemTemplate** projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.  
  
5.  V **přidat novou položku** dialogového okna zvolte **textový soubor** šablony.  
  
6.  V **název** zadejte **CustomAction.spdata**a klikněte na tlačítko **přidat** tlačítko.  
  
7.  Přidejte následující kód XML do *CustomAction.spdata* souboru a pak uložte a zavřete soubor.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Tento soubor obsahuje informace o souborech, které jsou obsaženy v položce projektu. `Type` Atribut `ProjectItem` element musí být nastaven na stejný řetězec, který je předán <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> na definici položky projektu ( `CustomActionProjectItemTypeProvider` třídy, které jste vytvořili dříve v tomto názorném postupu). Další informace o obsahu *.spdata* soubory, naleznete v tématu [referenční dokumentace schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  V **Průzkumníka řešení**, otevřete místní nabídku **ItemTemplate** projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.  
  
9. V **přidat novou položku** dialogového okna zvolte **soubor XML** šablony.  
  
10. V **název** zadejte **Elements.xml**a klikněte na tlačítko **přidat** tlačítko.  
  
11. Nahraďte obsah *Elements.xml* souboru následující kód XML a pak uložte a zavřete soubor.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Tento soubor definuje vlastní výchozí akci, která vytvoří položku nabídky na **Akce webu** nabídku z webu služby SharePoint. Po kliknutí na položku nabídky, v zadaná adresa URL `UrlAction` element otevře ve webovém prohlížeči. Další informace o elementech XML slouží k definování vlastní akci najdete v tématu [definice vlastní akce](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Volitelně můžete otevřít *ItemTemplate.ico* soubor a upravit ji tak, aby byly k návrhu, který dokáže rozpoznat. Tato ikona se zobrazí vedle položky projektu v **přidat novou položku** dialogové okno.  
  
13. V **Průzkumníka řešení**, otevřete místní nabídku **ItemTemplate** projektu a klikněte na tlačítko **uvolnit projekt**.  
  
14. Otevřete místní nabídku **ItemTemplate** projekt znovu a klikněte na tlačítko **upravit ItemTemplate.csproj** nebo **upravit ItemTemplate.vbproj**.  
  
15. Vyhledejte následující `VSTemplate` element v souboru projektu.  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Nahraďte `VSTemplate` element s následující kód XML a poté uložit a zavřít soubor.  
  
    ```xml  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Prvek určuje další složky v cestě, pod kterým šablona položky je vytvořen při sestavení projektu. Složky tady zadané, ujistěte se, že šablonu položky bude k dispozici pouze v případě, že zákazníci otevřít **přidat novou položku** dialogového okna rozbalte **SharePoint** uzel a klikněte na tlačítko **2010**  uzlu.  
  
17. V **Průzkumníka řešení**, otevřete místní nabídku **ItemTemplate** projektu a klikněte na tlačítko **znovu načíst projekt**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Vytvoření balíčku VSIX k nasazení položky projektu
 Pokud chcete nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejprve nakonfigurujte VSIX balíček úpravou souboru source.extension.vsixmanifest, který je součástí projektu VSIX. Potom vytvořte VSIX balíček vytvořením řešení.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **source.extension.vsixmanifest** souboru v projektu CustomActionProjectItem a klikněte na tlačítko **otevřete**.  
  
     Visual Studio otevře soubor v editoru manifestu. Soubor source.extension.vsixmanifest je základem pro soubor extension.vsixmanifest, které vyžadují všechny balíčky VSIX. Další informace o tomto souboru najdete v tématu [odkaz 1.0 schématu rozšíření VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  V **název produktu** zadejte **vlastní položky projektu akce**.  
  
3.  V **Autor** zadejte **Contoso**.  
  
4.  V **popis** zadejte **položky projektu služby SharePoint, která představuje vlastní akci**.  
  
5.  Na **prostředky** , vyberte **nový** tlačítko.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
6.  V **typ** klikněte na položku **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `ItemTemplate` element v souboru extension.vsixmanifest. Tento prvek určuje podsložce v balíčku souboru VSIX, který obsahuje šablonu položky projektu. Další informace najdete v tématu [ItemTemplate – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).  
  
7.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
8.  V **projektu** klikněte na položku **ItemTemplate**a klikněte na tlačítko **OK** tlačítko.  
  
9. V **prostředky** , vyberte **nový** tlačítko znovu.  
  
     **Přidat nové aktivum** zobrazí se dialogové okno.  
  
10. V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Tato hodnota odpovídá `MefComponent` element v souboru extension.vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku souboru VSIX. Další informace najdete v tématu [MEFComponent – Element (VSX schéma)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
11. V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
12. V **projektu** klikněte na položku **ProjectItemDefinition**.  
  
13. Zvolte **OK** tlačítko.  
  
14. V panelu nabídky zvolte **sestavení** > **sestavit řešení**a ujistěte se, že se projekt zkompiluje bez chyb.  
  
15. Ujistěte se, že výstupní složka sestavení pro projekt CustomActionProjectItem obsahuje soubor CustomActionProjectItem.vsix.  
  
     Výchozí je výstupní složka sestavení... složky \Bin\Debug ve složce, která obsahuje projekt CustomActionProjectItem.  
  
## <a name="test-the-project-item"></a>Testování položky projektu
 Nyní jste připraveni k testování položky projektu. Nejprve spusťte ladění řešení CustomActionProjectItem v experimentální instanci sady Visual Studio. Pak test **vlastní akce** položky projektu v projektu služby SharePoint v experimentální instanci sady Visual Studio. Nakonec sestavte a spusťte projekt SharePoint, chcete-li ověřit, že vlastní akce funguje podle očekávání.  
  
#### <a name="to-start-debugging-the-solution"></a>Spusťte ladění řešení  
  
1.  Restartujte sadu Visual Studio s přihlašovacími údaji správce a pak otevřete CustomActionProjectItem řešení.  
  
2.  Otevřete soubor kódu CustomAction a na první řádek kódu přidejte zarážku `InitializeType` metody.  
  
3.  Zvolte **F5** klíč pro spuštění ladění.  
  
     Visual Studio nainstaluje rozšíření %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom akce Project Item\1. 0 a spustí experimentální instanci sady Visual Studio. Položku projektu budete testovat v této instanci aplikace Visual Studio.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>K otestování položky projektu v sadě Visual Studio  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **souboru** > **nový** > **projektu**.  
  
2.  Rozbalte **Visual C#** nebo **jazyka Visual Basic** (v závislosti na jazyk, který podporuje vaši šablonu položky), rozbalte **SharePoint**a klikněte na tlačítko **2010**  uzlu.  
  
3.  V seznamu šablon projektu vyberte **projektu služby SharePoint 2010**.  
  
4.  V **název** zadejte **CustomActionTest**a klikněte na tlačítko **OK** tlačítko.  
  
5.  V **Průvodce přizpůsobením SharePoint**, zadejte adresu URL webu, který chcete použít pro ladění a klikněte na tlačítko **Dokončit** tlačítko.  
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku pro uzel projektu, zvolte **přidat**a klikněte na tlačítko **nová položka**.  
  
7.  V **přidat novou položku** dialogového okna zvolte **2010** pod uzlem **SharePoint** uzlu.  
  
     Ověřte, že **vlastní akce** položky se zobrazí v seznamu položek projektu.  
  
8.  Zvolte **vlastní akce** položku a klikněte na tlačítko **přidat** tlačítko.  
  
     Visual Studio přidá položku s názvem **CustomAction1** projekt a otevře *Elements.xml* souboru v editoru.  
  
9. Ověřte, že kód ve druhé instanci aplikace Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `InitializeType` metody.  
  
10. Zvolte **F5** klíč a pokračujte v ladění projektu.  
  
11. V experimentální instanci sady Visual Studio v **Průzkumníka řešení**, otevřete místní nabídku **CustomAction1** uzel a klikněte na tlačítko **návrháře zobrazení vlastní akce**.  
  
12. Ověřte, zda se zobrazí okno se zprávou a klikněte na tlačítko **OK** tlačítko.  
  
     Tuto nabídku můžete použít k poskytování dalších možností nebo příkazy pro vývojáře, jako je například zobrazení návrháře pro vlastní akci.  
  
13. V panelu nabídky zvolte **zobrazení** > **výstup**.  
  
     **Výstup** otevře se okno.  
  
14. V **Průzkumníka řešení**, otevřete místní nabídku **CustomAction1** položku a pak změňte její název na **MyCustomAction**.  
  
     V **výstup** okně zobrazí potvrzovací zpráva. Tato zpráva je vytvořená systémem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> obslužná rutina události, kterou jste definovali v `CustomActionProjectItemTypeProvider` třídy. Dokáže zpracovat této události a dalších událostí položky projektu k implementaci vlastní chování, když vývojáři změní položku projektu.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Testování vlastní akce v Sharepointu  
  
1.  V experimentální instanci sady Visual Studio, otevřete *Elements.xml* soubor, který je podřízeným prvkem **MyCustomAction** položky projektu.  
  
2.  V *Elements.xml* soubor, proveďte následující změny a pak soubor uložte:  
  
    -   V `CustomAction` element, nastaven `Id` atributu na identifikátor GUID nebo jiný jedinečný řetězec jako v následujícím příkladu:  
  
        ```xml  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   V `CustomAction` element, nastaven `Title` atribut jako v následujícím příkladu:  
  
        ```xml  
        Title="SharePoint Developer Center"  
        ```  
  
    -   V `CustomAction` element, nastaven `Description` atribut jako v následujícím příkladu:  
  
        ```xml  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   V `UrlAction` element, nastaven `Url` atribut jako v následujícím příkladu:  
  
        ```xml  
        Url="https://docs.microsoft.com/sharepoint/dev/"  
        ```  
  
3.  Zvolte **F5** klíč.  
  
     Vlastní akce se zabalí a nasadí na Sharepointovém webu, který je zadán v **adresa URL webu** vlastnost projektu. Webový prohlížeč otevře výchozí stránku webu.  
  
    > [!NOTE]  
    >  Pokud **ladění skriptů zakázáno** dialogové okno se zobrazí, zvolte **Ano** tlačítka pokračovat v ladění projektu.  
  
4.  Na **Akce webu** nabídce zvolte **středisko pro vývojáře služby SharePoint**, ověřte, že v prohlížeči se otevře web https://docs.microsoft.com/sharepoint/dev/a pak zavřete webový prohlížeč.  
  
## <a name="clean-up-the-development-computer"></a>Vyčištění vývojovém počítači
 Po dokončení testování položku projektu, odeberte šablony položky projektu z experimentální instanci sady Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Chcete-li vyčistit vývojovém počítači  
  
1.  V experimentální instanci sady Visual Studio na panelu nabídek zvolte **nástroje** > **rozšíření a aktualizace**.  
  
     **Rozšíření a aktualizace** zobrazí se dialogové okno.  
  
2.  V seznamu rozšíření zvolte **vlastní položky projektu akce**a klikněte na tlačítko **odinstalovat** tlačítko.  
  
3.  V dialogovém okně, které se zobrazí, zvolte **Ano** potvrďte, že chcete odinstalovat rozšíření.  
  
4.  Zvolte **restartovat nyní** tlačítko pro dokončení odinstalace.  
  
5.  Ukončete experimentální instanci sady Visual Studio a instance, ve kterém je otevřen CustomActionProjectItem řešení.  
  
## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto postupu můžete přidat průvodce k šabloně položky. Když uživatel přidá vlastní akce položky projektu do projektu služby SharePoint, Průvodce shromažďuje informace o akci (třeba jeho umístění a adresa URL pro navigaci při akci je vybrán) a přidá tyto informace *Elements.xml*soubor v nové položce projektu. Další informace najdete v tématu [návod: vytvoření vlastní akce položky projektu pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>Viz také:
 [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Vytváření šablon položek a projektů pro položky projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Odkaz na schéma šablon sady Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)   
 [Vytvoření ikony nebo jiného obrázku &#40;Editor obrázků pro ikony&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
