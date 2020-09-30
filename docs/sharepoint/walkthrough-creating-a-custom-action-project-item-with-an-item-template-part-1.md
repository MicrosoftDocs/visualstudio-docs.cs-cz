---
title: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5cdf574d17e63e1ef4906c629d43f5f928784d01
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585560"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1
  Systém projektu služby SharePoint v aplikaci Visual Studio můžete roztáhnout tak, že vytvoříte vlastní typy položek projektu. V tomto návodu vytvoříte položku projektu, kterou lze přidat do projektu služby SharePoint a vytvořit tak vlastní akci na webu služby SharePoint. Vlastní akce přidá položku nabídky do nabídky **Akce webu** na webu služby SharePoint.

 Tento názorný postup ukazuje následující úlohy:

- Vytvoření rozšíření aplikace Visual Studio, které definuje nový typ položky projektu služby SharePoint pro vlastní akci. Nový typ položky projektu implementuje několik vlastních funkcí:

  - Místní nabídka, která slouží jako výchozí bod pro další úkoly týkající se položky projektu, jako je například zobrazení návrháře pro vlastní akci v aplikaci Visual Studio.

  - Kód, který se spustí, když vývojář změní některé vlastnosti položky projektu a projektu, který jej obsahuje.

  - Vlastní ikona, která se zobrazí vedle položky projektu v **Průzkumník řešení**.

- Vytvoření šablony položky sady Visual Studio pro položku projektu.

- Sestavení balíčku rozšíření sady Visual Studio (VSIX) pro nasazení šablony položky projektu a sestavení rozšíření.

- Ladění a testování položky projektu.

  Toto je samostatný návod. Po dokončení tohoto návodu můžete vylepšit položku projektu přidáním průvodce do šablony položky. Další informace naleznete v tématu [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Ukázku si můžete stáhnout z [GitHubu](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , kde se dozvíte, jak vytvořit vlastní aktivity pro pracovní postup.

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto Názorného postupu potřebujete na vývojovém počítači následující komponenty:

- Podporované edice Microsoft Windows, SharePointu a sady Visual Studio.

- Hodnota [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] Tento návod používá šablonu **projektu VSIX** v sadě SDK k vytvoření balíčku VSIX pro nasazení položky projektu. Další informace najdete v tématu věnovaném [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znalosti následujících konceptů jsou užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Vlastní akce v SharePointu Další informace najdete v tématu [vlastní akce](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Šablony položek v aplikaci Visual Studio. Další informace naleznete v tématu [vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Vytváření projektů
 Chcete-li dokončit tento návod, je nutné vytvořit tři projekty:

- Projekt VSIX. Tento projekt vytvoří balíček VSIX pro nasazení položky SharePointového projektu.

- Projekt šablony položky Tento projekt vytvoří šablonu položky, kterou lze použít k přidání položky projektu služby SharePoint do projektu služby SharePoint.

- Projekt knihovny tříd. Tento projekt implementuje rozšíření aplikace Visual Studio, které definuje chování položky SharePointového projektu.

  Spusťte návod vytvořením projektů.

#### <a name="to-create-the-vsix-project"></a>Vytvoření projektu VSIX

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

3. V seznamu v horní části dialogového okna **Nový projekt** se ujistěte, že je vybrána možnost **.NET Framework 4,5** .

4. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

    > [!NOTE]
    > Uzel **rozšiřitelnosti** je k dispozici pouze v případě, že instalujete sadu Visual Studio SDK. Další informace najdete v části požadavky výše v tomto tématu.

5. Vyberte šablonu **projektu VSIX** .

6. Do pole **název** zadejte **CustomActionProjectItem**a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **CustomActionProjectItem** do **Průzkumník řešení**.

#### <a name="to-create-the-item-template-project"></a>Vytvoření projektu šablony položky

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat**a pak zvolte možnost **Nový projekt**.

2. V seznamu v horní části dialogového okna **Nový projekt** se ujistěte, že je vybrána možnost **.NET Framework 4,5** .

3. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** a pak zvolte uzel **rozšiřitelnost** .

4. V seznamu šablon projektů vyberte šablonu **položky C#** nebo šablona **šablony Visual Basic položky** .

5. Do pole **název** zadejte **ItemTemplate**a pak klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Přidá do řešení projekt **ItemTemplate** .

#### <a name="to-create-the-extension-project"></a>Vytvoření projektu rozšíření

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení, zvolte možnost **Přidat**a pak zvolte možnost **Nový projekt**.

2. V seznamu v horní části dialogového okna **Nový projekt** se ujistěte, že je vybrána možnost **.NET Framework 4,5** .

3. V dialogovém okně **Nový projekt** rozbalte uzly **Visual C#** nebo **Visual Basic** , zvolte uzel **Windows** a pak zvolte šablonu projektu **Knihovna tříd** .

4. Do pole **název** zadejte **ProjectItemDefinition**a poté klikněte na tlačítko **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] přidá projekt **ProjectItemDefinition** do řešení a otevře soubor Default Class1 Code.

5. Odstraňte soubor kódu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurace projektu rozšíření
 Předtím, než napíšete kód pro definování typu položky projektu služby SharePoint, je nutné přidat soubory kódu a odkazy na sestavení do projektu rozšíření.

#### <a name="to-configure-the-project"></a>Konfigurace projektu

1. V **Průzkumník řešení**otevřete místní nabídku projektu **ProjectItemDefinition** , zvolte možnost **Přidat**a pak zvolte možnost **Nová položka**.

2. V seznamu položek projektu vyberte možnost **soubor kódu**.

3. Do pole **název** zadejte název **CustomAction** s odpovídající příponou názvu souboru a pak klikněte na tlačítko **Přidat** .

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ProjectItemDefinition** a pak zvolte možnost **Přidat odkaz**.

5. V dialogovém okně **Správce odkazů – ProjectItemDefinition** zvolte uzel **sestavení** a pak zvolte uzel **rozhraní** .

6. Zaškrtněte políčko vedle každého z následujících sestavení:

    - System. ComponentModel. složení

    - System. Windows. Forms

7. Zvolte uzel **rozšíření** , zaškrtněte políčko vedle sestavení Microsoft. VisualStudio. SharePoint a pak klikněte na tlačítko **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Definovat nový typ položky projektu služby SharePoint
 Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> rozhraní pro definování chování nového typu položky projektu. Implementujte toto rozhraní vždy, když chcete definovat nový typ položky projektu.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Definování nového typu položky projektu služby SharePoint

1. V projektu ProjectItemDefinition otevřete soubor s kódem CustomAction.

2. Nahraďte kód v tomto souboru následujícím kódem.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Vytvořit ikonu pro položku projektu v Průzkumník řešení
 Když vytvoříte vlastní položku projektu služby SharePoint, můžete k položce projektu přidružit obrázek (ikonu nebo rastrový obrázek). Tento obrázek se zobrazí vedle položky projektu v **Průzkumník řešení**.

 V následujícím postupu vytvoříte ikonu pro položku projektu a vložíte ikonu do sestavení rozšíření. Na tuto ikonu odkazuje <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> `CustomActionProjectItemTypeProvider` třída, kterou jste vytvořili dříve.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Vytvoření vlastní ikony pro položku projektu

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ProjectItemDefinition** , zvolte možnost **Přidat**a pak zvolte možnost **Nová položka...**.

2. V seznamu položek projektu vyberte položku **soubor ikony** .

    > [!NOTE]
    > V Visual Basic projekty je nutné zvolit uzel **Obecné** pro zobrazení položky **souboru ikony** .

3. Do pole **název** zadejte **CustomAction_SolutionExplorer. ico**a pak klikněte na tlačítko **Přidat** .

     Nová ikona se otevře v **editoru obrázků**.

4. Upravte verzi 16x16 souboru ikony tak, aby měla návrh, který můžete rozpoznat a pak soubor ikony uložte.

5. V **Průzkumník řešení**vyberte **CustomAction_SolutionExplorer. ico**.

6. V okně **vlastnosti** klikněte na šipku vedle vlastnosti **Akce sestavení** .

7. V seznamu, který se zobrazí, vyberte možnost **Integrovaný prostředek**.

## <a name="checkpoint"></a>CheckPoint
 V tomto okamžiku v tomto návodu je veškerý kód položky projektu nyní v projektu. Sestavte projekt, aby se ověřilo, že se zkompiluje bez chyb.

#### <a name="to-build-your-project"></a>Sestavení projektu

1. Otevřete místní nabídku projektu **ProjectItemDefinition** a vyberte možnost **sestavit**.

## <a name="create-a-visual-studio-item-template"></a>Vytvoření šablony položky v aplikaci Visual Studio
 Chcete-li povolit jiným vývojářům používání položky projektu, je nutné vytvořit šablonu projektu nebo šablonu položky. Vývojáři používají tyto šablony v aplikaci Visual Studio k vytvoření instance položky projektu vytvořením nového projektu nebo přidáním položky do existujícího projektu. Pro tento návod použijte projekt ItemTemplate ke konfiguraci položky projektu.

#### <a name="to-create-the-item-template"></a>Vytvoření šablony položky

1. Odstraňte soubor kódu Class1 z projektu ItemTemplate.

2. V projektu ItemTemplate otevřete soubor *ItemTemplate. vstemplate* .

3. Nahraďte obsah souboru následujícím kódem XML a uložte a zavřete soubor.

    > [!NOTE]
    > Následující kód XML je pro šablonu položky Visual C#. Pokud vytváříte šablonu Visual Basic položky, nahraďte hodnotu `ProjectType` prvku hodnotou `VisualBasic` .

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

     Tento soubor definuje obsah a chování šablony položky. Další informace o obsahu tohoto souboru naleznete v tématu Referenční dokumentace [schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

4. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ItemTemplate** , zvolte možnost **Přidat**a poté možnost **Nová položka**.

5. V dialogovém okně **Přidat novou položku** vyberte šablonu **textový soubor** .

6. Do pole **název** zadejte **CustomAction. spdata**a pak klikněte na tlačítko **Přidat** .

7. Přidejte následující kód XML do souboru *CustomAction. spdata* a pak soubor uložte a zavřete.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Tento soubor obsahuje informace o souborech, které jsou obsaženy v položce projektu. `Type`Atribut `ProjectItem` elementu musí být nastaven na stejný řetězec, který je předán do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> definice položky projektu ( `CustomActionProjectItemTypeProvider` třída, kterou jste vytvořili dříve v tomto návodu). Další informace o obsahu souborů *. spdata* naleznete v tématu Referenční dokumentace [schématu položek projektu služby SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ItemTemplate** , zvolte možnost **Přidat**a poté možnost **Nová položka**.

9. V dialogovém okně **Přidat novou položku** vyberte šablonu **souboru XML** .

10. Do pole **název** zadejte **Elements.xml**a pak klikněte na tlačítko **Přidat** .

11. Obsah souboru *Elements.xml* nahraďte následujícím kódem XML a pak soubor uložte a zavřete.

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

     Tento soubor definuje výchozí vlastní akci, která vytvoří položku nabídky v nabídce **Akce webu** webu služby SharePoint. Když uživatel zvolí položku nabídky, otevře se v webovém prohlížeči adresa URL zadaná v `UrlAction` elementu. Další informace o prvcích XML, které lze použít k definování vlastní akce, naleznete v tématu [Custom Action definitions](/sharepoint/dev/schema/custom-action-definition-schema).

12. Volitelně otevřete soubor *ItemTemplate. ico* a upravte jej tak, aby měl návrh, který můžete rozpoznat. Tato ikona se zobrazí vedle položky projektu v dialogovém okně **Přidat novou položku** .

13. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ItemTemplate** a pak zvolte možnost **Uvolnit projekt**.

14. Znovu otevřete místní nabídku pro projekt **ItemTemplate** a pak zvolte **Upravit ItemTemplate. csproj** nebo **Upravit ItemTemplate. vbproj**.

15. `VSTemplate`V souboru projektu vyhledejte následující element.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Nahraďte tento `VSTemplate` prvek následujícím kódem XML a uložte a zavřete soubor.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Element určuje další složky v cestě, kde je vytvořena šablona položky při sestavování projektu. Složky, které jsou zde uvedeny, zajistí, že šablona položky bude k dispozici pouze v případě, že zákazníci otevřou dialogové okno **Přidat novou položku** , rozbalíte uzel **služby SharePoint** a pak zvolíte uzel **2010** .

17. V **Průzkumník řešení**otevřete místní nabídku pro projekt **ItemTemplate** a pak zvolte možnost **znovu načíst projekt**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Vytvoření balíčku VSIX pro nasazení položky projektu
 Chcete-li nasadit rozšíření, použijte VSIX projekt ve vašem řešení k vytvoření balíčku VSIX. Nejdřív nakonfigurujte balíček VSIX úpravou souboru source. extension. vsixmanifest, který je zahrnutý v projektu VSIX. Pak vytvořte balíček VSIX sestavením řešení.

#### <a name="to-configure-and-create-the-vsix-package"></a>Konfigurace a vytvoření balíčku VSIX

1. V **Průzkumník řešení**otevřete místní nabídku pro soubor **source. extension. vsixmanifest** v projektu CustomActionProjectItem a pak zvolte možnost **otevřít**.

     Visual Studio otevře soubor v editoru manifestu. Soubor source. extension. vsixmanifest je základem pro soubor Extension. vsixmanifest, který vyžaduje všechny balíčky VSIX. Další informace o tomto souboru najdete v referenčních informacích k [schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Do pole **název produktu** zadejte **vlastní položka projektu akce**.

3. Do pole **Autor** zadejte **Contoso**.

4. Do pole **Popis** zadejte **položku sharepointového projektu, která představuje vlastní akci**.

5. Na kartě **assets (prostředky** ) klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

6. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. ItemTemplate**.

    > [!NOTE]
    > Tato hodnota odpovídá `ItemTemplate` prvku v souboru extension. vsixmanifest. Tento prvek identifikuje podsložku v balíčku VSIX, který obsahuje šablonu položky projektu. Další informace naleznete v tématu [element ItemTemplate (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

8. V seznamu **projekt** zvolte možnost **ItemTemplate**a pak klikněte na tlačítko **OK** .

9. Na kartě **assety (prostředky** ) znovu klikněte na tlačítko **Nový** .

     Zobrazí se dialogové okno **Přidat nový prostředek** .

10. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Tato hodnota odpovídá `MefComponent` prvku v souboru extension. vsixmanifest. Tento prvek určuje název sestavení rozšíření v balíčku VSIX. Další informace naleznete v tématu [MefComponent element (VSX Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

12. V seznamu **projekt** vyberte možnost **ProjectItemDefinition**.

13. Klikněte na tlačítko **OK** .

14. V panelu nabídek zvolte **sestavit**  >  **sestavení řešení**a pak se ujistěte, že se projekt zkompiluje bez chyb.

15. Ujistěte se, že výstupní složka sestavení pro projekt CustomActionProjectItem obsahuje soubor CustomActionProjectItem. VSIX.

     Ve výchozím nastavení je výstupní složka sestavení.. Složka \bin\Debug ve složce, která obsahuje projekt CustomActionProjectItem.

## <a name="test-the-project-item"></a>Testování položky projektu
 Nyní jste připraveni otestovat položku projektu. Nejdřív začněte ladit řešení CustomActionProjectItem v experimentální instanci sady Visual Studio. Pak otestujte položku projektu **vlastní akce** v projektu služby SharePoint v experimentální instanci aplikace Visual Studio. Nakonec sestavte a spusťte projekt služby SharePoint, abyste ověřili, že vlastní akce funguje podle očekávání.

#### <a name="to-start-debugging-the-solution"></a>Spuštění ladění řešení

1. Restartujte Visual Studio s přihlašovacími údaji správce a pak otevřete řešení CustomActionProjectItem.

2. Otevřete soubor kódu CustomAction a pak přidejte zarážku do prvního řádku kódu v `InitializeType` metodě.

3. Kliknutím na klávesu **F5** spusťte ladění.

     Visual Studio nainstaluje rozšíření do projektu akce%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 a spustí experimentální instanci sady Visual Studio. Otestujete položku projektu v této instanci aplikace Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Testování položky projektu v aplikaci Visual Studio

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. Rozbalte položku **Visual C#** nebo **Visual Basic** (v závislosti na jazyku, který vaše šablona položky podporuje), rozbalte položku **SharePoint**a pak zvolte uzel **2010** .

3. V seznamu šablon projektu vyberte **projekt SharePoint 2010**.

4. Do pole **název** zadejte **CustomActionTest**a poté klikněte na tlačítko **OK** .

5. V **Průvodci vlastním nastavením služby SharePoint**zadejte adresu URL webu, který chcete použít pro ladění, a poté klikněte na tlačítko **Dokončit** .

6. V **Průzkumník řešení**otevřete místní nabídku uzlu projektu, zvolte možnost **Přidat**a poté **položku Nová položka**.

7. V dialogovém okně **Přidat novou položku** vyberte uzel **2010** pod uzlem **služby SharePoint** .

     Ověřte, zda se položka **vlastní akce** zobrazuje v seznamu položek projektu.

8. Zvolte položku **vlastní akce** a poté klikněte na tlačítko **Přidat** .

     Visual Studio přidá do projektu položku s názvem **CustomAction1** a otevře soubor *Elements.xml* v editoru.

9. Ověřte, zda se kód v jiné instanci sady Visual Studio zastaví na zarážce, kterou jste nastavili dříve v `InitializeType` metodě.

10. Kliknutím na klávesu **F5** pokračujte v ladění projektu.

11. V experimentální instanci aplikace Visual Studio v **Průzkumník řešení**otevřete místní nabídku uzlu **CustomAction1** a pak zvolte **Zobrazit vlastní Návrhář akcí**.

12. Ověřte, že se zobrazí okno se zprávou, a pak klikněte na tlačítko **OK** .

     Pomocí této místní nabídky můžete poskytnout další možnosti nebo příkazy pro vývojáře, jako je například zobrazení návrháře pro vlastní akci.

13. Na panelu nabídek vyberte možnost **Zobrazit**  >  **výstup**.

     Otevře se okno **výstup** .

14. V **Průzkumník řešení**otevřete místní nabídku pro položku **CustomAction1** a změňte její název na **MyCustomAction**.

     V okně **výstup** se zobrazí potvrzovací zpráva. Tato zpráva je zapsána <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> obslužnou rutinou události, kterou jste definovali ve `CustomActionProjectItemTypeProvider` třídě. Tuto událost a další události položky projektu můžete zpracovat pro implementaci vlastního chování, když vývojář změní položku projektu.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Testování vlastní akce v SharePointu

1. V experimentální instanci aplikace Visual Studio otevřete *Elements.xml* soubor, který je podřízenou položkou projektu **MyCustomAction** .

2. V *Elements.xml* souboru proveďte následující změny a pak soubor uložte:

    - V `CustomAction` elementu nastavte `Id` atribut na identifikátor GUID nebo nějaký jiný jedinečný řetězec, jak ukazuje následující příklad:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - V `CustomAction` elementu nastavte `Title` atribut tak, jak ukazuje následující příklad:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - V `CustomAction` elementu nastavte `Description` atribut tak, jak ukazuje následující příklad:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - V `UrlAction` elementu nastavte `Url` atribut tak, jak ukazuje následující příklad:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Klikněte na klávesu **F5** .

     Vlastní akce je zabalená a nasazená na SharePointový web, který je zadaný ve vlastnosti **Adresa URL webu** projektu. Webový prohlížeč otevře výchozí stránku tohoto webu.

    > [!NOTE]
    > Pokud se zobrazí dialogové okno **ladění skriptu zakázáno** , klikněte na tlačítko **Ano** a pokračujte v ladění projektu.

4. V nabídce **Akce webu** zvolte centrum pro **vývojáře služby SharePoint**, ověřte, že prohlížeč otevře web https://docs.microsoft.com/sharepoint/dev/ a pak zavře webový prohlížeč.

## <a name="clean-up-the-development-computer"></a>Vyčištění vývojového počítače
 Po dokončení testování položky projektu odeberte šablonu položky projektu z experimentální instance aplikace Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Vyčištění vývojového počítače

1. V experimentální instanci aplikace Visual Studio, na panelu nabídek vyberte **nástroje**  >  **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte **položku projekt vlastní akce**a poté klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Ano** a potvrďte tak, že chcete rozšíření odinstalovat.

4. Kliknutím na tlačítko **restartovat nyní** dokončete odinstalaci.

5. Zavřete experimentální instanci sady Visual Studio a instanci, ve které je řešení CustomActionProjectItem otevřené.

## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto návodu můžete přidat průvodce do šablony položky. Když uživatel přidá položku projektu vlastní akce do projektu služby SharePoint, průvodce shromáždí informace o akci (například jeho umístění a adresu URL, na které se má přejít, když je vybrána akce) a přidá tyto informace do souboru *Elements.xml* v nové položce projektu. Další informace naleznete v tématu [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definování vlastních typů položek projektu služby SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Vytváření šablon položek a šablon projektů pro položky projektu služby SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Použití služby projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)
- [Vytvoření ikony nebo jiného obrázku &#40;Editor obrázků pro ikony&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)